# Templated components
*Templated* controls enable the developer to specify a portion of the HTML used to render a container control. The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way. Examples of templated controls include `Repeater` and `DataList`.

Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`. 
A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.
A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.

## Child content
Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering. To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.

*_ChildComponent.razor*

    <div>
	    <div class="alert alert-info">@Title</div>
		    <div class="alert alert-success">
		        @if (ChildContent != null)
		        {
		            <span>@ChildContent</span>
		        }
		        else
		        {
		            <span>Hello</span>
		        }
		    </div>
	    <button class="btn btn-danger"
		     @onclick="OnButtonClick">
			 Click Here
		</button>
	</div>
    @code {
	    [Parameter]
		    public string Title { get; set; }
	    [Parameter]
		    public RenderFragment ChildContent { get; set; }
	    [Parameter]
		    public EventCallback OnButtonClick { get; set; }
    }

A parent component can then supply child content using normal Razor syntax

    @page "/learnBlazor/parentComponent"
    
    <h3>ParentComponent</h3>
    
    <_ChildComponent 
	    OnButtonClick="ShowMessgae" 
	    Title="This is passed as parameter">
        Render Fragment From Parent.
    </_ChildComponent>
    <br />
    <p><b>@messageText</b></p>
    <_ChildComponent 
	    Title="This is passed as parameter">
    </_ChildComponent>
    
    @code {
        public string messageText = "";
        private void ShowMessgae()
        {
            messageText = "button clicked";
        }
    }
