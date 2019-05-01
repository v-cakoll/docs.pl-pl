---
title: Używanie poleceń do modyfikacji danych
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: f2e3d162bfbdcb79cfecefa4ddc8e6a0dc46ee3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875956"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="69152-102">Używanie poleceń do modyfikacji danych</span><span class="sxs-lookup"><span data-stu-id="69152-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="69152-103">Za pomocą dostawcy danych .NET Framework, można wykonać procedury składowanej lub instrukcje języka definicji danych (na przykład polecenia CREATE TABLE i ALTER COLUMN) wykonywać operacje na schemat bazy danych lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="69152-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="69152-104">Te polecenia nie zwracają wiersze, tak jak zapytania, więc **polecenia** obiektu **ExecuteNonQuery** do ich przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="69152-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="69152-105">Oprócz używania **ExecuteNonQuery** do modyfikacji schematu, umożliwia także tę metodę w celu przetwarzania instrukcji SQL modyfikujących dane, ale nie zwraca wiersze, takich jak INSERT, UPDATE i usunąć.</span><span class="sxs-lookup"><span data-stu-id="69152-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="69152-106">Mimo że wierszy nie są zwracane przez **ExecuteNonQuery** przekazane i zwracane przez metody wejściowe i wyjściowe parametrów i zwracanych wartości **parametry** zbiór **polecenia**  obiektu.</span><span class="sxs-lookup"><span data-stu-id="69152-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69152-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="69152-107">In This Section</span></span>  
 [<span data-ttu-id="69152-108">Aktualizowanie danych w źródle danych</span><span class="sxs-lookup"><span data-stu-id="69152-108">Updating Data in a Data Source</span></span>](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 <span data-ttu-id="69152-109">W tym artykule opisano sposób wykonywania poleceń lub procedur składowanych, które modyfikują dane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="69152-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="69152-110">Wykonywanie operacji katalogu</span><span class="sxs-lookup"><span data-stu-id="69152-110">Performing Catalog Operations</span></span>](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 <span data-ttu-id="69152-111">W tym artykule opisano sposób wykonywania poleceń, które modyfikują schemat bazy danych.</span><span class="sxs-lookup"><span data-stu-id="69152-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69152-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69152-112">See also</span></span>

- [<span data-ttu-id="69152-113">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="69152-113">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="69152-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="69152-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="69152-115">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="69152-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
