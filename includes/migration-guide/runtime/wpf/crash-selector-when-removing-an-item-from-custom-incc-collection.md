### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Awarii w selektora podczas usuwania elementu z kolekcji niestandardowej INCC

|   |   |
|---|---|
|Szczegóły|<code>T:System.InvalidOperationException</code> Może wystąpić w następującym scenariuszu:<ul><li>Właściwość ItemsSource <code>T:System.Windows.Controls.Primitives.Selector</code> to kolekcja niestandardowych implementacji <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>Wybrany element został usunięty z kolekcji.</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> Ma <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (wskazującą nieznanej pozycji).</li></ul>Stos wywołań wyjątków zaczyna się od System.Windows.Threading.Dispatcher.VerifyAccess() w System.Windows.DependencyObject.GetValue (DependencyProperty dp) na System.Windows.Controls.Primitives.Selector.GetIsSelected (DependencyObject. element) ten wyjątek może wystąpić w programie .NET Framework 4.5, jeśli aplikacja ma więcej niż jeden wątek dyspozytora. W programie .NET Framework 4.7 wyjątek może również wystąpić w aplikacji za pomocą pojedynczego Wątek dyspozytora. Problem został rozwiązany w programie .NET Framework 4.7.1.|
|Sugestia|Uaktualnij do platformy .NET Framework 4.7.1.|
|Zakres|Pomocnicza|
|Wersja|4.7|
|Typ|środowisko uruchomieniowe|

