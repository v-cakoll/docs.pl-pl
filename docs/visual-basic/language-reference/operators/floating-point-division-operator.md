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
ms.openlocfilehash: af2316f92e2904eee1e8c046b34b8147e40cb513
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825069"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="02ca6-102">/ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02ca6-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="02ca6-103">Dzieli dwie liczby i zwraca wynik zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="02ca6-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02ca6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="02ca6-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="02ca6-105">Części</span><span class="sxs-lookup"><span data-stu-id="02ca6-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="02ca6-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="02ca6-106">Required.</span></span> <span data-ttu-id="02ca6-107">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="02ca6-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="02ca6-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="02ca6-108">Required.</span></span> <span data-ttu-id="02ca6-109">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="02ca6-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="02ca6-110">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="02ca6-110">Supported Types</span></span>  
 <span data-ttu-id="02ca6-111">Wszystkie typy liczbowe, w tym typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="02ca6-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="02ca6-112">Wynik</span><span class="sxs-lookup"><span data-stu-id="02ca6-112">Result</span></span>  
 <span data-ttu-id="02ca6-113">Wynikiem jest pełna iloraz `expression1` podzielona przez `expression2`, włączając wszelkie pozostałe.</span><span class="sxs-lookup"><span data-stu-id="02ca6-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="02ca6-114">[\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) Zwraca iloraz liczb całkowitych, co powoduje resztę.</span><span class="sxs-lookup"><span data-stu-id="02ca6-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02ca6-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02ca6-115">Remarks</span></span>  
 <span data-ttu-id="02ca6-116">Typ danych wynik zależy od typów argumentów.</span><span class="sxs-lookup"><span data-stu-id="02ca6-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="02ca6-117">W poniższej tabeli przedstawiono, jak typ danych wyniku jest określana.</span><span class="sxs-lookup"><span data-stu-id="02ca6-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="02ca6-118">Argumentami o typach danych</span><span class="sxs-lookup"><span data-stu-id="02ca6-118">Operand data types</span></span>|<span data-ttu-id="02ca6-119">Typ danych wyniku</span><span class="sxs-lookup"><span data-stu-id="02ca6-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="02ca6-120">Oba wyrażenia są integralnymi typami danych ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [całkowitą](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [długie](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="02ca6-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="02ca6-121">Jedno wyrażenie jest [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md) — typ danych, a druga nie jest [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="02ca6-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="02ca6-122">Jedno wyrażenie jest [dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — typ danych, a druga nie jest [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md) lub [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="02ca6-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="02ca6-123">Albo wyrażenie jest [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) — typ danych</span><span class="sxs-lookup"><span data-stu-id="02ca6-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="02ca6-124">Przed wykonaniem dzielenia rozszerzone do dowolnego typu całkowitego wyrażeń liczbowych `Double`.</span><span class="sxs-lookup"><span data-stu-id="02ca6-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="02ca6-125">Jeśli przypiszesz wynik do typu liczby całkowitej danych, Visual Basic stara się przekonwertować wynik `Double` do tego typu.</span><span class="sxs-lookup"><span data-stu-id="02ca6-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="02ca6-126">Może zgłosić wyjątek, jeśli wynik nie mieści się w tym typie.</span><span class="sxs-lookup"><span data-stu-id="02ca6-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="02ca6-127">W szczególności zobacz "Próba dzielenia przez Zero" na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="02ca6-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="02ca6-128">Jeśli `expression1` lub `expression2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest ona traktowana jak zero.</span><span class="sxs-lookup"><span data-stu-id="02ca6-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="02ca6-129">Próba dzielenia przez Zero</span><span class="sxs-lookup"><span data-stu-id="02ca6-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="02ca6-130">Jeśli `expression2` osiągnie wartość zero, `/` operator zachowuje się inaczej dla różnych argumentami o typach danych.</span><span class="sxs-lookup"><span data-stu-id="02ca6-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="02ca6-131">W poniższej tabeli przedstawiono możliwe zachowania.</span><span class="sxs-lookup"><span data-stu-id="02ca6-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="02ca6-132">Argumentami o typach danych</span><span class="sxs-lookup"><span data-stu-id="02ca6-132">Operand data types</span></span>|<span data-ttu-id="02ca6-133">Zachowanie Jeśli `expression2` wynosi zero</span><span class="sxs-lookup"><span data-stu-id="02ca6-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="02ca6-134">Zmiennoprzecinkowe (`Single` lub `Double`)</span><span class="sxs-lookup"><span data-stu-id="02ca6-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="02ca6-135">Zwraca infinity (<xref:System.Double.PositiveInfinity> lub <xref:System.Double.NegativeInfinity>), lub <xref:System.Double.NaN> (nie liczba) Jeśli `expression1` również wynosi zero</span><span class="sxs-lookup"><span data-stu-id="02ca6-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="02ca6-136">Zgłasza wyjątek <xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="02ca6-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="02ca6-137">Całkowite (podpisane lub niepodpisane)</span><span class="sxs-lookup"><span data-stu-id="02ca6-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="02ca6-138">Próba konwersji do typu całkowitego zgłasza <xref:System.OverflowException> ponieważ typów całkowitych nie może akceptować <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, lub <xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="02ca6-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="02ca6-139">`/` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="02ca6-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="02ca6-140">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="02ca6-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="02ca6-141">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="02ca6-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02ca6-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="02ca6-142">Example</span></span>  
 <span data-ttu-id="02ca6-143">W tym przykładzie użyto `/` operator przeprowadzić dzielenia liczb zmiennopozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="02ca6-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="02ca6-144">Wynik jest równy ilorazowi dwóch argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="02ca6-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="02ca6-145">Wyrażenia w poprzednim przykładzie wartości zwracanych z 2.5 i 3.333333.</span><span class="sxs-lookup"><span data-stu-id="02ca6-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="02ca6-146">Należy pamiętać, że wynik zawsze zmiennoprzecinkowych (`Double`), nawet jeśli oba operandy są stałe całkowite.</span><span class="sxs-lookup"><span data-stu-id="02ca6-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ca6-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02ca6-147">See also</span></span>

- [<span data-ttu-id="02ca6-148">/ = — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02ca6-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="02ca6-149">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02ca6-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="02ca6-150">Typy danych wyników operatora</span><span class="sxs-lookup"><span data-stu-id="02ca6-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [<span data-ttu-id="02ca6-151">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="02ca6-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="02ca6-152">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="02ca6-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="02ca6-153">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="02ca6-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="02ca6-154">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="02ca6-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
