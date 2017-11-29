---
title: "Kolejność wykonywania działań (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 484eedffeaffb625cd43352dadedb8c99fbc65ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="0db68-102">Kolejność wykonywania działań (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="0db68-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="0db68-103">Gdy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania ma wiele operatorów, kolejność określa kolejność, w którym wykonywane są operacje.</span><span class="sxs-lookup"><span data-stu-id="0db68-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="0db68-104">Kolejność wykonywania mogą znacznie wpływać na wynik zapytania.</span><span class="sxs-lookup"><span data-stu-id="0db68-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="0db68-105">Operatory ma poziomów pierwszeństwo przed, pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0db68-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="0db68-106">Operator o wyższym poziomie jest oceniane przed operatorem o niższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="0db68-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="0db68-107">Poziom</span><span class="sxs-lookup"><span data-stu-id="0db68-107">Level</span></span>|<span data-ttu-id="0db68-108">Typ operacji</span><span class="sxs-lookup"><span data-stu-id="0db68-108">Operation type</span></span>|<span data-ttu-id="0db68-109">Operator</span><span class="sxs-lookup"><span data-stu-id="0db68-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="0db68-110">1</span><span class="sxs-lookup"><span data-stu-id="0db68-110">1</span></span>|<span data-ttu-id="0db68-111">podstawowy</span><span class="sxs-lookup"><span data-stu-id="0db68-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="0db68-112">2</span><span class="sxs-lookup"><span data-stu-id="0db68-112">2</span></span>|<span data-ttu-id="0db68-113">Jednoargumentowe</span><span class="sxs-lookup"><span data-stu-id="0db68-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="0db68-114">3</span><span class="sxs-lookup"><span data-stu-id="0db68-114">3</span></span>|<span data-ttu-id="0db68-115">Mnożenia</span><span class="sxs-lookup"><span data-stu-id="0db68-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="0db68-116">4</span><span class="sxs-lookup"><span data-stu-id="0db68-116">4</span></span>|<span data-ttu-id="0db68-117">Dodatku</span><span class="sxs-lookup"><span data-stu-id="0db68-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="0db68-118">5</span><span class="sxs-lookup"><span data-stu-id="0db68-118">5</span></span>|<span data-ttu-id="0db68-119">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="0db68-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="0db68-120">6</span><span class="sxs-lookup"><span data-stu-id="0db68-120">6</span></span>|<span data-ttu-id="0db68-121">Równość</span><span class="sxs-lookup"><span data-stu-id="0db68-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="0db68-122">7</span><span class="sxs-lookup"><span data-stu-id="0db68-122">7</span></span>|<span data-ttu-id="0db68-123">AND warunkowe</span><span class="sxs-lookup"><span data-stu-id="0db68-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="0db68-124">8</span><span class="sxs-lookup"><span data-stu-id="0db68-124">8</span></span>|<span data-ttu-id="0db68-125">OR warunkowe</span><span class="sxs-lookup"><span data-stu-id="0db68-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="0db68-126">Po dwóch operatorów w wyrażeniu mają ten sam poziom pierwszeństwa operatora, ich są wykonywane od lewej do prawej, na podstawie ich położenia w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="0db68-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="0db68-127">Na przykład `x+y-z` jest szacowana jako `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="0db68-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="0db68-128">Można użyć nawiasów do zastąpienia zdefiniowane pierwszeństwo operatorów w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="0db68-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="0db68-129">Wszystkie elementy wewnątrz nawiasów oceny najpierw umożliwiające uzyskanie pojedynczego wyniku przed, czy wynik mogą być używane przez każdy podmiot poza nawiasów.</span><span class="sxs-lookup"><span data-stu-id="0db68-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="0db68-130">Na przykład `x+y*z` mnoży `y` przez `z` , a następnie dodaje `x`, ale `(x+y)*z` dodaje `x` do `y` , a następnie mnoży wynik przez `z`.</span><span class="sxs-lookup"><span data-stu-id="0db68-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db68-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0db68-131">See Also</span></span>  
 [<span data-ttu-id="0db68-132">Omówienie SQL jednostki</span><span class="sxs-lookup"><span data-stu-id="0db68-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
