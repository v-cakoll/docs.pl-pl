---
title: "Tworzenie zapytań SQL zagnieżdżonych jednostki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6aab21c4b22e731f3d85a2f444e82bc04906c320
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="a849e-102">Tworzenie zapytań SQL zagnieżdżonych jednostki</span><span class="sxs-lookup"><span data-stu-id="a849e-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a849e-103">jest bogaty język funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="a849e-103"> is a rich functional language.</span></span> <span data-ttu-id="a849e-104">Blokiem konstrukcyjnym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="a849e-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="a849e-105">W przeciwieństwie do konwencjonalnych SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest ograniczone do zestawu wyników tabelarycznym: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje tworzenie złożonych wyrażeń, które mogą mieć literały, parametry lub zagnieżdżonych wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a849e-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="a849e-106">Wartość w wyrażeniu można sparametryzowanych lub składa się z niektórych innych wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a849e-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="a849e-107">Zagnieżdżone wyrażenia</span><span class="sxs-lookup"><span data-stu-id="a849e-107">Nested Expressions</span></span>  
 <span data-ttu-id="a849e-108">Zagnieżdżone wyrażenia można umieścić w dowolnym wartości typu, zwracana jest akceptowany.</span><span class="sxs-lookup"><span data-stu-id="a849e-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="a849e-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a849e-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="a849e-110">Zapytanie zagnieżdżone można umieścić w klauzuli projekcji.</span><span class="sxs-lookup"><span data-stu-id="a849e-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="a849e-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a849e-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="a849e-112">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zapytania zagnieżdżone zawsze musi być ujęta w nawiasy:</span><span class="sxs-lookup"><span data-stu-id="a849e-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="a849e-113">W poniższym przykładzie pokazano sposób poprawnie zagnieździć wyrażenia w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [porady: kolejność Unii o dwa zapytania](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313).</span><span class="sxs-lookup"><span data-stu-id="a849e-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="a849e-114">Zapytania zagnieżdżone w projekcji</span><span class="sxs-lookup"><span data-stu-id="a849e-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="a849e-115">Zapytania zagnieżdżone w klauzuli projektu może pobrać przetłumaczyć iloczyn kartezjański zapytania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="a849e-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="a849e-116">W niektórych serwerów wewnętrznej bazy danych, w tym SQL Server może to spowodować tabeli bazy danych TempDB uzyskanie bardzo duży, które może niekorzystnie wpłynąć na wydajność serwera.</span><span class="sxs-lookup"><span data-stu-id="a849e-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="a849e-117">Poniżej przedstawiono przykład takiego kwerendy:</span><span class="sxs-lookup"><span data-stu-id="a849e-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="a849e-118">Porządkowanie zapytania zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="a849e-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="a849e-119">W ramach jednostki zagnieżdżone wyrażenia można umieścić dowolne miejsce w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="a849e-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="a849e-120">Ponieważ SQL jednostki pozwala dużą elastyczność w Pisanie zapytań, istnieje możliwość Napisz zapytanie, które zawiera kolejność kwerend zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="a849e-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="a849e-121">Kolejność zapytanie zagnieżdżone nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="a849e-121">However, the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a849e-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a849e-122">See Also</span></span>  
 [<span data-ttu-id="a849e-123">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a849e-123">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
