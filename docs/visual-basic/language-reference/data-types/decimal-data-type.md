---
title: Decimal — Typ danych (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 4d530a8c1f85d2f0045184c05df63849047a8204
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834104"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="fb3fc-102">Decimal — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb3fc-102">Decimal Data Type (Visual Basic)</span></span>
<span data-ttu-id="fb3fc-103">Przechowuje podpisany 128-bitowego (16-bajtową) wartości reprezentujących numery 96-bitową liczbę całkowitą z (12-bajtową) skalowania przez zmienną potęgą liczby 10.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="fb3fc-104">Czynnik skalowania określa liczbę cyfr z prawej strony punktu dziesiętnego; waha się od 0 do 28.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="fb3fc-105">O skali 0 (bez miejsc dziesiętnych) największa możliwa wartość to +/-79,228,162,514,264,337,593,543,950,335 (+/-7 .9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="fb3fc-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="fb3fc-106">28 miejsc dziesiętnych największa wartość jest +/-7.9228162514264337593543950335 i najmniejszą wartość różną od zera jest +/-0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="fb3fc-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb3fc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb3fc-107">Remarks</span></span>  
 <span data-ttu-id="fb3fc-108">`Decimal` — Typ danych zapewnia największą liczbę cyfr znaczących liczbą.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="fb3fc-109">Obsługuje więcej niż 29 cyfr znaczących i może reprezentować wartości przekraczające 7.9228 x 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="fb3fc-110">Jest szczególnie przydatny w obliczeniach, takich jak finansowych, które wymagają dużej liczby cyfr, ale nie tolerują błędy zaokrągleń.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>  
  
 <span data-ttu-id="fb3fc-111">Wartość domyślna `Decimal` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-111">The default value of `Decimal` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="fb3fc-112">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="fb3fc-112">Programming Tips</span></span>  
  
-   <span data-ttu-id="fb3fc-113">**Dokładność.**</span><span class="sxs-lookup"><span data-stu-id="fb3fc-113">**Precision.**</span></span> <span data-ttu-id="fb3fc-114">`Decimal` nie jest typem danych zmiennopozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="fb3fc-115">`Decimal` Struktury przechowuje wartość całkowitą binarne, wraz z bitem znaku i współczynnik, która określa, jaka część wartości jest ułamek dziesiętny skalowania liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="fb3fc-116">W związku z tym `Decimal` liczby mają bardziej precyzyjne reprezentacji w pamięci, niż typów zmiennoprzecinkowych (`Single` i `Double`).</span><span class="sxs-lookup"><span data-stu-id="fb3fc-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>  
  
-   <span data-ttu-id="fb3fc-117">**Wydajność.**</span><span class="sxs-lookup"><span data-stu-id="fb3fc-117">**Performance.**</span></span> <span data-ttu-id="fb3fc-118">`Decimal` Typ danych jest najwolniejsze wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="fb3fc-119">Należy porównać znaczenie dokładności względem wydajności przed wybraniem typu danych.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>  
  
-   <span data-ttu-id="fb3fc-120">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="fb3fc-120">**Widening.**</span></span> <span data-ttu-id="fb3fc-121">`Decimal` — Typ danych rozszerza się na `Single` lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="fb3fc-122">Oznacza to, że możesz przekonwertować `Decimal` do jednej z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="fb3fc-123">**Końcowe zera.**</span><span class="sxs-lookup"><span data-stu-id="fb3fc-123">**Trailing Zeros.**</span></span> <span data-ttu-id="fb3fc-124">Visual Basic nie przechowuje zera końcowe w `Decimal` literału.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="fb3fc-125">Jednak `Decimal` zmienna zachowuje dowolne zera końcowe, które zostały nabyte w praktyce.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="fb3fc-126">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-126">The following example illustrates this.</span></span>  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     <span data-ttu-id="fb3fc-127">Dane wyjściowe `MsgBox` w powyższym przykładzie jest następująca:</span><span class="sxs-lookup"><span data-stu-id="fb3fc-127">The output of `MsgBox` in the preceding example is as follows:</span></span>  
  
     <span data-ttu-id="fb3fc-128">d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4</span><span class="sxs-lookup"><span data-stu-id="fb3fc-128">d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4</span></span>  
  
-   <span data-ttu-id="fb3fc-129">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="fb3fc-129">**Type Characters.**</span></span> <span data-ttu-id="fb3fc-130">Dołączanie znaku typu literał `D` do literału wymusza `Decimal` typu danych.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="fb3fc-131">Dołączanie znaku typu identyfikator `@` do jakiegokolwiek identyfikatora wymusza `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>  
  
-   <span data-ttu-id="fb3fc-132">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="fb3fc-132">**Framework Type.**</span></span> <span data-ttu-id="fb3fc-133">Odpowiedni typ w .NET Framework jest <xref:System.Decimal?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="fb3fc-134">Zakres</span><span class="sxs-lookup"><span data-stu-id="fb3fc-134">Range</span></span>  
 <span data-ttu-id="fb3fc-135">Może być konieczne użycie `D` wpisz znak duża wartość, aby przypisać `Decimal` zmienną lub stałą.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="fb3fc-136">Jest to wymaganie, ponieważ kompilator interpretuje słowa kluczowe literału jako `Long` chyba, że znak literalny typu następuje literału, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 <span data-ttu-id="fb3fc-137">Deklaracja `bigDec1` nie generuje przepełnienie, ponieważ wartość, która jest przypisana do niego znajduje się w zakresie dla `Long`.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="fb3fc-138">`Long` Można przypisać wartości do `Decimal` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="fb3fc-139">Deklaracja `bigDec2` generuje błąd przepełnienia, ponieważ wartość, która jest przypisana do niego jest za duży dla `Long`.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="fb3fc-140">Ponieważ literału liczbowego najpierw nie mogą być interpretowane jako `Long`, nie można przypisać do `Decimal` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="fb3fc-141">Aby uzyskać `bigDec3`, znak literalny typu `D` rozwiązuje problem, wymuszając na kompilatorze interpretowanie literału jako `Decimal` zamiast jako `Long`.</span><span class="sxs-lookup"><span data-stu-id="fb3fc-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3fc-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb3fc-142">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fb3fc-143">Typy danych</span><span class="sxs-lookup"><span data-stu-id="fb3fc-143">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="fb3fc-144">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="fb3fc-144">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="fb3fc-145">Double, typ danych</span><span class="sxs-lookup"><span data-stu-id="fb3fc-145">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="fb3fc-146">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="fb3fc-146">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="fb3fc-147">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="fb3fc-147">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="fb3fc-148">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="fb3fc-148">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
