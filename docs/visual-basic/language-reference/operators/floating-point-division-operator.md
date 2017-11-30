---
title: "/ — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb./
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f221e863725b9aeb0b3fa3219b3a881541e2be0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b0075-102">/ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0075-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="b0075-103">Dzieli dwie liczby i zwraca wynik zmiennoprzecinkowy.</span><span class="sxs-lookup"><span data-stu-id="b0075-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0075-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0075-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="b0075-105">Części</span><span class="sxs-lookup"><span data-stu-id="b0075-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="b0075-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b0075-106">Required.</span></span> <span data-ttu-id="b0075-107">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="b0075-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="b0075-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b0075-108">Required.</span></span> <span data-ttu-id="b0075-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="b0075-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="b0075-110">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="b0075-110">Supported Types</span></span>  
 <span data-ttu-id="b0075-111">Wszystkie typy liczbowe w tym typy bez znaku i liczb zmiennoprzecinkowych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="b0075-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="b0075-112">Wynik</span><span class="sxs-lookup"><span data-stu-id="b0075-112">Result</span></span>  
 <span data-ttu-id="b0075-113">Wynik jest pełna iloraz `expression1` podzielona przez `expression2`, w tym wszelkie pozostałe.</span><span class="sxs-lookup"><span data-stu-id="b0075-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="b0075-114">[\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) Zwraca iloraz liczb całkowitych, co powoduje resztę.</span><span class="sxs-lookup"><span data-stu-id="b0075-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0075-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0075-115">Remarks</span></span>  
 <span data-ttu-id="b0075-116">Typ danych w wyniku zależy od typów argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="b0075-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="b0075-117">W poniższej tabeli przedstawiono, jak typ danych wyniku jest określana.</span><span class="sxs-lookup"><span data-stu-id="b0075-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="b0075-118">Argument operacji typy danych</span><span class="sxs-lookup"><span data-stu-id="b0075-118">Operand data types</span></span>|<span data-ttu-id="b0075-119">Typ danych wyników</span><span class="sxs-lookup"><span data-stu-id="b0075-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="b0075-120">Oba wyrażenia są typy całkowite danych ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [całkowitą](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [długi](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="b0075-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="b0075-121">Jedno wyrażenie jest [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md) — typ danych, a druga nie jest [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="b0075-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="b0075-122">Jedno wyrażenie jest [dziesiętną](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — typ danych, a druga nie jest [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md) lub [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="b0075-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="b0075-123">Jedno z wyrażeń ma [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md) — typ danych</span><span class="sxs-lookup"><span data-stu-id="b0075-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="b0075-124">Przed wykonaniem dzielenia rozszerzone są wszystkie wartości całkowitych wyrażenia liczbowego, tak aby `Double`.</span><span class="sxs-lookup"><span data-stu-id="b0075-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="b0075-125">Jeśli Przypisz wynik do typu całkowitego danych, Visual Basic próbuje przekonwertować wynik `Double` dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="b0075-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="b0075-126">To Zgłoś wyjątek, jeśli wynik nie mieści się w danym typie.</span><span class="sxs-lookup"><span data-stu-id="b0075-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="b0075-127">Na tej stronie pomocy, w szczególności, zobacz "Próba dzielenia przez Zero".</span><span class="sxs-lookup"><span data-stu-id="b0075-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="b0075-128">Jeśli `expression1` lub `expression2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.</span><span class="sxs-lookup"><span data-stu-id="b0075-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="b0075-129">Próba dzielenia przez Zero</span><span class="sxs-lookup"><span data-stu-id="b0075-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="b0075-130">Jeśli `expression2` daje w wyniku wartość 0, `/` operator zależy od operand różne typy danych.</span><span class="sxs-lookup"><span data-stu-id="b0075-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="b0075-131">W poniższej tabeli przedstawiono możliwe zachowania.</span><span class="sxs-lookup"><span data-stu-id="b0075-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="b0075-132">Argument operacji typy danych</span><span class="sxs-lookup"><span data-stu-id="b0075-132">Operand data types</span></span>|<span data-ttu-id="b0075-133">Zachowanie Jeśli `expression2` wynosi zero</span><span class="sxs-lookup"><span data-stu-id="b0075-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="b0075-134">Zmiennoprzecinkowe (`Single` lub `Double`)</span><span class="sxs-lookup"><span data-stu-id="b0075-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="b0075-135">Zwraca infinity (<xref:System.Double.PositiveInfinity> lub <xref:System.Double.NegativeInfinity>), lub <xref:System.Double.NaN> (nie liczba) Jeśli `expression1` również wynosi zero</span><span class="sxs-lookup"><span data-stu-id="b0075-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="b0075-136">Zgłasza wyjątek<xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="b0075-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="b0075-137">Typy całkowite (podpisane lub bez znaku)</span><span class="sxs-lookup"><span data-stu-id="b0075-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="b0075-138">Próba konwersji do typu całkowitego zgłasza <xref:System.OverflowException> ponieważ typy całkowite nie akceptuje <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, lub<xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="b0075-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="b0075-139">`/` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b0075-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b0075-140">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="b0075-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b0075-141">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b0075-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0075-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0075-142">Example</span></span>  
 <span data-ttu-id="b0075-143">W tym przykładzie użyto `/` operatora, aby wykonać dzielenia liczb zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="b0075-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="b0075-144">Wynik jest równy ilorazowi dwóch argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="b0075-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 <span data-ttu-id="b0075-145">Wyrażenia w poprzednim przykładzie zwracać wartości 2.5 i 3.333333.</span><span class="sxs-lookup"><span data-stu-id="b0075-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="b0075-146">Należy pamiętać, że wynik zawsze liczb zmiennoprzecinkowych (`Double`), nawet jeśli obydwa argumenty operacji są stałe całkowite.</span><span class="sxs-lookup"><span data-stu-id="b0075-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0075-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0075-147">See Also</span></span>  
 [<span data-ttu-id="b0075-148">/ = — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0075-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="b0075-149">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0075-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="b0075-150">Typy danych wyników operatora</span><span class="sxs-lookup"><span data-stu-id="b0075-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
 [<span data-ttu-id="b0075-151">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="b0075-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="b0075-152">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0075-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="b0075-153">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="b0075-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="b0075-154">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0075-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
