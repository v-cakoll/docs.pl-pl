---
title: Wykonywanie operacji katalogu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: c1d8b9dd579cae7f4868058343c034caf17c5fff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="00649-102">Wykonywanie operacji katalogu</span><span class="sxs-lookup"><span data-stu-id="00649-102">Performing Catalog Operations</span></span>
<span data-ttu-id="00649-103">Do wykonania polecenia, aby zmodyfikować bazy danych lub katalogu, takie jak wykonywanie instrukcji CREATE TABLE lub CREATE PROCEDURE utworzyć **polecenia** przy użyciu odpowiedniej instrukcji SQL i **połączenia** obiektu.</span><span class="sxs-lookup"><span data-stu-id="00649-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="00649-104">Wykonaj polecenie z **ExecuteNonQuery** metody **polecenia** obiektu.</span><span class="sxs-lookup"><span data-stu-id="00649-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="00649-105">Poniższy przykład kodu tworzy procedurę przechowywaną w bazie danych programu Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="00649-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="00649-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00649-106">See Also</span></span>  
 [<span data-ttu-id="00649-107">Używanie poleceń do modyfikacji danych</span><span class="sxs-lookup"><span data-stu-id="00649-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="00649-108">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="00649-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="00649-109">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="00649-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
