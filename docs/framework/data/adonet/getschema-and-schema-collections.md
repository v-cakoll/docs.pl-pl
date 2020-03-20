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
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="9b777-102">GetSchema i kolekcje schematów</span><span class="sxs-lookup"><span data-stu-id="9b777-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="9b777-103">**Klasy połączenia** w każdym z dostawców zarządzanych programu .NET Framework implementują metodę **GetSchema,** która jest używana do pobierania informacji o schemacie o aktualnie połączonej bazie danych, a informacje o schemacie zwrócone z metody **GetSchema** są dostępne w postaci pliku <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="9b777-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="9b777-104">**Metoda GetSchema** jest przeciążona metoda, która zapewnia opcjonalne parametry do określania kolekcji schematu do zwrócenia i ograniczania ilości zwracanych informacji.</span><span class="sxs-lookup"><span data-stu-id="9b777-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="9b777-105">Określanie kolekcji schematu</span><span class="sxs-lookup"><span data-stu-id="9b777-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="9b777-106">Pierwszy opcjonalny parametr **Metody GetSchema** jest nazwą kolekcji, która jest określona jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="9b777-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="9b777-107">Istnieją dwa typy kolekcji schematu: typowe kolekcje schematów, które są wspólne dla wszystkich dostawców i kolekcje określonego schematu, które są specyficzne dla każdego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="9b777-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="9b777-108">Można zbadać dostawcę zarządzanego programu .NET Framework, aby określić listę obsługiwanych kolekcji schematu, wywołując metodę **GetSchema** bez argumentów lub o nazwie kolekcji schematu "MetaDataCollections".</span><span class="sxs-lookup"><span data-stu-id="9b777-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="9b777-109">Spowoduje to <xref:System.Data.DataTable> zwrócenie a z listy obsługiwanych kolekcji schematu, liczba ograniczeń, które obsługują, a liczba części identyfikatorów, które używają.</span><span class="sxs-lookup"><span data-stu-id="9b777-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="9b777-110">Przykład pobierania kolekcji schematów</span><span class="sxs-lookup"><span data-stu-id="9b777-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="9b777-111">Poniższe przykłady pokazują, <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> jak używać metody dostawcy danych programu <xref:System.Data.SqlClient.SqlConnection> .NET Framework dla klasy PROGRAMU SQL Server do pobierania informacji o schemacie wszystkich tabel zawartych w przykładowej bazie danych **AdventureWorks:**</span><span class="sxs-lookup"><span data-stu-id="9b777-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9b777-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b777-112">See also</span></span>

- [<span data-ttu-id="9b777-113">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="9b777-113">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="9b777-114">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b777-114">ADO.NET Overview</span></span>](ado-net-overview.md)
