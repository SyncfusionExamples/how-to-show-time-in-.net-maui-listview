# How to show time value in items in .NET MAUI ListView (SfListView)?

The [.NET MAUI ListView](https://www.syncfusion.com/maui-controls/maui-listview) enables customization of the ItemTemplate to display time values by using [StringFormat](https://learn.microsoft.com/en-us/dotnet/maui/fundamentals/data-binding/string-formatting?view=net-maui-8.0) in data binding.

**XAML**

Bind the **CheckIn** `DateTime` property to a `Label` and apply the **StringFormat** to format the time.

```
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:local="clr-namespace:ListViewMaui"
             xmlns:syncfusion="clr-namespace:Syncfusion.Maui.ListView;assembly=Syncfusion.Maui.ListView"
             x:Class="ListViewMaui.MainPage">

    
 <ContentPage.BindingContext>
     <local:EmployeeViewModel/>
 </ContentPage.BindingContext>

 <ContentPage.Resources>
     <ResourceDictionary>
         <local:DateConverter x:Key="converter"/>
     </ResourceDictionary>
 </ContentPage.Resources>

    <ContentPage.Content>
        <syncfusion:SfListView x:Name="listView" ItemSpacing="1" AutoFitMode="Height" ItemsSource="{Binding EmployeeInfo}">
                <syncfusion:SfListView.HeaderTemplate>
                    <DataTemplate>
                        <Grid RowSpacing="0">
                            <Grid RowSpacing="0" BackgroundColor="Gray" >
                                <Label Text="{Binding Converter={StaticResource converter}}" FontSize="30" HorizontalOptions="CenterAndExpand" VerticalOptions="CenterAndExpand"
                                    TextColor="White"/>
                            </Grid>
                            <Grid RowSpacing="0" BackgroundColor="LightGray" Grid.Row="1">
                                <Grid.RowDefinitions>
                                    <RowDefinition Height="50" />
                                    <RowDefinition Height="1" />
                                </Grid.RowDefinitions>
                                <Grid RowSpacing="0">
                                    <Grid.ColumnDefinitions>
                                        <ColumnDefinition Width="70" />
                                        <ColumnDefinition Width="*" />
                                        <ColumnDefinition Width="100" />
                                    </Grid.ColumnDefinitions>
                                    <Label Grid.ColumnSpan="2" HorizontalOptions="StartAndExpand" VerticalOptions="CenterAndExpand" Text="Employee" Margin="15,0,0,0"/>
                                    <Label Grid.Column="2" HorizontalOptions="StartAndExpand" VerticalOptions="CenterAndExpand" Text="Check In"/>
                                </Grid>
                            </Grid>
                        </Grid>
                    </DataTemplate>
                </syncfusion:SfListView.HeaderTemplate>
                <syncfusion:SfListView.ItemTemplate >
                    <DataTemplate>
                        <Grid RowSpacing="0">
                            <Grid.RowDefinitions>
                                <RowDefinition Height="*" />
                                <RowDefinition Height="1" />
                            </Grid.RowDefinitions>
                            <Grid RowSpacing="0">
                                <Grid.ColumnDefinitions>
                                    <ColumnDefinition Width="70" />
                                    <ColumnDefinition Width="*" />
                                    <ColumnDefinition Width="100" />
                                </Grid.ColumnDefinitions>
                                <Image Source="{Binding EmployeeImage}" VerticalOptions="Center" HorizontalOptions="Center"
                                    HeightRequest="50" WidthRequest="50"/>
                                <Grid Grid.Column="1">
                                    <Grid.RowDefinitions>
                                        <RowDefinition Height="30" />
                                        <RowDefinition Height="30" />
                                    </Grid.RowDefinitions>
                                    <Label  VerticalOptions="Center" HorizontalOptions="Start" Text="{Binding EmployeeName}" Grid.Row="0" FontSize="20"/>
                                <Label  VerticalOptions="Center" HorizontalOptions="Start" Text="{Binding Designation}" Grid.Row="1" FontSize="13" TextColor="Gold"/>
                                </Grid>
                                <Label Grid.Column="2" HorizontalOptions="StartAndExpand" VerticalOptions="CenterAndExpand" Text="{Binding CheckIn, StringFormat='{0:hh:mm tt}'}"/>
                            </Grid>
                            <Grid Grid.Row="1" BackgroundColor="Black"/>
                        </Grid>
                    </DataTemplate>
                </syncfusion:SfListView.ItemTemplate>
            </syncfusion:SfListView>
    </ContentPage.Content>
</ContentPage>
```

**C#**
Define the **CheckIn** property in the **Model** and implement property change notifications.
```
namespace ListViewMaui
{
    public class Employee : INotifyPropertyChanged
    {
        private DateTime checkIn

        public Employee()
        {

        }

        public DateTime CheckIn
        {
            get { return checkIn; }
            set
            {
                if (checkIn != value)
                {
                    checkIn = value;
                    this.RaisedOnPropertyChanged("CheckIn");
                }
            }
        }

        public event PropertyChangedEventHandler PropertyChanged;

        public void RaisedOnPropertyChanged(string _PropertyName)
        {
            if (PropertyChanged != null)
            {
                PropertyChanged(this, new PropertyChangedEventArgs(_PropertyName));
            }
        }
    }
}
```

**Output:**
 
 ![timeformat.PNG](https://support.syncfusion.com/kb/attachment/article/14980/inline?token=eyJhbGciOiJodHRwOi8vd3d3LnczLm9yZy8yMDAxLzA0L3htbGRzaWctbW9yZSNobWFjLXNoYTI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjE3MzU2Iiwib3JnaWQiOiIzIiwiaXNzIjoic3VwcG9ydC5zeW5jZnVzaW9uLmNvbSJ9.JkOfZJTJny7izxbfA92o2v8-jdeOuRSyDW4YvYygqAc)

**Conclusion**

I hope you enjoyed learning how to show time values in items within .NET MAUI ListView.

You can refer to our [.NET MAUI ListView feature tour](https://www.syncfusion.com/maui-controls/maui-listview) page to know about its other groundbreaking feature representations and [documentation](https://help.syncfusion.com/maui/listview/getting-started), and how to quickly get started with configuration specifications. Explore our [.NET MAUI ListView example](https://github.com/syncfusion/maui-demos/tree/master/MAUI/ListView) to understand how to create and manipulate data.

You can check out our components from the [License and Downloads](https://www.syncfusion.com/sales/teamlicense) page for current customers. If you are new to Syncfusion®, try our 30-day [free trial](https://www.syncfusion.com/downloads/maui/confirm) to check out our other controls.

Please let us know in the comments section if you have any queries or require clarification. You can also contact us through our [support forums](https://www.syncfusion.com/forums), [Direct-Trac](https://support.syncfusion.com/create), or [feedback portal](https://www.syncfusion.com/feedback/maui?control=sflistview). We are always happy to assist you!
