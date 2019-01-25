---
title: Aggregate Functions (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: e606d0e355bb715cfa0536ad9e33f08f5f692951
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492055"
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="a9c66-102">Aggregate Functions (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a9c66-102">Aggregate Functions (Entity SQL)</span></span>
<span data-ttu-id="a9c66-103">Wartość zagregowana jest konstrukcją języka, która zmniejsza objętość kolekcji do skalaru jako część operacji grupy.</span><span class="sxs-lookup"><span data-stu-id="a9c66-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a9c66-104">agregacje są dostępne w dwóch formach:</span><span class="sxs-lookup"><span data-stu-id="a9c66-104">aggregates come in two forms:</span></span>  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a9c66-105">Funkcje kolekcji, które mogą być używane w dowolnym miejscu w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a9c66-105">collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="a9c66-106">W tym za pomocą funkcji agregujących w projekcji oraz predykatów, które działają w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="a9c66-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="a9c66-107">Kolekcja funkcji jest preferowany tryb, określania wartości zagregowanych umieszczonych w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9c66-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
-   <span data-ttu-id="a9c66-108">Grupy agregacje w wyrażeniach zapytań, które zawierać klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="a9c66-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="a9c66-109">Podobnie jak w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], agregacje grupy Zaakceptuj DISTINCT, a wszystkie jako modyfikatory do agregacji danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a9c66-109">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a9c66-110">po raz pierwszy próbuje można zinterpretować wyrażenia w funkcji kolekcji i jeśli wyrażenie ma w kontekście wyrażenia wybierz je zinterpretuje ją jako agregację grupy.</span><span class="sxs-lookup"><span data-stu-id="a9c66-110">first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a9c66-111">definiuje specjalny aggregate-operator o nazwie [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a9c66-111">defines a special aggregate operator called [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span></span> <span data-ttu-id="a9c66-112">Ten operator można uzyskać odwołanie do zestawu pogrupowanych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a9c66-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="a9c66-113">Umożliwia to bardziej zaawansowanych zapytań, grupowanie, której wyniki w klauzuli GROUP BY może służyć w miejsc innych niż agregacji grup lub kolekcji funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9c66-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="a9c66-114">Kolekcja funkcji</span><span class="sxs-lookup"><span data-stu-id="a9c66-114">Collection Functions</span></span>  
 <span data-ttu-id="a9c66-115">Funkcje kolekcji działają w kolekcjach i zwracać wartość skalarną.</span><span class="sxs-lookup"><span data-stu-id="a9c66-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="a9c66-116">Na przykład jeśli `orders` to zbiór wszystkich `orders`, można obliczyć Najwcześniejsza data wysyłki za pomocą następującego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="a9c66-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="a9c66-117">Agregacje grupy</span><span class="sxs-lookup"><span data-stu-id="a9c66-117">Group Aggregates</span></span>  
 <span data-ttu-id="a9c66-118">Agregacje grupy są obliczane w wyniku grupy, zgodnie z definicją w klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="a9c66-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="a9c66-119">W klauzuli GROUP BY partycjonowania danych w grupy.</span><span class="sxs-lookup"><span data-stu-id="a9c66-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="a9c66-120">Dla każdej grupy w wyniku zastosowaniu funkcji agregującej i oddzielnych agregacji jest obliczana przy użyciu elementów w każdej grupie jako dane wejściowe do obliczania agregacji.</span><span class="sxs-lookup"><span data-stu-id="a9c66-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="a9c66-121">Gdy klauzula GROUP BY jest używany w wyrażeniu wybierz tylko grupowanie nazwy wyrażeń, agregacje lub wyrażeń stałych może znajdować się w projekcji, problemy, lub klauzula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="a9c66-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="a9c66-122">W poniższym przykładzie oblicza średnią ilość uporządkowane dla każdego produktu.</span><span class="sxs-lookup"><span data-stu-id="a9c66-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="a9c66-123">Istnieje możliwość mają grupy agregacji bez jawnej klauzuli GROUP BY w wyrażeniu SELECT.</span><span class="sxs-lookup"><span data-stu-id="a9c66-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="a9c66-124">Wszystkie elementy są traktowane jako pojedynczej grupy odpowiednikiem w przypadku określenia grupowanie oparte na stałą.</span><span class="sxs-lookup"><span data-stu-id="a9c66-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="a9c66-125">Wyrażenia używane w klauzuli GROUP BY są oceniane przy użyciu tego samego zakresu rozpoznawania nazw, które będą widoczne dla wyrażenie klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="a9c66-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c66-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9c66-126">See also</span></span>
- [<span data-ttu-id="a9c66-127">Funkcje</span><span class="sxs-lookup"><span data-stu-id="a9c66-127">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
