---
title: ^ — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
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
ms.openlocfilehash: 2fb52a57a9d96f93c31ab1419e81e7f05967f831
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659725"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="dfb89-102">^ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfb89-102">^ Operator (Visual Basic)</span></span>
<span data-ttu-id="dfb89-103">Podnosi liczbę do potęgi równej innej liczbie.</span><span class="sxs-lookup"><span data-stu-id="dfb89-103">Raises a number to the power of another number.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfb89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfb89-104">Syntax</span></span>  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a><span data-ttu-id="dfb89-105">Części</span><span class="sxs-lookup"><span data-stu-id="dfb89-105">Parts</span></span>  
 `number`  
 <span data-ttu-id="dfb89-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="dfb89-106">Required.</span></span> <span data-ttu-id="dfb89-107">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="dfb89-107">Any numeric expression.</span></span>  
  
 `exponent`  
 <span data-ttu-id="dfb89-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="dfb89-108">Required.</span></span> <span data-ttu-id="dfb89-109">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="dfb89-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="dfb89-110">Wynik</span><span class="sxs-lookup"><span data-stu-id="dfb89-110">Result</span></span>  
 <span data-ttu-id="dfb89-111">Wynik jest `number` podniesione do potęgi równej `exponent`, zawsze jako `Double` wartość.</span><span class="sxs-lookup"><span data-stu-id="dfb89-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="dfb89-112">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="dfb89-112">Supported Types</span></span>  
 <span data-ttu-id="dfb89-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="dfb89-113">`Double`.</span></span> <span data-ttu-id="dfb89-114">Operandy dowolnego innego typu są konwertowane na `Double`.</span><span class="sxs-lookup"><span data-stu-id="dfb89-114">Operands of any different type are converted to `Double`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfb89-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dfb89-115">Remarks</span></span>  
 <span data-ttu-id="dfb89-116">Visual Basic zawsze wykonuje potęgowania w [typ danych Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="dfb89-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>  
  
 <span data-ttu-id="dfb89-117">Wartość `exponent` może być ułamkową ujemne lub obu.</span><span class="sxs-lookup"><span data-stu-id="dfb89-117">The value of `exponent` can be fractional, negative, or both.</span></span>  
  
 <span data-ttu-id="dfb89-118">Gdy więcej niż jeden potęgowania odbywa się w jednym wyrażeniu `^` operator jest oceniane jako napotkano od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="dfb89-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfb89-119">`^` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="dfb89-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="dfb89-120">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="dfb89-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="dfb89-121">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="dfb89-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfb89-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="dfb89-122">Example</span></span>  
 <span data-ttu-id="dfb89-123">W poniższym przykładzie użyto `^` operatora w celu podniesienia liczby do potęgi równej wykładnik.</span><span class="sxs-lookup"><span data-stu-id="dfb89-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="dfb89-124">Wynik jest pierwszy operand podniesioną do potęgi drugiego.</span><span class="sxs-lookup"><span data-stu-id="dfb89-124">The result is the first operand raised to the power of the second.</span></span>  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 <span data-ttu-id="dfb89-125">Poprzedni przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="dfb89-125">The preceding example produces the following results:</span></span>  
  
 <span data-ttu-id="dfb89-126">`exp1` jest równa 4 (kwadrat 2).</span><span class="sxs-lookup"><span data-stu-id="dfb89-126">`exp1` is set to 4 (2 squared).</span></span>  
  
 <span data-ttu-id="dfb89-127">`exp2` ustawiono 19683 (3 cubed, następnie wartości sześcianu).</span><span class="sxs-lookup"><span data-stu-id="dfb89-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>  
  
 <span data-ttu-id="dfb89-128">`exp3` ustawiono-125 (sześcianu -5).</span><span class="sxs-lookup"><span data-stu-id="dfb89-128">`exp3` is set to -125 (-5 cubed).</span></span>  
  
 <span data-ttu-id="dfb89-129">`exp4` ustawiono 625 (-5 do potęgi czwarty).</span><span class="sxs-lookup"><span data-stu-id="dfb89-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>  
  
 <span data-ttu-id="dfb89-130">`exp5` jest równa 2 (element główny modułu 8).</span><span class="sxs-lookup"><span data-stu-id="dfb89-130">`exp5` is set to 2 (cube root of 8).</span></span>  
  
 <span data-ttu-id="dfb89-131">`exp6` wynosi 0,5 (1.0 podzielona przez główny modułu 8).</span><span class="sxs-lookup"><span data-stu-id="dfb89-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>  
  
 <span data-ttu-id="dfb89-132">Należy zwrócić uwagę znaczenie nawiasów w wyrażeniach w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dfb89-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="dfb89-133">Z powodu *pierwszeństwo operatorów*, Visual Basic zwykle wykonuje `^` operatora przed wszystkie inne pola, nawet jednoargumentowe `–` operatora.</span><span class="sxs-lookup"><span data-stu-id="dfb89-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="dfb89-134">Jeśli `exp4` i `exp6` była obliczona bez nawiasów, czy zostały utworzone następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="dfb89-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>  
  
 <span data-ttu-id="dfb89-135">`exp4 = -5 ^ 4` oblicza — 5 do potęgi czwarty, które mogłyby spowodować-625.</span><span class="sxs-lookup"><span data-stu-id="dfb89-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>  
  
 <span data-ttu-id="dfb89-136">`exp6 = 8 ^ -1.0 / 3.0` oblicza (od 8 do potęgi-1 lub 0,125) podzielony przez 3.0, co mogłoby spowodować 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="dfb89-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb89-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfb89-137">See also</span></span>
- [<span data-ttu-id="dfb89-138">^=, operator</span><span class="sxs-lookup"><span data-stu-id="dfb89-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="dfb89-139">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="dfb89-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="dfb89-140">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfb89-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="dfb89-141">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="dfb89-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="dfb89-142">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfb89-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
