### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ListBoxItem IsSelected powiązania problem z obiektu ObservableCollection&lt;T&gt;. Przenieś

|   |   |
|---|---|
|Szczegóły|Wywoływanie <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> lub <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> w kolekcji powiązany <xref:System.Windows.Controls.ListBox?displayProperty=name> z zaznaczonych elementów może prowadzić do dziwne zachowanie w przypadku zaznaczenia w przyszłości lub unselection z <xref:System.Windows.Controls.ListBox?displayProperty=name> elementów.|
|Sugestia|Wywoływanie <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> i <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> zamiast <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> będzie obejść ten problem. Alternatywnie ten problem został rozwiązany w .NET Framework 4.6 i mogą być kierowane przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

