### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>Połączenie nie będzie można podłączyć do programu SQL Server 1997 lub baz danych przy użyciu karty VIA

|   |   |
|---|---|
|Szczegóły|Połączenia z bazami danych programu SQL Server przy użyciu [protokołu wirtualnego Interface Adapter (VIA)](https://technet.microsoft.com/library/ms191229%28v=sql.105%29.aspx) nie są już obsługiwane. Protokół używany do łączenia z bazą danych programu SQL Server jest widoczna w parametrach połączenia. Połączenie VIA będzie zawierać za pośrednictwem:&lt;servername&gt;. Jeśli ta aplikacja nawiązuje połączenie z SQL za pomocą protokołu innego niż VIA (tcp: lub nazwane: na przykład), a następnie zostanie napotkana nie istotnej zmiany. Ponadto połączenia z SQL Server 7 (1997) nie są już obsługiwane.|
|Sugestia|Protokołu VIA jest przestarzały, więc alternatywnych protokół powinna być używana z bazami danych SQL. Protokół najczęściej używany jest protokół TCP/IP. Instrukcje dotyczące włączania protokołu TCP/IP można znaleźć [tutaj](https://msdn.microsoft.com/library/bb909712.aspx). Jeśli baza danych jest dostępny tylko z firmowej sieci intranet, protokół potoków udostępniony może zapewnić lepszą wydajność, jeśli sieć jest powolne.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

