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
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="5a751-102">GetSchema i kolekcje schematów</span><span class="sxs-lookup"><span data-stu-id="5a751-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="5a751-103">**Połączenia** klas w każdej implementacji zarządzanego dostawcy .NET Framework **GetSchema** metodę, która służy do pobierania informacji o schemacie o bazie danych, który jest obecnie połączony, i informacje o schemacie zwróciło **GetSchema** metody jest dostarczany w formie <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="5a751-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="5a751-104">**GetSchema** metodą jest przeciążona metoda, która zapewnia następujące parametry opcjonalne określanie kolekcji schematów, aby powrócić i ograniczając ilość zwracanych informacji.</span><span class="sxs-lookup"><span data-stu-id="5a751-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="5a751-105">Określanie kolekcje schematów</span><span class="sxs-lookup"><span data-stu-id="5a751-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="5a751-106">Pierwszy parametr opcjonalny **GetSchema** metoda to nazwa kolekcji, która jest określana jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="5a751-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="5a751-107">Istnieją dwa typy kolekcje schematów: Typowe kolekcje schematów, które są wspólne dla wszystkich dostawców i kolekcje określonego schematu, które są specyficzne dla każdego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5a751-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="5a751-108">Można tworzyć zapytania zarządzanego dostawcy .NET Framework, aby określić listę kolekcje schematów obsługiwanych przez wywołanie metody **GetSchema** metody bez argumentów lub nazwą kolekcji schematów "MetaDataCollections".</span><span class="sxs-lookup"><span data-stu-id="5a751-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="5a751-109">Spowoduje to zwrócenie <xref:System.Data.DataTable> z listą kolekcje schematów obsługiwanych, liczba ograniczeń, które obsługują one każdego i części identyfikator, których używają.</span><span class="sxs-lookup"><span data-stu-id="5a751-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="5a751-110">Pobieranie schematu przykład kolekcji</span><span class="sxs-lookup"><span data-stu-id="5a751-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="5a751-111">W poniższych przykładach pokazano sposób użycia <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metody .NET Framework Data Provider for SQL Server <xref:System.Data.SqlClient.SqlConnection> klasy do pobrania informacji o schemacie o wszystkich tabelach zawartych w **AdventureWorks**przykładowej bazy danych:</span><span class="sxs-lookup"><span data-stu-id="5a751-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a751-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a751-112">See Also</span></span>  
 [<span data-ttu-id="5a751-113">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="5a751-113">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="5a751-114">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="5a751-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
