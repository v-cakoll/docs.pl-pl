---
title: Duże typów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 3c74bed67069740354b36891db73ed80b952f0c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="large-udts"></a>Duże typów
Typy danych zdefiniowane przez użytkownika (UDTs) umożliwiają deweloperom rozszerzyć system skalarną typu serwera, przechowując wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów w bazie danych programu SQL Server. UDTs może zawierać wielu elementów i może zawierać zachowania, w przeciwieństwie do tradycyjnych alias typów danych, składające się z jednego typu danych systemu programu SQL Server.  
  
> [!NOTE]
>  .NET Framework 3.5 z dodatkiem SP1 należy zainstalować (lub nowsza) przeprowadzać SqlClient ulepszoną obsługę dużych typów.  
  
 Wcześniej UDTs były ograniczone do maksymalnie rozmiar równy 8 kilobajtów. W programie SQL Server 2008, to ograniczenie zostało usunięte w przypadku typów, które mają format <xref:Microsoft.SqlServer.Server.Format.UserDefined>.  
  
 Pełną dokumentację dla typów zdefiniowanych przez użytkownika na ten temat można znaleźć w wersji SQL Server — książki online dla używanej wersji programu SQL Server są używane.  
  
 **SQL Server — książki Online**  
  
1.  [Zdefiniowane przez użytkownika typy CLR](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Trwa pobieranie przy użyciu GetSchema schematy UDT  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Metody <xref:System.Data.SqlClient.SqlConnection> zwraca bazy danych informacji o schemacie w <xref:System.Data.DataTable>. Aby uzyskać więcej informacji, zobacz [kolekcje schematów programu SQL Server](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>Wartości w kolumnie GetSchemaTable dla typów  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Metody <xref:System.Data.SqlClient.SqlDataReader> zwraca <xref:System.Data.DataTable> opisujący metadanych kolumn. W poniższej tabeli opisano różnice w metadanych kolumn dla dużych UDTs między programu SQL Server 2005 i SQL Server 2008.  
  
|Kolumna SqlDataReader|SQL Server 2005|SQL Server 2008 lub nowszy|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Zmienia się|Zmienia się|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|Wystąpienie UDT|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|Wystąpienie UDT|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Nazwa określona jako część trzech *Database.SchemaName.TypeName*.|  
|`IsLong`|Zmienia się|Zmienia się|  
  
## <a name="sqldatareader-considerations"></a>Zagadnienia dotyczące SqlDataReader  
 <xref:System.Data.SqlClient.SqlDataReader> Został rozszerzony w programie SQL Server 2008 do obsługi pobieranie dużych wartości UDT. Jak duże wartości UDT są przetwarzane przez <xref:System.Data.SqlClient.SqlDataReader> zależy od wersji programu SQL Server są używane, jak również na `Type System Version` określone w parametrach połączenia. Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Następujące metody <xref:System.Data.SqlClient.SqlDataReader> zwróci <xref:System.Data.SqlTypes.SqlBinary> zamiast UDT podczas `Type System Version` ustawiono programu SQL Server 2005:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Zwraca tablicę następujących metod `Byte[]` zamiast UDT podczas `Type System Version` ustawiono programu SQL Server 2005:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Należy pamiętać, że dokonano konwersji na bieżącą wersję programu ADO.NET.  
  
## <a name="specifying-sqlparameters"></a>Specifying SqlParameters  
 Następujące <xref:System.Data.SqlClient.SqlParameter> właściwości zostały rozszerzone do pracy z dużą typów.  
  
|Właściwość SqlParameter|Opis|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Pobiera lub ustawia obiekt reprezentujący wartość parametru. Domyślny ma wartość null. Właściwość może być `SqlBinary`, `Byte[]`, lub zarządzanego obiektu.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Pobiera lub ustawia obiekt reprezentujący wartość parametru. Domyślny ma wartość null. Właściwość może być `SqlBinary`, `Byte[]`, lub zarządzanego obiektu.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Pobiera lub ustawia rozmiar wartość parametru do rozpoznania. Wartość domyślna to 0. Właściwość może być liczba całkowita, która reprezentuje rozmiar wartość parametru. Dla dużych typów może być rzeczywisty rozmiar UDT, lub wartość -1 nieznany.|  
  
## <a name="retrieving-data-example"></a>Przykład podczas pobierania danych  
 Poniższy fragment kodu pokazano, jak pobrać UDT dużej ilości danych. `connectionString` Zmienna przyjmuje prawidłowe połączenie z bazą danych programu SQL Server i `commandString` zmienna przyjmuje poprawną instrukcją SELECT z pierwszym kolumna klucza podstawowego.  
  
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
 [Konfigurowanie parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Pobieranie informacji o schemacie bazy danych](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Dane binarne i dużej wartości w programie SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
