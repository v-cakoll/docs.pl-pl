### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open w systemie Windows 7 kończy się niepowodzeniem z systemem innym niż — IFS podstawowego dostawcy usługi Winsock lub LSP obecne

|   |   |
|---|---|
|Szczegóły|<xref:System.Data.SqlClient.SqlConnection.Open> i <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> Niepowodzenie w programie .NET Framework 4.5, jeśli zostanie uruchomione na komputerze z systemem Windows 7 z systemem innym niż — IFS podstawowego dostawcy usługi Winsock lub LSP znajdują się na komputerze. Aby określić, czy zainstalowano podstawowego dostawcy nie - IFS lub LSP, użyj <code>netsh WinSock Show Catalog</code> polecenia i sprawdź, czy każdy <code>Winsock Catalog Provider Entry</code> elementu, który jest zwracany. Jeśli ma wartość flagi usługi <code>0x20000</code> ustawiony bit, dostawca używa uchwytów IFS i będzie pracował prawidłowo. Jeśli <code>0x20000</code> bit jest wyczyszczone (nie ustawiono), jest podstawowego dostawcy nie - IFS lub LSP.|
|Sugestia|Ten błąd został rozwiązany w programie .NET Framework 4.5.2, więc można uniknąć przez uaktualnienie programu .NET Framework. Alternatywnie można uniknąć przez usunięcie wszelkich zainstalowanych z systemem innym niż — IFS dostawców LSP interfejsu Winsock.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

