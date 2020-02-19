---
title: Ciągi
description: Dowiedz się F# , jak typ "String" reprezentuje niezmienny tekst jako sekwencję znaków Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 002de464d09a49b6161608db6e46c619369f5ceb
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452821"
---
# <a name="strings"></a><span data-ttu-id="d3fcf-103">Ciągi</span><span class="sxs-lookup"><span data-stu-id="d3fcf-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="d3fcf-104">Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="d3fcf-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="d3fcf-106">Typ `string` reprezentuje niezmienny tekst jako sekwencję znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="d3fcf-107">`string` jest aliasem `System.String` w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="d3fcf-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3fcf-108">Remarks</span></span>

<span data-ttu-id="d3fcf-109">Literały ciągów są rozdzielane znakami cudzysłowu (").</span><span class="sxs-lookup"><span data-stu-id="d3fcf-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="d3fcf-110">Znak ukośnika odwrotnego (\\) jest używany do kodowania niektórych znaków specjalnych.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="d3fcf-111">Ukośnik odwrotny i następny znak razem są znane jako *sekwencja ucieczki*.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="d3fcf-112">Sekwencje ucieczki F# obsługiwane w literałach ciągów są pokazane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="d3fcf-113">Znak</span><span class="sxs-lookup"><span data-stu-id="d3fcf-113">Character</span></span>|<span data-ttu-id="d3fcf-114">Sekwencja ucieczki</span><span class="sxs-lookup"><span data-stu-id="d3fcf-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="d3fcf-115">Alerty</span><span class="sxs-lookup"><span data-stu-id="d3fcf-115">Alert</span></span>|`\a`|
|<span data-ttu-id="d3fcf-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="d3fcf-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="d3fcf-117">Kanał informacyjny formularza</span><span class="sxs-lookup"><span data-stu-id="d3fcf-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="d3fcf-118">Ani</span><span class="sxs-lookup"><span data-stu-id="d3fcf-118">Newline</span></span>|`\n`|
|<span data-ttu-id="d3fcf-119">Znak powrotu karetki</span><span class="sxs-lookup"><span data-stu-id="d3fcf-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="d3fcf-120">Tab</span><span class="sxs-lookup"><span data-stu-id="d3fcf-120">Tab</span></span>|`\t`|
|<span data-ttu-id="d3fcf-121">Tabulator pionowy</span><span class="sxs-lookup"><span data-stu-id="d3fcf-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="d3fcf-122">Ukośnik odwrotny</span><span class="sxs-lookup"><span data-stu-id="d3fcf-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="d3fcf-123">Cudzysłów</span><span class="sxs-lookup"><span data-stu-id="d3fcf-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="d3fcf-124">Apostrof</span><span class="sxs-lookup"><span data-stu-id="d3fcf-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="d3fcf-125">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="d3fcf-125">Unicode character</span></span>|<span data-ttu-id="d3fcf-126">`\DDD` (gdzie `D` wskazuje cyfrę dziesiętną; zakres 000-255; na przykład, `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="d3fcf-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="d3fcf-127">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="d3fcf-127">Unicode character</span></span>|<span data-ttu-id="d3fcf-128">`\xHH` (gdzie `H` wskazuje cyfrę szesnastkową; zakres 00-FF; na przykład, `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="d3fcf-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="d3fcf-129">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="d3fcf-129">Unicode character</span></span>|<span data-ttu-id="d3fcf-130">`\uHHHH` (UTF-16) (gdzie `H` wskazuje cyfrę szesnastkową; zakres 0000-FFFF;  na przykład `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="d3fcf-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="d3fcf-131">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="d3fcf-131">Unicode character</span></span>|<span data-ttu-id="d3fcf-132">`\U00HHHHHH` (UTF-32) (gdzie `H` wskazuje cyfrę szesnastkową; zakres 000000-10FFFF;  na przykład `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="d3fcf-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="d3fcf-133">Sekwencja ucieczki `\DDD` jest notacją dziesiętną, a nie notacją ósemkową, taką jak w większości innych języków.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="d3fcf-134">W związku z tym cyfry `8` i `9` są prawidłowe, a sekwencja `\032` reprezentuje spację (U + 0020), natomiast ten sam punkt kodu w notacji ósemkowej będzie `\040`.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="d3fcf-135">Z ograniczeniem do zakresu 0-255 (0xFF), `\DDD` i `\x` sekwencje ucieczki są skutecznie zestawem znaków [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , ponieważ dopasowuje pierwsze 256 punktów kodowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="d3fcf-136">Verbatim ciągi</span><span class="sxs-lookup"><span data-stu-id="d3fcf-136">Verbatim Strings</span></span>

<span data-ttu-id="d3fcf-137">Jeśli poprzedzany przez symbol @, literał jest ciągiem Verbatim.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="d3fcf-138">Oznacza to, że wszystkie sekwencje ucieczki są ignorowane, z tą różnicą, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="d3fcf-139">Potrójne ciągi ujęte w cudzysłów</span><span class="sxs-lookup"><span data-stu-id="d3fcf-139">Triple Quoted Strings</span></span>

<span data-ttu-id="d3fcf-140">Ponadto ciąg może być ujęty w potrójne cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="d3fcf-141">W takim przypadku wszystkie sekwencje ucieczki są ignorowane, w tym znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="d3fcf-142">Aby określić ciąg zawierający osadzony ciąg ujęty w cudzysłów, można użyć ciągu Verbatim lub ciągu z potrójnym cudzysłowem.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="d3fcf-143">W przypadku używania ciągu Verbatim należy określić dwa znaki cudzysłowu, aby wskazać znak pojedynczego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="d3fcf-144">Jeśli używasz ciągu z potrójnym cudzysłowem, możesz użyć znaków pojedynczego cudzysłowu bez ich analizowania jako końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="d3fcf-145">Ta technika może być przydatna podczas pracy z danymi XML lub innymi strukturami, które zawierają osadzone znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="d3fcf-146">W kodzie, ciągi, które mają podziały wierszy są akceptowane, a podziały wierszy są interpretowane dosłownie jako znaki nowego wiersza, chyba że znak ukośnika odwrotnego jest ostatnim znakiem przed przerwaniem.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="d3fcf-147">Wiodący biały znak w następnym wierszu jest ignorowany, gdy jest używany ukośnik odwrotny.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="d3fcf-148">Poniższy kod generuje ciąg `str1`, który ma `"abc\ndef"` wartości i ciąg `str2`, który ma `"abcdef"`wartości.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="d3fcf-149">Indeksowanie ciągów i skalowanie</span><span class="sxs-lookup"><span data-stu-id="d3fcf-149">String Indexing and Slicing</span></span>

<span data-ttu-id="d3fcf-150">Można uzyskać dostęp do pojedynczych znaków w ciągu za pomocą składni podobnej do tablicy, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="d3fcf-151">Dane wyjściowe są `b`.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-151">The output is `b`.</span></span>

<span data-ttu-id="d3fcf-152">Lub można wyodrębnić podciągi przy użyciu składni wycinka tablicy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="d3fcf-153">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="d3fcf-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="d3fcf-154">Można reprezentować ciągi ASCII według tablic bajtów bez znaku, typu `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="d3fcf-155">Należy dodać sufiks `B` do literału ciągu, aby wskazać, że jest to ciąg ASCII.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="d3fcf-156">Literały ciągu ASCII używane z tablicami bajtowymi obsługują te same sekwencje unikowe co ciągi Unicode, z wyjątkiem sekwencji unikowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="d3fcf-157">Operatory ciągów</span><span class="sxs-lookup"><span data-stu-id="d3fcf-157">String Operators</span></span>

<span data-ttu-id="d3fcf-158">Istnieją dwa sposoby łączenia ciągów: przy użyciu operatora `+` lub operatora `^`.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-158">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="d3fcf-159">Operator `+` zachowuje zgodność z funkcjami obsługi ciągów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-159">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="d3fcf-160">Poniższy przykład ilustruje łączenie ciągów.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-160">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="d3fcf-161">String — Klasa</span><span class="sxs-lookup"><span data-stu-id="d3fcf-161">String Class</span></span>

<span data-ttu-id="d3fcf-162">Ponieważ typ ciągu w jest F# w rzeczywistości typem .NET Framework `System.String`, dostępne są wszystkie `System.String` elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-162">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="d3fcf-163">Obejmuje operator `+`, który jest używany do łączenia ciągów, właściwość `Length` i Właściwość `Chars`, która zwraca ciąg jako tablicę znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-163">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="d3fcf-164">Aby uzyskać więcej informacji na temat ciągów, zobacz `System.String`.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-164">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="d3fcf-165">Korzystając z właściwości `Chars` `System.String`, można uzyskać dostęp do poszczególnych znaków w ciągu, określając indeks, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-165">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="d3fcf-166">Moduł String</span><span class="sxs-lookup"><span data-stu-id="d3fcf-166">String Module</span></span>

<span data-ttu-id="d3fcf-167">Dodatkowe funkcje obsługi ciągów są zawarte w module `String` w przestrzeni nazw `FSharp.Core`.</span><span class="sxs-lookup"><span data-stu-id="d3fcf-167">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="d3fcf-168">Aby uzyskać więcej informacji, zobacz [moduł Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="d3fcf-168">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="d3fcf-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3fcf-169">See also</span></span>

- [<span data-ttu-id="d3fcf-170">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="d3fcf-170">F# Language Reference</span></span>](index.md)
