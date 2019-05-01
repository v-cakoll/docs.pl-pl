---
title: GROUPPARTITION (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774728"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="bfdb4-102">GROUPPARTITION (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="bfdb4-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="bfdb4-103">Zwraca kolekcję wartości argumentów, które są pokazane poza bieżącą partycję grupy, do którego odnosi się agregacji.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="bfdb4-104">`GroupPartition` Agregacji jest oparte na grupach agregacji i nie ma związanych z kolekcjami formy.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfdb4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bfdb4-105">Syntax</span></span>  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="bfdb4-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bfdb4-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="bfdb4-107">Wszelkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfdb4-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfdb4-108">Remarks</span></span>  
 <span data-ttu-id="bfdb4-109">Następujące zapytanie generuje listę produktów i zbiór ilości wierszy w kolejności dla każdego produktu:</span><span class="sxs-lookup"><span data-stu-id="bfdb4-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="bfdb4-110">Następujące dwa zapytania są semantycznie równe:</span><span class="sxs-lookup"><span data-stu-id="bfdb4-110">The following two queries are semantically equal:</span></span>  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="bfdb4-111">`GROUPPARTITION` Operatora można używać w połączeniu z funkcjami agregującymi zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
 <span data-ttu-id="bfdb4-112">`GROUPPARTITION` to specjalne aggregate-operator, który zawiera odwołanie do zestawu pogrupowanych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="bfdb4-113">Ta dokumentacja może służyć wszędzie w zapytaniu gdzie GROUP BY znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="bfdb4-114">Na przykład</span><span class="sxs-lookup"><span data-stu-id="bfdb4-114">For example,</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="bfdb4-115">Za pomocą regularnego GROUP BY wyniki grupowania są ukryte.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-115">With a regular GROUP BY, the results of the grouping are hidden.</span></span> <span data-ttu-id="bfdb4-116">Wyniki można używać tylko w funkcji agregującej.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="bfdb4-117">Aby wyświetlić wyniki grupowania, należy skorelować wyniki, grupowanie i ustawić za pomocą podzapytania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="bfdb4-118">Następujące dwa zapytania są równoważne:</span><span class="sxs-lookup"><span data-stu-id="bfdb4-118">The following two queries are equivalent:</span></span>  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="bfdb4-119">Jak widać w przykładzie, aggregate-operator GROUPPARTITION sprawia, że łatwiej uzyskać odwołanie do ustawienia po grupowania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="bfdb4-120">GROUPPARTITION operator można określić dowolną [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażenie w operatorze danych wejściowych, gdy używasz `expression` parametru.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="bfdb4-121">Na przykład wszystkie poniższe wyrażenia wejściowego do partycji grupy są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="bfdb4-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="bfdb4-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="bfdb4-122">Example</span></span>  
 <span data-ttu-id="bfdb4-123">Poniższy przykład przedstawia sposób użycia klauzuli GROUPPARTITION z klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="bfdb4-124">Grupy klauzuli GROUP BY `SalesOrderHeader` jednostek według ich `Contact`.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="bfdb4-125">Klauzula GROUPPARTITION, a następnie projekty `TotalDue` właściwości dla każdej grupy, wynikiem kolekcji miejsc po przecinku.</span><span class="sxs-lookup"><span data-stu-id="bfdb4-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
