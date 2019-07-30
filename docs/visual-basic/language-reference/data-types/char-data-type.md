---
title: Char — Typ danych (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 8313c2282a3b4b7b035f9f3b685a786c4471f53a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630143"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="e30d7-102">Char — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e30d7-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="e30d7-103">Przechowuje 16-bitowe (2-bajtowe) punkty kodu bez znaku w zakresie wartości z zakresu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="e30d7-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="e30d7-104">Każdy *punkt kodu*lub znak, reprezentuje pojedynczy znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="e30d7-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="e30d7-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e30d7-105">Remarks</span></span>

<span data-ttu-id="e30d7-106">Użyj typu `String`danych, gdy musisz przechowywać tylko jeden znak i nie potrzebujesz nakładu pracy. `Char`</span><span class="sxs-lookup"><span data-stu-id="e30d7-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="e30d7-107">W niektórych przypadkach można użyć `Char()` `Char` tablicy elementów, aby przechowywać wiele znaków.</span><span class="sxs-lookup"><span data-stu-id="e30d7-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="e30d7-108">Wartość `Char` domyślna to znak z punktem kodu równym 0.</span><span class="sxs-lookup"><span data-stu-id="e30d7-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="e30d7-109">Znaki Unicode</span><span class="sxs-lookup"><span data-stu-id="e30d7-109">Unicode Characters</span></span>

<span data-ttu-id="e30d7-110">Pierwsze 128 punktów kodowych (0 – 127) Unicode odpowiada literom i symbolom na standardowej klawiaturze amerykańskiej.</span><span class="sxs-lookup"><span data-stu-id="e30d7-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="e30d7-111">Te pierwsze 128 punktów kodowych są takie same jak w zestawie znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="e30d7-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="e30d7-112">Drugie 128 punktów kodowych (128 – 255) reprezentuje znaki specjalne, takie jak litery alfabetu łacińskiego, akcenty, symbole waluty i ułamki.</span><span class="sxs-lookup"><span data-stu-id="e30d7-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="e30d7-113">Unicode używa pozostałych punktów kodowych (256-65535) dla wielu różnych symboli, w tym na całym świecie, znaki diakrytyczne i symbole matematyczne i techniczne.</span><span class="sxs-lookup"><span data-stu-id="e30d7-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="e30d7-114">Aby określić swoją klasyfikację <xref:System.Char.IsDigit%2A> Unicode <xref:System.Char.IsPunctuation%2A> , można `Char` użyć metod takich jak i na zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e30d7-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="e30d7-115">Konwersje typu</span><span class="sxs-lookup"><span data-stu-id="e30d7-115">Type Conversions</span></span>

<span data-ttu-id="e30d7-116">Visual Basic nie konwertuje bezpośrednio między `Char` i typu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="e30d7-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="e30d7-117">Można użyć <xref:Microsoft.VisualBasic.Strings.Asc%2A> funkcji lub <xref:Microsoft.VisualBasic.Strings.AscW%2A> , `Char` Aby`Integer` przekonwertować wartość na, która reprezentuje swój punkt kodu.</span><span class="sxs-lookup"><span data-stu-id="e30d7-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="e30d7-118">Można użyć <xref:Microsoft.VisualBasic.Strings.Chr%2A> funkcji lub <xref:Microsoft.VisualBasic.Strings.ChrW%2A> , `Integer` Aby`Char` przekonwertować wartość na, która ma ten punkt kodu.</span><span class="sxs-lookup"><span data-stu-id="e30d7-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="e30d7-119">Jeśli przełącznik sprawdzania typu ( [instrukcja Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest włączona, należy dołączyć znak literału typu do literału ciągu pojedynczego znaku, aby zidentyfikować go jako `Char` typ danych.</span><span class="sxs-lookup"><span data-stu-id="e30d7-119">If the type checking switch (the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="e30d7-120">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e30d7-120">The following example illustrates this.</span></span> <span data-ttu-id="e30d7-121">Pierwsze przypisanie do `charVar` zmiennej generuje błąd kompilatora [BC30512](../../misc/bc30512.md) , ponieważ `Option Strict` jest on włączony.</span><span class="sxs-lookup"><span data-stu-id="e30d7-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="e30d7-122">Druga kompilacja powiodła się, ponieważ `c` znak typu literału identyfikuje literał `Char` jako wartość.</span><span class="sxs-lookup"><span data-stu-id="e30d7-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a><span data-ttu-id="e30d7-123">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="e30d7-123">Programming Tips</span></span>

- <span data-ttu-id="e30d7-124">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="e30d7-124">**Negative Numbers.**</span></span> <span data-ttu-id="e30d7-125">`Char`jest typem bez znaku i nie może reprezentować wartości ujemnej.</span><span class="sxs-lookup"><span data-stu-id="e30d7-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="e30d7-126">W każdym przypadku nie należy używać `Char` do przechowywania wartości numerycznych.</span><span class="sxs-lookup"><span data-stu-id="e30d7-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="e30d7-127">**Zagadnienia dotyczące międzyoperacyjnych.**</span><span class="sxs-lookup"><span data-stu-id="e30d7-127">**Interop Considerations.**</span></span> <span data-ttu-id="e30d7-128">Jeśli interfejs zawiera składniki, które nie są przeznaczone dla .NET Framework, na przykład obiekty Automation lub COM, należy pamiętać, że typy znaków mają różną szerokość danych (8 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="e30d7-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="e30d7-129">W przypadku przekazania do takiego składnika argumentu 8-bitowego należy zadeklarować go jako `Byte` `Char` zamiast w nowym kodzie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e30d7-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="e30d7-130">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="e30d7-130">**Widening.**</span></span> <span data-ttu-id="e30d7-131">Typ `Char` danych jest rozszerzany do `String`.</span><span class="sxs-lookup"><span data-stu-id="e30d7-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="e30d7-132">Oznacza to, że można `Char` przeprowadzić `String` konwersję do <xref:System.OverflowException?displayProperty=nameWithType>i nie napotkasz.</span><span class="sxs-lookup"><span data-stu-id="e30d7-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="e30d7-133">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="e30d7-133">**Type Characters.**</span></span> <span data-ttu-id="e30d7-134">Dołączanie znaku `C` typu literału do literału ciągu z pojedynczym znakiem wymusza `Char` do tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="e30d7-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="e30d7-135">`Char`nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="e30d7-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="e30d7-136">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="e30d7-136">**Framework Type.**</span></span> <span data-ttu-id="e30d7-137">Odpowiedni typ w .NET Framework jest <xref:System.Char?displayProperty=nameWithType> strukturą.</span><span class="sxs-lookup"><span data-stu-id="e30d7-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="e30d7-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e30d7-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="e30d7-139">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e30d7-139">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="e30d7-140">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="e30d7-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="e30d7-141">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="e30d7-141">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="e30d7-142">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="e30d7-142">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="e30d7-143">Instrukcje: wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="e30d7-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="e30d7-144">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="e30d7-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
