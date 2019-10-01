---
title: String — Typ danych (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 6d2fd226735622de5cd7197060c05b8ac12b69f1
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696844"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="b9ae5-102">String — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9ae5-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="b9ae5-103">Przechowuje sekwencje 16-bitowego (2-bajtowego) kodu bez znaku, który ma wartość z zakresu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="b9ae5-104">Każdy *punkt kodu*lub znak, reprezentuje pojedynczy znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="b9ae5-105">Ciąg może zawierać od 0 do około 2 000 000 000 (2 ^ 31) znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9ae5-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9ae5-106">Remarks</span></span>  
 <span data-ttu-id="b9ae5-107">Użyj typu danych `String`, aby przechowywać wiele znaków bez obciążeń związanych z zarządzaniem tablicą `Char()`, tablicy elementów `Char`.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="b9ae5-108">Wartość domyślna `String` to `Nothing` (odwołanie o wartości null).</span><span class="sxs-lookup"><span data-stu-id="b9ae5-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="b9ae5-109">Należy zauważyć, że nie jest to ten sam ciąg, który jest ciągiem pustym (wartość `""`).</span><span class="sxs-lookup"><span data-stu-id="b9ae5-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="b9ae5-110">Znaki Unicode</span><span class="sxs-lookup"><span data-stu-id="b9ae5-110">Unicode Characters</span></span>  
 <span data-ttu-id="b9ae5-111">Pierwsze 128 punktów kodowych (0 – 127) Unicode odpowiada literom i symbolom na standardowej klawiaturze amerykańskiej.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="b9ae5-112">Te pierwsze 128 punktów kodowych są takie same jak w zestawie znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="b9ae5-113">Drugie 128 punktów kodowych (128 – 255) reprezentuje znaki specjalne, takie jak litery alfabetu łacińskiego, akcenty, symbole waluty i ułamki.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="b9ae5-114">Unicode używa pozostałych punktów kodowych (256-65535) dla wielu różnych symboli.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="b9ae5-115">Obejmuje to ogólnoświatowe znaki tekstowe, znaki diakrytyczne i symbole matematyczne i techniczne.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="b9ae5-116">Możesz użyć metod, takich jak <xref:System.Char.IsDigit%2A> i <xref:System.Char.IsPunctuation%2A> dla pojedynczego znaku w zmiennej `String`, aby określić jego klasyfikację Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="b9ae5-117">Wymagania dotyczące formatu</span><span class="sxs-lookup"><span data-stu-id="b9ae5-117">Format Requirements</span></span>  
 <span data-ttu-id="b9ae5-118">Należy ująć literał `String` w cudzysłowie (`" "`).</span><span class="sxs-lookup"><span data-stu-id="b9ae5-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="b9ae5-119">Jeśli musisz zawierać znak cudzysłowu jako jeden ze znaków w ciągu, użyj dwóch znaków cudzysłowu (`""`).</span><span class="sxs-lookup"><span data-stu-id="b9ae5-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="b9ae5-120">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-120">The following example illustrates this.</span></span>  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="b9ae5-121">Należy zauważyć, że ciągły cudzysłów, który reprezentuje znak cudzysłowu w ciągu, jest niezależny od znaków cudzysłowu, które zaczynają i kończą literał `String`.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="b9ae5-122">Manipulowanie ciągami</span><span class="sxs-lookup"><span data-stu-id="b9ae5-122">String Manipulations</span></span>  
 <span data-ttu-id="b9ae5-123">Po przypisaniu ciągu do zmiennej `String` ten ciąg jest *niezmienny*, co oznacza, że nie można zmienić jego długości ani zawartości.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="b9ae5-124">Gdy zmieniasz ciąg w dowolny sposób, Visual Basic tworzy nowy ciąg i porzuca poprzednią wartość.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="b9ae5-125">Zmienna `String` wskazuje nowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="b9ae5-126">Zawartość zmiennej `String` można manipulować przy użyciu różnych funkcji ciągu.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="b9ae5-127">Poniższy przykład ilustruje funkcję <xref:Microsoft.VisualBasic.Strings.Left%2A></span><span class="sxs-lookup"><span data-stu-id="b9ae5-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="b9ae5-128">Ciąg utworzony przez inny składnik może być uzupełniony spacjami wiodącymi lub końcowymi.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="b9ae5-129">Jeśli otrzymasz taki ciąg, możesz użyć funkcji <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A> i <xref:Microsoft.VisualBasic.Strings.RTrim%2A>, aby usunąć te spacje.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="b9ae5-130">Aby uzyskać więcej informacji na temat manipulowania ciągami, zobacz [ciągi](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="b9ae5-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="b9ae5-131">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="b9ae5-131">Programming Tips</span></span>  
  
- <span data-ttu-id="b9ae5-132">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="b9ae5-132">**Negative Numbers.**</span></span> <span data-ttu-id="b9ae5-133">Należy pamiętać, że znaki przechowywane przez `String` są niepodpisane i nie mogą reprezentować wartości ujemnych.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="b9ae5-134">W każdym przypadku nie należy używać `String` do przechowywania wartości numerycznych.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
- <span data-ttu-id="b9ae5-135">**Zagadnienia dotyczące międzyoperacyjnych.**</span><span class="sxs-lookup"><span data-stu-id="b9ae5-135">**Interop Considerations.**</span></span> <span data-ttu-id="b9ae5-136">Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że znaki ciągu mają różną szerokość danych (8 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="b9ae5-137">Jeśli przekazujesz argument ciągu znaków 8-bitowy do takiego składnika, zadeklaruj go jako `Byte()`, tablicę elementów `Byte`, a nie `String` w nowym kodzie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="b9ae5-138">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="b9ae5-138">**Type Characters.**</span></span> <span data-ttu-id="b9ae5-139">Dołączanie znaku typu identyfikatora `$` do dowolnego identyfikatora zmusza go do typu danych `String`.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="b9ae5-140">`String` nie ma znaku typu literału.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-140">`String` has no literal type character.</span></span> <span data-ttu-id="b9ae5-141">Jednak kompilator traktuje literały ujęte w znaki cudzysłowu (`" "`) jako `String`.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
- <span data-ttu-id="b9ae5-142">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="b9ae5-142">**Framework Type.**</span></span> <span data-ttu-id="b9ae5-143">Odpowiedni typ w .NET Framework jest klasą <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9ae5-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9ae5-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="b9ae5-145">Typy danych</span><span class="sxs-lookup"><span data-stu-id="b9ae5-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="b9ae5-146">Char, typ danych</span><span class="sxs-lookup"><span data-stu-id="b9ae5-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="b9ae5-147">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="b9ae5-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="b9ae5-148">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="b9ae5-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="b9ae5-149">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="b9ae5-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="b9ae5-150">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="b9ae5-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
