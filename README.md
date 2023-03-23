# Event Handler
In Blazor, we can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`. The `{event}` placeholder represents the name of the event.

Event handlers can accept an optional, event-specific argument to provide more information about the event. For example, mouse events can take a `MouseEventArgs` argument, but it isn’t required.

Instead of referring to a method group for an event handler, can use a lambda expression. A lambda expression allows you to close over other in-scope values. 

[*_IndividualProduct.razor*](https://github.com/Shalini-lodhi/BlazorServer/blob/2_Event_Handlers/BlazorServer_TangyWeb/Pages/LearnBlazor/LearnBlazorComponent/_IndividualComponent.razor)

    <div 
	    class="bg-light border p-2 m-1 col-3" 
	    @onclick="(args)=>LastSelectedProductChange(args, Product.Name)" 
	    style="background-color:white"
    >
    @code 
    {
    [Parameter]
    public EventCallback<string> OnLastSelectedProductChange { get; set; }
    
    private async Task LastSelectedProductChange(MouseEventArgs e, string name)
	    {
	        await OnLastSelectedProductChange.InvokeAsync(name);
	    }
    }
   
   [*ProductDemo.razor*](https://github.com/Shalini-lodhi/BlazorServer/blob/2_Event_Handlers/BlazorServer_TangyWeb/Pages/LearnBlazor/DemoProduct.razor)
  

    @page "/learnBlazor/demoProduct"
    
    <p>Selected Item: @LastSelectedProduct</p>
    <div class="border p-4 mt-2" style="background-color:azure">
    <div class="row">
        @foreach (var prod in Products)
        {
            <_IndividualComponent Product="prod"
                              OnFavoriteUpdated="FavoriteCountUpdate"
                              OnLastSelectedProductChange="SelectedProductUpdate">
            </_IndividualComponent>
        }
    </div>
    @code{
	    private string LastSelectedProduct { get; set; }
	    protected void SelectedProductUpdate(string productName)
	    {
	        LastSelectedProduct = productName;
	    }
    }
