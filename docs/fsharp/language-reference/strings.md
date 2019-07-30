---
title: Ciągi
description: Dowiedz się F# , jak typ "String" reprezentuje niezmienny tekst jako sekwencję znaków Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 284de939c90c4d9d4ea064fb4db1fb90a37038e2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627105"
---
# <a name="strings"></a><span data-ttu-id="843e7-103">Ciągi</span><span class="sxs-lookup"><span data-stu-id="843e7-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="843e7-104">Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN.</span><span class="sxs-lookup"><span data-stu-id="843e7-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="843e7-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="843e7-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="843e7-106">`string` Typ reprezentuje niezmienny tekst jako sekwencję znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="843e7-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="843e7-107">`string`jest aliasem dla `System.String` .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="843e7-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="843e7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="843e7-108">Remarks</span></span>

<span data-ttu-id="843e7-109">Literały ciągów są rozdzielane znakami cudzysłowu (").</span><span class="sxs-lookup"><span data-stu-id="843e7-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="843e7-110">Znak ukośnika odwrotnego \\ () jest używany do kodowania niektórych znaków specjalnych.</span><span class="sxs-lookup"><span data-stu-id="843e7-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="843e7-111">Ukośnik odwrotny i następny znak razem są znane jako *sekwencja ucieczki*.</span><span class="sxs-lookup"><span data-stu-id="843e7-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="843e7-112">Sekwencje ucieczki F# obsługiwane w literałach ciągów są pokazane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="843e7-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="843e7-113">Znak</span><span class="sxs-lookup"><span data-stu-id="843e7-113">Character</span></span>|<span data-ttu-id="843e7-114">Sekwencja ucieczki</span><span class="sxs-lookup"><span data-stu-id="843e7-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="843e7-115">Alerty</span><span class="sxs-lookup"><span data-stu-id="843e7-115">Alert</span></span>|`\a`|
|<span data-ttu-id="843e7-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="843e7-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="843e7-117">Kanał informacyjny formularza</span><span class="sxs-lookup"><span data-stu-id="843e7-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="843e7-118">Ani</span><span class="sxs-lookup"><span data-stu-id="843e7-118">Newline</span></span>|`\n`|
|<span data-ttu-id="843e7-119">Znak powrotu karetki</span><span class="sxs-lookup"><span data-stu-id="843e7-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="843e7-120">Tab</span><span class="sxs-lookup"><span data-stu-id="843e7-120">Tab</span></span>|`\t`|
|<span data-ttu-id="843e7-121">Tabulator pionowy</span><span class="sxs-lookup"><span data-stu-id="843e7-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="843e7-122">Ukośnik odwrotny</span><span class="sxs-lookup"><span data-stu-id="843e7-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="843e7-123">Cudzysłów</span><span class="sxs-lookup"><span data-stu-id="843e7-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="843e7-124">Apostrof</span><span class="sxs-lookup"><span data-stu-id="843e7-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="843e7-125">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="843e7-125">Unicode character</span></span>|<span data-ttu-id="843e7-126">`\DDD`(gdzie `D` wskazuje cyfrę dziesiętną; zakres 000-255; na `\231` przykład = "ç")</span><span class="sxs-lookup"><span data-stu-id="843e7-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="843e7-127">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="843e7-127">Unicode character</span></span>|<span data-ttu-id="843e7-128">`\xHH`(gdzie `H` wskazuje cyfrę szesnastkową; zakres 00-FF; na `\xE7` przykład = "ç")</span><span class="sxs-lookup"><span data-stu-id="843e7-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="843e7-129">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="843e7-129">Unicode character</span></span>|<span data-ttu-id="843e7-130">`\uHHHH`(UTF-16) (gdzie `H` wskazuje cyfrę szesnastkową; zakres 0000-FFFF;  na przykład `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="843e7-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="843e7-131">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="843e7-131">Unicode character</span></span>|<span data-ttu-id="843e7-132">`\U00HHHHHH`(UTF-32) (gdzie `H` wskazuje cyfrę szesnastkową; zakres 000000-10FFFF;  na przykład `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="843e7-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="843e7-133">Sekwencja `\DDD` ucieczki jest notacją dziesiętną, a nie notacją ósemkową, taką jak w większości innych języków.</span><span class="sxs-lookup"><span data-stu-id="843e7-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="843e7-134">W związku z `8` `9` `\040`tym cyfry i są prawidłowe, a sekwencja reprezentuje spację (U + 0020), natomiast ten sam punkt kodu w notacji ósemkowej będzie. `\032`</span><span class="sxs-lookup"><span data-stu-id="843e7-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="843e7-135">Są ograniczone do zakresu 0-255 (0xFF), `\DDD` a `\x` sekwencje ucieczki są efektywnie zestawem znaków [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , ponieważ dopasowuje pierwsze 256 punktów kodowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="843e7-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="843e7-136">Jeśli poprzedzany przez symbol @, literał jest ciągiem Verbatim.</span><span class="sxs-lookup"><span data-stu-id="843e7-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="843e7-137">Oznacza to, że wszystkie sekwencje ucieczki są ignorowane, z tą różnicą, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="843e7-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="843e7-138">Ponadto ciąg może być ujęty w potrójne cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="843e7-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="843e7-139">W takim przypadku wszystkie sekwencje ucieczki są ignorowane, w tym znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="843e7-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="843e7-140">Aby określić ciąg zawierający osadzony ciąg ujęty w cudzysłów, można użyć ciągu Verbatim lub ciągu z potrójnym cudzysłowem.</span><span class="sxs-lookup"><span data-stu-id="843e7-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="843e7-141">W przypadku używania ciągu Verbatim należy określić dwa znaki cudzysłowu, aby wskazać znak pojedynczego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="843e7-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="843e7-142">Jeśli używasz ciągu z potrójnym cudzysłowem, możesz użyć znaków pojedynczego cudzysłowu bez ich analizowania jako końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="843e7-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="843e7-143">Ta technika może być przydatna podczas pracy z danymi XML lub innymi strukturami, które zawierają osadzone znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="843e7-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="843e7-144">W kodzie, ciągi, które mają podziały wierszy są akceptowane, a podziały wierszy są interpretowane dosłownie jako znaki nowego wiersza, chyba że znak ukośnika odwrotnego jest ostatnim znakiem przed przerwaniem.</span><span class="sxs-lookup"><span data-stu-id="843e7-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="843e7-145">Wiodący biały znak w następnym wierszu jest ignorowany, gdy jest używany ukośnik odwrotny.</span><span class="sxs-lookup"><span data-stu-id="843e7-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="843e7-146">Poniższy kod generuje `str1` ciąg, który ma wartość `"abc\ndef"` i ciąg `str2` , który ma wartość `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="843e7-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="843e7-147">Można uzyskać dostęp do pojedynczych znaków w ciągu za pomocą składni podobnej do tablicy, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="843e7-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="843e7-148">Dane wyjściowe to `b`.</span><span class="sxs-lookup"><span data-stu-id="843e7-148">The output is `b`.</span></span>

<span data-ttu-id="843e7-149">Lub można wyodrębnić podciągi przy użyciu składni wycinka tablicy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="843e7-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="843e7-150">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="843e7-150">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="843e7-151">Ciągi ASCII można reprezentować według tablic bajtów `byte[]`bez znaku.</span><span class="sxs-lookup"><span data-stu-id="843e7-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="843e7-152">Należy dodać sufiks `B` do literału ciągu, aby wskazać, że jest to ciąg ASCII.</span><span class="sxs-lookup"><span data-stu-id="843e7-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="843e7-153">Literały ciągu ASCII używane z tablicami bajtowymi obsługują te same sekwencje unikowe co ciągi Unicode, z wyjątkiem sekwencji unikowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="843e7-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="843e7-154">Operatory ciągów</span><span class="sxs-lookup"><span data-stu-id="843e7-154">String Operators</span></span>

<span data-ttu-id="843e7-155">Istnieją dwa sposoby łączenia ciągów: przy użyciu `+` operatora lub `^` operatora.</span><span class="sxs-lookup"><span data-stu-id="843e7-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="843e7-156">`+` Operator zachowuje zgodność z funkcjami obsługi ciągów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="843e7-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="843e7-157">Poniższy przykład ilustruje łączenie ciągów.</span><span class="sxs-lookup"><span data-stu-id="843e7-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="843e7-158">String — Klasa</span><span class="sxs-lookup"><span data-stu-id="843e7-158">String Class</span></span>

<span data-ttu-id="843e7-159">Ponieważ typ ciągu w jest F# w rzeczywistości `System.String` typem .NET Framework `System.String` , wszystkie elementy członkowskie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="843e7-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="843e7-160">Obejmuje `+` operator, który jest używany do łączenia ciągów `Length` , właściwość i `Chars` właściwość, która zwraca ciąg jako tablicę znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="843e7-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="843e7-161">Aby uzyskać więcej informacji na temat ciągów `System.String`, zobacz.</span><span class="sxs-lookup"><span data-stu-id="843e7-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="843e7-162">Za pomocą `Chars` `System.String`właściwości, można uzyskać dostęp do poszczególnych znaków w ciągu, określając indeks, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="843e7-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="843e7-163">Moduł String</span><span class="sxs-lookup"><span data-stu-id="843e7-163">String Module</span></span>

<span data-ttu-id="843e7-164">Dodatkowe funkcje obsługi ciągów są zawarte w `String` module `FSharp.Core` w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="843e7-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="843e7-165">Aby uzyskać więcej informacji, zobacz [moduł Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="843e7-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="843e7-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="843e7-166">See also</span></span>

- [<span data-ttu-id="843e7-167">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="843e7-167">F# Language Reference</span></span>](index.md)
