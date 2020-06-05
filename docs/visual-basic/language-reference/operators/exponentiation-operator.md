---
title: ^ — Operator
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
ms.openlocfilehash: e139becf74ae367266a23513e18d0bdbdd24cdea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371391"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f87af-102">^ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f87af-102">^ Operator (Visual Basic)</span></span>

<span data-ttu-id="f87af-103">Podnosi liczbę do potęgi innej liczby.</span><span class="sxs-lookup"><span data-stu-id="f87af-103">Raises a number to the power of another number.</span></span>

## <a name="syntax"></a><span data-ttu-id="f87af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f87af-104">Syntax</span></span>

```vb
number ^ exponent
```

## <a name="parts"></a><span data-ttu-id="f87af-105">Części</span><span class="sxs-lookup"><span data-stu-id="f87af-105">Parts</span></span>

`number`\
<span data-ttu-id="f87af-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f87af-106">Required.</span></span> <span data-ttu-id="f87af-107">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="f87af-107">Any numeric expression.</span></span>

`exponent`\
<span data-ttu-id="f87af-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f87af-108">Required.</span></span> <span data-ttu-id="f87af-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="f87af-109">Any numeric expression.</span></span>

## <a name="result"></a><span data-ttu-id="f87af-110">Wynik</span><span class="sxs-lookup"><span data-stu-id="f87af-110">Result</span></span>

<span data-ttu-id="f87af-111">Wynik jest `number` wywoływany do potęgi `exponent` , zawsze jako `Double` wartość.</span><span class="sxs-lookup"><span data-stu-id="f87af-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>

## <a name="supported-types"></a><span data-ttu-id="f87af-112">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="f87af-112">Supported Types</span></span>

<span data-ttu-id="f87af-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="f87af-113">`Double`.</span></span> <span data-ttu-id="f87af-114">Operandy dowolnego typu są konwertowane na `Double` .</span><span class="sxs-lookup"><span data-stu-id="f87af-114">Operands of any different type are converted to `Double`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f87af-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f87af-115">Remarks</span></span>

<span data-ttu-id="f87af-116">Visual Basic zawsze wykonuje potęgowanie w [podwójnym typie danych](../data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="f87af-116">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span>

<span data-ttu-id="f87af-117">Wartość `exponent` może być ułamkowa, ujemna lub obie.</span><span class="sxs-lookup"><span data-stu-id="f87af-117">The value of `exponent` can be fractional, negative, or both.</span></span>

<span data-ttu-id="f87af-118">Gdy w jednym wyrażeniu jest wykonywana więcej niż jedna potęga, `^` operator jest oceniany, ponieważ napotka się od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="f87af-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>

> [!NOTE]
> <span data-ttu-id="f87af-119">`^`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f87af-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f87af-120">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f87af-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f87af-121">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f87af-121">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="f87af-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f87af-122">Example</span></span>

<span data-ttu-id="f87af-123">Poniższy przykład używa operatora, `^` Aby podnieść liczbę do potęgi wykładnika.</span><span class="sxs-lookup"><span data-stu-id="f87af-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="f87af-124">Wynikiem jest pierwszy operand podniesiony do potęgi sekundy.</span><span class="sxs-lookup"><span data-stu-id="f87af-124">The result is the first operand raised to the power of the second.</span></span>

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

<span data-ttu-id="f87af-125">Poprzedni przykład daje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f87af-125">The preceding example produces the following results:</span></span>

<span data-ttu-id="f87af-126">`exp1`jest ustawiony na 4 (2 kwadraty).</span><span class="sxs-lookup"><span data-stu-id="f87af-126">`exp1` is set to 4 (2 squared).</span></span>

<span data-ttu-id="f87af-127">`exp2`jest ustawiona na 19683 (3 Cubed, a następnie ta wartość cubed).</span><span class="sxs-lookup"><span data-stu-id="f87af-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>

<span data-ttu-id="f87af-128">`exp3`jest ustawiony na-125 (-5 cubed).</span><span class="sxs-lookup"><span data-stu-id="f87af-128">`exp3` is set to -125 (-5 cubed).</span></span>

<span data-ttu-id="f87af-129">`exp4`jest ustawiony na 625 (-5 do czwartej potęgi).</span><span class="sxs-lookup"><span data-stu-id="f87af-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>

<span data-ttu-id="f87af-130">`exp5`jest ustawiony na 2 (korzeń modułu 8).</span><span class="sxs-lookup"><span data-stu-id="f87af-130">`exp5` is set to 2 (cube root of 8).</span></span>

<span data-ttu-id="f87af-131">`exp6`jest ustawiony na 0,5 (1,0 podzielony przez korzeń modułu 8).</span><span class="sxs-lookup"><span data-stu-id="f87af-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>

<span data-ttu-id="f87af-132">Zanotuj znaczenie nawiasów w wyrażeniach w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f87af-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="f87af-133">Ze względu na *kolejność operatorów*, Visual Basic zwykle wykonuje `^` operator przed innymi, nawet operator jednoargumentowy `–` .</span><span class="sxs-lookup"><span data-stu-id="f87af-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="f87af-134">Jeśli `exp4` i `exp6` zostały obliczone bez nawiasów, zostałyby utworzone następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f87af-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>

<span data-ttu-id="f87af-135">`exp4 = -5 ^ 4`zostanie obliczony jako – (5 do czwartej potęgi), co spowoduje, że 625.</span><span class="sxs-lookup"><span data-stu-id="f87af-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>

<span data-ttu-id="f87af-136">`exp6 = 8 ^ -1.0 / 3.0`zostanie obliczona jako (8 do potęgi – 1 lub 0,125) podzielona przez 3,0, co spowodowałoby 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="f87af-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>

## <a name="see-also"></a><span data-ttu-id="f87af-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f87af-137">See also</span></span>

- [<span data-ttu-id="f87af-138">^ = — Operator</span><span class="sxs-lookup"><span data-stu-id="f87af-138">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="f87af-139">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="f87af-139">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="f87af-140">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f87af-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f87af-141">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="f87af-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f87af-142">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f87af-142">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
