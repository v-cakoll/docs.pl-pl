---
title: GetSchema i kolekcje schematów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: 4ac0216ce2965d555f7283ba66a085ea9d7cac3c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783836"
---
# <a name="getschema-and-schema-collections"></a>GetSchema i kolekcje schematów
Klasy **połączeń** w każdym z .NET Framework dostawców zarządzanych implementują metodę **GetSchema** , która jest używana do pobierania informacji o schemacie, która jest aktualnie połączona, oraz informacji o schemacie zwróconych z  **Metoda GetSchema** ma <xref:System.Data.DataTable>postać. Metoda **GetSchema** jest przeciążoną metodą, która zapewnia parametry opcjonalne do określania kolekcji schematów do zwrócenia i ograniczając ilość zwracanych informacji.  
  
## <a name="specifying-the-schema-collections"></a>Określanie kolekcji schematów  
 Pierwszy opcjonalny parametr metody **GetSchema** jest nazwą kolekcji, która jest określona jako ciąg. Istnieją dwa typy kolekcji schematów: wspólne kolekcje schematów, które są wspólne dla wszystkich dostawców i konkretne kolekcje schematów, które są specyficzne dla każdego dostawcy.  
  
 Można wysłać zapytanie do dostawcy zarządzanego .NET Framework, aby określić listę obsługiwanych kolekcji schematów przez wywołanie metody **GetSchema** bez argumentów lub z nazwą kolekcji schematów "MetaDataCollections". Spowoduje to zwrócenie <xref:System.Data.DataTable> listy obsługiwanych kolekcji schematów, liczbę ograniczeń, które one obsługują, oraz liczbę używanych przez nich części identyfikatora.  
  
### <a name="retrieving-schema-collections-example"></a>Przykład pobierania kolekcji schematów  
 W poniższych przykładach pokazano, jak za <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> pomocą metody dostawca danych .NET Framework dla klasy SQL Server <xref:System.Data.SqlClient.SqlConnection> pobrać informacje o schemacie dotyczące wszystkich tabel zawartych w przykładowej bazie danych **AdventureWorks** :  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie informacji o schemacie bazy danych](retrieving-database-schema-information.md)
- [Omówienie ADO.NET](ado-net-overview.md)
