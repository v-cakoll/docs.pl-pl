### <a name="non-pooled-sql-connections-will-leak-memory-if-not-explicitly-disposed"></a>Inne niż w puli połączeń z serwerem SQL zostanie wyciek pamięci, jeśli nie jawnie zlikwidowany

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5 niebuforowanych połączeń SQL, które nie są widoczne jawnie (za pośrednictwem metodę Dispose, zamknij lub przy użyciu) będzie przecieki pamięci|
|Sugestia|Tego problemu w programie .NET Framework 4.5 obsługi aktualizacji. Zaktualizuj .NET Framework 4.5, lub uaktualnienia programu .NET Framework 4.5.1 lub nowszej, aby rozwiązać ten problem. Alternatywnie można uniknąć tego problemu, przy użyciu <xref:System.Data.SqlClient.SqlConnection?displayProperty=name> w &#39;przy użyciu&#39; wzorca (która jest najlepszym rozwiązaniem) lub przez jawne wywoływanie metodą Dispose lub Close gdy połączenie jest już potrzebne.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String%2CSystem.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

