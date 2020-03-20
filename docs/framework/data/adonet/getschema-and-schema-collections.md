---
title: GetSchema i kolekcje schematów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: e18c23e9bbec97a64110aba6eb7241761ecece06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149560"
---
# <a name="getschema-and-schema-collections"></a>GetSchema i kolekcje schematów
**Klasy połączenia** w każdym z dostawców zarządzanych programu .NET Framework implementują metodę **GetSchema,** która jest używana do pobierania informacji o schemacie o aktualnie połączonej bazie danych, a informacje o schemacie zwrócone z metody **GetSchema** są dostępne w postaci pliku <xref:System.Data.DataTable>. **Metoda GetSchema** jest przeciążona metoda, która zapewnia opcjonalne parametry do określania kolekcji schematu do zwrócenia i ograniczania ilości zwracanych informacji.  
  
## <a name="specifying-the-schema-collections"></a>Określanie kolekcji schematu  
 Pierwszy opcjonalny parametr **Metody GetSchema** jest nazwą kolekcji, która jest określona jako ciąg. Istnieją dwa typy kolekcji schematu: typowe kolekcje schematów, które są wspólne dla wszystkich dostawców i kolekcje określonego schematu, które są specyficzne dla każdego dostawcy.  
  
 Można zbadać dostawcę zarządzanego programu .NET Framework, aby określić listę obsługiwanych kolekcji schematu, wywołując metodę **GetSchema** bez argumentów lub o nazwie kolekcji schematu "MetaDataCollections". Spowoduje to <xref:System.Data.DataTable> zwrócenie a z listy obsługiwanych kolekcji schematu, liczba ograniczeń, które obsługują, a liczba części identyfikatorów, które używają.  
  
### <a name="retrieving-schema-collections-example"></a>Przykład pobierania kolekcji schematów  
 Poniższe przykłady pokazują, <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> jak używać metody dostawcy danych programu <xref:System.Data.SqlClient.SqlConnection> .NET Framework dla klasy PROGRAMU SQL Server do pobierania informacji o schemacie wszystkich tabel zawartych w przykładowej bazie danych **AdventureWorks:**  
  
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

- [Pobieranie informacji o schemacie bazy danych](retrieving-database-schema-information.md)
- [Omówienie ADO.NET](ado-net-overview.md)
