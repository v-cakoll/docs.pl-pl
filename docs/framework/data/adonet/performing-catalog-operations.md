---
title: Wykonywanie operacji katalogu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 0291b6684092ec15fc672c39c909caf7781194e3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783256"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="7c313-102">Wykonywanie operacji katalogu</span><span class="sxs-lookup"><span data-stu-id="7c313-102">Performing Catalog Operations</span></span>
<span data-ttu-id="7c313-103">Aby wykonać polecenie modyfikacji bazy danych lub wykazu, takie jak CREATE TABLE lub CREATE PROCEDURe, Utwórz obiekt **Command** przy użyciu odpowiednich instrukcji SQL i obiektu **Connection** .</span><span class="sxs-lookup"><span data-stu-id="7c313-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="7c313-104">Wykonaj polecenie za pomocą metody **ExecuteNonQuery** obiektu **Command** .</span><span class="sxs-lookup"><span data-stu-id="7c313-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="7c313-105">Poniższy przykład kodu tworzy procedurę przechowywaną w bazie danych Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7c313-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c313-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c313-106">See also</span></span>

- [<span data-ttu-id="7c313-107">Używanie poleceń do modyfikacji danych</span><span class="sxs-lookup"><span data-stu-id="7c313-107">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="7c313-108">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="7c313-108">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="7c313-109">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7c313-109">ADO.NET Overview</span></span>](ado-net-overview.md)
