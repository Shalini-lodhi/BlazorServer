## Event Call Back

Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`. Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.

In File [_IndividualProduct](https://github.com/Shalini-lodhi/BlazorServer/blob/1_Event_Call_Back/BlazorServer_TangyWeb/Pages/LearnBlazor/LearnBlazorComponent/_IndividualComponent.razor), event call back is done for adding `OnFavoriteUpdate` which update the Favorite product count.

[*_IndividualProduct.razor*](https://github.com/Shalini-lodhi/BlazorServer/blob/1_Event_Call_Back/BlazorServer_TangyWeb/Pages/LearnBlazor/LearnBlazorComponent/_IndividualComponent.razor)

    <input type="checkbox" @onchange="FavoriteUpdated" /> 
    Add to Favorite  
    <br /><br />
    [Parameter]
    public EventCallback<bool> OnFavoriteUpdated { get; set;}
    private async Task FavoriteUpdated(ChangeEventArgs e)
    {
        await OnFavoriteUpdated.InvokeAsync((bool)e.Value);
    }

[*DemoProduct.razor*](https://github.com/Shalini-lodhi/BlazorServer/blob/1_Event_Call_Back/BlazorServer_TangyWeb/Pages/LearnBlazor/DemoProduct.razor)

    @foreach (var prod in Products)
        {
            <_IndividualComponent Product="prod" OnFavoriteUpdated="FavoriteCountUpdate">
            </_IndividualComponent>
        }
    @code 
    {
	    private int SelectedFavoriteCount { get; set; } = 0;
	    List<Demo_Product> Products = new();
	    protected void FavoriteCountUpdate(bool isSelected)
	    {
	        if (isSelected)
	        {
	            SelectedFavoriteCount++;
	        }
	        else if (!isSelected)
	        {
	            SelectedFavoriteCount--;
	        }
	    }
	}
