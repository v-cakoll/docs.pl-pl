### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Sporadycznie mógł przewiń do dołu elementu ItemsControls (takich jak ListBox i DataGrid) podczas korzystania z niestandardowego DataTemplates

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach przyczyną ItemsControls usterki w programie .NET Framework 4.5 (takich jak <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>, itd.) nie przewiń ich elementów bottom w przypadku korzystania z niestandardowego DataTemplates. Przewijanie zostanie podjęta po raz drugi (po przewijanie, Utwórz kopię zapasową), będzie działać następnie.|
|Sugestia|Ten problem został rozwiązany w programie .NET Framework 4.5.2 i mogą być kierowane przez uaktualnienie do tej wersji (lub nowszym) programu .NET Framework. Alternatywnie użytkownicy nadal przeciągać pasków przewijania do końcowego elementów w kolekcjach, ale może być konieczne spróbuj dwa razy zrobić pomyślnie.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|

