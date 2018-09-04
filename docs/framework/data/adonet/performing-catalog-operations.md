---
title: Wykonywanie operacji katalogu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 7588b2b4592a5298a69eb4adfbc06edb6913ef76
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519099"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="d5a8a-102">Wykonywanie operacji katalogu</span><span class="sxs-lookup"><span data-stu-id="d5a8a-102">Performing Catalog Operations</span></span>
<span data-ttu-id="d5a8a-103">Wykonanie polecenia do modyfikowania bazy danych lub katalogu, np. wykonywanie instrukcji CREATE TABLE lub utworzyć procedurę tworzenia **polecenia** przy użyciu odpowiedniej instrukcji SQL i **połączenia** obiektu.</span><span class="sxs-lookup"><span data-stu-id="d5a8a-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="d5a8a-104">Wykonanie polecenia za pomocą **ExecuteNonQuery** metody **polecenia** obiektu.</span><span class="sxs-lookup"><span data-stu-id="d5a8a-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="d5a8a-105">Poniższy przykład kodu tworzy procedurę składowaną w bazie danych programu Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d5a8a-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +   
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +   
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +   
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5a8a-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5a8a-106">See Also</span></span>  
 [<span data-ttu-id="d5a8a-107">Używanie poleceń do modyfikacji danych</span><span class="sxs-lookup"><span data-stu-id="d5a8a-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="d5a8a-108">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="d5a8a-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="d5a8a-109">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d5a8a-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
