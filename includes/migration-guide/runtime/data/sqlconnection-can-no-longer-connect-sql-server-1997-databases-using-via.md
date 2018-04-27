### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>Połączenie nie może nawiązać 1997 serwera SQL lub bazy danych za pomocą karty VIA

|   |   |
|---|---|
|Szczegóły|Połączenia z bazami danych programu SQL Server przy użyciu [wirtualne karty interfejsu (VIA) protokołu](https://technet.microsoft.com/library/ms191229%28v=sql.105%29.aspx) nie są już obsługiwane. Protokół używany do łączenia z bazą danych programu SQL Server jest widoczna w parametrach połączenia. Połączenie VIA będzie zawierać za pośrednictwem:&lt;servername&gt;. Jeśli ta aplikacja łączy się z serwerem SQL za pomocą protokołu innego niż VIA (tcp: lub np: na przykład), a następnie nie istotne zmiany będą napotkał. Ponadto połączenia SQL Server 7 (1997) nie są już obsługiwane.|
|Sugestia|Protokół VIA jest przestarzały, więc alternatywnych protokołu używanego do nawiązania połączenia bazy danych SQL. Protokół najczęściej używany jest protokół TCP/IP. Instrukcje dotyczące włączania protokołu TCP/IP można znaleźć [tutaj](https://msdn.microsoft.com/library/bb909712.aspx). Jeśli bazy danych jest dostępne tylko z w intranecie, protokołu potoków udostępnionego może zapewnić lepszą wydajność, jeśli sieć jest powolne.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

