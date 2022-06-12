---
title: IsEnabledTextBox
---

# Attributes

| Name |
|-|
|Text|

# Example

```xml
<CheckBox Name="check">
    <StackPanel Orientation="Vertical">
        <TextBlock x:Name="IncludeInGlobalResultTitle"
                    Margin="0,10,0,0"
                    Text="Include in global result" />
        <controls:IsEnabledTextBlock FontSize="{StaticResource SecondaryTextFontSize}"
                                        IsEnabled="{Binding ElementName=check, Path=IsChecked}"
                                        Text="Show results on queries without direct activation command" />
    </StackPanel>
</CheckBox>
```

# Demo
you can run [demo](https://github.com/ghost1372/SettingsUI) and see this feature.

![SettingsUI](https://raw.githubusercontent.com/ghost1372/Resources/main/SettingsUI/Samples/IsEnabledTextBox_UnChecked.png)

![SettingsUI](https://raw.githubusercontent.com/ghost1372/Resources/main/SettingsUI/Samples/IsEnabledTextBox_Checked.png)