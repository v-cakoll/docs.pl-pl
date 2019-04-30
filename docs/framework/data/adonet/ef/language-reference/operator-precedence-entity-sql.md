---
title: Kolejność wykonywania działań (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 722ebe5f0ec530f8c7f86e9f9901451b060903f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760353"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="d037b-102">Kolejność wykonywania działań (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="d037b-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="d037b-103">Gdy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie ma wiele operatory, pierwszeństwo operatorów określa kolejność, w której operacje są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="d037b-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="d037b-104">Kolejność wykonywania może znacząco wpłynąć na wynik zapytania.</span><span class="sxs-lookup"><span data-stu-id="d037b-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="d037b-105">Operatory mają poziomy pierwszeństwa, pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d037b-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="d037b-106">Operator na wyższym poziomie jest oceniany przed operatorem o niższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="d037b-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="d037b-107">Poziom</span><span class="sxs-lookup"><span data-stu-id="d037b-107">Level</span></span>|<span data-ttu-id="d037b-108">Typ operacji</span><span class="sxs-lookup"><span data-stu-id="d037b-108">Operation type</span></span>|<span data-ttu-id="d037b-109">Operator</span><span class="sxs-lookup"><span data-stu-id="d037b-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="d037b-110">1</span><span class="sxs-lookup"><span data-stu-id="d037b-110">1</span></span>|<span data-ttu-id="d037b-111">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="d037b-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="d037b-112">2</span><span class="sxs-lookup"><span data-stu-id="d037b-112">2</span></span>|<span data-ttu-id="d037b-113">Jednoargumentowy</span><span class="sxs-lookup"><span data-stu-id="d037b-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="d037b-114">3</span><span class="sxs-lookup"><span data-stu-id="d037b-114">3</span></span>|<span data-ttu-id="d037b-115">Mnożeniowy</span><span class="sxs-lookup"><span data-stu-id="d037b-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="d037b-116">4</span><span class="sxs-lookup"><span data-stu-id="d037b-116">4</span></span>|<span data-ttu-id="d037b-117">Dodatku</span><span class="sxs-lookup"><span data-stu-id="d037b-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="d037b-118">5</span><span class="sxs-lookup"><span data-stu-id="d037b-118">5</span></span>|<span data-ttu-id="d037b-119">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="d037b-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="d037b-120">6</span><span class="sxs-lookup"><span data-stu-id="d037b-120">6</span></span>|<span data-ttu-id="d037b-121">Równości</span><span class="sxs-lookup"><span data-stu-id="d037b-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="d037b-122">7</span><span class="sxs-lookup"><span data-stu-id="d037b-122">7</span></span>|<span data-ttu-id="d037b-123">Warunkowego AND</span><span class="sxs-lookup"><span data-stu-id="d037b-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="d037b-124">8</span><span class="sxs-lookup"><span data-stu-id="d037b-124">8</span></span>|<span data-ttu-id="d037b-125">Warunkowego OR</span><span class="sxs-lookup"><span data-stu-id="d037b-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="d037b-126">Gdy dwa operatory w wyrażeniu mają pierwszeństwo przed operatorem na tym samym poziomie, ich są obliczane od lewej do prawej, na podstawie ich pozycji w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="d037b-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="d037b-127">Na przykład `x+y-z` jest oceniane jako `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="d037b-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="d037b-128">Można użyć nawiasów do zastąpienia zdefiniowane pierwszeństwo operatorów w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="d037b-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="d037b-129">Wszystko wewnątrz nawiasów jest stosowana jako pierwsza umożliwiające uzyskanie pojedynczego wyniku przed, że wyniki mogą być używane przez dowolny operator poza nawiasami.</span><span class="sxs-lookup"><span data-stu-id="d037b-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="d037b-130">Na przykład `x+y*z` mnoży `y` przez `z` , a następnie dodaje `x`, ale `(x+y)*z` dodaje `x` do `y` i następnie mnoży wynik przez `z`.</span><span class="sxs-lookup"><span data-stu-id="d037b-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d037b-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d037b-131">See also</span></span>

- [<span data-ttu-id="d037b-132">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d037b-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
