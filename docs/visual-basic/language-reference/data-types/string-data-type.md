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
ms.openlocfilehash: 3e87dc6527b4351467b1155439ee8266157c16ff
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842294"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="ee64a-102">String — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee64a-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="ee64a-103">Zawiera sekwencje punktów niepodpisanego kodu (2-bajtowych) 16-bitowych tego zakresu wartości od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="ee64a-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="ee64a-104">Każdy *punktem kodu*, lub kod znaku reprezentuje pojedynczy znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="ee64a-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="ee64a-105">Ciąg może zawierać od 0 do około miliarda dwóch (2 ^ 31) znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="ee64a-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee64a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee64a-106">Remarks</span></span>  
 <span data-ttu-id="ee64a-107">Użyj `String` typ danych do przechowywania wielu znaków, bez konieczności zarządzania tablicy `Char()`, tablicę `Char` elementów.</span><span class="sxs-lookup"><span data-stu-id="ee64a-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="ee64a-108">Wartość domyślna `String` jest `Nothing` (odwołanie o wartości null).</span><span class="sxs-lookup"><span data-stu-id="ee64a-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="ee64a-109">Należy pamiętać, że nie jest taka sama jak pusty ciąg (wartość `""`).</span><span class="sxs-lookup"><span data-stu-id="ee64a-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="ee64a-110">Znaki Unicode</span><span class="sxs-lookup"><span data-stu-id="ee64a-110">Unicode Characters</span></span>  
 <span data-ttu-id="ee64a-111">Pierwsze punkty kodowe 128 (0 – 127), znaków Unicode odpowiadają litery i symbole na klawiaturze standardowej Stanów Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="ee64a-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="ee64a-112">Te pierwsze punkty kodowe 128 są takie same, jak definiuje zestaw znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="ee64a-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="ee64a-113">Drugi 128 punkty kodowe (128-255) reprezentują znaków specjalnych, takich jak litery alfabetu alfabetu łacińskiego, akcentów, symbole walut i ułamki.</span><span class="sxs-lookup"><span data-stu-id="ee64a-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="ee64a-114">Unicode używa różnorodnych symbole pozostałe punkty kodowe (256-65535).</span><span class="sxs-lookup"><span data-stu-id="ee64a-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="ee64a-115">W tym znaki tekstowe na całym świecie, znaki diakrytyczne i symbole matematyczne i technicznych.</span><span class="sxs-lookup"><span data-stu-id="ee64a-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="ee64a-116">Można używać metod, takich jak <xref:System.Char.IsDigit%2A> i <xref:System.Char.IsPunctuation%2A> na pojedynczy znak w `String` zmiennej, aby określić klasyfikację Unicode.</span><span class="sxs-lookup"><span data-stu-id="ee64a-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="ee64a-117">Wymagania dotyczące formatu</span><span class="sxs-lookup"><span data-stu-id="ee64a-117">Format Requirements</span></span>  
 <span data-ttu-id="ee64a-118">Należy ująć `String` literału w cudzysłowie (`" "`).</span><span class="sxs-lookup"><span data-stu-id="ee64a-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="ee64a-119">Musi zawierać znak cudzysłowu, jako jeden ze znaków w ciągu, użycie dwóch sąsiadujących znaków cudzysłowu (`""`).</span><span class="sxs-lookup"><span data-stu-id="ee64a-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="ee64a-120">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="ee64a-120">The following example illustrates this.</span></span>  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="ee64a-121">Należy zauważyć, że ciągłych znaków cudzysłowu, które reprezentują znak cudzysłowu w ciągu niezależne od znaków cudzysłowu, rozpoczęcia i zakończenia `String` literału.</span><span class="sxs-lookup"><span data-stu-id="ee64a-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="ee64a-122">Działań na ciągach</span><span class="sxs-lookup"><span data-stu-id="ee64a-122">String Manipulations</span></span>  
 <span data-ttu-id="ee64a-123">Po przypisaniu ciąg `String` zmiennej, ten ciąg jest *niezmienne*, co oznacza nie można zmienić jego długość lub zawartości.</span><span class="sxs-lookup"><span data-stu-id="ee64a-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="ee64a-124">Zmianę ciągu w jakikolwiek sposób języka Visual Basic tworzy nowy ciąg i porzuca poprzedniego.</span><span class="sxs-lookup"><span data-stu-id="ee64a-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="ee64a-125">`String` Zmienna następnie wskazuje nowe parametry.</span><span class="sxs-lookup"><span data-stu-id="ee64a-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="ee64a-126">Możesz manipulować zawartością `String` zmiennej przy użyciu różnych funkcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="ee64a-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="ee64a-127">W poniższym przykładzie pokazano <xref:Microsoft.VisualBasic.Strings.Left%2A> — funkcja</span><span class="sxs-lookup"><span data-stu-id="ee64a-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="ee64a-128">Ciąg, który został utworzony przez inny składnik, może być dopełniana spacji wiodących albo końcowych.</span><span class="sxs-lookup"><span data-stu-id="ee64a-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="ee64a-129">Jeśli wystąpi taki ciąg, możesz użyć <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, i <xref:Microsoft.VisualBasic.Strings.RTrim%2A> funkcji, aby usunąć te miejsca do magazynowania.</span><span class="sxs-lookup"><span data-stu-id="ee64a-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="ee64a-130">Aby uzyskać więcej informacji na temat działań na ciągach, zobacz [ciągi](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee64a-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="ee64a-131">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="ee64a-131">Programming Tips</span></span>  
  
-   <span data-ttu-id="ee64a-132">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="ee64a-132">**Negative Numbers.**</span></span> <span data-ttu-id="ee64a-133">Należy pamiętać, że znaki w posiadaniu `String` niepodpisanych i nie może reprezentować wartości ujemnych.</span><span class="sxs-lookup"><span data-stu-id="ee64a-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="ee64a-134">W każdym przypadku, nie należy używać `String` do przechowywania wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="ee64a-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="ee64a-135">**Uwagi dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="ee64a-135">**Interop Considerations.**</span></span> <span data-ttu-id="ee64a-136">Jeśli są komunikowanie się ze składnikami programu .NET Framework na przykład obiektami automatyzacji lub COM, pamiętaj, że znaków w ciągu ma różną szerokość danych (8 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="ee64a-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="ee64a-137">Jeśli przekazujesz argumentu ciągu znaków 8-bitowych do takiego składnika, Zadeklaruj go jako `Byte()`, tablicę `Byte` elementów, zamiast `String` nowego kodu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ee64a-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="ee64a-138">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="ee64a-138">**Type Characters.**</span></span> <span data-ttu-id="ee64a-139">Dołączanie znaku typu identyfikator `$` do jakiegokolwiek identyfikatora wymusza `String` typu danych.</span><span class="sxs-lookup"><span data-stu-id="ee64a-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="ee64a-140">`String` nie ma typ literału znaku.</span><span class="sxs-lookup"><span data-stu-id="ee64a-140">`String` has no literal type character.</span></span> <span data-ttu-id="ee64a-141">Jednak kompilator traktuje literały ujęta w znaki cudzysłowu (`" "`) jako `String`.</span><span class="sxs-lookup"><span data-stu-id="ee64a-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
-   <span data-ttu-id="ee64a-142">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="ee64a-142">**Framework Type.**</span></span> <span data-ttu-id="ee64a-143">Odpowiedni typ w .NET Framework jest <xref:System.String?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="ee64a-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee64a-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee64a-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="ee64a-145">Typy danych</span><span class="sxs-lookup"><span data-stu-id="ee64a-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="ee64a-146">Char, typ danych</span><span class="sxs-lookup"><span data-stu-id="ee64a-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="ee64a-147">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="ee64a-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="ee64a-148">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="ee64a-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="ee64a-149">Instrukcje: wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="ee64a-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="ee64a-150">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="ee64a-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
