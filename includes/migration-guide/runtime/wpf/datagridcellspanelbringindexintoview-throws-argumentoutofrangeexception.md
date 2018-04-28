### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView zgłasza ArgumentOutOfRangeException

|   |   |
|---|---|
|Szczegóły|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> będzie działać asynchronicznie, gdy włączona jest wirtualizacja kolumny, ale szerokości kolumn, które nie zostały jeszcze określić.  Jeśli kolumny zostaną usunięte przed sytuacji asynchroniczne <xref:System.ArgumentOutOfRangeException?displayProperty=name> może wystąpić.|
|Sugestia|Jeden z następujących czynności:<ol><li>Uaktualnij platformę .NET 4.7.</li><li>Zainstaluj najnowsze obsługi poprawki dla platformy .NET 4.6.2.</li><li>Unikaj usuwanie kolumn do asynchronicznego odpowiedzi na <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> zostało ukończone.</li></ol>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

