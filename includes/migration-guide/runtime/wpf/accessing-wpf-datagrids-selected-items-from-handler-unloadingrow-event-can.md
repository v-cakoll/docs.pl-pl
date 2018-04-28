### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Uzyskiwanie dostępu do elementu DataGrid WPF wybrane elementy z obsługi zdarzeń UnloadingRow w elemencie DataGrid mogą powodować NullReferenceException

|   |   |
|---|---|
|Szczegóły|Z powodu usterki w programie .NET Framework 4.5, programy obsługi zdarzeń dla <xref:System.Windows.Controls.DataGrid> zdarzenia dotyczące usuwania wiersza może spowodować <xref:System.NullReferenceException?displayProperty=name> zostanie wygenerowany, jeśli uzyskują oni dostęp do <xref:System.Windows.Controls.DataGrid>w <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> lub <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> właściwości.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.6 i mogą być kierowane przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

