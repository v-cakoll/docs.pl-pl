---
title: Ograniczenia schematu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149014"
---
# <a name="schema-restrictions"></a>Ograniczenia schematu
Drugi parametr opcjonalny **Metody GetSchema** jest ograniczenia, które są używane do ograniczenia ilości informacji o schemacie zwracane i jest przekazywana do **Metody GetSchema** jako tablicy ciągów. Położenie w tablicy określa wartości, które można przekazać, a to jest równoważne z numerem ograniczenia.  
  
 Na przykład w poniższej tabeli opisano ograniczenia obsługiwane przez kolekcję schematów "Tabele" przy użyciu dostawcy danych programu .NET Framework dla programu SQL Server. Dodatkowe ograniczenia dla kolekcji schematów programu SQL Server są wymienione na końcu tego tematu.  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Name|TABLE_NAME|3|  
|Typ tabeli|@TableType|Table_type|4|  
  
## <a name="specifying-restriction-values"></a>Określanie wartości ograniczeń  
 Aby użyć jednego z ograniczeń kolekcji schematu "Tabele", wystarczy utworzyć tablicę ciągów z czterema elementami, a następnie umieścić wartość w elemencie, który pasuje do numeru ograniczenia. Na przykład, aby ograniczyć tabele zwrócone przez **Metodę GetSchema** tylko do tych tabel w schemacie "Sprzedaż", należy ustawić drugi element tablicy na "Sprzedaż" przed przekazaniem go do **Metody GetSchema.**  
  
> [!NOTE]
> Kolekcje ograniczeń i `SqlClient` `OracleClient` mają dodatkową `ParameterName` kolumnę. Domyślna kolumna ograniczenia jest nadal tam dla zgodności z powrotem, ale jest obecnie ignorowana. Sparametryzowane kwerendy, a nie zastępowanie ciągów powinny być używane w celu zminimalizowania ryzyka ataku iniekcji SQL podczas określania wartości ograniczeń.  
  
> [!NOTE]
> Liczba elementów w tablicy musi być mniejsza lub równa liczbie ograniczeń obsługiwanych dla <xref:System.ArgumentException> określonej kolekcji schematu inaczej zostanie rzucona. Może być mniejsza niż maksymalna liczba ograniczeń. Zakłada się, że brakujące ograniczenia mają wartość null (bez ograniczeń).  
  
 Można zbadać .NET Framework zarządzanego dostawcy, aby określić listę obsługiwanych ograniczeń, wywołując **GetSchema** metody o nazwie kolekcji schematu ograniczeń, który jest "Ograniczenia". Spowoduje to <xref:System.Data.DataTable> zwrócenie a z listy nazw kolekcji, nazwy ograniczeń, domyślne wartości ograniczeń i numery ograniczeń.  
  
### <a name="example"></a>Przykład  
 Poniższe przykłady pokazują, <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> jak używać metody dostawcy danych programu <xref:System.Data.SqlClient.SqlConnection> .NET Framework dla klasy PROGRAMU SQL Server do pobierania informacji o schemacie wszystkich tabel zawartych w przykładowej bazie danych **AdventureWorks** i ograniczania informacji zwracanych tylko do tych tabel w schemacie "Sprzedaż":  
  
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
 W poniższych tabelach przedstawiono ograniczenia dotyczące kolekcji schematów programu SQL Server.  
  
### <a name="users"></a>Użytkownicy  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Nazwa_użytkownika|@Name|name|1|  
  
### <a name="databases"></a>Bazy danych  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Nazwa|@Name|Nazwa|1|  
  
### <a name="tables"></a>Tabele  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Name|TABLE_NAME|3|  
|Typ tabeli|@TableType|Table_type|4|  
  
### <a name="columns"></a>Kolumny  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Widoki  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns (Wychwki)  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|VIEW_CATALOG|1|  
|Właściciel|@Owner|VIEW_SCHEMA|2|  
|Tabela|@Table|VIEW_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProceduryParametry  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|SPECIFIC_CATALOG|1|  
|Właściciel|@Owner|SPECIFIC_SCHEMA|2|  
|Nazwa|@Name|SPECIFIC_NAME|3|  
|Parametr|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>Procedury  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|SPECIFIC_CATALOG|1|  
|Właściciel|@Owner|SPECIFIC_SCHEMA|2|  
|Nazwa|@Name|SPECIFIC_NAME|3|  
|Typ|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns (Kody indeksu)  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|db_name()|1|  
|Właściciel|@Owner|user_name()|2|  
|Tabela|@Table|o.name|3|  
|Nazwa ograniczenia|@ConstraintName|x.name|4|  
|Kolumna|@Column|c.name|5|  
  
### <a name="indexes"></a>Indeksy  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|db_name()|1|  
|Właściciel|@Owner|user_name()|2|  
|Tabela|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>Zdefiniowane typy użytkownika  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|typy.assembly_class|2|  
  
### <a name="foreignkeys"></a>Klawisze obce  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|CONSTRAINT_CATALOG|1|  
|Właściciel|@Owner|CONSTRAINT_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Nazwa|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>Ograniczenia schematu programu SQL Server 2008  
 W poniższych tabelach przedstawiono ograniczenia dotyczące kolekcji schematów programu SQL Server 2008. Te ograniczenia są prawidłowe począwszy od wersji 3.5 SP1 programu .NET Framework i SQL Server 2008. Nie są one obsługiwane we wcześniejszych wersjach programu .NET Framework i SQL Server.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns (Typy kolumn)  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllKolumny  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie ADO.NET](ado-net-overview.md)
