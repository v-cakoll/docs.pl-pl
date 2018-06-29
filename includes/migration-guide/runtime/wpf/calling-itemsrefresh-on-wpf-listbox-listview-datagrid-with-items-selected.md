### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Wywołania Items.Refresh na WPF ListBox, ListView lub DataGrid z zaznaczonych elementów może spowodować zduplikowane elementy pojawią się w elemencie

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5, wywoływanie ListBox.Items.Refresh z kodu, gdy wybrano elementów w <xref:System.Windows.Controls.ListBox?displayProperty=name> może spowodować, że wybrane elementy, które ma być duplikowany na liście. Podobne problemu z <xref:System.Windows.Controls.ListView?displayProperty=name> i <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Jest to stała w .NET Framework 4.6.|
|Sugestia|Ten problem może być pracy wokół programowo unselecting elementów przed <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> nosi nazwę, a następnie ponownie wybierając je, po zakończeniu wywołania. Alternatywnie ten problem został rozwiązany w .NET Framework 4.6 i mogą być kierowane przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

