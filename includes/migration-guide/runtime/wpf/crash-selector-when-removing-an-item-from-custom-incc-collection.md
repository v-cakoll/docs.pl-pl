### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Ulec awarii w selektorze, jeśli usunięcie elementu z kolekcji niestandardowej INCC

|   |   |
|---|---|
|Szczegóły|<code>T:System.InvalidOperationException</code> Może wystąpić w następującym scenariuszu:<ul><li>ItemsSource dla <code>T:System.Windows.Controls.Primitives.Selector</code> to kolekcja niestandardowych implementacji <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>Wybrany element zostanie usunięty z kolekcji.</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> Ma <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (wskazującą położenie nieznany).</li></ul>Stos wywołań wyjątków, który rozpoczyna się od System.Windows.Threading.Dispatcher.VerifyAccess() na System.Windows.DependencyObject.GetValue (DependencyProperty dp) na System.Windows.Controls.Primitives.Selector.GetIsSelected (DependencyObject element) ten wyjątek może wystąpić w .NET Framework 4.5, jeśli aplikacja ma więcej niż jeden wątek dyspozytora. W programie .NET Framework 4.7 wyjątek może również wystąpić w aplikacjach z jednym wątkiem, dyspozytora. Problem został rozwiązany w programie .NET Framework 4.7.1.|
|Sugestia|Uaktualnianie do programu .NET Framework 4.7.1.|
|Zakres|Mały|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|

