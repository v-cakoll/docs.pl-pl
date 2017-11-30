---
title: "^ — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e06da-102">^ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e06da-102">^ Operator (Visual Basic)</span></span>
<span data-ttu-id="e06da-103">Podnosi liczbę do potęgi równej innej liczbie.</span><span class="sxs-lookup"><span data-stu-id="e06da-103">Raises a number to the power of another number.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e06da-104">Syntax</span></span>  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a><span data-ttu-id="e06da-105">Części</span><span class="sxs-lookup"><span data-stu-id="e06da-105">Parts</span></span>  
 `number`  
 <span data-ttu-id="e06da-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e06da-106">Required.</span></span> <span data-ttu-id="e06da-107">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="e06da-107">Any numeric expression.</span></span>  
  
 `exponent`  
 <span data-ttu-id="e06da-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e06da-108">Required.</span></span> <span data-ttu-id="e06da-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="e06da-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="e06da-110">Wynik</span><span class="sxs-lookup"><span data-stu-id="e06da-110">Result</span></span>  
 <span data-ttu-id="e06da-111">Wynik jest `number` podniesionej do potęgi równej `exponent`, zawsze jako `Double` wartość.</span><span class="sxs-lookup"><span data-stu-id="e06da-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="e06da-112">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="e06da-112">Supported Types</span></span>  
 <span data-ttu-id="e06da-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="e06da-113">`Double`.</span></span> <span data-ttu-id="e06da-114">Argumenty operacji dowolnego innego typu są konwertowane na `Double`.</span><span class="sxs-lookup"><span data-stu-id="e06da-114">Operands of any different type are converted to `Double`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e06da-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e06da-115">Remarks</span></span>  
 <span data-ttu-id="e06da-116">Visual Basic zawsze przeprowadza potęgowania w [— typ danych Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e06da-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>  
  
 <span data-ttu-id="e06da-117">Wartość `exponent` może być ułamkową ujemne lub oba.</span><span class="sxs-lookup"><span data-stu-id="e06da-117">The value of `exponent` can be fractional, negative, or both.</span></span>  
  
 <span data-ttu-id="e06da-118">Gdy więcej niż jeden potęgowania odbywa się w jednym wyrażeniu `^` operator jest oceniane, ponieważ napotkano od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="e06da-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e06da-119">`^` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="e06da-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e06da-120">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="e06da-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e06da-121">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e06da-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e06da-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e06da-122">Example</span></span>  
 <span data-ttu-id="e06da-123">W poniższym przykładzie użyto `^` operatora, aby podnieść liczbę do potęgi wykładnik.</span><span class="sxs-lookup"><span data-stu-id="e06da-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="e06da-124">Wynik jest pierwszym argumentem podniesionej do potęgi drugiego.</span><span class="sxs-lookup"><span data-stu-id="e06da-124">The result is the first operand raised to the power of the second.</span></span>  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 <span data-ttu-id="e06da-125">Powyższy przykład tworzy następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e06da-125">The preceding example produces the following results:</span></span>  
  
 <span data-ttu-id="e06da-126">`exp1`ma ustawioną wartość 4 (kwadrat 2).</span><span class="sxs-lookup"><span data-stu-id="e06da-126">`exp1` is set to 4 (2 squared).</span></span>  
  
 <span data-ttu-id="e06da-127">`exp2`ustawiono 19683 (3 sześcian, następnie tę wartość do sześcianu).</span><span class="sxs-lookup"><span data-stu-id="e06da-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>  
  
 <span data-ttu-id="e06da-128">`exp3`ustawiono-125 (-5 do sześcianu).</span><span class="sxs-lookup"><span data-stu-id="e06da-128">`exp3` is set to -125 (-5 cubed).</span></span>  
  
 <span data-ttu-id="e06da-129">`exp4`ustawiono 625 (-5 do potęgi czwarty).</span><span class="sxs-lookup"><span data-stu-id="e06da-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>  
  
 <span data-ttu-id="e06da-130">`exp5`wynosi 2 (główny modułu 8).</span><span class="sxs-lookup"><span data-stu-id="e06da-130">`exp5` is set to 2 (cube root of 8).</span></span>  
  
 <span data-ttu-id="e06da-131">`exp6`wynosi 0,5 (podzielona przez główny modułu 8 1.0).</span><span class="sxs-lookup"><span data-stu-id="e06da-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>  
  
 <span data-ttu-id="e06da-132">Należy zwrócić uwagę znaczenie nawiasów w wyrażeniach w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e06da-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="e06da-133">Z powodu *kolejność*, Visual Basic zazwyczaj wykonuje `^` operator przed innych, nawet jednoargumentowego `–` operatora.</span><span class="sxs-lookup"><span data-stu-id="e06da-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="e06da-134">Jeśli `exp4` i `exp6` został wyliczony bez nawiasów, czy zostały utworzone następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e06da-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>  
  
 <span data-ttu-id="e06da-135">`exp4 = -5 ^ 4`oblicza — (5 do potęgi czwarty), co mogłoby spowodować-625.</span><span class="sxs-lookup"><span data-stu-id="e06da-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>  
  
 <span data-ttu-id="e06da-136">`exp6 = 8 ^ -1.0 / 3.0`oblicza (od 8 do potęgi-1 lub 0,125) podzielony przez 3.0, co spowoduje 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="e06da-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06da-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e06da-137">See Also</span></span>  
 [<span data-ttu-id="e06da-138">^ = — Operator</span><span class="sxs-lookup"><span data-stu-id="e06da-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [<span data-ttu-id="e06da-139">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="e06da-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="e06da-140">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e06da-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="e06da-141">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="e06da-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="e06da-142">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e06da-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
