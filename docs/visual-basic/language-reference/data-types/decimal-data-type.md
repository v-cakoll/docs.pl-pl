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
ms.openlocfilehash: 892824b61cfb6a0172361d220c638cab0a78565d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700873"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="df9bf-102">Decimal — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df9bf-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="df9bf-103">Przechowuje podpisane 128-bitowe (16-bajtowe) wartości reprezentujące liczby całkowite 96-bitowe (12-bajtowe) skalowane przez zmienną moc 10.</span><span class="sxs-lookup"><span data-stu-id="df9bf-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="df9bf-104">Współczynnik skalowania określa liczbę cyfr z prawej strony punktu dziesiętnego; dział IT mieści się w zakresie od 0 do 28.</span><span class="sxs-lookup"><span data-stu-id="df9bf-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="df9bf-105">W przypadku skali 0 (bez miejsc dziesiętnych) największa możliwa wartość to +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="df9bf-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="df9bf-106">W przypadku 28 miejsc dziesiętnych największą wartością jest +/-7.9228162514264337593543950335, a najmniejsza wartość niezerowa to +/-0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="df9bf-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="df9bf-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df9bf-107">Remarks</span></span>

<span data-ttu-id="df9bf-108">Typ danych `Decimal` zapewnia największą liczbę cyfr znaczących w liczbie.</span><span class="sxs-lookup"><span data-stu-id="df9bf-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="df9bf-109">Obsługuje do 29 cyfr znaczących i może reprezentować wartości przekraczające 7,9228 x 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="df9bf-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="df9bf-110">Jest to szczególnie przydatne w przypadku obliczeń, takich jak finansowe, które wymagają dużej liczby cyfr, ale nie mogą tolerować błędów zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="df9bf-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="df9bf-111">Wartość domyślna `Decimal` to 0.</span><span class="sxs-lookup"><span data-stu-id="df9bf-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="df9bf-112">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="df9bf-112">Programming Tips</span></span>

- <span data-ttu-id="df9bf-113">**Dokładne.**</span><span class="sxs-lookup"><span data-stu-id="df9bf-113">**Precision.**</span></span> <span data-ttu-id="df9bf-114">`Decimal` nie jest typem danych zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="df9bf-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="df9bf-115">Struktura `Decimal` zawiera binarną wartość całkowitą, łącznie z bitem znaku i czynnikiem skalowania liczby całkowitej, która określa, jaka część wartości jest ułamk dziesiętny.</span><span class="sxs-lookup"><span data-stu-id="df9bf-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="df9bf-116">Z tego powodu numery `Decimal` mają dokładniejszą reprezentację w pamięci niż typy zmiennoprzecinkowe (`Single` i `Double`).</span><span class="sxs-lookup"><span data-stu-id="df9bf-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="df9bf-117">**Skuteczności.**</span><span class="sxs-lookup"><span data-stu-id="df9bf-117">**Performance.**</span></span> <span data-ttu-id="df9bf-118">Typ danych `Decimal` to najwolniejsze ze wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="df9bf-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="df9bf-119">Przed wybraniem typu danych należy zaważyć znaczenie dokładności względem wydajności.</span><span class="sxs-lookup"><span data-stu-id="df9bf-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="df9bf-120">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="df9bf-120">**Widening.**</span></span> <span data-ttu-id="df9bf-121">Typ danych `Decimal` jest rozszerzany do `Single` lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="df9bf-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="df9bf-122">Oznacza to, że można skonwertować `Decimal` do jednego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="df9bf-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="df9bf-123">**Końcowe zera.**</span><span class="sxs-lookup"><span data-stu-id="df9bf-123">**Trailing Zeros.**</span></span> <span data-ttu-id="df9bf-124">Visual Basic nie przechowuje końcowych zer w literale `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="df9bf-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="df9bf-125">Jednak zmienna `Decimal` zachowuje obliczenia w sposób obliczeniowy.</span><span class="sxs-lookup"><span data-stu-id="df9bf-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="df9bf-126">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="df9bf-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="df9bf-127">Dane wyjściowe `MsgBox` w poprzednim przykładzie są następujące:</span><span class="sxs-lookup"><span data-stu-id="df9bf-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="df9bf-128">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="df9bf-128">**Type Characters.**</span></span> <span data-ttu-id="df9bf-129">Dołączanie znaku typu literału `D` do literału wymusza go do typu danych `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="df9bf-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="df9bf-130">Dołączanie znaku typu identyfikatora `@` do dowolnego identyfikatora wymusza `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="df9bf-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="df9bf-131">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="df9bf-131">**Framework Type.**</span></span> <span data-ttu-id="df9bf-132">Odpowiedni typ w .NET Framework jest strukturą <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df9bf-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="df9bf-133">Zakres</span><span class="sxs-lookup"><span data-stu-id="df9bf-133">Range</span></span>
 <span data-ttu-id="df9bf-134">Może być konieczne użycie znaku typu `D`, aby przypisać dużą wartość do zmiennej `Decimal` lub stałej.</span><span class="sxs-lookup"><span data-stu-id="df9bf-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="df9bf-135">To wymaganie wynika z faktu, że kompilator interpretuje literał jako `Long`, chyba że znak typu literału jest zgodny z literałem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="df9bf-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="df9bf-136">Deklaracja dla `bigDec1` nie produkuje przepełnienia, ponieważ przypisana do niej wartość znajduje się w zakresie dla `Long`.</span><span class="sxs-lookup"><span data-stu-id="df9bf-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="df9bf-137">Wartość `Long` można przypisać do zmiennej `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="df9bf-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="df9bf-138">Deklaracja `bigDec2` generuje błąd przepełnienia, ponieważ przypisana do niego wartość jest za duża dla `Long`.</span><span class="sxs-lookup"><span data-stu-id="df9bf-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="df9bf-139">Ponieważ nie można najpierw zinterpretować literału numerycznego jako `Long`, nie można go przypisać do zmiennej `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="df9bf-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="df9bf-140">W przypadku `bigDec3` znak typu literału `D` rozwiązuje problem, wymuszając kompilator do interpretowania literału jako `Decimal` zamiast jako `Long`.</span><span class="sxs-lookup"><span data-stu-id="df9bf-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="df9bf-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df9bf-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="df9bf-142">Typy danych</span><span class="sxs-lookup"><span data-stu-id="df9bf-142">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="df9bf-143">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="df9bf-143">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="df9bf-144">Double, typ danych</span><span class="sxs-lookup"><span data-stu-id="df9bf-144">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="df9bf-145">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="df9bf-145">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="df9bf-146">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="df9bf-146">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="df9bf-147">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="df9bf-147">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
