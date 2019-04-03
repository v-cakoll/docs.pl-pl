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
ms.openlocfilehash: b50c902f69f7602dbad4663dc35bf0a2b932973f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832093"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="a7ecd-102">Char — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7ecd-102">Char Data Type (Visual Basic)</span></span>
<span data-ttu-id="a7ecd-103">Wskazuje niepodpisanego kodu (2-bajtowych) 16-bitowych blokady z zakresu od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="a7ecd-104">Każdy *punktem kodu*, lub kod znaku reprezentuje pojedynczy znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-104">Each *code point*, or character code, represents a single Unicode character.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7ecd-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7ecd-105">Remarks</span></span>  
 <span data-ttu-id="a7ecd-106">Użyj `Char` — typ danych Jeśli potrzebujesz do przechowywania tylko jeden znak i nie trzeba korzystać z `String`.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="a7ecd-107">W niektórych przypadkach można użyć `Char()`, tablicę `Char` elementy do przechowywania wielu znaków.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>  
  
 <span data-ttu-id="a7ecd-108">Wartość domyślna `Char` to znak z punktem kodu w 0.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-108">The default value of `Char` is the character with a code point of 0.</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="a7ecd-109">Znaki Unicode</span><span class="sxs-lookup"><span data-stu-id="a7ecd-109">Unicode Characters</span></span>  
 <span data-ttu-id="a7ecd-110">Pierwsze punkty kodowe 128 (0 – 127), znaków Unicode odpowiadają litery i symbole na klawiaturze standardowej Stanów Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="a7ecd-111">Te pierwsze punkty kodowe 128 są takie same, jak definiuje zestaw znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="a7ecd-112">Drugi 128 punkty kodowe (128-255) reprezentują znaków specjalnych, takich jak litery alfabetu alfabetu łacińskiego, akcentów, symbole walut i ułamki.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="a7ecd-113">Unicode używa pozostałe punkty kodowe (256-65535) dla szerokiej gamy symbole, w tym znaki tekstowe na całym świecie, znaki diakrytyczne i symbole matematyczne i technicznych.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="a7ecd-114">Można użyć metod, takich jak <xref:System.Char.IsDigit%2A> i <xref:System.Char.IsPunctuation%2A> na `Char` zmiennej, aby określić klasyfikację Unicode.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="a7ecd-115">Konwersje typu</span><span class="sxs-lookup"><span data-stu-id="a7ecd-115">Type Conversions</span></span>  
 <span data-ttu-id="a7ecd-116">Visual Basic nie konwertuje bezpośrednio między `Char` typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="a7ecd-117">Możesz użyć <xref:Microsoft.VisualBasic.Strings.Asc%2A> lub <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkcję, aby skonwertować `Char` wartość `Integer` reprezentujący jego punkt kodu.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="a7ecd-118">Możesz użyć <xref:Microsoft.VisualBasic.Strings.Chr%2A> lub <xref:Microsoft.VisualBasic.Strings.ChrW%2A> funkcję, aby skonwertować `Integer` wartość `Char` zawierający ten punkt kodu.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>  
  
 <span data-ttu-id="a7ecd-119">Jeśli kontrola typów w przełącznik ([Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest włączona, należy dołączyć znak literalny typu do jednoznakowy ciąg literału w celu zidentyfikowania go jako `Char` typu danych.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="a7ecd-120">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-120">The following example illustrates this.</span></span>  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a><span data-ttu-id="a7ecd-121">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="a7ecd-121">Programming Tips</span></span>  
  
-   <span data-ttu-id="a7ecd-122">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="a7ecd-122">**Negative Numbers.**</span></span> <span data-ttu-id="a7ecd-123">`Char` jest typ bez znaku, a nie może reprezentować wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="a7ecd-124">W każdym przypadku, nie należy używać `Char` do przechowywania wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-124">In any case, you should not use `Char` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="a7ecd-125">**Uwagi dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="a7ecd-125">**Interop Considerations.**</span></span> <span data-ttu-id="a7ecd-126">Jeśli interfejs ze składnikami programu .NET Framework na przykład obiektami automatyzacji lub COM, pamiętaj, że znaki — typy mają różną szerokość danych (8 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="a7ecd-127">Jeśli przekażesz 8-bitowy argument do takiego składnika, Zadeklaruj go jako `Byte` zamiast `Char` nowego kodu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="a7ecd-128">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="a7ecd-128">**Widening.**</span></span> <span data-ttu-id="a7ecd-129">`Char` — Typ danych rozszerza się na `String`.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="a7ecd-130">Oznacza to, że możesz przekonwertować `Char` do `String` i nie będzie występować <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="a7ecd-131">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="a7ecd-131">**Type Characters.**</span></span> <span data-ttu-id="a7ecd-132">Dołączanie znaku typu literał `C` na ciąg pojedynczych znaków literału wymusza `Char` typu danych.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="a7ecd-133">`Char` nie ma identyfikatora typ znaku.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-133">`Char` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="a7ecd-134">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="a7ecd-134">**Framework Type.**</span></span> <span data-ttu-id="a7ecd-135">Odpowiedni typ w .NET Framework jest <xref:System.Char?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="a7ecd-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ecd-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7ecd-136">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="a7ecd-137">Typy danych</span><span class="sxs-lookup"><span data-stu-id="a7ecd-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a7ecd-138">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="a7ecd-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="a7ecd-139">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="a7ecd-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a7ecd-140">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="a7ecd-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="a7ecd-141">Instrukcje: wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="a7ecd-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="a7ecd-142">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="a7ecd-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
