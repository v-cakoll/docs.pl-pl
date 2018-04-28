### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET teraz próbuje automatycznie ponownie zestawione zerwane połączenia SQL

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5.1 programu .NET Framework spróbuje automatycznie ponownie zestawione zerwane połączenia SQL. Chociaż zazwyczaj będzie aplikacje bardziej niezawodne, istnieją przypadki krawędzi, w których trzeba wiedzieć, że połączenie zostało utracone, dzięki czemu może potrwać kilka akcji po ponownym aplikacji.|
|Sugestia|Jeśli ta funkcja jest niepożądane z powodu problemów ze zgodnością, można ją wyłączyć, ustawiając <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=name> właściwości ciągu połączenia (lub <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=name>) na wartość 0.|
|Zakres|Krawędź|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)?displayProperty=nameWithType></li></ul>|

