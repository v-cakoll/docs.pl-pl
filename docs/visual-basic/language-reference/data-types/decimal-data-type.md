---
title: Decimal, typ danych
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
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243326"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="531ed-102">Decimal — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="531ed-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="531ed-103">Posiada podpisane wartości całkowite 128-bitowe (16-bajtowe) reprezentujące 96-bitowe (12-bajtowe) liczby całkowite skalowane o zmienną moc 10.</span><span class="sxs-lookup"><span data-stu-id="531ed-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="531ed-104">Współczynnik skalowania określa liczbę cyfr po prawej stronie przecinka dziesiętnego; waha się od 0 do 28.</span><span class="sxs-lookup"><span data-stu-id="531ed-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="531ed-105">Przy skali 0 (bez miejsc dziesiętnych) największa możliwa wartość to +/-79,228,162,514,264,337,593,1543 950 335 (+/-7,922816251426437593543950335E+28).</span><span class="sxs-lookup"><span data-stu-id="531ed-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="531ed-106">Z miejscami po przecinku 28, największa wartość to +/-7.92281625251426437593543950335, a najmniejsza wartość niezerowa to +/-0.000000000000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="531ed-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="531ed-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="531ed-107">Remarks</span></span>

<span data-ttu-id="531ed-108">Typ `Decimal` danych zapewnia największą liczbę cyfr znaczących dla liczby.</span><span class="sxs-lookup"><span data-stu-id="531ed-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="531ed-109">Obsługuje do 29 cyfr znaczących i może reprezentować wartości przekraczające 7,9228 x 10^28.</span><span class="sxs-lookup"><span data-stu-id="531ed-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="531ed-110">Jest to szczególnie odpowiednie dla obliczeń, takich jak finansowe, które wymagają dużej liczby cyfr, ale nie tolerują błędów zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="531ed-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="531ed-111">Wartość domyślna `Decimal` to 0.</span><span class="sxs-lookup"><span data-stu-id="531ed-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="531ed-112">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="531ed-112">Programming Tips</span></span>

- <span data-ttu-id="531ed-113">**Precyzji.**</span><span class="sxs-lookup"><span data-stu-id="531ed-113">**Precision.**</span></span> <span data-ttu-id="531ed-114">`Decimal`nie jest typem danych zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="531ed-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="531ed-115">Struktura `Decimal` zawiera binarną wartość całkowitą, wraz z bitem znaku i współczynnik skalowania liczby całkowitej, który określa, jaka część wartości jest ułamkiem dziesiętnym.</span><span class="sxs-lookup"><span data-stu-id="531ed-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="531ed-116">Z tego `Decimal` powodu liczby mają bardziej precyzyjną reprezentację w`Single` `Double`pamięci niż typy zmiennoprzecinkowe ( i ).</span><span class="sxs-lookup"><span data-stu-id="531ed-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="531ed-117">**Wydajności.**</span><span class="sxs-lookup"><span data-stu-id="531ed-117">**Performance.**</span></span> <span data-ttu-id="531ed-118">Typ `Decimal` danych jest najwolniejszy ze wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="531ed-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="531ed-119">Przed wybraniem typu danych należy rozważyć znaczenie precyzji w stosunku do wydajności.</span><span class="sxs-lookup"><span data-stu-id="531ed-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="531ed-120">**Poszerzenie.**</span><span class="sxs-lookup"><span data-stu-id="531ed-120">**Widening.**</span></span> <span data-ttu-id="531ed-121">Typ `Decimal` danych rozszerza `Single` się `Double`do lub .</span><span class="sxs-lookup"><span data-stu-id="531ed-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="531ed-122">Oznacza to, `Decimal` że można przekonwertować do <xref:System.OverflowException?displayProperty=nameWithType> jednego z tych typów bez napotkania błędu.</span><span class="sxs-lookup"><span data-stu-id="531ed-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="531ed-123">**Końcowe zera.**</span><span class="sxs-lookup"><span data-stu-id="531ed-123">**Trailing Zeros.**</span></span> <span data-ttu-id="531ed-124">Visual Basic nie przechowuje końcowych `Decimal` zer w literału.</span><span class="sxs-lookup"><span data-stu-id="531ed-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="531ed-125">Jednak zmienna `Decimal` zachowuje wszystkie końcowe zera nabyte obliczeniowo.</span><span class="sxs-lookup"><span data-stu-id="531ed-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="531ed-126">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="531ed-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="531ed-127">Dane wyjściowe `MsgBox` w poprzednim przykładzie są następujące:</span><span class="sxs-lookup"><span data-stu-id="531ed-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="531ed-128">**Wpisz znaki.**</span><span class="sxs-lookup"><span data-stu-id="531ed-128">**Type Characters.**</span></span> <span data-ttu-id="531ed-129">Dołączenie znaku literału `D` do literału wymusza go do `Decimal` typu danych.</span><span class="sxs-lookup"><span data-stu-id="531ed-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="531ed-130">Dołączenie znaku `@` typu identyfikatora do dowolnego identyfikatora wymusza jego `Decimal`</span><span class="sxs-lookup"><span data-stu-id="531ed-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="531ed-131">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="531ed-131">**Framework Type.**</span></span> <span data-ttu-id="531ed-132">Odpowiedni typ w .NET Framework <xref:System.Decimal?displayProperty=nameWithType> jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="531ed-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="531ed-133">Zakres</span><span class="sxs-lookup"><span data-stu-id="531ed-133">Range</span></span>

 <span data-ttu-id="531ed-134">Może być konieczne `D` użycie znaku typu, aby `Decimal` przypisać dużą wartość do zmiennej lub stałej.</span><span class="sxs-lookup"><span data-stu-id="531ed-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="531ed-135">To wymaganie jest, ponieważ kompilator `Long` interpretuje literału, chyba że znak typu literału następuje literał, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="531ed-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="531ed-136">Deklaracja `bigDec1` dla nie powoduje przepełnienia, ponieważ wartość, która jest przypisana `Long`do niego mieści się w zakresie .</span><span class="sxs-lookup"><span data-stu-id="531ed-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="531ed-137">Wartość `Long` można przypisać do `Decimal` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="531ed-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="531ed-138">Deklaracja `bigDec2` dla generuje błąd przepełnienia, ponieważ wartość, która jest `Long`przypisana do niego jest zbyt duża dla .</span><span class="sxs-lookup"><span data-stu-id="531ed-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="531ed-139">Ponieważ literał numeryczny nie może być najpierw `Long`interpretowany jako , nie `Decimal` można go przypisać do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="531ed-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="531ed-140">Dla `bigDec3`, literał `D` typu znak rozwiązuje problem, zmuszając kompilator do `Decimal` interpretacji literału jako litera zamiast jako `Long`.</span><span class="sxs-lookup"><span data-stu-id="531ed-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="531ed-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="531ed-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="531ed-142">Typy danych</span><span class="sxs-lookup"><span data-stu-id="531ed-142">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="531ed-143">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="531ed-143">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="531ed-144">Double, typ danych</span><span class="sxs-lookup"><span data-stu-id="531ed-144">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="531ed-145">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="531ed-145">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="531ed-146">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="531ed-146">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="531ed-147">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="531ed-147">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
