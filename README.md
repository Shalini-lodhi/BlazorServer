# Attribute Mapping

*_AnotherChildComponent.razor*

    <div>
    <h4 class="text-primary pt-3">Child Component</h4>
    <input id="nametemp" @attributes="InputAttributes"/
    </div>
    @code {
    //[Parameter]
    //public string Placeholder { get; set; }
    //[Parameter]
    //public string Required { get; set; }
    //[Parameter]
    //public int MaxLength { get; set; }
    [Parameter]
    public Dictionary<string, object> InputAttributes { get; set; } = new Dictionary<string, object>()
    {
        {"required", "required"},
        {"placeholder", "Enter name from parent"},
        {"maxlength", 5}
    };
    }

*ParentComponent.razor*

    @page "/learnBlazor/parentComponent"
    h3>ParentComponent</h3>
    <_ChildComponent OnButtonClick="ShowMessgae" Title="This is passed as parameter">
    Render Fragment From Parent.
    </_ChildComponent><br /> 
    <p><b>@messageText</b></p>
    <_ChildComponent Title="This is passed as parameter"></_ChildComponent>
    @*<_AnotherChildComponent Placeholder="Your Name" MaxLength="5"></_AnotherChildComponent>*@
    <_AnotherChildComponent InputAttributes="InputAttributesFromParent"></_AnotherChildComponent>
    
    @code {
    public Dictionary<string, object> InputAttributesFromParent { get; set; } = new Dictionary<string, object>()
    {
        {"required", "required"},
        {"placeholder", "Enter name from parent"},
        {"maxlength", 5}
    };
    public string messageText = "";
    private void ShowMessgae()
    {
        messageText = "button clicked";
    }
    }
