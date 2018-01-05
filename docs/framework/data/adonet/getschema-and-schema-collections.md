---
title: "GetSchema i kolekcje schematów"
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
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d982964b596528b091f5367edd38e0cee5f923c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getschema-and-schema-collections"></a>GetSchema i kolekcje schematów
**Połączenia** klasy w każdej implementacji zarządzanego dostawcy .NET Framework **GetSchema** metodę, która służy do pobierania informacji dotyczących bazy danych, który jest obecnie połączony, schematów i informacje o schemacie zwrócony z **GetSchema** metody jest dostarczany w formie <xref:System.Data.DataTable>. **GetSchema** metody jest przeciążona metoda, która zapewnia następujące parametry opcjonalne określanie kolekcji schematów, aby wrócić i ograniczanie ilość zwracanych informacji.  
  
## <a name="specifying-the-schema-collections"></a>Określanie kolekcje schematów  
 Pierwszy parametr opcjonalny **GetSchema** metoda jest nazwę kolekcji, które jest określone jako ciąg. Istnieją dwa typy kolekcji schematu: Typowe kolekcje schematów, które są wspólne dla wszystkich dostawców i kolekcji schematu, które są specyficzne dla każdego dostawcy.  
  
 Można zbadać zarządzanego dostawcy .NET Framework, można ustalić listy kolekcji schematu obsługiwanych przez wywołanie metody **GetSchema** metody bez argumentów lub nazwą kolekcji schematów "MetaDataCollections". Spowoduje to zwrócenie <xref:System.Data.DataTable> z listą kolekcji obsługiwanych schematu, liczba ograniczeń obsługiwanych przez każdy z nich i części identyfikatora, które korzystają z.  
  
### <a name="retrieving-schema-collections-example"></a>Pobieranie schematu przykład kolekcje  
 W poniższych przykładach pokazano, jak używać <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metody dostawcy danych programu .NET Framework dla programu SQL Server <xref:System.Data.SqlClient.SqlConnection> klasy można pobrać informacji schematu o wszystkie tabele zawarte w **AdventureWorks**przykładowa baza danych:  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,    
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
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
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
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
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
