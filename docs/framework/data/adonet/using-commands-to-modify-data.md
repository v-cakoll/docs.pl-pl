---
title: Używanie poleceń do modyfikacji danych
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 34c73549f18cd4bebb8caf842b252828b7f0a185
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780562"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="dc428-102">Używanie poleceń do modyfikacji danych</span><span class="sxs-lookup"><span data-stu-id="dc428-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="dc428-103">Za pomocą .NET Framework dostawcy danych można wykonać procedury składowane lub instrukcje języka definicji danych (na przykład CREATE TABLE i zmienić kolumnę), aby wykonać manipulowanie schematem bazy danych lub wykazu.</span><span class="sxs-lookup"><span data-stu-id="dc428-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="dc428-104">Te polecenia nie zwracają wierszy jako zapytania, dlatego obiekt **Command** udostępnia **ExecuteNonQuery** do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="dc428-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="dc428-105">Oprócz używania **ExecuteNonQuery** do modyfikowania schematu, można również użyć tej metody do przetwarzania instrukcji SQL, które modyfikują dane, ale nie zwracają wierszy, takich jak INSERT, Update i DELETE.</span><span class="sxs-lookup"><span data-stu-id="dc428-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="dc428-106">Chociaż wiersze nie są zwracane przez metodę **ExecuteNonQuery** , parametry wejściowe i wyjściowe oraz zwracane wartości mogą być przekazywane i zwracane za pośrednictwem kolekcji **Parameters** obiektu **Command** .</span><span class="sxs-lookup"><span data-stu-id="dc428-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc428-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dc428-107">In This Section</span></span>  
 [<span data-ttu-id="dc428-108">Aktualizowanie danych w źródle danych</span><span class="sxs-lookup"><span data-stu-id="dc428-108">Updating Data in a Data Source</span></span>](updating-data-in-a-data-source.md)  
 <span data-ttu-id="dc428-109">Opisuje sposób wykonywania poleceń lub procedur składowanych, które modyfikują dane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="dc428-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="dc428-110">Wykonywanie operacji katalogu</span><span class="sxs-lookup"><span data-stu-id="dc428-110">Performing Catalog Operations</span></span>](performing-catalog-operations.md)  
 <span data-ttu-id="dc428-111">Opisuje sposób wykonywania poleceń, które modyfikują schemat bazy danych.</span><span class="sxs-lookup"><span data-stu-id="dc428-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc428-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc428-112">See also</span></span>

- [<span data-ttu-id="dc428-113">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dc428-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="dc428-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="dc428-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="dc428-115">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dc428-115">ADO.NET Overview</span></span>](ado-net-overview.md)
