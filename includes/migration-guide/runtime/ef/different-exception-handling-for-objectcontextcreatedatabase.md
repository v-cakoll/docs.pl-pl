### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Obsługa metod ObjectContext.CreateDatabase i DbProviderServices.CreateDatabase różnych wyjątków

|   |   |
|---|---|
|Szczegóły|W programie .NET 4.5, w przypadku niepowodzenia tworzenia bazy danych <code>CreateDatabase</code> metody podejmie próbę porzucić pustej bazy danych. Jeśli ta operacja zakończy się powodzeniem, oryginalny <xref:System.Data.SqlClient.SqlException?displayProperty=name> będzie propagowane (zamiast <xref:System.InvalidOperationException?displayProperty=name> który zawsze zgłosiła wyjątek .NET 4.0)|
|Sugestia|Gdy przechwytywanie <xref:System.InvalidOperationException?displayProperty=name> podczas wykonywania <xref:System.Data.Objects.ObjectContext.CreateDatabase> lub <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions powinny teraz również zostać przechwycony.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|

