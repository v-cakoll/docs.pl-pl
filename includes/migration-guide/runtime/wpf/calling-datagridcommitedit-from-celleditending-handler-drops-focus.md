### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Wywoływanie DataGrid.CommitEdit z obsługi CellEditEnding porzuca fokus

|   |   |
|---|---|
|Szczegóły|Wywoływanie <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednego z <xref:System.Windows.Controls.DataGrid?displayProperty=name>w <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> powoduje, że obsługi zdarzeń <xref:System.Windows.Controls.DataGrid?displayProperty=name> utratę fokusu.|
|Sugestia|Ten błąd został rozwiązany w programie .NET Framework 4.5.2, więc można uniknąć przez uaktualnienie programu .NET Framework. Alternatywnie można należy unikać ponownie, wybierając jawnie <xref:System.Windows.Controls.DataGrid?displayProperty=name> po wywołaniu <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

