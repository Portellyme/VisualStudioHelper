# WPF


## TextBox_SelectAll_MouseClick
SelectAll in TextBox when TextBox gets focus by mouse click

**XAML Code** 
```
<TextBox 
PreviewMouseLeftButtonDown="SelectivelyIgnoreMouseButton"
MouseDoubleClick="SelectAddress" 
GotKeyboardFocus="SelectAddress"
/>
```

**MainWindow.xaml.cs**
```
private void SelectAddress(object sender, RoutedEventArgs e)
{
	//CS8600 
	//TextBox tb = (sender as TextBox);
	TextBox tb = (TextBox)sender;
	if (tb != null)
	{
		tb.SelectAll();
	}
}

private void SelectivelyIgnoreMouseButton(object sender, MouseButtonEventArgs e)
{
	//CS8600 
	//TextBox tb = (sender as TextBox);
	TextBox tb = (TextBox)sender;
	if (tb != null)
	{
		if (!tb.IsKeyboardFocusWithin)
		{
			e.Handled = true;
			tb.Focus();
		}
	}
}
```
