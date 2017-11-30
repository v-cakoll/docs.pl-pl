---
title: "Decimal — Typ danych (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Decimal
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55a9293fa680a7a04cff4099654d4d66790e8d3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="9e4df-102">Decimal — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e4df-102">Decimal Data Type (Visual Basic)</span></span>
<span data-ttu-id="9e4df-103">Blokad podpisany 128-bitowego (16-bajtową) wartości reprezentujących skalowania zmiennej siły 10 numerów 96-bitową liczbę całkowitą (12-bajtowych).</span><span class="sxs-lookup"><span data-stu-id="9e4df-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="9e4df-104">Czynnik skalowania określa liczbę cyfr z prawej strony punktu dziesiętnego; zakresy go z zakresu od 0 do 28.</span><span class="sxs-lookup"><span data-stu-id="9e4df-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="9e4df-105">O skali 0 (bez miejsc dziesiętnych), największa możliwa wartość to +/-79,228,162,514,264,337,593,543,950,335 (+/-7 .9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="9e4df-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="9e4df-106">28 miejsc dziesiętnych największą wartość jest +/-7.9228162514264337593543950335 i najmniejszą wartość niezerową jest +/-0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="9e4df-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e4df-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e4df-107">Remarks</span></span>  
 <span data-ttu-id="9e4df-108">`Decimal` — Typ danych zapewnia największą liczbę cyfr znaczących liczbą.</span><span class="sxs-lookup"><span data-stu-id="9e4df-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="9e4df-109">Obsługuje maksymalnie 29 cyfr znaczących i może reprezentować wartości ponad 7.9228 x 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="9e4df-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="9e4df-110">Jest szczególnie przydatny w obliczeniach, takich jak finansowych, które wymagają dużą liczbę cyfr, ale nie może tolerować błędy zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="9e4df-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>  
  
 <span data-ttu-id="9e4df-111">Wartość domyślna `Decimal` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="9e4df-111">The default value of `Decimal` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="9e4df-112">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="9e4df-112">Programming Tips</span></span>  
  
-   <span data-ttu-id="9e4df-113">**Precyzja.**</span><span class="sxs-lookup"><span data-stu-id="9e4df-113">**Precision.**</span></span> <span data-ttu-id="9e4df-114">`Decimal`nie jest typem danych zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="9e4df-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="9e4df-115">`Decimal` Struktura zawiera wartość całkowitą binarnego, wraz z bitowego logowania i całkowitą skalowanie czynnik, który określa, jaka część wartość ułamek dziesiętny.</span><span class="sxs-lookup"><span data-stu-id="9e4df-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="9e4df-116">W związku z tym `Decimal` liczby mają dokładniejsze reprezentacji w pamięci, niż typów zmiennoprzecinkowych (`Single` i `Double`).</span><span class="sxs-lookup"><span data-stu-id="9e4df-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>  
  
-   <span data-ttu-id="9e4df-117">**Wydajność.**</span><span class="sxs-lookup"><span data-stu-id="9e4df-117">**Performance.**</span></span> <span data-ttu-id="9e4df-118">`Decimal` — Typ danych jest ładowane najwolniej wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="9e4df-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="9e4df-119">Należy porównać znaczenie dokładności względem wydajności przed wybraniem typu danych.</span><span class="sxs-lookup"><span data-stu-id="9e4df-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>  
  
-   <span data-ttu-id="9e4df-120">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="9e4df-120">**Widening.**</span></span> <span data-ttu-id="9e4df-121">`Decimal` Rozszerzenie typu danych do `Single` lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="9e4df-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="9e4df-122">Oznacza to, że można przekonwertować `Decimal` jednej z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="9e4df-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="9e4df-123">**Końcowe zero.**</span><span class="sxs-lookup"><span data-stu-id="9e4df-123">**Trailing Zeros.**</span></span> <span data-ttu-id="9e4df-124">Visual Basic nie przechowuje końcowe zero w `Decimal` literału.</span><span class="sxs-lookup"><span data-stu-id="9e4df-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="9e4df-125">Jednak `Decimal` zmiennej zachowuje końcowe zera nabyte w praktyce.</span><span class="sxs-lookup"><span data-stu-id="9e4df-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="9e4df-126">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="9e4df-126">The following example illustrates this.</span></span>  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     <span data-ttu-id="9e4df-127">Dane wyjściowe `MsgBox` w poprzednim przykładzie ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="9e4df-127">The output of `MsgBox` in the preceding example is as follows:</span></span>  
  
     <span data-ttu-id="9e4df-128">D1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4</span><span class="sxs-lookup"><span data-stu-id="9e4df-128">d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4</span></span>  
  
-   <span data-ttu-id="9e4df-129">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="9e4df-129">**Type Characters.**</span></span> <span data-ttu-id="9e4df-130">Znak literalny typu dołączanie `D` do literału wymusza `Decimal` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="9e4df-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="9e4df-131">Dołączanie znak typu identyfikator `@` dla wszystkich identyfikatorów wymusza `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9e4df-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>  
  
-   <span data-ttu-id="9e4df-132">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="9e4df-132">**Framework Type.**</span></span> <span data-ttu-id="9e4df-133">Danego typu w programie .NET Framework jest <xref:System.Decimal?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="9e4df-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="9e4df-134">Zakres</span><span class="sxs-lookup"><span data-stu-id="9e4df-134">Range</span></span>  
 <span data-ttu-id="9e4df-135">Konieczne może być `D` znak można przypisać duża wartość do typu `Decimal` zmiennej lub stałą.</span><span class="sxs-lookup"><span data-stu-id="9e4df-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="9e4df-136">To wymaganie dotyczy, ponieważ kompilator interpretowana jako literału `Long` , chyba że znak literalny typu następuje literału, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9e4df-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 <span data-ttu-id="9e4df-137">Deklaracja `bigDec1` nie tworzy przepełnienie, ponieważ wartość przypisana do niego znajduje się w zakresie `Long`.</span><span class="sxs-lookup"><span data-stu-id="9e4df-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="9e4df-138">`Long` Można przypisać wartości do `Decimal` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9e4df-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="9e4df-139">Deklaracja `bigDec2` generuje błąd przepełnienia, ponieważ wartość, która jest do niego przypisany jest za duża dla `Long`.</span><span class="sxs-lookup"><span data-stu-id="9e4df-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="9e4df-140">Ponieważ literał liczbowy najpierw nie może być interpretowane jako `Long`, nie można przypisać do `Decimal` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9e4df-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="9e4df-141">Aby uzyskać `bigDec3`, znak literalny typu `D` rozwiązuje problem, powodując, że kompilator, aby zinterpretować jako literał `Decimal` zamiast jako `Long`.</span><span class="sxs-lookup"><span data-stu-id="9e4df-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4df-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e4df-142">See Also</span></span>  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="9e4df-143">Typy danych</span><span class="sxs-lookup"><span data-stu-id="9e4df-143">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="9e4df-144">Single — typ danych</span><span class="sxs-lookup"><span data-stu-id="9e4df-144">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [<span data-ttu-id="9e4df-145">Double — typ danych</span><span class="sxs-lookup"><span data-stu-id="9e4df-145">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [<span data-ttu-id="9e4df-146">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="9e4df-146">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="9e4df-147">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="9e4df-147">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="9e4df-148">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="9e4df-148">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
