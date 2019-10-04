---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 19df566c254a3f3202eb3554ab43ee0d7c944181
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833755"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="8f170-102">GROUPPARTITION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8f170-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="8f170-103">Zwraca kolekcję wartości argumentów, które są rzutowane na bieżącą partycję grupy, z którą jest powiązana agregacja.</span><span class="sxs-lookup"><span data-stu-id="8f170-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="8f170-104">Agregacja `GroupPartition` jest agregacją opartą na grupach i nie ma formy opartej na kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8f170-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f170-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f170-105">Syntax</span></span>  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f170-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8f170-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8f170-107">Dowolne wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f170-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f170-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f170-108">Remarks</span></span>  
 <span data-ttu-id="8f170-109">Następujące zapytanie tworzy listę produktów i zbiór ilości wierszy zamówień dla każdego produktu:</span><span class="sxs-lookup"><span data-stu-id="8f170-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="8f170-110">Następujące dwa zapytania są semantycznie równe:</span><span class="sxs-lookup"><span data-stu-id="8f170-110">The following two queries are semantically equal:</span></span>  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 <span data-ttu-id="8f170-111">Operatora `GROUPPARTITION` można używać w połączeniu z funkcjami agregującymi zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8f170-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
<span data-ttu-id="8f170-112">`GROUPPARTITION` jest specjalnym operatorem agregującym, który przechowuje odwołanie do zgrupowanego zestawu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8f170-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="8f170-113">Tego odwołania można użyć w dowolnym miejscu w zapytaniu, w którym Grupuj według znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="8f170-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="8f170-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8f170-114">For example:</span></span>
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="8f170-115">W przypadku zwykłego `GROUP BY` wyniki grupowania są ukryte.</span><span class="sxs-lookup"><span data-stu-id="8f170-115">With a regular `GROUP BY`, the results of the grouping are hidden.</span></span> <span data-ttu-id="8f170-116">Wyniki można używać tylko w funkcji agregującej.</span><span class="sxs-lookup"><span data-stu-id="8f170-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="8f170-117">Aby wyświetlić wyniki grupowania, należy skorelować wyniki grupowania i zestawu wejściowego za pomocą podzapytania...</span><span class="sxs-lookup"><span data-stu-id="8f170-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="8f170-118">Następujące dwa zapytania są równoważne:</span><span class="sxs-lookup"><span data-stu-id="8f170-118">The following two queries are equivalent:</span></span>  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="8f170-119">Jak pokazano na przykładzie, operator agregujący GROUPPARTITION ułatwia uzyskanie odwołania do zestawu wejściowego po grupowaniu.</span><span class="sxs-lookup"><span data-stu-id="8f170-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="8f170-120">Operator GROUPPARTITION może określić dowolne wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w danych wejściowych operatora, gdy używany jest parametr `expression`.</span><span class="sxs-lookup"><span data-stu-id="8f170-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="8f170-121">Dla wystąpienia wszystkie następujące wyrażenia wejściowe do partycji grupy są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="8f170-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="8f170-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f170-122">Example</span></span>  
 <span data-ttu-id="8f170-123">Poniższy przykład pokazuje, jak używać klauzuli GROUPPARTITION z klauzulą GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="8f170-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="8f170-124">Klauzula GROUP BY grupuje jednostki `SalesOrderHeader` według ich `Contact`.</span><span class="sxs-lookup"><span data-stu-id="8f170-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="8f170-125">Klauzula GROUPPARTITION następnie projektuje Właściwość `TotalDue` dla każdej grupy, co skutkuje kolekcją miejsc dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="8f170-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
