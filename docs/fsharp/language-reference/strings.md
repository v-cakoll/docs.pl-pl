---
title: Ciągi (F#)
description: 'Dowiedz się, jak typ "string" języka F # reprezentuje niezmienne tekst sekwencję znaków Unicode.'
ms.date: 05/16/2016
ms.openlocfilehash: bdd1d1a542e70bcd95fce51e75d0c1ddffceb008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="strings"></a><span data-ttu-id="7e670-103">Ciągi</span><span class="sxs-lookup"><span data-stu-id="7e670-103">Strings</span></span>

> [!NOTE]
<span data-ttu-id="7e670-104">Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="7e670-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="7e670-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="7e670-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="7e670-106">`string` Typu reprezentuje niezmienne tekst sekwencję znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="7e670-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="7e670-107">`string` alias jest `System.String` w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7e670-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e670-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e670-108">Remarks</span></span>
<span data-ttu-id="7e670-109">Literały ciągu są rozdzielone znakiem cudzysłowu (").</span><span class="sxs-lookup"><span data-stu-id="7e670-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="7e670-110">Znak ukośnika odwrotnego (\) jest używany do kodowania niektórych znaków specjalnych.</span><span class="sxs-lookup"><span data-stu-id="7e670-110">The backslash character (\) is used to encode certain special characters.</span></span> <span data-ttu-id="7e670-111">Ukośniku odwrotnym i znakiem następnym razem są nazywane *sekwencja unikowa*.</span><span class="sxs-lookup"><span data-stu-id="7e670-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="7e670-112">Sekwencje obsługiwane w F # ciąg, który w poniższej tabeli przedstawiono literały specjalne.</span><span class="sxs-lookup"><span data-stu-id="7e670-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="7e670-113">Znak</span><span class="sxs-lookup"><span data-stu-id="7e670-113">Character</span></span>|<span data-ttu-id="7e670-114">Sekwencja specjalna</span><span class="sxs-lookup"><span data-stu-id="7e670-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="7e670-115">Backspace</span><span class="sxs-lookup"><span data-stu-id="7e670-115">Backspace</span></span>|<span data-ttu-id="7e670-116">\b</span><span class="sxs-lookup"><span data-stu-id="7e670-116">\b</span></span>|
|<span data-ttu-id="7e670-117">Nowy wiersz</span><span class="sxs-lookup"><span data-stu-id="7e670-117">Newline</span></span>|<span data-ttu-id="7e670-118">\n</span><span class="sxs-lookup"><span data-stu-id="7e670-118">\n</span></span>|
|<span data-ttu-id="7e670-119">Powrót karetki</span><span class="sxs-lookup"><span data-stu-id="7e670-119">Carriage return</span></span>|<span data-ttu-id="7e670-120">\r</span><span class="sxs-lookup"><span data-stu-id="7e670-120">\r</span></span>|
|<span data-ttu-id="7e670-121">Tab</span><span class="sxs-lookup"><span data-stu-id="7e670-121">Tab</span></span>|<span data-ttu-id="7e670-122">\t</span><span class="sxs-lookup"><span data-stu-id="7e670-122">\t</span></span>|
|<span data-ttu-id="7e670-123">ukośnik odwrotny</span><span class="sxs-lookup"><span data-stu-id="7e670-123">Backslash</span></span>|\\|
|<span data-ttu-id="7e670-124">Znak cudzysłowu</span><span class="sxs-lookup"><span data-stu-id="7e670-124">Quotation mark</span></span>|\"|
|<span data-ttu-id="7e670-125">Apostrof</span><span class="sxs-lookup"><span data-stu-id="7e670-125">Apostrophe</span></span>|\'|
|<span data-ttu-id="7e670-126">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="7e670-126">Unicode character</span></span>|<span data-ttu-id="7e670-127">\u*XXXX* lub \U*XXXXXXXX* (gdzie *X* oznacza cyfrę szesnastkową)</span><span class="sxs-lookup"><span data-stu-id="7e670-127">\u*XXXX* or \U*XXXXXXXX* (where *X* indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="7e670-128">Jeśli poprzedzone symbolem @ literału jest ciągu dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7e670-128">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="7e670-129">Oznacza to, że wszystkie sekwencje specjalne są ignorowane, z wyjątkiem tego, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="7e670-129">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="7e670-130">Ponadto ciąg może być ujęta w cudzysłów Potrójna.</span><span class="sxs-lookup"><span data-stu-id="7e670-130">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="7e670-131">W takim przypadku wszystkie sekwencje specjalne są ignorowane, łącznie ze znakami cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="7e670-131">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="7e670-132">Aby określić ciąg, który zawiera osadzony jako ciąg, możesz użyć ciągu dosłownego wyrażenia lub ciąg potrójne cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="7e670-132">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="7e670-133">Jeśli używasz ciągu dosłownego wyrażenia, należy określić dwóch znaków cudzysłowu do wskazywania znak pojedynczego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="7e670-133">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="7e670-134">Użycie ciągu potrójne cudzysłowy, można użyć znaków pojedynczego cudzysłowu bez nich przeanalizowany jako końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="7e670-134">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="7e670-135">Ta technika może być przydatne podczas pracy z XML lub inne struktury, które osadzonych znaków cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="7e670-135">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="7e670-136">W kodzie ciągów, które mają podziały wierszy są akceptowane i podziały wierszy są interpretowane jako literału jako newlines, chyba że ostatni znak przed podział wiersza jest ukośnikiem odwrotnym.</span><span class="sxs-lookup"><span data-stu-id="7e670-136">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="7e670-137">Spacje wiodące w następnym wierszu jest ignorowane, gdy jest używany znak ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="7e670-137">Leading whitespace on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="7e670-138">Poniższy kod tworzy ciąg `str1` wartością `"abc\n     def"` i ciąg `str2` wartością `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="7e670-138">The following code produces a string `str1` that has value `"abc\n     def"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="7e670-139">Można uzyskać dostępu do poszczególnych znaków w ciągu za pomocą składni tablicy w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="7e670-139">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="7e670-140">Dane wyjściowe `b`.</span><span class="sxs-lookup"><span data-stu-id="7e670-140">The output is `b`.</span></span>

<span data-ttu-id="7e670-141">Lub może wyodrębnić podciągów przy użyciu składni wycinek tablicy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7e670-141">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="7e670-142">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="7e670-142">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="7e670-143">Ciągi ASCII może reprezentować przez tablice bajtów bez znaku, typ `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="7e670-143">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="7e670-144">Dodaj sufiks `B` z ciągiem literału, aby wskazać, że ciąg znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="7e670-144">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="7e670-145">Literały ciągu ASCII używane z tablic bajtowych obsługuje tej samej sekwencji unikowych jako ciągów Unicode, z wyjątkiem sekwencje specjalne Unicode.</span><span class="sxs-lookup"><span data-stu-id="7e670-145">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a><span data-ttu-id="7e670-146">Operatory ciągów</span><span class="sxs-lookup"><span data-stu-id="7e670-146">String Operators</span></span>
<span data-ttu-id="7e670-147">Istnieją dwa sposoby ciągów: za pomocą `+` operator lub za pomocą `^` operatora.</span><span class="sxs-lookup"><span data-stu-id="7e670-147">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="7e670-148">`+` Operator zachowuje zgodność z obsługi funkcji ciągów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7e670-148">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="7e670-149">Poniższy przykład przedstawia ciągów.</span><span class="sxs-lookup"><span data-stu-id="7e670-149">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a><span data-ttu-id="7e670-150">String — klasa</span><span class="sxs-lookup"><span data-stu-id="7e670-150">String Class</span></span>
<span data-ttu-id="7e670-151">Ponieważ typ ciągu w języku F # jest rzeczywiście .NET Framework `System.String` wpisz wszystkie `System.String` elementy są dostępne.</span><span class="sxs-lookup"><span data-stu-id="7e670-151">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="7e670-152">Obejmuje to `+` operatora, który jest używany do łączenia ciągów, `Length` właściwości oraz `Chars` właściwość, która zwraca ciąg w formie tablicy znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="7e670-152">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="7e670-153">Aby uzyskać więcej informacji na temat ciągów, zobacz `System.String`.</span><span class="sxs-lookup"><span data-stu-id="7e670-153">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="7e670-154">Za pomocą `Chars` właściwość `System.String`, dostęp do poszczególnych znaków w ciągu, określając indeksu, jak to pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7e670-154">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a><span data-ttu-id="7e670-155">Moduł ciągu</span><span class="sxs-lookup"><span data-stu-id="7e670-155">String Module</span></span>
<span data-ttu-id="7e670-156">Dodatkowe funkcje obsługi ciągu znajduje się w `String` modułu w `FSharp.Core` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7e670-156">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="7e670-157">Aby uzyskać więcej informacji, zobacz [Core.String — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="7e670-157">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e670-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e670-158">See Also</span></span>
[<span data-ttu-id="7e670-159">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="7e670-159">F# Language Reference</span></span>](index.md)
