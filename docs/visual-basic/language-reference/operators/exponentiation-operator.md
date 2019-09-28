---
title: ^ — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 8cdfbec917608211e19c39eb37bd12dbc7c4d33f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592222"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e80c5-102">^ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e80c5-102">^ Operator (Visual Basic)</span></span>

<span data-ttu-id="e80c5-103">Podnosi liczbę do potęgi innej liczby.</span><span class="sxs-lookup"><span data-stu-id="e80c5-103">Raises a number to the power of another number.</span></span>

## <a name="syntax"></a><span data-ttu-id="e80c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e80c5-104">Syntax</span></span>

```vb
number ^ exponent
```

## <a name="parts"></a><span data-ttu-id="e80c5-105">Części</span><span class="sxs-lookup"><span data-stu-id="e80c5-105">Parts</span></span>

`number`\
<span data-ttu-id="e80c5-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e80c5-106">Required.</span></span> <span data-ttu-id="e80c5-107">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="e80c5-107">Any numeric expression.</span></span>

`exponent`\
<span data-ttu-id="e80c5-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e80c5-108">Required.</span></span> <span data-ttu-id="e80c5-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="e80c5-109">Any numeric expression.</span></span>

## <a name="result"></a><span data-ttu-id="e80c5-110">Wynik</span><span class="sxs-lookup"><span data-stu-id="e80c5-110">Result</span></span>

<span data-ttu-id="e80c5-111">Wynikiem jest `number` podniesioną do potęgi `exponent`, zawsze jako wartość `Double`.</span><span class="sxs-lookup"><span data-stu-id="e80c5-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>

## <a name="supported-types"></a><span data-ttu-id="e80c5-112">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="e80c5-112">Supported Types</span></span>

<span data-ttu-id="e80c5-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="e80c5-113">`Double`.</span></span> <span data-ttu-id="e80c5-114">Operandy dowolnego typu są konwertowane na `Double`.</span><span class="sxs-lookup"><span data-stu-id="e80c5-114">Operands of any different type are converted to `Double`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e80c5-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e80c5-115">Remarks</span></span>

<span data-ttu-id="e80c5-116">Visual Basic zawsze wykonuje potęgowanie w [podwójnym typie danych](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e80c5-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>

<span data-ttu-id="e80c5-117">Wartość `exponent` może być ułamkowa, ujemna lub jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e80c5-117">The value of `exponent` can be fractional, negative, or both.</span></span>

<span data-ttu-id="e80c5-118">Gdy w jednym wyrażeniu jest wykonywanych więcej niż jedna potęga, operator `^` jest oceniany, ponieważ występuje od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="e80c5-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>

> [!NOTE]
> <span data-ttu-id="e80c5-119">Operator `^` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="e80c5-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e80c5-120">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e80c5-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e80c5-121">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e80c5-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="e80c5-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e80c5-122">Example</span></span>

<span data-ttu-id="e80c5-123">Poniższy przykład używa operatora `^`, aby podnieść liczbę do potęgi wykładnika.</span><span class="sxs-lookup"><span data-stu-id="e80c5-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="e80c5-124">Wynikiem jest pierwszy operand podniesiony do potęgi sekundy.</span><span class="sxs-lookup"><span data-stu-id="e80c5-124">The result is the first operand raised to the power of the second.</span></span>

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

<span data-ttu-id="e80c5-125">Poprzedni przykład daje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e80c5-125">The preceding example produces the following results:</span></span>

<span data-ttu-id="e80c5-126">wartość `exp1` to 4 (2 kwadraty).</span><span class="sxs-lookup"><span data-stu-id="e80c5-126">`exp1` is set to 4 (2 squared).</span></span>

<span data-ttu-id="e80c5-127">`exp2` jest ustawiona na 19683 (3 Cubed, a następnie wartość cubed).</span><span class="sxs-lookup"><span data-stu-id="e80c5-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>

<span data-ttu-id="e80c5-128">`exp3` jest ustawiona na-125 (-5 cubed).</span><span class="sxs-lookup"><span data-stu-id="e80c5-128">`exp3` is set to -125 (-5 cubed).</span></span>

<span data-ttu-id="e80c5-129">`exp4` jest ustawiona na 625 (-5 do czwartej potęgi).</span><span class="sxs-lookup"><span data-stu-id="e80c5-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>

<span data-ttu-id="e80c5-130">`exp5` jest ustawiona na 2 (korzeń modułu 8).</span><span class="sxs-lookup"><span data-stu-id="e80c5-130">`exp5` is set to 2 (cube root of 8).</span></span>

<span data-ttu-id="e80c5-131">`exp6` jest ustawiony na 0,5 (1,0 podzielony przez korzeń modułu 8).</span><span class="sxs-lookup"><span data-stu-id="e80c5-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>

<span data-ttu-id="e80c5-132">Zanotuj znaczenie nawiasów w wyrażeniach w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e80c5-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="e80c5-133">Ze względu na *pierwszeństwo operatorów*, Visual Basic zwykle wykonuje operator `^` przed innymi, nawet jednoargumentowy operator `–`.</span><span class="sxs-lookup"><span data-stu-id="e80c5-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="e80c5-134">Jeśli `exp4` i `exp6` zostały obliczone bez nawiasów, zostałyby utworzone następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e80c5-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>

<span data-ttu-id="e80c5-135">`exp4 = -5 ^ 4` zostałyby obliczone jako – (5 do czwartej potęgi), co spowodowałoby 625.</span><span class="sxs-lookup"><span data-stu-id="e80c5-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>

<span data-ttu-id="e80c5-136">`exp6 = 8 ^ -1.0 / 3.0` zostałaby obliczona jako (8 do potęgi – 1 lub 0,125) podzielona przez 3,0, co spowodowałoby 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="e80c5-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>

## <a name="see-also"></a><span data-ttu-id="e80c5-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e80c5-137">See also</span></span>

- [<span data-ttu-id="e80c5-138">^=, operator</span><span class="sxs-lookup"><span data-stu-id="e80c5-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="e80c5-139">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="e80c5-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="e80c5-140">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e80c5-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e80c5-141">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="e80c5-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e80c5-142">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e80c5-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
