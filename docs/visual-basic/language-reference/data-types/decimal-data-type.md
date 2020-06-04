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
ms.openlocfilehash: 690c8061b6df1115aa24668520170b44edfa8287
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415650"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="15987-102">Decimal — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15987-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="15987-103">Przechowuje podpisane 128-bitowe (16-bajtowe) wartości reprezentujące liczby całkowite 96-bitowe (12-bajtowe) skalowane przez zmienną moc 10.</span><span class="sxs-lookup"><span data-stu-id="15987-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="15987-104">Współczynnik skalowania określa liczbę cyfr z prawej strony punktu dziesiętnego; dział IT mieści się w zakresie od 0 do 28.</span><span class="sxs-lookup"><span data-stu-id="15987-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="15987-105">W przypadku skali 0 (bez miejsc dziesiętnych) największa możliwa wartość to +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="15987-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="15987-106">W przypadku 28 miejsc dziesiętnych największą wartością jest +/-7.9228162514264337593543950335, a najmniejsza wartość niezerowa to +/-0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="15987-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="15987-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15987-107">Remarks</span></span>

<span data-ttu-id="15987-108">`Decimal`Typ danych zapewnia największą liczbę cyfr znaczących w liczbie.</span><span class="sxs-lookup"><span data-stu-id="15987-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="15987-109">Obsługuje do 29 cyfr znaczących i może reprezentować wartości przekraczające 7,9228 x 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="15987-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="15987-110">Jest to szczególnie przydatne w przypadku obliczeń, takich jak finansowe, które wymagają dużej liczby cyfr, ale nie mogą tolerować błędów zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="15987-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="15987-111">Wartość domyślna `Decimal` to 0.</span><span class="sxs-lookup"><span data-stu-id="15987-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="15987-112">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="15987-112">Programming Tips</span></span>

- <span data-ttu-id="15987-113">**Dokładne.**</span><span class="sxs-lookup"><span data-stu-id="15987-113">**Precision.**</span></span> <span data-ttu-id="15987-114">`Decimal`nie jest typem danych zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="15987-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="15987-115">`Decimal`Struktura zawiera binarną wartość całkowitą, łącznie z bitem znaku i czynnikiem skalowania liczby całkowitej, która określa, jaka część wartości jest ułamk dziesiętny.</span><span class="sxs-lookup"><span data-stu-id="15987-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="15987-116">Z tego powodu `Decimal` liczby mają bardziej precyzyjną reprezentację w pamięci niż typy zmiennoprzecinkowe ( `Single` i `Double` ).</span><span class="sxs-lookup"><span data-stu-id="15987-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="15987-117">**Skuteczności.**</span><span class="sxs-lookup"><span data-stu-id="15987-117">**Performance.**</span></span> <span data-ttu-id="15987-118">`Decimal`Typ danych jest najwolniej ze wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="15987-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="15987-119">Przed wybraniem typu danych należy zaważyć znaczenie dokładności względem wydajności.</span><span class="sxs-lookup"><span data-stu-id="15987-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="15987-120">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="15987-120">**Widening.**</span></span> <span data-ttu-id="15987-121">`Decimal`Typ danych poszerza do `Single` lub `Double` .</span><span class="sxs-lookup"><span data-stu-id="15987-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="15987-122">Oznacza to, że można przekonwertować `Decimal` na jeden z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="15987-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="15987-123">**Końcowe zera.**</span><span class="sxs-lookup"><span data-stu-id="15987-123">**Trailing Zeros.**</span></span> <span data-ttu-id="15987-124">Visual Basic nie przechowuje końcowych zer w `Decimal` literale.</span><span class="sxs-lookup"><span data-stu-id="15987-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="15987-125">Jednak `Decimal` zmienna zachowuje obliczenia w sposób obliczeniowy.</span><span class="sxs-lookup"><span data-stu-id="15987-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="15987-126">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="15987-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="15987-127">Dane wyjściowe `MsgBox` w poprzednim przykładzie są następujące:</span><span class="sxs-lookup"><span data-stu-id="15987-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="15987-128">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="15987-128">**Type Characters.**</span></span> <span data-ttu-id="15987-129">Dołączanie znaku typu literału `D` do literału wymusza jego `Decimal` Typ danych.</span><span class="sxs-lookup"><span data-stu-id="15987-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="15987-130">Dołączanie znaku typu identyfikatora `@` do dowolnego identyfikatora zmusza go do `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="15987-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="15987-131">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="15987-131">**Framework Type.**</span></span> <span data-ttu-id="15987-132">Odpowiedni typ w .NET Framework jest <xref:System.Decimal?displayProperty=nameWithType> strukturą.</span><span class="sxs-lookup"><span data-stu-id="15987-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="15987-133">Zakres</span><span class="sxs-lookup"><span data-stu-id="15987-133">Range</span></span>

 <span data-ttu-id="15987-134">Może być konieczne użycie `D` znaku typu, aby przypisać dużą wartość do `Decimal` zmiennej lub stałej.</span><span class="sxs-lookup"><span data-stu-id="15987-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="15987-135">To wymaganie wynika z faktu, że kompilator interpretuje literał jako `Long` , chyba że znak typu literału jest zgodny z literałem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15987-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="15987-136">Deklaracja dla `bigDec1` nie produkuje przepełnienia, ponieważ przypisana do niej wartość znajduje się w zakresie dla `Long` .</span><span class="sxs-lookup"><span data-stu-id="15987-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="15987-137">`Long`Wartość może być przypisana do `Decimal` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="15987-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="15987-138">Deklaracja dla `bigDec2` generuje błąd przepełnienia, ponieważ przypisana do niego wartość jest za duża dla `Long` .</span><span class="sxs-lookup"><span data-stu-id="15987-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="15987-139">Ponieważ literał liczbowy nie może być najpierw interpretowany jako `Long` , nie można go przypisać do `Decimal` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="15987-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="15987-140">W przypadku `bigDec3` , znak typu literału `D` rozwiązuje problem, wymuszając kompilator, aby interpretował literał jako `Decimal` zamiast `Long` .</span><span class="sxs-lookup"><span data-stu-id="15987-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="15987-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15987-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="15987-142">Typy danych</span><span class="sxs-lookup"><span data-stu-id="15987-142">Data Types</span></span>](index.md)
- [<span data-ttu-id="15987-143">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="15987-143">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="15987-144">Double, typ danych</span><span class="sxs-lookup"><span data-stu-id="15987-144">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="15987-145">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="15987-145">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="15987-146">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="15987-146">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="15987-147">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="15987-147">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
