---
title: GROUPPARTITION (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ceadd193784a2c1936b0dcc2d634ae87b513e57e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="20bf8-102">GROUPPARTITION (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="20bf8-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="20bf8-103">Zwraca kolekcję wartości argumentów, które są przewidywane poza bieżącą partycję grupy, do którego odnosi się agregacji.</span><span class="sxs-lookup"><span data-stu-id="20bf8-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="20bf8-104">`GroupPartition` Agregacji jest oparte na grupach agregacji i nie ma opartego na kolekcji formy.</span><span class="sxs-lookup"><span data-stu-id="20bf8-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20bf8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="20bf8-105">Syntax</span></span>  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="20bf8-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="20bf8-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="20bf8-107">Wszelkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="20bf8-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20bf8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20bf8-108">Remarks</span></span>  
 <span data-ttu-id="20bf8-109">Następujące zapytanie generuje listę produktów i kolekcję ilości wierszy w kolejności dla każdego produktu:</span><span class="sxs-lookup"><span data-stu-id="20bf8-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="20bf8-110">Następujące dwa zapytania są semantycznie równe:</span><span class="sxs-lookup"><span data-stu-id="20bf8-110">The following two queries are semantically equal:</span></span>  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="20bf8-111">`GROUPPARTITION` Operator może być używany w połączeniu z funkcjami agregującymi zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="20bf8-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
 <span data-ttu-id="20bf8-112">`GROUPPARTITION`to specjalne operatora agregacji, który zawiera odwołanie do zestawu wejściowego grupowanych.</span><span class="sxs-lookup"><span data-stu-id="20bf8-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="20bf8-113">To odwołanie można dowolne miejsce w zapytaniu gdzie GROUP BY znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="20bf8-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="20bf8-114">Na przykład</span><span class="sxs-lookup"><span data-stu-id="20bf8-114">For example,</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="20bf8-115">Regularne GROUP BY wyniki grupowanie są ukryte.</span><span class="sxs-lookup"><span data-stu-id="20bf8-115">With a regular GROUP BY, the results of the grouping are hidden.</span></span> <span data-ttu-id="20bf8-116">Wyniki można używać tylko w funkcji agregującej.</span><span class="sxs-lookup"><span data-stu-id="20bf8-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="20bf8-117">Aby wyświetlić wyniki grupowanie, masz służące do skorelowania wyniki grupowanie i ustawić przy użyciu podzapytania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="20bf8-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="20bf8-118">Następujące dwa zapytania są równoważne:</span><span class="sxs-lookup"><span data-stu-id="20bf8-118">The following two queries are equivalent:</span></span>  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="20bf8-119">Jak pokazano w przykładzie, operatora agregacji GROUPPARTITION ułatwia odwołać się do danych wejściowych po grupowanie.</span><span class="sxs-lookup"><span data-stu-id="20bf8-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="20bf8-120">GROUPPARTITION operator można określić dowolną [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażenie w operatorze wejściowych, jeśli używasz `expression` parametru.</span><span class="sxs-lookup"><span data-stu-id="20bf8-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="20bf8-121">Na przykład wszystkie następujące wyrażeń wejściowych do partycji grupy są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="20bf8-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="20bf8-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="20bf8-122">Example</span></span>  
 <span data-ttu-id="20bf8-123">Poniższy przykład przedstawia sposób użycia klauzuli GROUPPARTITION z klauzulą GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="20bf8-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="20bf8-124">Grupy klauzuli GROUP BY `SalesOrderHeader` jednostek według ich `Contact`.</span><span class="sxs-lookup"><span data-stu-id="20bf8-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="20bf8-125">Klauzula GROUPPARTITION, a następnie projekty `TotalDue` właściwości dla każdej grupy, co w kolekcji miejsc dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="20bf8-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
