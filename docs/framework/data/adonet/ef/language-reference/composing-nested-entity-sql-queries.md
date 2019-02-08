---
title: Tworzenie zagnieżdżonych zapytań jednostki SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: b5fc39a25b5b8592117348b150da9d82454a1562
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827321"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="c72f0-102">Tworzenie zagnieżdżonych zapytań jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c72f0-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c72f0-103">jest bogaty język funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="c72f0-103">is a rich functional language.</span></span> <span data-ttu-id="c72f0-104">Elementem składowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="c72f0-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="c72f0-105">W przeciwieństwie do poziomu konwencjonalnego SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest ograniczona do zestawu wyniku tabelarycznym: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje tworzenie złożonych wyrażeń, które mogą mieć literały, parametry lub zagnieżdżonych wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="c72f0-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="c72f0-106">Wartości w wyrażeniu można ustawiać parametry lub składa się z niektóre inne wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="c72f0-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="c72f0-107">Nested Expressions</span><span class="sxs-lookup"><span data-stu-id="c72f0-107">Nested Expressions</span></span>  
 <span data-ttu-id="c72f0-108">Zagnieżdżone wyrażenie można umieścić w dowolnym miejscu wartości typu, zwracana jest akceptowany.</span><span class="sxs-lookup"><span data-stu-id="c72f0-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="c72f0-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c72f0-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="c72f0-110">Zapytanie zagnieżdżone można umieścić w klauzuli projekcji.</span><span class="sxs-lookup"><span data-stu-id="c72f0-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="c72f0-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c72f0-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="c72f0-112">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zapytań zagnieżdżonej zawsze muszą być ujęte w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="c72f0-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="c72f0-113">Poniższy przykład pokazuje, jak poprawnie zagnieździć wyrażeń w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [Instrukcje: Kolejność sumę dwóch zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c72f0-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="c72f0-114">Zapytania zagnieżdżone w projekcji</span><span class="sxs-lookup"><span data-stu-id="c72f0-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="c72f0-115">Zapytania zagnieżdżone w klauzuli projektu może uzyskać przetłumaczone na zapytania formułuje iloczyn na serwerze.</span><span class="sxs-lookup"><span data-stu-id="c72f0-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="c72f0-116">W niektórych serwerów wewnętrznej bazy danych, w tym SQL Server może to spowodować tabeli bazy danych TempDB, aby stać się bardzo duże, który może niekorzystnie wpłynąć na wydajność serwera.</span><span class="sxs-lookup"><span data-stu-id="c72f0-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="c72f0-117">Oto przykład w przypadku takiego zapytania:</span><span class="sxs-lookup"><span data-stu-id="c72f0-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="c72f0-118">Określanie kolejności zapytań zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="c72f0-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="c72f0-119">Platformy Entity Framework zagnieżdżone wyrażenie można umieścić dowolne miejsce w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="c72f0-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="c72f0-120">Ponieważ jednostka SQL pozwala na większą elastyczność w pisaniu zapytań, istnieje możliwość napisania zapytanie, które zawiera kolejność zapytań zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="c72f0-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="c72f0-121">Kolejność zapytanie zagnieżdżone nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="c72f0-121">However, the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="c72f0-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c72f0-122">See also</span></span>
- [<span data-ttu-id="c72f0-123">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c72f0-123">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
