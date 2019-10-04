---
title: Tworzenie zagnieżdżonych zapytań w języku Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 0ab92c1e41c89f141c3cbd37be3e1e18e64d9666
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833915"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="f9b04-102">Tworzenie zagnieżdżonych zapytań w języku Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f9b04-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f9b04-103">to bogaty język funkcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f9b04-103">is a rich functional language.</span></span> <span data-ttu-id="f9b04-104">Blok konstrukcyjny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="f9b04-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="f9b04-105">W przeciwieństwie do konwencjonalnych SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest ograniczony do tabelarycznego zestawu wyników: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje redagowanie złożonych wyrażeń, które mogą mieć literały, parametry lub wyrażenia zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="f9b04-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="f9b04-106">Wartość w wyrażeniu może być sparametryzowane lub składać się z innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f9b04-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="f9b04-107">Wyrażenia zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="f9b04-107">Nested Expressions</span></span>  
 <span data-ttu-id="f9b04-108">Wyrażenie zagnieżdżone można umieścić wszędzie tam, gdzie wartość zwracanego typu jest akceptowana.</span><span class="sxs-lookup"><span data-stu-id="f9b04-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="f9b04-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f9b04-109">For example:</span></span>  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="f9b04-110">Zagnieżdżona kwerenda może być umieszczona w klauzuli projekcji.</span><span class="sxs-lookup"><span data-stu-id="f9b04-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="f9b04-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f9b04-111">For example:</span></span>  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="f9b04-112">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania zagnieżdżone muszą zawsze być ujęte w nawiasy:</span><span class="sxs-lookup"><span data-stu-id="f9b04-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="f9b04-113">W poniższym przykładzie pokazano, jak prawidłowo zagnieżdżać wyrażenia w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order Union of dwa zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f9b04-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="f9b04-114">Zagnieżdżone zapytania w projekcji</span><span class="sxs-lookup"><span data-stu-id="f9b04-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="f9b04-115">Zagnieżdżone zapytania w klauzuli Project mogą zostać przetłumaczone na zapytania dotyczące produktu kartezjańskiego na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f9b04-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="f9b04-116">W przypadku niektórych serwerów zaplecza, w tym serwera magazynem, może to spowodować, że tabela TempDB będzie bardzo duża, co może negatywnie wpłynąć na wydajność serwera.</span><span class="sxs-lookup"><span data-stu-id="f9b04-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="f9b04-117">Oto przykład takiego zapytania:</span><span class="sxs-lookup"><span data-stu-id="f9b04-117">The following is an example of such a query:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="f9b04-118">Porządkowanie zagnieżdżonych zapytań</span><span class="sxs-lookup"><span data-stu-id="f9b04-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="f9b04-119">W Entity Framework wyrażenie zagnieżdżone można umieścić w dowolnym miejscu zapytania.</span><span class="sxs-lookup"><span data-stu-id="f9b04-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="f9b04-120">Ponieważ Entity SQL zapewnia dużą elastyczność podczas pisania zapytań, można napisać zapytanie zawierające kolejność zagnieżdżonych zapytań.</span><span class="sxs-lookup"><span data-stu-id="f9b04-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="f9b04-121">Jednak kolejność zagnieżdżonych zapytań nie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="f9b04-121">However, the order of a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9b04-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9b04-122">See also</span></span>

- [<span data-ttu-id="f9b04-123">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f9b04-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
