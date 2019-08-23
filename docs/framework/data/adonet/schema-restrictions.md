---
title: Ograniczenia schematu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 1a2c32d133799ee5338c18d0f51bced49cb3dc4b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963179"
---
# <a name="schema-restrictions"></a>Ograniczenia schematu
Drugim parametrem opcjonalnym metody **GetSchema** jest ograniczenia, które są używane do ograniczenia ilości zwracanych informacji o schemacie i są przesyłane do metody **GetSchema** jako tablica ciągów. Pozycja w tablicy określa wartości, które można przekazać, i jest równoważne z numerem ograniczenia.  
  
 Na przykład w poniższej tabeli opisano ograniczenia obsługiwane przez kolekcję schematów "tabele" przy użyciu Dostawca danych .NET Framework dla SQL Server. Dodatkowe ograniczenia dotyczące kolekcji schematów SQL Server są wymienione na końcu tego tematu.  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Name|TABLE_NAME|3|  
|Tabletype|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Określanie wartości ograniczeń  
 Aby użyć jednego z ograniczeń kolekcji schematów "tabele", po prostu Utwórz tablicę ciągów z czterema elementami, a następnie umieść wartość w elemencie, który jest zgodny z numerem ograniczenia. Na przykład aby ograniczyć tabele zwracane przez metodę **GetSchema** do tylko tych tabel w schemacie "Sales", należy ustawić drugi element tablicy na "Sales" przed przekazaniem go do metody **GetSchema** .  
  
> [!NOTE]
> Kolekcje ograniczeń dla `SqlClient` i `OracleClient` mają dodatkową `ParameterName` kolumnę. Domyślna kolumna ograniczenia nadal ma zgodność z poprzednimi wersjami, ale jest obecnie ignorowana. Zapytania sparametryzowane zamiast zamiany ciągu powinny służyć do zminimalizowania ryzyka związanego z iniekcją kodu SQL podczas określania wartości ograniczeń.  
  
> [!NOTE]
> Liczba elementów w tablicy musi być mniejsza lub równa liczbie ograniczeń, które są obsługiwane dla określonej kolekcji schematów, w przeciwnym razie <xref:System.ArgumentException> zostanie zgłoszony. Może być mniejsza niż maksymalna liczba ograniczeń. W przypadku brakujących ograniczeń przyjmuje się, że wartość jest równa null (bez ograniczeń).  
  
 Można wysłać zapytanie do dostawcy zarządzanego .NET Framework, aby określić listę obsługiwanych ograniczeń, wywołując metodę **GetSchema** z nazwą kolekcji schematów ograniczeń, która jest "ograniczenia". Spowoduje to zwrócenie <xref:System.Data.DataTable> listy nazw kolekcji, nazw ograniczeń, domyślnych wartości ograniczeń oraz numerów ograniczeń.  
  
### <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak za <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> pomocą metody dostawca danych .NET Framework dla klasy SQL Server <xref:System.Data.SqlClient.SqlConnection> pobrać informacje o schemacie dotyczące wszystkich tabel zawartych w przykładowej bazie danych **AdventureWorks** , i w celu ograniczenia informacji zwracanych do tylko tych tabel w schemacie "Sales":  
  
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
  
## <a name="sql-server-schema-restrictions"></a>SQL Server ograniczenia schematu  
 W poniższej tabeli wymieniono ograniczenia dotyczące SQL Serverych kolekcji schematów.  
  
### <a name="users"></a>Użytkownicy  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Nazwa_użytkownika|@Name|nazwa|1|  
  
### <a name="databases"></a>Bazy danych  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Nazwa|@Name|Nazwa|1|  
  
### <a name="tables"></a>Tabelę  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Name|TABLE_NAME|3|  
|Tabletype|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Kolumny  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Widoki  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|VIEW_CATALOG|1|  
|Właściciel|@Owner|VIEW_SCHEMA|2|  
|tabela|@Table|VIEW_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
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
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|db_name()|1|  
|Właściciel|@Owner|user_name()|2|  
|tabela|@Table|o.name|3|  
|Element ConstraintName|@ConstraintName|x.name|4|  
|Kolumna|@Column|c.name|5|  
  
### <a name="indexes"></a>Zwiększa  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|db_name()|1|  
|Właściciel|@Owner|user_name()|2|  
|tabela|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|typy. assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|CONSTRAINT_CATALOG|1|  
|Właściciel|@Owner|CONSTRAINT_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Nazwa|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>Ograniczenia schematu SQL Server 2008  
 W poniższej tabeli wymieniono ograniczenia dotyczące kolekcji schematów SQL Server 2008. Te ograniczenia są prawidłowe od wersji 3,5 SP1 .NET Framework i SQL Server 2008. Nie są one obsługiwane we wcześniejszych wersjach .NET Framework i SQL Server.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Domyślne ograniczenie|Numer ograniczenia|  
|----------------------|--------------------|-------------------------|------------------------|  
|Wykaz|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Kolumna|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
