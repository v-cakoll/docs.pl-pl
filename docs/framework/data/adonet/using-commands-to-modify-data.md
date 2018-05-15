---
title: Aby zmodyfikować danych za pomocą poleceń
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 9f13eb2079df959281a44086edf84c34f3c63a14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="71833-102">Aby zmodyfikować danych za pomocą poleceń</span><span class="sxs-lookup"><span data-stu-id="71833-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="71833-103">Przy użyciu dostawcy danych .NET Framework, można wykonać procedur składowanych lub instrukcje języka definicji danych (na przykład CREATE TABLE i ALTER COLUMN) podczas manipulowania schematu bazy danych lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="71833-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="71833-104">Tych poleceń nie zwracają wierszy, jak zapytania, więc **polecenia** zawiera obiekt **ExecuteNonQuery** do ich przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="71833-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="71833-105">Oprócz używania **ExecuteNonQuery** do modyfikowania schematu, umożliwia także tę metodę, aby proces instrukcji SQL, które modyfikują dane, ale nie zwracanie wszystkich wierszy, takie jak INSERT, UPDATE i usunąć.</span><span class="sxs-lookup"><span data-stu-id="71833-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="71833-106">Mimo że wierszy nie są zwracane przez **ExecuteNonQuery** przekazany i zwracane przez metody wejściowe i wyjściowe parametrów i zwracanych wartości **parametry** Kolekcja **polecenia**  obiektu.</span><span class="sxs-lookup"><span data-stu-id="71833-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71833-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="71833-107">In This Section</span></span>  
 [<span data-ttu-id="71833-108">Aktualizowanie danych w źródle danych</span><span class="sxs-lookup"><span data-stu-id="71833-108">Updating Data in a Data Source</span></span>](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 <span data-ttu-id="71833-109">Opisuje sposób wykonywania poleceń lub procedur składowanych, które modyfikują dane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="71833-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="71833-110">Wykonywanie operacji katalogu</span><span class="sxs-lookup"><span data-stu-id="71833-110">Performing Catalog Operations</span></span>](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 <span data-ttu-id="71833-111">Opisuje sposób wykonywania poleceń, które modyfikują schemat bazy danych.</span><span class="sxs-lookup"><span data-stu-id="71833-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71833-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71833-112">See Also</span></span>  
 [<span data-ttu-id="71833-113">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="71833-113">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="71833-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="71833-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="71833-115">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="71833-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
