### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Obsługa dla metod ObjectContext.CreateDatabase i DbProviderServices.CreateDatabase różnych wyjątków

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, w przypadku niepowodzenia tworzenia bazy danych <code>CreateDatabase</code> metod będzie próbował usunąć pustej bazy danych. Jeśli ta operacja zakończy się powodzeniem, oryginalnym <xref:System.Data.SqlClient.SqlException?displayProperty=name> będą propagowane (zamiast <xref:System.InvalidOperationException?displayProperty=name> , zawsze został zgłoszony w .NET Framework 4.0)|
|Sugestia|Gdy przechwytywanie <xref:System.InvalidOperationException?displayProperty=name> podczas wykonywania <xref:System.Data.Objects.ObjectContext.CreateDatabase> lub <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions powinien teraz również zostać przechwycony.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|

