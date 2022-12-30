---
title: WinUICommunity.SettingsUI.SettingsControls
---

{% note warning %}
ported from https://github.com/CommunityToolkit/Labs-Windows
{% endnote %}

```
Install-Package WinUICommunity.SettingsUI
```
After installing, add the following resource to app.xaml

```xml
<ResourceDictionary Source="ms-appx:///SettingsUI/Themes/Generic.xaml"/>
```
See the Demo app to see how to use it.

# SettingsPage
This example uses SettingsCard and SettingsExpander to showcase a complete Windows 11 style settings page.

```xml
<Page.Resources>
    <!--  These styles can be referenced to create a consistent SettingsPage layout  -->
    <x:Double x:Key="SettingsCardSpacing">3</x:Double>
    <Style x:Key="SettingsGroupTextBlockStyle"
            BasedOn="{StaticResource BodyStrongTextBlockStyle}"
            TargetType="TextBlock">
        <Style.Setters>
            <Setter Property="Margin" Value="1,30,0,4" />
        </Style.Setters>
    </Style>
</Page.Resources>

<ScrollViewer>
    <StackPanel MaxWidth="1000"
        HorizontalAlignment="Stretch"
        Spacing="{StaticResource SettingsCardSpacing}">
        <!--  TODO: @Niels - I just copied everything here, not sure if any values need adjusting. We should probably use this as a place to have more bespoke examples of each type of content like Slider, ComboBox, TextBox, etc...  -->
        <TextBlock Style="{StaticResource SettingsGroupTextBlockStyle}"
            Text="Group of settings" />
        <labs:SettingsCard Description="This is a default card, with the Header, HeaderIcon, Description and Content set."
                    Header="This is the Header">
            <labs:SettingsCard.HeaderIcon>
                <FontIcon Glyph="&#xE799;" />
            </labs:SettingsCard.HeaderIcon>
            <ComboBox SelectedIndex="0">
                <ComboBoxItem>Option 1</ComboBoxItem>
                <ComboBoxItem>Option 2</ComboBoxItem>
                <ComboBoxItem>Option 3</ComboBoxItem>
            </ComboBox>
        </labs:SettingsCard>

        <labs:SettingsCard Description="You can use a FontIcon, SymbolIcon or BitmapIcon to set the cards HeaderIcon."
                    Header="Icon options">
            <labs:SettingsCard.HeaderIcon>
                <BitmapIcon ShowAsMonochrome="False"
                    UriSource="https://raw.githubusercontent.com/microsoft/PowerToys/main/src/settings-ui/Settings.UI/Assets/FluentIcons/FluentIconsImageResizer.png" />
            </labs:SettingsCard.HeaderIcon>
            <ToggleSwitch />
        </labs:SettingsCard>

        <labs:SettingsCard Header="A card with custom objects as its Description">
            <labs:SettingsCard.Description>
                <HyperlinkButton Content="Learn more about Phone Link" />
            </labs:SettingsCard.Description>
            <Button Content="Open Phone Link"
            Style="{StaticResource AccentButtonStyle}" />
        </labs:SettingsCard>

        <labs:SettingsCard Description="When resizing a SettingsCard, the Content will wrap vertically. You can override this breakpoint by setting the SettingsCardWrapThreshold resource."
                    Header="Adaptive layouts">
            <labs:SettingsCard.HeaderIcon>
                <FontIcon Glyph="&#xE745;" />
            </labs:SettingsCard.HeaderIcon>
            <labs:SettingsCard.Resources>
                <x:Double x:Key="SettingsCardWrapThreshold">800</x:Double>
            </labs:SettingsCard.Resources>
            <Button Content="This control will wrap vertically!"
            Style="{StaticResource AccentButtonStyle}" />
        </labs:SettingsCard>

        <TextBlock Style="{StaticResource SettingsGroupTextBlockStyle}"
            Text="Next group of settings" />

        <labs:SettingsCard Description="A SettingsCard can be made clickable and you can leverage the Command property or Click event."
                    Header="A clickable SettingsCard"
                    IsClickEnabled="True">
            <labs:SettingsCard.HeaderIcon>
                <FontIcon Glyph="&#xE799;" />
            </labs:SettingsCard.HeaderIcon>
        </labs:SettingsCard>

        <labs:SettingsCard ActionIconToolTip="Open in new window"
                    Description="You can customize the ActionIcon and ActionIconToolTip."
                    Header="Customizing the ActionIcon"
                    IsClickEnabled="True">
            <labs:SettingsCard.HeaderIcon>
                <FontIcon Glyph="&#xE12B;" />
            </labs:SettingsCard.HeaderIcon>
            <labs:SettingsCard.ActionIcon>
                <FontIcon FontSize="12"
                    Glyph="&#xE8A7;" />
            </labs:SettingsCard.ActionIcon>
        </labs:SettingsCard>

        <TextBlock Style="{StaticResource SettingsGroupTextBlockStyle}"
            Text="Final group of settings" />

        <labs:SettingsExpander Description="The SettingsExpander has the same properties as a Card, and you can set SettingsCard as part of the Items collection."
                        Header="SettingsExpander">
            <labs:SettingsExpander.HeaderIcon>
                <FontIcon Glyph="&#xE91B;" />
            </labs:SettingsExpander.HeaderIcon>
            <ComboBox SelectedIndex="0">
                <ComboBoxItem>Option 1</ComboBoxItem>
                <ComboBoxItem>Option 2</ComboBoxItem>
                <ComboBoxItem>Option 3</ComboBoxItem>
            </ComboBox>

            <labs:SettingsExpander.Items>
                <labs:SettingsCard Header="A basic SettingsCard within an SettingsExpander">
                    <Button Content="Button" />
                </labs:SettingsCard>
                <labs:SettingsCard Description="SettingsCard within an Expander can be made clickable too!"
                            Header="This item can be clicked"
                            IsClickEnabled="True" />

                <labs:SettingsCard ContentAlignment="Left">
                    <CheckBox Content="Here the ContentAlignment is set to Left. This is great for e.g. CheckBoxes or RadioButtons." />
                </labs:SettingsCard>

                <labs:SettingsCard HorizontalContentAlignment="Left"
                            ContentAlignment="Vertical"
                            Description="You can also align your content vertically. Make sure to set the HorizontalAlignment to Left when you do!"
                            Header="Vertically aligned">
                    <GridView SelectedIndex="1">
                        <GridViewItem>
                            <Border Width="64"
                            Height="64"
                            Background="#0078D4"
                            CornerRadius="4" />
                        </GridViewItem>
                        <GridViewItem>
                            <Border Width="64"
                            Height="64"
                            Background="#005EB7"
                            CornerRadius="4" />
                        </GridViewItem>
                        <GridViewItem>
                            <Border Width="64"
                            Height="64"
                            Background="#003D92"
                            CornerRadius="4" />
                        </GridViewItem>
                        <GridViewItem>
                            <Border Width="64"
                            Height="64"
                            Background="#001968"
                            CornerRadius="4" />
                        </GridViewItem>
                    </GridView>
                </labs:SettingsCard>
                <labs:SettingsCard Description="You can override the Left indention of a SettingsCard by overriding the SettingsCardLeftIndention"
                            Header="Customization">
                    <labs:SettingsCard.Resources>
                        <x:Double x:Key="SettingsCardLeftIndention">40</x:Double>
                    </labs:SettingsCard.Resources>
                </labs:SettingsCard>
            </labs:SettingsExpander.Items>
        </labs:SettingsExpander>
    </StackPanel>
</ScrollViewer>
```

# Clickable SettingsCard

```cs
public bool IsCardEnabled { get; set; } = true;
public bool IsCardExpanded { get; set; } = false;

private async void OnCardClicked(object sender, RoutedEventArgs e)
{
    await Windows.System.Launcher.LaunchUriAsync(new Uri("https://www.microsoft.com"));
}
```

```xml
<StackPanel Spacing="3">

    <labs:SettingsCard x:Name="settingsCard2"
                Description="A SettingsCard can be made clickable and you can leverage the Command property or Click event."
                Header="A clickable SettingsCard"
                IsClickEnabled="True"
                Click="OnCardClicked"
                IsEnabled="{x:Bind IsCardEnabled, Mode=OneWay}">
        <labs:SettingsCard.HeaderIcon>
            <FontIcon Glyph="&#xE799;" />
        </labs:SettingsCard.HeaderIcon>
    </labs:SettingsCard>

    <labs:SettingsCard ActionIconToolTip="Open in new window"
                Description="You can customize the ActionIcon and ActionIconToolTip."
                Header="Customizing the ActionIcon"
                IsClickEnabled="True"
                Click="OnCardClicked"
                IsEnabled="{x:Bind IsCardEnabled, Mode=OneWay}">
        <labs:SettingsCard.HeaderIcon>
            <FontIcon Glyph="&#xE12B;" />
        </labs:SettingsCard.HeaderIcon>
        <labs:SettingsCard.ActionIcon>
            <FontIcon Glyph="&#xE8A7;" />
        </labs:SettingsCard.ActionIcon>
    </labs:SettingsCard>
</StackPanel>
```

# SettingsCard
SettingsCard is a control that can be used to display settings in your experience. It uses the default styling found in Windows 11 and is easy to use, meets all accesibility standards and will make your settings page look great! You can set the Header, Description, HeaderIcon and Content properties to create an easy to use experience.

SettingsCard can also be turned into a button, by setting the `IsClickEnabled` property. This can be useful whenever you want your settings component to navigate to a detail page or open an external link.

```xml
<StackPanel Spacing="3">
    <TextBlock Margin="1,0,0,4"
        Style="{StaticResource BodyStrongTextBlockStyle}"
        Text="Group of settings" />
    <labs:SettingsCard
                Description="This is a default card, with the Header, HeaderIcon, Description and Content set."
                Header="This is the Header"
                IsEnabled="{x:Bind IsCardEnabled, Mode=OneWay}">
        <labs:SettingsCard.HeaderIcon>
            <FontIcon Glyph="&#xE799;" />
        </labs:SettingsCard.HeaderIcon>
        <ComboBox SelectedIndex="0">
            <ComboBoxItem>Option 1</ComboBoxItem>
            <ComboBoxItem>Option 2</ComboBoxItem>
            <ComboBoxItem>Option 3</ComboBoxItem>
        </ComboBox>
    </labs:SettingsCard>

    <labs:SettingsCard Description="You can use a FontIcon, SymbolIcon or BitmapIcon to set the cards HeaderIcon."
                Header="Icon options"
                IsEnabled="{x:Bind IsCardEnabled, Mode=OneWay}">
        <labs:SettingsCard.HeaderIcon>
            <BitmapIcon ShowAsMonochrome="False"
                UriSource="https://raw.githubusercontent.com/microsoft/PowerToys/main/src/settings-ui/Settings.UI/Assets/FluentIcons/FluentIconsImageResizer.png" />
        </labs:SettingsCard.HeaderIcon>
        <ToggleSwitch />
    </labs:SettingsCard>

    <labs:SettingsCard Header="A card with custom objects as its Description"
                IsEnabled="{x:Bind IsCardEnabled, Mode=OneWay}">
        <labs:SettingsCard.Description>
            <HyperlinkButton Content="Learn more about Phone Link" />
        </labs:SettingsCard.Description>
        <Button Content="Open Phone Link"
        Style="{StaticResource AccentButtonStyle}" />
    </labs:SettingsCard>

    <labs:SettingsCard Description="When resizing a SettingsCard, the Content will wrap vertically. You can override this breakpoint by setting the SettingsCardWrapThreshold resource."
                Header="Adaptive layouts"
                IsEnabled="{x:Bind IsCardEnabled, Mode=OneWay}">
        <labs:SettingsCard.HeaderIcon>
            <FontIcon Glyph="&#xE745;" />
        </labs:SettingsCard.HeaderIcon>
        <labs:SettingsCard.Resources>
            <x:Double x:Key="SettingsCardWrapThreshold">800</x:Double>
        </labs:SettingsCard.Resources>
        <Button Content="This control will wrap vertically!"
        Style="{StaticResource AccentButtonStyle}" />
    </labs:SettingsCard>
</StackPanel>
```

# SettingsExpander ItemsSource

```cs
public class MyDataModel
{
    public string? Name { get; set; }

    public string? Info { get; set; }

    public string? LinkDescription { get; set; }

    public string? Url { get; set; }
}

public ObservableCollection<MyDataModel> MyDataSet = new() {
    new()
    {
        Name = "First Item",
        Info = "More about first item.",
        LinkDescription = "Click here for more on first item.",
        Url = "https://microsoft.com/",
    },
    new()
    {
        Name = "Second Item",
        Info = "More about second item.",
        LinkDescription = "Click here for more on second item.",
        Url = "https://xbox.com/",
    },
    new()
    {
        Name = "Third Item",
        Info = "More about third item.",
        LinkDescription = "Click here for more on third item.",
        Url = "https://toolkitlabs.dev/",
    },
};
```xml
<labs:SettingsExpander Description="The SettingsExpander can use ItemsSource to define its Items."
                Header="Settings Expander with ItemsSource"
                ItemsSource="{x:Bind MyDataSet}">
    <labs:SettingsExpander.HeaderIcon>
        <FontIcon Glyph="&#xEA37;" />
    </labs:SettingsExpander.HeaderIcon>
    <labs:SettingsExpander.ItemTemplate>
        <DataTemplate x:DataType="local:MyDataModel">
            <labs:SettingsCard Description="{x:Bind Info}"
                        Header="{x:Bind Name}">
                <HyperlinkButton Content="{x:Bind LinkDescription}"
                            NavigateUri="{x:Bind Url}" />
            </labs:SettingsCard>
        </DataTemplate>
    </labs:SettingsExpander.ItemTemplate>
    <labs:SettingsExpander.ItemsHeader>
        <InfoBar Title="This is the ItemsHeader"
                CornerRadius="0,0,4,4"
                IsIconVisible="False"
                IsOpen="True"
                Severity="Success">
            <InfoBar.ActionButton>
                <HyperlinkButton Content="It can host custom content" />
            </InfoBar.ActionButton>
        </InfoBar>
    </labs:SettingsExpander.ItemsHeader>
    <labs:SettingsExpander.ItemsFooter>
        <InfoBar Title="This is the ItemsFooter"
                CornerRadius="0,0,4,4"
                IsIconVisible="False"
                IsOpen="True"
                Severity="Informational">
            <InfoBar.ActionButton>
                <HyperlinkButton Content="It can host custom content" />
            </InfoBar.ActionButton>
        </InfoBar>
    </labs:SettingsExpander.ItemsFooter>
</labs:SettingsExpander>
```

# SettingsExpander
The SettingsExpander can be used to group multiple SettingsCards into a single collapsable group.

A SettingsExpander can have it's own content to display a setting on the right, just like a SettingsCard, but in addition can have any number of extra Items to include as additional settings. These items are SettingsCards themselves, which means you can easily move a setting into or out of Expanders just by cutting and pasting their XAML!
You can easily override certain properties to create custom experiences. For instance, you can customize the ContentAlignment of a SettingsCard, to align your content to the Right (default), Left (hiding the HeaderIcon, Header and Description) or Vertically (usually best paired with changing the HorizontalContentAlignment to Stretch).

SettingsExpander is also an ItemsControl, so its items can be driven by a collection and the ItemsSource property. You can use the ItemTemplate to define how your data object is represented as a SettingsCard, as shown below. The ItemsHeader and ItemsFooter property can be used to host custom content at the start or end of the items list.

```xml
<ScrollViewer>
    <labs:SettingsExpander x:Name="settingsCard"
                    Description="The SettingsExpander has the same properties as a Card, and you can set SettingsCard as part of the Items collection."
                    Header="SettingsExpander"
                    IsEnabled="{x:Bind IsCardEnabled, Mode=OneWay}"
                    IsExpanded="{x:Bind IsCardExpanded, Mode=OneWay}">
        <!--  TODO: This should be TwoWay bound but throws compile error in Uno.  -->
        <labs:SettingsExpander.HeaderIcon>
            <FontIcon Glyph="&#xE91B;" />
        </labs:SettingsExpander.HeaderIcon>
        <ComboBox SelectedIndex="0">
            <ComboBoxItem>Option 1</ComboBoxItem>
            <ComboBoxItem>Option 2</ComboBoxItem>
            <ComboBoxItem>Option 3</ComboBoxItem>
        </ComboBox>

        <labs:SettingsExpander.Items>
            <labs:SettingsCard Header="A basic SettingsCard within an SettingsExpander">
                <Button Content="Button" />
            </labs:SettingsCard>
            <labs:SettingsCard Description="SettingsCard within an Expander can be made clickable too!"
                        Header="This item can be clicked"
                        IsClickEnabled="True" />

            <labs:SettingsCard ContentAlignment="Left">
                <CheckBox Content="Here the ContentAlignment is set to Left. This is great for e.g. CheckBoxes or RadioButtons." />
            </labs:SettingsCard>

            <labs:SettingsCard HorizontalContentAlignment="Left"
                        ContentAlignment="Vertical"
                        Description="You can also align your content vertically. Make sure to set the HorizontalAlignment to Left when you do!"
                        Header="Vertically aligned">
                <GridView SelectedIndex="1">
                    <GridViewItem>
                        <Border Width="64"
                        Height="64"
                        Background="#0078D4"
                        CornerRadius="4" />
                    </GridViewItem>
                    <GridViewItem>
                        <Border Width="64"
                        Height="64"
                        Background="#005EB7"
                        CornerRadius="4" />
                    </GridViewItem>
                    <GridViewItem>
                        <Border Width="64"
                        Height="64"
                        Background="#003D92"
                        CornerRadius="4" />
                    </GridViewItem>
                    <GridViewItem>
                        <Border Width="64"
                        Height="64"
                        Background="#001968"
                        CornerRadius="4" />
                    </GridViewItem>
                </GridView>
            </labs:SettingsCard>
            <labs:SettingsCard Description="You can override the Left indention of a SettingsCard by overriding the SettingsCardLeftIndention"
                        Header="Customization">
                <labs:SettingsCard.Resources>
                    <x:Double x:Key="SettingsCardLeftIndention">40</x:Double>
                </labs:SettingsCard.Resources>
            </labs:SettingsCard>
        </labs:SettingsExpander.Items>
    </labs:SettingsExpander>
</ScrollViewer>
```