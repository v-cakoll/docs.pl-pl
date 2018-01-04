---
title: Ograniczenia schematu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4a3cc1f0c27af1ad41e14374b4c155e6b8620f28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="schema-restrictions"></a>Ograniczenia schematu
Drugi parametr opcjonalny **GetSchema** metoda jest zwracane ograniczenia, które są używane w celu ograniczenia ilości informacji o schemacie, a jest przekazywana do **GetSchema** metodę jako tablica ciągów . Pozycja w tablicy określa wartości, które mogą upłynąć, a jest to równoważne numer ograniczeń.  
  
 Na przykład w poniższej tabeli opisano ograniczenia obsługiwane przez kolekcji schematów "Tabele" za pomocą dostawcy .NET Framework Data Provider for SQL Server. Dodatkowe ograniczenia dotyczące kolekcji schematu programu SQL Server są wymienione na końcu tego tematu.  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Name|TABLE_NAME|3|  
|Typem|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Określanie wartości ograniczeń  
 Do korzystania z jednego z ograniczeń kolekcji schematów "Tabele", po prostu utworzyć tablicy ciągów z czterech elementów, a następnie umieść wartość w elemencie, który jest zgodna z liczbą ograniczeń. Na przykład, aby ograniczyć tabele zwrócony przez **GetSchema** metody tylko tych tabel w schemacie "Sprzedaż" ustawienie drugiego elementu tablicy, tak aby "Sprzedaż" przed przekazaniem go do **GetSchema** metody.  
  
> [!NOTE]
>  Kolekcje ograniczenia dla `SqlClient` i `OracleClient` dodatkowych `ParameterName` kolumny. Ograniczenie domyślna kolumna jest nadal istnieje dla zapewnienia zgodności, ale obecnie jest ignorowana. Zapytania sparametryzowane zamiast zastępowania ciągów należy ograniczyć ryzyko ataku polegającego na iniekcji SQL podczas określania wartości ograniczeń.  
  
> [!NOTE]
>  Liczba elementów w tablicy musi być mniejsza niż liczba obsługiwana w przypadku kolekcji określony schemat else ograniczeń <xref:System.ArgumentException> zostanie wygenerowany. Może być krótsza niż maksymalna liczba ograniczenia. Brak ograniczeń są rozpatrywane null (bez ograniczeń).  
  
 Można zbadać zarządzanego dostawcy .NET Framework, można ustalić listy ograniczeń obsługiwanych przez wywołanie metody **GetSchema** metodę o nazwie kolekcji ograniczeń schematu, czyli "Ograniczenia". Spowoduje to zwrócenie <xref:System.Data.DataTable> listę nazwy kolekcji, nazwy ograniczenia wartości domyślne ograniczenia i ograniczenie liczby.  
  
### <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak używać <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metody dostawcy danych programu .NET Framework dla programu SQL Server <xref:System.Data.SqlClient.SqlConnection> klasy można pobrać informacji schematu o wszystkie tabele zawarte w **AdventureWorks**przykładowe bazy danych i ograniczyć informacje zwracane tylko tych tabel w schemacie "Sprzedaż":  
  
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
  
## <a name="sql-server-schema-restrictions"></a>Ograniczenia schematu serwera SQL  
 W poniższej tabeli wymieniono ograniczenia dotyczące kolekcji schematu programu SQL Server.  
  
### <a name="users"></a>Użytkownicy  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Nazwa_użytkownika|@Name|nazwa|1|  
  
### <a name="databases"></a>Bazy danych  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Nazwa|@Name|Nazwa|1|  
  
### <a name="tables"></a>Tabele  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Name|TABLE_NAME|3|  
|Typem|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Kolumny  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Kolumny|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Kolumny|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Widoki  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|VIEW_CATALOG|1|  
|Właściciel|@Owner|VIEW_SCHEMA|2|  
|tabela|@Table|VIEW_NAME|3|  
|Kolumny|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|SPECIFIC_CATALOG|1|  
|Właściciel|@Owner|SPECIFIC_SCHEMA|2|  
|Nazwa|@Name|SPECIFIC_NAME|3|  
|Parametr|@Parameter|NAZWA_PARAMETRU|4|  
  
### <a name="procedures"></a>Procedury  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|SPECIFIC_CATALOG|1|  
|Właściciel|@Owner|SPECIFIC_SCHEMA|2|  
|Nazwa|@Name|SPECIFIC_NAME|3|  
|Typ|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|db_name()|1|  
|Właściciel|@Owner|User_name()|2|  
|tabela|@Table|o.name|3|  
|ConstraintName|@ConstraintName|x.name|4|  
|Kolumny|@Column|c.name|5|  
  
### <a name="indexes"></a>Indeksy  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|db_name()|1|  
|Właściciel|@Owner|User_name()|2|  
|tabela|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|nazwa_zestawu|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|CONSTRAINT_CATALOG|1|  
|Właściciel|@Owner|CONSTRAINT_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Nazwa|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>Ograniczenia schematu programu SQL Server 2008  
 W poniższej tabeli wymieniono ograniczenia dotyczące kolekcji schematu programu SQL Server 2008. Ograniczenia te są prawidłowe, począwszy od wersji 3.5 z dodatkiem SP1, .NET Framework i programu SQL Server 2008. Nie są obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|Nazwa ograniczenia|Nazwa parametru|Ograniczenie domyślne|Liczba ograniczeń|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Właściciel|@Owner|TABLE_SCHEMA|2|  
|tabela|@Table|TABLE_NAME|3|  
|Kolumny|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
