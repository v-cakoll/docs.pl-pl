---
title: "Funkcje agregujące (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1ed9a7532269a149f6f522e8fe9c6161e1aae27
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="f719f-102">Funkcje agregujące (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="f719f-102">Aggregate Functions (Entity SQL)</span></span>
<span data-ttu-id="f719f-103">Wartość zagregowana jest konstrukcji języka, który pozwala zapisać kolekcji do skalarnej w ramach operacji grupy.</span><span class="sxs-lookup"><span data-stu-id="f719f-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="f719f-104">agregacje są dostępne w dwóch formach:</span><span class="sxs-lookup"><span data-stu-id="f719f-104"> aggregates come in two forms:</span></span>  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="f719f-105">Kolekcja funkcji, które mogą być używane w dowolnym miejscu w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="f719f-105"> collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="f719f-106">W tym za pomocą funkcji agregujących w projekcjach i predykatów, które działają w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="f719f-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="f719f-107">Funkcji kolekcji jest preferowanym trybem określania wartości zagregowanych w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f719f-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
-   <span data-ttu-id="f719f-108">Grupuj wartości zagregowanych w wyrażeniach zapytań, które mają klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="f719f-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="f719f-109">Podobnie jak w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], agregacje grupy Zaakceptuj DISTINCT, a wszystkie jako modyfikatory do agregacji danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f719f-109">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="f719f-110">po raz pierwszy próbuje zinterpretować wyrażenia w funkcji kolekcji i jeśli wyrażenie jest w kontekście wyrażenia SELECT zinterpretuje ją jako agregacja grupy.</span><span class="sxs-lookup"><span data-stu-id="f719f-110"> first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="f719f-111">Definiuje specjalne operatora agregacji o nazwie [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f719f-111"> defines a special aggregate operator called [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span></span> <span data-ttu-id="f719f-112">Ten operator pozwala uzyskać odwołania do zestawu wejściowego grupowanych.</span><span class="sxs-lookup"><span data-stu-id="f719f-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="f719f-113">Umożliwia to bardziej zaawansowanych zapytań, grupowanie, gdzie można wyniki w klauzuli GROUP BY w miejscach innych niż agregacji grup lub kolekcji funkcji.</span><span class="sxs-lookup"><span data-stu-id="f719f-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="f719f-114">Kolekcja funkcji</span><span class="sxs-lookup"><span data-stu-id="f719f-114">Collection Functions</span></span>  
 <span data-ttu-id="f719f-115">Kolekcja funkcji działać w kolekcjach i zwracać wartość skalarną.</span><span class="sxs-lookup"><span data-stu-id="f719f-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="f719f-116">Na przykład jeśli `orders` to zbiór wszystkich `orders`, można obliczyć Najwcześniejsza data wysyłki z następującym wyrażeniem:</span><span class="sxs-lookup"><span data-stu-id="f719f-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="f719f-117">Agreguje grupy</span><span class="sxs-lookup"><span data-stu-id="f719f-117">Group Aggregates</span></span>  
 <span data-ttu-id="f719f-118">Agreguje grupy są obliczane w wyniku grupy, zgodnie z definicją w klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="f719f-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="f719f-119">W klauzuli GROUP BY partycje danych w grupach.</span><span class="sxs-lookup"><span data-stu-id="f719f-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="f719f-120">Dla każdej grupy w wyniku zastosowaniu funkcji agregującej i oddzielne agregacji jest obliczana przy użyciu elementów w każdej grupie jako danych wejściowych w celu obliczania agregacji.</span><span class="sxs-lookup"><span data-stu-id="f719f-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="f719f-121">Po klauzuli GROUP BY jest używany w wyrażeniu Wybierz grupowanie tylko nazwy wyrażeń, agregacje lub wyrażenia stałe może znajdować się w projekcji, mając, lub klauzula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="f719f-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="f719f-122">W poniższym przykładzie oblicza średnią ilość uporządkowane dla każdego produktu.</span><span class="sxs-lookup"><span data-stu-id="f719f-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="f719f-123">Jest możliwe w wyrażeniu wybierz grupę agregacji bez jawnej klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="f719f-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="f719f-124">Wszystkie elementy będą traktowane jako pojedynczej grupy odpowiednikiem w przypadku określania grupowanie oparte na stałą.</span><span class="sxs-lookup"><span data-stu-id="f719f-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="f719f-125">Wyrażenia używane w klauzuli GROUP BY są oceniane przy użyciu tego samego zakresu rozpoznawania nazw, które będą widoczne dla wyrażenia klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="f719f-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f719f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f719f-126">See Also</span></span>  
 [<span data-ttu-id="f719f-127">Funkcje</span><span class="sxs-lookup"><span data-stu-id="f719f-127">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
