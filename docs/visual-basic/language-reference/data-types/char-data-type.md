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
ms.openlocfilehash: e672402535215ca30d19cc480e39b42b0364f137
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590819"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="97fc6-102">Char — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97fc6-102">Char Data Type (Visual Basic)</span></span>
<span data-ttu-id="97fc6-103">Punkty niepodpisanego kodu (2-bajtowych) 16-bitowych blokady z zakresu od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="97fc6-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="97fc6-104">Każdy *punktem kodu*, lub kod znaku reprezentuje pojedynczy znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="97fc6-104">Each *code point*, or character code, represents a single Unicode character.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97fc6-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97fc6-105">Remarks</span></span>  
 <span data-ttu-id="97fc6-106">Użyj `Char` typu danych, gdy potrzebne do przechowywania tylko jeden znak i nie trzeba korzystać z `String`.</span><span class="sxs-lookup"><span data-stu-id="97fc6-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="97fc6-107">W niektórych przypadkach można użyć `Char()`, tablicę `Char` elementów, aby pomieścić wielu znaków.</span><span class="sxs-lookup"><span data-stu-id="97fc6-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>  
  
 <span data-ttu-id="97fc6-108">Wartość domyślna `Char` to znak o punkt kodu 0.</span><span class="sxs-lookup"><span data-stu-id="97fc6-108">The default value of `Char` is the character with a code point of 0.</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="97fc6-109">Znaki Unicode</span><span class="sxs-lookup"><span data-stu-id="97fc6-109">Unicode Characters</span></span>  
 <span data-ttu-id="97fc6-110">Pierwszy punktów 128 kodu (0 – 127), znaków Unicode odpowiadają liter i symboli na klawiaturze standardowej Stanów Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="97fc6-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="97fc6-111">Pierwszy punkty 128 kodu są takie same jak definiuje zestaw znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="97fc6-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="97fc6-112">Drugi punkty 128 kodu (128 – 255) reprezentują znaków specjalnych, takich jak litery alfabetu łacińskiego —, akcentów symbol waluty i ułamków.</span><span class="sxs-lookup"><span data-stu-id="97fc6-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="97fc6-113">Unicode używa pozostałe punkty kodu (256-65535) dla różnych typów symboli, w tym na całym świecie tekstową znaków, znaków diakrytycznych i symbole matematyczne i technicznych.</span><span class="sxs-lookup"><span data-stu-id="97fc6-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="97fc6-114">Można użyć metody, takie jak <xref:System.Char.IsDigit%2A> i <xref:System.Char.IsPunctuation%2A> na `Char` zmiennej do określenia jego klasyfikację Unicode.</span><span class="sxs-lookup"><span data-stu-id="97fc6-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="97fc6-115">Konwersje typu</span><span class="sxs-lookup"><span data-stu-id="97fc6-115">Type Conversions</span></span>  
 <span data-ttu-id="97fc6-116">Visual Basic nie konwertuje bezpośrednio między `Char` typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="97fc6-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="97fc6-117">Można użyć <xref:Microsoft.VisualBasic.Strings.Asc%2A> lub <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkcji konwersji `Char` do wartości `Integer` reprezentujący punktu kodu.</span><span class="sxs-lookup"><span data-stu-id="97fc6-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="97fc6-118">Można użyć <xref:Microsoft.VisualBasic.Strings.Chr%2A> lub <xref:Microsoft.VisualBasic.Strings.ChrW%2A> funkcji konwersji `Integer` do wartości `Char` mający tego punktu kodu.</span><span class="sxs-lookup"><span data-stu-id="97fc6-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>  
  
 <span data-ttu-id="97fc6-119">Jeśli sprawdzanie typu przełącznik ([Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest włączona, należy dołączyć znak literalny typu do jednoznakowym literału ciągu na identyfikację jako `Char` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="97fc6-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="97fc6-120">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="97fc6-120">The following example illustrates this.</span></span>  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a><span data-ttu-id="97fc6-121">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="97fc6-121">Programming Tips</span></span>  
  
-   <span data-ttu-id="97fc6-122">**Wartości ujemne.**</span><span class="sxs-lookup"><span data-stu-id="97fc6-122">**Negative Numbers.**</span></span> <span data-ttu-id="97fc6-123">`Char` jest to typ bez znaku i nie może reprezentować wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="97fc6-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="97fc6-124">W żadnym przypadku nie należy używać `Char` do przechowywania wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="97fc6-124">In any case, you should not use `Char` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="97fc6-125">**Zagadnienia dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="97fc6-125">**Interop Considerations.**</span></span> <span data-ttu-id="97fc6-126">Jeśli interfejs ze składnikami, które nie są zapisywane dla programu .NET Framework dla obiektów automatyzacji lub COM przykład pamiętać, że znaki — typy są różne dane szerokości (8 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="97fc6-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="97fc6-127">Argument 8-bitową w przypadku przekazania do tych składników, Zadeklaruj ją jako `Byte` zamiast `Char` w nowy kod Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="97fc6-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="97fc6-128">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="97fc6-128">**Widening.**</span></span> <span data-ttu-id="97fc6-129">`Char` Rozszerzenie typu danych do `String`.</span><span class="sxs-lookup"><span data-stu-id="97fc6-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="97fc6-130">Oznacza to, że można przekonwertować `Char` do `String` i nie wystąpi <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="97fc6-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="97fc6-131">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="97fc6-131">**Type Characters.**</span></span> <span data-ttu-id="97fc6-132">Znak literalny typu dołączanie `C` z ciągiem jednoznakowym literał wymusza `Char` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="97fc6-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="97fc6-133">`Char` nie ma identyfikatora typu znaku.</span><span class="sxs-lookup"><span data-stu-id="97fc6-133">`Char` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="97fc6-134">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="97fc6-134">**Framework Type.**</span></span> <span data-ttu-id="97fc6-135">Danego typu w programie .NET Framework jest <xref:System.Char?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="97fc6-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fc6-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97fc6-136">See Also</span></span>  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="97fc6-137">Typy danych</span><span class="sxs-lookup"><span data-stu-id="97fc6-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="97fc6-138">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="97fc6-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="97fc6-139">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="97fc6-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="97fc6-140">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="97fc6-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="97fc6-141">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="97fc6-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="97fc6-142">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="97fc6-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
