---
title: Pierwszeństwo operatorów (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 2d8c78f410708fd1aa843ee8f14f7243a9f686c0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249783"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="09ee4-102">Pierwszeństwo operatorów (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="09ee4-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="09ee4-103">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Gdy zapytanie ma wiele operatorów, pierwszeństwo operatorów określa kolejność wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="09ee4-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="09ee4-104">Kolejność wykonywania może znacząco wpłynąć na wynik zapytania.</span><span class="sxs-lookup"><span data-stu-id="09ee4-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="09ee4-105">Operatory mają poziomy pierwszeństwa pokazane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="09ee4-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="09ee4-106">Operator o wyższym poziomie jest obliczany przed operatorem o niższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="09ee4-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="09ee4-107">Poziom</span><span class="sxs-lookup"><span data-stu-id="09ee4-107">Level</span></span>|<span data-ttu-id="09ee4-108">Typ operacji</span><span class="sxs-lookup"><span data-stu-id="09ee4-108">Operation type</span></span>|<span data-ttu-id="09ee4-109">Operator</span><span class="sxs-lookup"><span data-stu-id="09ee4-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="09ee4-110">1</span><span class="sxs-lookup"><span data-stu-id="09ee4-110">1</span></span>|<span data-ttu-id="09ee4-111">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="09ee4-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="09ee4-112">2</span><span class="sxs-lookup"><span data-stu-id="09ee4-112">2</span></span>|<span data-ttu-id="09ee4-113">Jednostk</span><span class="sxs-lookup"><span data-stu-id="09ee4-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="09ee4-114">3</span><span class="sxs-lookup"><span data-stu-id="09ee4-114">3</span></span>|<span data-ttu-id="09ee4-115">Mnożeniowy</span><span class="sxs-lookup"><span data-stu-id="09ee4-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="09ee4-116">4</span><span class="sxs-lookup"><span data-stu-id="09ee4-116">4</span></span>|<span data-ttu-id="09ee4-117">Dana</span><span class="sxs-lookup"><span data-stu-id="09ee4-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="09ee4-118">5</span><span class="sxs-lookup"><span data-stu-id="09ee4-118">5</span></span>|<span data-ttu-id="09ee4-119">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="09ee4-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="09ee4-120">6</span><span class="sxs-lookup"><span data-stu-id="09ee4-120">6</span></span>|<span data-ttu-id="09ee4-121">Równości</span><span class="sxs-lookup"><span data-stu-id="09ee4-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="09ee4-122">7</span><span class="sxs-lookup"><span data-stu-id="09ee4-122">7</span></span>|<span data-ttu-id="09ee4-123">Warunkowego AND</span><span class="sxs-lookup"><span data-stu-id="09ee4-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="09ee4-124">8</span><span class="sxs-lookup"><span data-stu-id="09ee4-124">8</span></span>|<span data-ttu-id="09ee4-125">Warunkowego OR</span><span class="sxs-lookup"><span data-stu-id="09ee4-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="09ee4-126">Gdy dwa operatory w wyrażeniu mają ten sam poziom pierwszeństwa operatora, są oceniane od lewej do prawej na podstawie ich pozycji w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="09ee4-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="09ee4-127">Na przykład, `x+y-z` jest oceniane jako `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="09ee4-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="09ee4-128">Możesz użyć nawiasów, aby przesłonić zdefiniowane pierwszeństwo operatorów w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="09ee4-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="09ee4-129">Wszystkie elementy w nawiasach są oceniane jako pierwsze w celu uzyskania pojedynczego wyniku, zanim ten wynik może być używany przez dowolny operator poza nawiasami.</span><span class="sxs-lookup"><span data-stu-id="09ee4-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="09ee4-130">`x+y*z` Na przykład `x` `x` `(x+y)*z` `y` mnoży wartość `z`przez, a następnie dodaje, ale dodaje do, a następnie mnoży wynik przez `z`. `y`</span><span class="sxs-lookup"><span data-stu-id="09ee4-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ee4-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09ee4-131">See also</span></span>

- [<span data-ttu-id="09ee4-132">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="09ee4-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
