---
title: Ograniczenia schematu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: b5044d39d1dc5d2fa7d2ce691cdda7075fa0e32a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151206"
---
# <a name="schema-restrictions"></a>Ograniczenia schematu
Drugi parametr opcjonalny **GetSchema** metodą jest zwracane ograniczenia, które są używane do ograniczenia ilości informacji o schemacie, a zostanie on przekazany do **GetSchema** metodę jako tablica ciągów . Pozycja w tablicy określa wartości, które można przekazać, a jest równa liczbie ograniczania.  
  
 Na przykład w poniższej tabeli opisano ograniczenia dotyczące obsługiwanych przez kolekcji schematów "Tabele" przy użyciu .NET Framework Data Provider for SQL Server. Dodatkowe ograniczenia dotyczące kolekcje schematów programu SQL Server są wymienione na końcu tego tematu.  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Name|TABLE_NAME|3|  
|Typem|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Określanie wartości ograniczeń  
 Aby użyć jednego z ograniczeń kolekcji schematów "Tabele", po prostu utworzyć tablicę ciągów z czterema elementami, a następnie umieść wartość w elemencie który odpowiada liczbie ograniczania. Na przykład, aby ograniczyć tabele zwracane przez **GetSchema** metody tylko do tabel schematu "Sprzedaż", ustaw drugiego elementu tablicy, aby "Sprzedaż" przed przekazaniem go do **GetSchema** metody.  
  
> [!NOTE]
>  Kolekcje ograniczenia dla `SqlClient` i `OracleClient` dodatkową `ParameterName` kolumny. Ograniczenie domyślną kolumnę jest nadal dostępna dla wstecznej zgodności, ale obecnie jest ignorowana. Aby zminimalizować ryzyko ataku polegającego na iniekcji SQL podczas określania wartości ograniczenia należy używać zamiast zastępowania ciągów zapytań sparametryzowanych.  
  
> [!NOTE]
>  Liczba elementów w tablicy musi być mniejsza niż liczba ograniczeń obsługiwane w przypadku kolekcji określony schemat else <xref:System.ArgumentException> zostanie zgłoszony. Może być mniejsza niż maksymalna liczba ograniczeń. Brak ograniczeń są uznawane za wartość null (nieograniczony).  
  
 Można tworzyć zapytania zarządzanego dostawcy .NET Framework, aby określić listę ograniczeń obsługiwanych przez wywołanie metody **GetSchema** metodę o nazwie kolekcji schematów ograniczeniom, czyli "Ograniczenia". Spowoduje to zwrócenie <xref:System.Data.DataTable> listę nazw kolekcji, nazwy ograniczeń, wartości domyślne ograniczenia i ograniczenie liczby.  
  
### <a name="example"></a>Przykład  
 W poniższych przykładach pokazano sposób użycia <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metody .NET Framework Data Provider for SQL Server <xref:System.Data.SqlClient.SqlConnection> klasy do pobrania informacji o schemacie o wszystkich tabelach zawartych w **AdventureWorks**przykładowe bazy danych i ograniczyć informacje zwrócone do tylko tych tabel w schemacie "terminy sprzedaż":  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a>Ograniczenia schematu programu SQL Server  
 W poniższej tabeli wymieniono ograniczenia dotyczące kolekcje schematów programu SQL Server.  
  
### <a name="users"></a>Użytkownicy  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Nazwa_użytkownika|@Name|nazwa|1|  
  
### <a name="databases"></a>Bazy danych  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Nazwa|@Name|Nazwa|1|  
  
### <a name="tables"></a>Tabele  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Name|TABLE_NAME|3|  
|Typem|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Kolumny  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Widoki  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|VIEW_CATALOG|1|  
|Właściciel|@Owner|VIEW_SCHEMA|2|  
|tabela|@Table|VIEW_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|SPECIFIC_CATALOG|1|  
|Właściciel|@Owner|SPECIFIC_SCHEMA|2|  
|Nazwa|@Name|SPECIFIC_NAME|3|  
|Parametr|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>Procedury  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|SPECIFIC_CATALOG|1|  
|Właściciel|@Owner|SPECIFIC_SCHEMA|2|  
|Nazwa|@Name|SPECIFIC_NAME|3|  
|Typ|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|db_name()|1|  
|Właściciel|@Owner|user_name()|2|  
|tabela|@Table|o.name|3|  
|ConstraintName|@ConstraintName|x.name|4|  
|Kolumna|@Column|c.name|5|  
  
### <a name="indexes"></a>Indeksy  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|db_name()|1|  
|Właściciel|@Owner|user_name()|2|  
|tabela|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|CONSTRAINT_CATALOG|1|  
|Właściciel|@Owner|CONSTRAINT_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Nazwa|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 Schema Restrictions  
 W poniższej tabeli wymieniono ograniczenia dotyczące kolekcje schematów programu SQL Server 2008. Te ograniczenia są prawidłowe, począwszy od wersji 3.5 z dodatkiem SP1, .NET Framework i programu SQL Server 2008. Nie są obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenia domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
