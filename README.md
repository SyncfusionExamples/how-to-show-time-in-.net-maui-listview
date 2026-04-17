# how-to-show-time-in-.net-maui-listview

This example demonstrates how to show time in .NET MAUI ListView (SfListView).

## Sample

```xaml
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
```

## Requirements to run the demo

* [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) or [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)
* Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## Troubleshooting

### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.
