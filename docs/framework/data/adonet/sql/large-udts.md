---
title: Duże UDT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: f55f6eccf3566a2391204e1ca4349ae5dff01954
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148559"
---
# <a name="large-udts"></a>Duże UDT
Typy zdefiniowane przez użytkownika (UDTs) umożliwiają deweloperowi rozszerzenie systemu typu skalarnego serwera przez przechowywanie obiektów wspólnego środowiska wykonawczego języka (CLR) w bazie danych programu SQL Server. UDTs może zawierać wiele elementów i może mieć zachowania, w przeciwieństwie do tradycyjnych typów danych alias, które składają się z jednego typu danych systemu SQL Server.  
  
> [!NOTE]
> Należy zainstalować .NET Framework 3.5 SP1 (lub nowsze), aby skorzystać z rozszerzonej obsługi SqlClient dla dużych UDTs.  
  
 Wcześniej UDTs były ograniczone do maksymalnego rozmiaru 8 kilobajtów. W programie SQL Server 2008 to ograniczenie zostało usunięte dla <xref:Microsoft.SqlServer.Server.Format.UserDefined>UDTs, które mają format .  
  
 Aby uzyskać pełną dokumentację typów zdefiniowanych przez użytkownika, zobacz wersję programu SQL Server Books Online dla używanej wersji programu SQL Server.  
  
 **SQL Server documentation (Dokumentacja programu SQL Server)**  
  
1. [Zdefiniowane przez użytkownika typy CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Pobieranie schematów UDT przy użyciu getschema  
 Metoda <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> <xref:System.Data.SqlClient.SqlConnection> zwraca informacje o schemacie bazy danych w pliku <xref:System.Data.DataTable>. Aby uzyskać więcej informacji, zobacz [Kolekcje schematów programu SQL Server](../sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>Wartości kolumny GetSchemaTable dla UDTs  
 Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> <xref:System.Data.SqlClient.SqlDataReader> zwraca, <xref:System.Data.DataTable> który opisuje metadane kolumny. W poniższej tabeli opisano różnice w metadanych kolumn dla dużych UDTs między SQL Server 2005 i SQL Server 2008.  
  
|Kolumna SqlDataReader|SQL Server 2005|SQL Server 2008 i nowsze|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Różna|Różna|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|Wystąpienie UDT|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|Wystąpienie UDT|  
|`ProviderType`|21`SqlDbType.VarBinary`( )|29`SqlDbType.Udt`( )|  
|`NonVersionedProviderType`|29`SqlDbType.Udt`( )|29`SqlDbType.Udt`( )|  
|`DataTypeName`|`SqlDbType.VarBinary`|Nazwa trzech części określona jako *Database.SchemaName.TypeName*.|  
|`IsLong`|Różna|Różna|  
  
## <a name="sqldatareader-considerations"></a>Zagadnienia dotyczące programu SqlDataReader  
 Został <xref:System.Data.SqlClient.SqlDataReader> rozszerzony począwszy od programu SQL Server 2008 do obsługi pobierania dużych wartości UDT. Jak duże wartości UDT są <xref:System.Data.SqlClient.SqlDataReader> przetwarzane przez a zależy od wersji programu SQL `Type System Version` Server, którego używasz, a także od określonych w ciągu połączenia. Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Następujące metody <xref:System.Data.SqlClient.SqlDataReader> zwróci <xref:System.Data.SqlTypes.SqlBinary> zamiast UDT, gdy `Type System Version` jest ustawiona na SQL Server 2005:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Następujące metody zwróci tablicy `Byte[]` zamiast UDT, gdy `Type System Version` jest ustawiona na SQL Server 2005:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Pamiętaj, że dla bieżącej wersji ADO.NET nie są dokonywane żadne konwersje.  
  
## <a name="specifying-sqlparameters"></a>Określanie parametrów SqlParameters  
 Następujące <xref:System.Data.SqlClient.SqlParameter> właściwości zostały rozszerzone do pracy z dużymi UDTs.  
  
|Właściwość sqlparameter|Opis|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Pobiera lub ustawia obiekt, który reprezentuje wartość parametru. Domyślny ma wartość null. Właściwość może `SqlBinary` `Byte[]`być , lub obiekt zarządzany.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Pobiera lub ustawia obiekt, który reprezentuje wartość parametru. Domyślny ma wartość null. Właściwość może `SqlBinary` `Byte[]`być , lub obiekt zarządzany.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Pobiera lub ustawia rozmiar wartości parametru do rozwiązania. Wartość domyślna to 0. Właściwość może być liczebną, która reprezentuje rozmiar wartości parametru. W przypadku dużych UDT może to być rzeczywisty rozmiar UDT lub -1 dla nieznanych.|  
  
## <a name="retrieving-data-example"></a>Przykład pobierania danych  
 Poniższy fragment kodu pokazuje, jak pobrać duże dane UDT. Zmienna `connectionString` zakłada prawidłowe połączenie z bazą `commandString` danych programu SQL Server, a zmienna przyjmuje prawidłową instrukcję SELECT z kolumną klucza podstawowego wymienioną jako pierwsza.  
  
```csharp  
using (SqlConnection connection = new SqlConnection(
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie parametrów i typów danych parametrów](../configuring-parameters-and-parameter-data-types.md)
- [Pobieranie informacji o schemacie bazy danych](../retrieving-database-schema-information.md)
- [Mapowanie typu danych serwera SQL](../sql-server-data-type-mappings.md)
- [Dane binarne i dużej wartości w programie SQL Server](sql-server-binary-and-large-value-data.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
