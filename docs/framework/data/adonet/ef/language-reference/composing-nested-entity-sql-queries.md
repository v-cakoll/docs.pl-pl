---
title: Tworzenie zagnieżdżonych zapytań w języku Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 6b2fc9a32fc30d205b9c33257bf98781cfa07499
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150392"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="5b693-102">Tworzenie zagnieżdżonych zapytań w języku Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5b693-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5b693-103">jest bogatym językiem funkcjonalnym.</span><span class="sxs-lookup"><span data-stu-id="5b693-103">is a rich functional language.</span></span> <span data-ttu-id="5b693-104">Budulcem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="5b693-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="5b693-105">W przeciwieństwie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do konwencjonalnego SQL, nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ogranicza się do zestaw wyników tabelaryczne: obsługuje tworzenie złożonych wyrażeń, które mogą mieć literały, parametry lub wyrażenia zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="5b693-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="5b693-106">Wartość w wyrażeniu może być sparametryzowana lub składa się z innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5b693-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="5b693-107">Wyrażenia zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="5b693-107">Nested Expressions</span></span>  
 <span data-ttu-id="5b693-108">Wyrażenie zagnieżdżone można umieścić w dowolnym miejscu akceptowana jest wartość typu zwracanego przez niego.</span><span class="sxs-lookup"><span data-stu-id="5b693-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="5b693-109">Przykład:</span><span class="sxs-lookup"><span data-stu-id="5b693-109">For example:</span></span>  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="5b693-110">Zagnieżdżone zapytanie można umieścić w klauzuli rzutowania.</span><span class="sxs-lookup"><span data-stu-id="5b693-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="5b693-111">Przykład:</span><span class="sxs-lookup"><span data-stu-id="5b693-111">For example:</span></span>  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="5b693-112">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zagnieżdżone kwerendy muszą być zawsze ujęte w nawiasy:</span><span class="sxs-lookup"><span data-stu-id="5b693-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="5b693-113">W poniższym przykładzie pokazano, jak [!INCLUDE[esql](../../../../../../includes/esql-md.md)]prawidłowo zagnieżdżać wyrażenia w : [Jak: Kolejność Unii dwóch zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5b693-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="5b693-114">Zagnieżdżone kwerendy w rzutach</span><span class="sxs-lookup"><span data-stu-id="5b693-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="5b693-115">Zagnieżdżone zapytania w klauzuli projektu mogą zostać przetłumaczone na zapytania produktów kartezjańskich na serwerze.</span><span class="sxs-lookup"><span data-stu-id="5b693-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="5b693-116">W niektórych serwerach wewnętrznej bazy danych, w tym SQL Server, może to spowodować, że tabela TempDB uzyskać bardzo duże, co może niekorzystnie wpłynąć na wydajność serwera.</span><span class="sxs-lookup"><span data-stu-id="5b693-116">In some backend servers, including SQL Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="5b693-117">Oto przykład takiej kwerendy:</span><span class="sxs-lookup"><span data-stu-id="5b693-117">The following is an example of such a query:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="5b693-118">Zamawianie zapytań zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="5b693-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="5b693-119">W entity framework zagnieżdżone wyrażenie można umieścić w dowolnym miejscu w kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="5b693-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="5b693-120">Ponieważ entity SQL umożliwia dużą elastyczność w pisaniu zapytań, istnieje możliwość zapisu kwerendy, która zawiera kolejność zapytań zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="5b693-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="5b693-121">Jednak kolejność kwerendy zagnieżdżonej nie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="5b693-121">However, the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b693-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b693-122">See also</span></span>

- [<span data-ttu-id="5b693-123">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b693-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
