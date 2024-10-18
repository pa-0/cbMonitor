# ClipboardMonitor

A small C# Library for Monitoring Clipboard with P/Invokes (e.g.: Clipboard Content Changed event)

## Download

[Download the Library (.dll)](https://raw.githubusercontent.com/mrousavy/ClipboardMonitor/master/Downloads/ClipboardMonitor.dll)

## Usage

Add the `.dll` to your .NET Project's `References` Tree in the Solution View.

>[!Note]
>_ClipboardMonitor has to create a Window in order to get hwnd to process WndProc messages in WPF. The window is hidden by default, created once in the background, so (though you won't see it) keep in mind that it is there nonetheless._

### Example 1

Attach (C#):

```csharp
var cm = new ClipboardMonitor();
cm.ClipboardData += (ClipboardDataEventArgs args) => {
    MessageBox.Show($"Clipboard Changed! {args.Data.ToString()}");
};
```

### Example 2

```csharp
public partial class MainWindow
{
    public ClipboardMonitor Monitor { get; set; }

    public MainWindow()
    {
        Monitor = new ClipboardMonitor();
        Monitor .ClipboardData += (ClipboardDataEventArgs args) => {
            MessageBox.Show($"Clipboard Changed! {args.Data.ToString()}");
        };
    }
}
```
