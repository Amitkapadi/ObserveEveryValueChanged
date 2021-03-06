ObserveEveryValueChanged
---
Voodoo Magic for WPF.

You can observe all properties that is not implements `INotifyPropertyChanged`.

Sample
---
```csharp
using Reactive.Bindings.Extensions;

public partial class MainWindow : Window
{
    public MainWindow()
    {
        InitializeComponent();

        this.ObserveEveryValueChanged(x => x.Width).Subscribe(x => WidthText.Text = x.ToString());
        this.ObserveEveryValueChanged(x => x.Height).Subscribe(x => HeightText.Text = x.ToString());
    }
}
```

![wpfgif](https://cloud.githubusercontent.com/assets/46207/15827886/1573ff16-2c48-11e6-9876-4e4455d7eced.gif)

`ObserveEveryValueChanged(propertySelector)`. That's all.

with [ReactiveProperty](https://github.com/runceel/ReactiveProperty/), you can create bindable notify property changed value.

> ReactiveProperty v2.7.3 includes this extensions 

```csharp
public class MyClass
{
    public int MyProperty { get; set; }
}


public partial class MainWindow : Window
{
    MyClass model;
    public IReadOnlyReactiveProperty<int> MyClassMyProperty { get; }

    public MainWindow()
    {
        InitializeComponent();

        model = new MyClass();
        this.MyClassMyProperty = model.ObserveEveryValueChanged(x => x.MyProperty).ToReadOnlyReactiveProperty();
    }
}
```
