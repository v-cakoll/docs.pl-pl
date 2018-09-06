---
title: GetSchema i kolekcje schematów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: 6c6ea41b9da9c98f8c4ee45ca1e223a29712729a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742504"
---
# <a name="getschema-and-schema-collections"></a>GetSchema i kolekcje schematów
**Połączenia** klas w każdej implementacji zarządzanego dostawcy .NET Framework **GetSchema** metodę, która służy do pobierania informacji o schemacie o bazie danych, który jest obecnie połączony, i informacje o schemacie zwróciło **GetSchema** metody jest dostarczany w formie <xref:System.Data.DataTable>. **GetSchema** metodą jest przeciążona metoda, która zapewnia następujące parametry opcjonalne określanie kolekcji schematów, aby powrócić i ograniczając ilość zwracanych informacji.  
  
## <a name="specifying-the-schema-collections"></a>Określanie kolekcje schematów  
 Pierwszy parametr opcjonalny **GetSchema** metoda to nazwa kolekcji, która jest określana jako ciąg. Istnieją dwa typy kolekcje schematów: Typowe kolekcje schematów, które są wspólne dla wszystkich dostawców i kolekcje określonego schematu, które są specyficzne dla każdego dostawcy.  
  
 Można tworzyć zapytania zarządzanego dostawcy .NET Framework, aby określić listę kolekcje schematów obsługiwanych przez wywołanie metody **GetSchema** metody bez argumentów lub nazwą kolekcji schematów "MetaDataCollections". Spowoduje to zwrócenie <xref:System.Data.DataTable> z listą kolekcje schematów obsługiwanych, liczba ograniczeń, które obsługują one każdego i części identyfikator, których używają.  
  
### <a name="retrieving-schema-collections-example"></a>Pobieranie schematu przykład kolekcji  
 W poniższych przykładach pokazano sposób użycia <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metody .NET Framework Data Provider for SQL Server <xref:System.Data.SqlClient.SqlConnection> klasy do pobrania informacji o schemacie o wszystkich tabelach zawartych w **AdventureWorks**przykładowej bazy danych:  
  
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
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
