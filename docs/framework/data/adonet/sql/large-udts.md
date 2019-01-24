---
title: Duże UDT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 259b8e6df9b302ec50fe84a3b57d4597821bdcc8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533471"
---
# <a name="large-udts"></a>Duże UDT
Typy zdefiniowane przez użytkownika (UDTs) umożliwiają deweloperom rozszerzenie serwera typ skalarny systemu, przechowując wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów w bazie danych programu SQL Server. Typów zdefiniowanych przez użytkownika może zawierać wiele elementów i może mieć zachowań, w przeciwieństwie do typów danych tradycyjnych aliasu, które składają się z jednego typu danych systemu programu SQL Server.  
  
> [!NOTE]
>  Należy zainstalować .NET Framework 3.5 z dodatkiem SP1 (lub nowszym) z zalet rozszerzona obsługa SqlClient duże UDT.  
  
 Wcześniej rozszerzeń UDT nie zostały ograniczone do maksymalnie 8 kilobajtów. W programie SQL Server 2008 to ograniczenie zostało usunięte dla typów zdefiniowanych przez użytkownika, które formatu w <xref:Microsoft.SqlServer.Server.Format.UserDefined>.  
  
 Aby uzyskać pełną dokumentację dla typów zdefiniowanych przez użytkownika Zobacz wersja programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.  
  
 **SQL Server Books Online**  
  
1.  [Zdefiniowane przez użytkownika typy CLR](https://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Trwa pobieranie schematy UDT przy użyciu GetSchema  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Metody <xref:System.Data.SqlClient.SqlConnection> zwraca bazy danych informacji o schemacie w <xref:System.Data.DataTable>. Aby uzyskać więcej informacji, zobacz [kolekcje schematów programu SQL Server](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>Wartości kolumn GetSchemaTable dla typów zdefiniowanych przez użytkownika  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Metody <xref:System.Data.SqlClient.SqlDataReader> zwraca <xref:System.Data.DataTable> opisującą kolumny metadanych. W poniższej tabeli opisano różnice w metadanych kolumn, aby uzyskać duże UDT między programu SQL Server 2005 i SQL Server 2008.  
  
|Kolumna SqlDataReader|SQL Server 2005|SQL Server 2008 lub nowszy|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Różni się|Różni się|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|Wystąpienie UDT|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|Wystąpienie UDT|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Trzy części nazwy określonej jako *Database.SchemaName.TypeName*.|  
|`IsLong`|Różni się|Różni się|  
  
## <a name="sqldatareader-considerations"></a>SqlDataReader Considerations  
 <xref:System.Data.SqlClient.SqlDataReader> Został rozszerzony począwszy od programu SQL Server 2008 do obsługi pobierania dużych wartości UDT. Jak duże UDT wartości są przetwarzane przez <xref:System.Data.SqlClient.SqlDataReader> zależy od wersji programu SQL Server, które są używane, jak również na `Type System Version` określone w parametrach połączenia. Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Następujące metody <xref:System.Data.SqlClient.SqlDataReader> zwróci <xref:System.Data.SqlTypes.SqlBinary> zamiast UDT po `Type System Version` jest ustawiona na program SQL Server 2005:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Następujące metody zwraca tablicę `Byte[]` zamiast UDT po `Type System Version` jest ustawiona na program SQL Server 2005:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Należy pamiętać, że konwersji zostały wprowadzone w bieżącej wersji programu ADO.NET.  
  
## <a name="specifying-sqlparameters"></a>Specifying SqlParameters  
 Następujące <xref:System.Data.SqlClient.SqlParameter> właściwości zostały rozszerzone do pracy z duże UDT.  
  
|Parametr SqlParameter właściwości|Opis|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Pobiera lub ustawia obiekt, który reprezentuje wartość parametru. Domyślny ma wartość null. Właściwość może być `SqlBinary`, `Byte[]`, lub zarządzanego obiektu.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Pobiera lub ustawia obiekt, który reprezentuje wartość parametru. Domyślny ma wartość null. Właściwość może być `SqlBinary`, `Byte[]`, lub zarządzanego obiektu.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Pobiera lub ustawia rozmiar wartości parametru, aby rozwiązać. Wartość domyślna to 0. Właściwość może być liczba całkowita, która reprezentuje rozmiar wartości parametru. Aby uzyskać duże UDT może być rzeczywisty rozmiar UDT albo -1 nieznany.|  
  
## <a name="retrieving-data-example"></a>Przykład pobierania danych  
 Poniższy fragment kodu przedstawia sposób pobierania dużych ilości danych UDT. `connectionString` Zmiennej zakłada prawidłowe połączenie z bazą danych programu SQL Server i `commandString` zmiennej zakłada poprawną instrukcją SELECT z kolumny klucza podstawowego, wymienione jako pierwsze.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Konfigurowanie parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Pobieranie informacji o schemacie bazy danych](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [Mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Dane binarne i dużej wartości w programie SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
