---
title: "Not — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ac160aef7b7dc8acb8bf0211b403599692f2373c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="80866-102">Not — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80866-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="80866-103">Wykonuje logiczną negację na `Boolean` wyrażenie lub bitowego zaprzeczenia wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="80866-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80866-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80866-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="80866-105">Części</span><span class="sxs-lookup"><span data-stu-id="80866-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="80866-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="80866-106">Required.</span></span> <span data-ttu-id="80866-107">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="80866-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="80866-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="80866-108">Required.</span></span> <span data-ttu-id="80866-109">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="80866-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80866-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80866-110">Remarks</span></span>  
 <span data-ttu-id="80866-111">Dla `Boolean` wyrażenia w poniższej tabeli przedstawiono sposób `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="80866-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="80866-112">Jeśli `expression` jest</span><span class="sxs-lookup"><span data-stu-id="80866-112">If `expression` is</span></span>|<span data-ttu-id="80866-113">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="80866-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="80866-114">Dla wyrażeń liczbowych `Not` operator odwraca wartości bitowe dowolne wyrażenie liczbowe i ustawia bit w odpowiedniej `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="80866-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="80866-115">Jeśli bit w `expression` jest</span><span class="sxs-lookup"><span data-stu-id="80866-115">If bit in `expression` is</span></span>|<span data-ttu-id="80866-116">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="80866-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="80866-117">1</span><span class="sxs-lookup"><span data-stu-id="80866-117">1</span></span>|<span data-ttu-id="80866-118">0</span><span class="sxs-lookup"><span data-stu-id="80866-118">0</span></span>|  
|<span data-ttu-id="80866-119">0</span><span class="sxs-lookup"><span data-stu-id="80866-119">0</span></span>|<span data-ttu-id="80866-120">1</span><span class="sxs-lookup"><span data-stu-id="80866-120">1</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="80866-121">Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne arytmetyczne operatorów, wszystkie operacje bitowe powinny być ujęte w nawiasy, aby zapewnić dokładne wykonywania.</span><span class="sxs-lookup"><span data-stu-id="80866-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="80866-122">Typy danych</span><span class="sxs-lookup"><span data-stu-id="80866-122">Data Types</span></span>  
 <span data-ttu-id="80866-123">Logiczna Negacja, jest typ danych w wyniku `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="80866-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="80866-124">Dla bitową negację, typu danych jest taka sama, jak te `expression`.</span><span class="sxs-lookup"><span data-stu-id="80866-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="80866-125">Jednak jeśli wyrażenie jest `Decimal`, wynikiem jest `Long`.</span><span class="sxs-lookup"><span data-stu-id="80866-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="80866-126">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="80866-126">Overloading</span></span>  
 <span data-ttu-id="80866-127">`Not` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowania podczas jej argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="80866-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="80866-128">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="80866-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="80866-129">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="80866-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80866-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="80866-130">Example</span></span>  
 <span data-ttu-id="80866-131">W poniższym przykładzie użyto `Not` operator logiczny negacji podczas `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="80866-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="80866-132">Wynik jest `Boolean` wartość, która reprezentuje odwrotnej wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="80866-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 <span data-ttu-id="80866-133">Powyższy przykład produkuje wyniki `False` i `True`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="80866-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80866-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="80866-134">Example</span></span>  
 <span data-ttu-id="80866-135">W poniższym przykładzie użyto `Not` operatora, aby wykonać logiczny negacji poszczególnych bitów wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="80866-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="80866-136">Bit we wzorcu wynik jest ustawiony na odpowiadający mu bit we wzorcu operand, łącznie z bitem odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="80866-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 <span data-ttu-id="80866-137">Powyższy przykład produkuje wyników –11, –9 i –7, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="80866-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80866-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80866-138">See Also</span></span>  
 [<span data-ttu-id="80866-139">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80866-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="80866-140">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80866-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="80866-141">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="80866-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="80866-142">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80866-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
