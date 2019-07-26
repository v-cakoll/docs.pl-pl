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
ms.openlocfilehash: ca40e6c8dcba3da29bdb68b29c91c852e477f8f7
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512787"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="4375c-102">Char — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4375c-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="4375c-103">Przechowuje 16-bitowe (2-bajtowe) punkty kodu bez znaku w zakresie wartości z zakresu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="4375c-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="4375c-104">Każdy *punkt kodu*lub znak, reprezentuje pojedynczy znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="4375c-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="4375c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4375c-105">Remarks</span></span>

<span data-ttu-id="4375c-106">Użyj typu `String`danych, gdy musisz przechowywać tylko jeden znak i nie potrzebujesz nakładu pracy. `Char`</span><span class="sxs-lookup"><span data-stu-id="4375c-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="4375c-107">W niektórych przypadkach można użyć `Char()` `Char` tablicy elementów, aby przechowywać wiele znaków.</span><span class="sxs-lookup"><span data-stu-id="4375c-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="4375c-108">Wartość `Char` domyślna to znak z punktem kodu równym 0.</span><span class="sxs-lookup"><span data-stu-id="4375c-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="4375c-109">Znaki Unicode</span><span class="sxs-lookup"><span data-stu-id="4375c-109">Unicode Characters</span></span>

<span data-ttu-id="4375c-110">Pierwsze 128 punktów kodowych (0 – 127) Unicode odpowiada literom i symbolom na standardowej klawiaturze amerykańskiej.</span><span class="sxs-lookup"><span data-stu-id="4375c-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="4375c-111">Te pierwsze 128 punktów kodowych są takie same jak w zestawie znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="4375c-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="4375c-112">Drugie 128 punktów kodowych (128 – 255) reprezentuje znaki specjalne, takie jak litery alfabetu łacińskiego, akcenty, symbole waluty i ułamki.</span><span class="sxs-lookup"><span data-stu-id="4375c-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="4375c-113">Unicode używa pozostałych punktów kodowych (256-65535) dla wielu różnych symboli, w tym na całym świecie, znaki diakrytyczne i symbole matematyczne i techniczne.</span><span class="sxs-lookup"><span data-stu-id="4375c-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="4375c-114">Aby określić swoją klasyfikację <xref:System.Char.IsDigit%2A> Unicode <xref:System.Char.IsPunctuation%2A> , można `Char` użyć metod takich jak i na zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4375c-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="4375c-115">Konwersje typu</span><span class="sxs-lookup"><span data-stu-id="4375c-115">Type Conversions</span></span>

<span data-ttu-id="4375c-116">Visual Basic nie konwertuje bezpośrednio między `Char` i typu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="4375c-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="4375c-117">Można użyć <xref:Microsoft.VisualBasic.Strings.Asc%2A> funkcji lub <xref:Microsoft.VisualBasic.Strings.AscW%2A> , `Char` Aby`Integer` przekonwertować wartość na, która reprezentuje swój punkt kodu.</span><span class="sxs-lookup"><span data-stu-id="4375c-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="4375c-118">Można użyć <xref:Microsoft.VisualBasic.Strings.Chr%2A> funkcji lub <xref:Microsoft.VisualBasic.Strings.ChrW%2A> , `Integer` Aby`Char` przekonwertować wartość na, która ma ten punkt kodu.</span><span class="sxs-lookup"><span data-stu-id="4375c-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="4375c-119">Jeśli przełącznik sprawdzania typu ([instrukcja Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest włączony, należy dołączyć znak literału typu do literału ciągu pojedynczego znaku, aby zidentyfikować go jako `Char` typ danych.</span><span class="sxs-lookup"><span data-stu-id="4375c-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="4375c-120">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="4375c-120">The following example illustrates this.</span></span>

```vb
Option Strict On
Dim charVar As Char
' The following statement attempts to convert a String literal to Char.
' Because Option Strict is On, it generates a compiler error.
charVar = "Z"
' The following statement succeeds because it specifies a Char literal.
charVar = "Z"C
```

## <a name="programming-tips"></a><span data-ttu-id="4375c-121">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="4375c-121">Programming Tips</span></span>

- <span data-ttu-id="4375c-122">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="4375c-122">**Negative Numbers.**</span></span> <span data-ttu-id="4375c-123">`Char`jest typem bez znaku i nie może reprezentować wartości ujemnej.</span><span class="sxs-lookup"><span data-stu-id="4375c-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="4375c-124">W każdym przypadku nie należy używać `Char` do przechowywania wartości numerycznych.</span><span class="sxs-lookup"><span data-stu-id="4375c-124">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="4375c-125">**Zagadnienia dotyczące międzyoperacyjnych.**</span><span class="sxs-lookup"><span data-stu-id="4375c-125">**Interop Considerations.**</span></span> <span data-ttu-id="4375c-126">Jeśli interfejs zawiera składniki, które nie są przeznaczone dla .NET Framework, na przykład obiekty Automation lub COM, należy pamiętać, że typy znaków mają różną szerokość danych (8 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="4375c-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="4375c-127">W przypadku przekazania do takiego składnika argumentu 8-bitowego należy zadeklarować go jako `Byte` `Char` zamiast w nowym kodzie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4375c-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="4375c-128">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="4375c-128">**Widening.**</span></span> <span data-ttu-id="4375c-129">Typ `Char` danych jest rozszerzany do `String`.</span><span class="sxs-lookup"><span data-stu-id="4375c-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="4375c-130">Oznacza to, że można `Char` dokonać `String` konwersji do <xref:System.OverflowException?displayProperty=nameWithType> i nie napotkasz błędu.</span><span class="sxs-lookup"><span data-stu-id="4375c-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="4375c-131">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="4375c-131">**Type Characters.**</span></span> <span data-ttu-id="4375c-132">Dołączanie znaku `C` typu literału do literału ciągu z pojedynczym znakiem wymusza `Char` do tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="4375c-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="4375c-133">`Char`nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="4375c-133">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="4375c-134">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="4375c-134">**Framework Type.**</span></span> <span data-ttu-id="4375c-135">Odpowiedni typ w .NET Framework jest <xref:System.Char?displayProperty=nameWithType> strukturą.</span><span class="sxs-lookup"><span data-stu-id="4375c-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="4375c-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4375c-136">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="4375c-137">Typy danych</span><span class="sxs-lookup"><span data-stu-id="4375c-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="4375c-138">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="4375c-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="4375c-139">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="4375c-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="4375c-140">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="4375c-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="4375c-141">Instrukcje: wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="4375c-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="4375c-142">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="4375c-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
