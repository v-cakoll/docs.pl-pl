---
title: / — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: d30d871d48bc87e050a072cd01a38065be20616c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933260"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="306dc-102">/ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="306dc-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="306dc-103">Dzieli dwie liczby i zwraca wynik zmiennoprzecinkowy.</span><span class="sxs-lookup"><span data-stu-id="306dc-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="306dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="306dc-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="306dc-105">Części</span><span class="sxs-lookup"><span data-stu-id="306dc-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="306dc-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="306dc-106">Required.</span></span> <span data-ttu-id="306dc-107">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="306dc-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="306dc-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="306dc-108">Required.</span></span> <span data-ttu-id="306dc-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="306dc-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="306dc-110">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="306dc-110">Supported Types</span></span>  
 <span data-ttu-id="306dc-111">Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="306dc-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="306dc-112">Wynik</span><span class="sxs-lookup"><span data-stu-id="306dc-112">Result</span></span>  
 <span data-ttu-id="306dc-113">Wynikiem jest pełny iloraz `expression1` podzielony przez `expression2`, łącznie z dowolnymi resztami.</span><span class="sxs-lookup"><span data-stu-id="306dc-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="306dc-114">[Operator \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) zwraca iloraz całkowity, który porzuca resztę.</span><span class="sxs-lookup"><span data-stu-id="306dc-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="306dc-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="306dc-115">Remarks</span></span>  
 <span data-ttu-id="306dc-116">Typ danych wyniku zależy od typów operandów.</span><span class="sxs-lookup"><span data-stu-id="306dc-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="306dc-117">W poniższej tabeli przedstawiono sposób określania typu danych wyniku.</span><span class="sxs-lookup"><span data-stu-id="306dc-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="306dc-118">Typy danych operandu</span><span class="sxs-lookup"><span data-stu-id="306dc-118">Operand data types</span></span>|<span data-ttu-id="306dc-119">Typ danych wynikowych</span><span class="sxs-lookup"><span data-stu-id="306dc-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="306dc-120">Oba wyrażenia są typami danych całkowitych[](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)(bajty, [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótkie](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULONG](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="306dc-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="306dc-121">Jedno wyrażenie jest [pojedynczym](../../../visual-basic/language-reference/data-types/single-data-type.md) typem danych, a drugi nie jest [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="306dc-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="306dc-122">Jedno wyrażenie jest typu [](../../../visual-basic/language-reference/data-types/decimal-data-type.md) danych dziesiętnych, a drugi nie jest [pojedynczym](../../../visual-basic/language-reference/data-types/single-data-type.md) lub [podwójnym](../../../visual-basic/language-reference/data-types/double-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="306dc-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="306dc-123">Jedno wyrażenie jest [podwójnym](../../../visual-basic/language-reference/data-types/double-data-type.md) typem danych</span><span class="sxs-lookup"><span data-stu-id="306dc-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="306dc-124">Przed wykonaniem dzielenia wszystkie całkowite wyrażenia liczbowe są rozszerzane do `Double`.</span><span class="sxs-lookup"><span data-stu-id="306dc-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="306dc-125">Jeśli zostanie przypisany wynik do typu danych całkowitych, Visual Basic próbuje skonwertować wynik z `Double` do tego typu.</span><span class="sxs-lookup"><span data-stu-id="306dc-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="306dc-126">Może zgłosić wyjątek, jeśli wynik nie mieści się w danym typie.</span><span class="sxs-lookup"><span data-stu-id="306dc-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="306dc-127">W szczególności Zobacz "Próba dzielenia przez zero" na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="306dc-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="306dc-128">Jeśli `expression1` lub`expression2` zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.</span><span class="sxs-lookup"><span data-stu-id="306dc-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="306dc-129">Próba dzielenia przez zero</span><span class="sxs-lookup"><span data-stu-id="306dc-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="306dc-130">Jeśli `expression2` wartość jest równa zero `/` , operator działa inaczej dla różnych typów danych operandu.</span><span class="sxs-lookup"><span data-stu-id="306dc-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="306dc-131">W poniższej tabeli przedstawiono możliwe zachowania.</span><span class="sxs-lookup"><span data-stu-id="306dc-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="306dc-132">Typy danych operandu</span><span class="sxs-lookup"><span data-stu-id="306dc-132">Operand data types</span></span>|<span data-ttu-id="306dc-133">Zachowanie jeśli `expression2` jest równe zero</span><span class="sxs-lookup"><span data-stu-id="306dc-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="306dc-134">Zmiennoprzecinkowe (`Single` lub `Double`)</span><span class="sxs-lookup"><span data-stu-id="306dc-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="306dc-135">Zwraca nieskończoność<xref:System.Double.PositiveInfinity> ( <xref:System.Double.NegativeInfinity>lub) lub <xref:System.Double.NaN> (nie liczbę), jeśli `expression1` również jest równa zero</span><span class="sxs-lookup"><span data-stu-id="306dc-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="306dc-136">Generuje<xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="306dc-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="306dc-137">Całka (ze znakiem lub bez znaku)</span><span class="sxs-lookup"><span data-stu-id="306dc-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="306dc-138">Próba konwersji z powrotem na typ całkowity zgłasza <xref:System.OverflowException> , ponieważ typy całkowite nie <xref:System.Double.PositiveInfinity>mogą <xref:System.Double.NegativeInfinity>akceptować, lub<xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="306dc-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="306dc-139">Operator może być przeciążony, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. `/`</span><span class="sxs-lookup"><span data-stu-id="306dc-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="306dc-140">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="306dc-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="306dc-141">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="306dc-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="306dc-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="306dc-142">Example</span></span>  
 <span data-ttu-id="306dc-143">Ten przykład używa `/` operatora do wykonywania dzielenia zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="306dc-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="306dc-144">Wynik jest ilorazem dwóch operandów.</span><span class="sxs-lookup"><span data-stu-id="306dc-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="306dc-145">Wyrażenia w poprzednim przykładzie zwracają wartości 2,5 i 3,333333.</span><span class="sxs-lookup"><span data-stu-id="306dc-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="306dc-146">Należy zauważyć, że wynik jest zawsze zmiennoprzecinkowy (`Double`), mimo że oba operandy są stałymi całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="306dc-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306dc-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="306dc-147">See also</span></span>

- [<span data-ttu-id="306dc-148">Operator/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="306dc-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="306dc-149">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="306dc-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="306dc-150">Typy danych wyników operatora</span><span class="sxs-lookup"><span data-stu-id="306dc-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [<span data-ttu-id="306dc-151">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="306dc-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="306dc-152">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="306dc-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="306dc-153">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="306dc-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="306dc-154">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="306dc-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
