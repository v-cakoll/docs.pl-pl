---
title: Ciągi
description: Dowiedz się, jak typ "string" języka F# reprezentuje niezmienny tekst jako sekwencję znaków Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739572"
---
# <a name="strings"></a><span data-ttu-id="535e1-103">Ciągi</span><span class="sxs-lookup"><span data-stu-id="535e1-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="535e1-104">Łącza odwołania interfejsu API w tym artykule spowoduje, że przejdziesz do usługi MSDN.</span><span class="sxs-lookup"><span data-stu-id="535e1-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="535e1-105">Odwołanie docs.microsoft.com interfejsu API nie jest kompletne.</span><span class="sxs-lookup"><span data-stu-id="535e1-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="535e1-106">Typ `string` reprezentuje niezmienny tekst jako sekwencję znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="535e1-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="535e1-107">`string`jest aliasem `System.String` w ramach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="535e1-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="535e1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="535e1-108">Remarks</span></span>

<span data-ttu-id="535e1-109">Literały ciągów są rozdzielane znakiem cudzysłowu (").</span><span class="sxs-lookup"><span data-stu-id="535e1-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="535e1-110">Znak ukośnika \\ odwrotnego ( ) służy do kodowania niektórych znaków specjalnych.</span><span class="sxs-lookup"><span data-stu-id="535e1-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="535e1-111">Ukośnik odwrotny i następny znak razem są znane jako *sekwencja ucieczki*.</span><span class="sxs-lookup"><span data-stu-id="535e1-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="535e1-112">Sekwencje ucieczki obsługiwane w literałach ciągu F# są wyświetlane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="535e1-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="535e1-113">Znak</span><span class="sxs-lookup"><span data-stu-id="535e1-113">Character</span></span>|<span data-ttu-id="535e1-114">Sekwencja ucieczki</span><span class="sxs-lookup"><span data-stu-id="535e1-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="535e1-115">Alerty</span><span class="sxs-lookup"><span data-stu-id="535e1-115">Alert</span></span>|`\a`|
|<span data-ttu-id="535e1-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="535e1-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="535e1-117">Pasza formularza</span><span class="sxs-lookup"><span data-stu-id="535e1-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="535e1-118">Newline</span><span class="sxs-lookup"><span data-stu-id="535e1-118">Newline</span></span>|`\n`|
|<span data-ttu-id="535e1-119">Powrót karetki</span><span class="sxs-lookup"><span data-stu-id="535e1-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="535e1-120">Tab</span><span class="sxs-lookup"><span data-stu-id="535e1-120">Tab</span></span>|`\t`|
|<span data-ttu-id="535e1-121">Zakładka Pionowa</span><span class="sxs-lookup"><span data-stu-id="535e1-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="535e1-122">Ukośnik odwrotny</span><span class="sxs-lookup"><span data-stu-id="535e1-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="535e1-123">Cudzysłowu</span><span class="sxs-lookup"><span data-stu-id="535e1-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="535e1-124">Apostrof</span><span class="sxs-lookup"><span data-stu-id="535e1-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="535e1-125">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="535e1-125">Unicode character</span></span>|<span data-ttu-id="535e1-126">`\DDD`(gdzie `D` wskazuje cyfrę dziesiętną; zakres od 000 do 255; na przykład `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="535e1-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="535e1-127">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="535e1-127">Unicode character</span></span>|<span data-ttu-id="535e1-128">`\xHH`(gdzie `H` wskazuje cyfrę szesnastową; zakres 00 - `\xE7` FF; na przykład = "ç")</span><span class="sxs-lookup"><span data-stu-id="535e1-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="535e1-129">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="535e1-129">Unicode character</span></span>|<span data-ttu-id="535e1-130">`\uHHHH`(UTF-16) (gdzie `H` wskazuje cyfrę szesnastową; zakres 0000 - FFFF;  na przykład `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="535e1-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="535e1-131">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="535e1-131">Unicode character</span></span>|<span data-ttu-id="535e1-132">`\U00HHHHHH`(UTF-32) (gdzie `H` wskazuje cyfrę szesnastową; zakres 000000 - 10FFFF;  na przykład `\U0001F47D` =👽" ")</span><span class="sxs-lookup"><span data-stu-id="535e1-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="535e1-133">Sekwencja `\DDD` ucieczki jest notacją dziesiętną, a nie notacją ósemkową, jak w większości innych języków.</span><span class="sxs-lookup"><span data-stu-id="535e1-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="535e1-134">W związku z `8` `9` tym cyfry i `\032` są prawidłowe, a sekwencja reprezentuje spację (U + 0020), podczas gdy ten sam punkt kodu w notacji ósemkowej będzie `\040`.</span><span class="sxs-lookup"><span data-stu-id="535e1-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="535e1-135">Są ograniczone do zakresu od 0 - 255 (0xFF), `\DDD` i `\x` sekwencje ucieczki są skutecznie [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) zestaw znaków, ponieważ pasuje do pierwszych 256 punktów kodu Unicode.</span><span class="sxs-lookup"><span data-stu-id="535e1-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="535e1-136">Dosłownie ciągi</span><span class="sxs-lookup"><span data-stu-id="535e1-136">Verbatim Strings</span></span>

<span data-ttu-id="535e1-137">Jeśli poprzedzone symbol @, literał jest ciągiem dosłownie.</span><span class="sxs-lookup"><span data-stu-id="535e1-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="535e1-138">Oznacza to, że wszystkie sekwencje unikowe są ignorowane, z tą różnicą, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="535e1-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="535e1-139">Potrójne notowane ciągi</span><span class="sxs-lookup"><span data-stu-id="535e1-139">Triple Quoted Strings</span></span>

<span data-ttu-id="535e1-140">Ponadto ciąg może być ujęty potrójnymi cudzysłowami.</span><span class="sxs-lookup"><span data-stu-id="535e1-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="535e1-141">W takim przypadku wszystkie sekwencje ucieczki są ignorowane, w tym znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="535e1-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="535e1-142">Aby określić ciąg, który zawiera osadzony ciąg cudzysłowu, można użyć ciągu dosłownie lub ciągu potrójnego.</span><span class="sxs-lookup"><span data-stu-id="535e1-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="535e1-143">W przypadku użycia ciągu dosłownego należy określić dwa znaki cudzysłowu, aby wskazać pojedynczy znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="535e1-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="535e1-144">Jeśli używasz potrójnego ciągu, można użyć pojedynczych znaków cudzysłowu bez ich analizowania jako końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="535e1-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="535e1-145">Ta technika może być przydatna podczas pracy z xml lub innymi strukturami, które zawierają osadzone cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="535e1-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="535e1-146">W kodzie ciągi, które mają podziały wierszy są akceptowane, a podziały wierszy są interpretowane dosłownie jako nowe linie, chyba że znak ukośnika odwrotnego jest ostatnim znakiem przed podziałem wiersza.</span><span class="sxs-lookup"><span data-stu-id="535e1-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="535e1-147">Początkowa biały znak w następnym wierszu jest ignorowana, gdy używany jest znak ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="535e1-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="535e1-148">Poniższy kod tworzy `str1` ciąg, `"abc\ndef"` który ma `str2` wartość `"abcdef"`i ciąg, który ma wartość .</span><span class="sxs-lookup"><span data-stu-id="535e1-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="535e1-149">Indeksowanie ciągów i krojenie</span><span class="sxs-lookup"><span data-stu-id="535e1-149">String Indexing and Slicing</span></span>

<span data-ttu-id="535e1-150">Dostęp do poszczególnych znaków w ciągu można uzyskać przy użyciu składni podobnej do tablicy, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="535e1-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="535e1-151">Wyjście jest `b`.</span><span class="sxs-lookup"><span data-stu-id="535e1-151">The output is `b`.</span></span>

<span data-ttu-id="535e1-152">Można też wyodrębnić podciągi przy użyciu składni plasterka tablicy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="535e1-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="535e1-153">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="535e1-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="535e1-154">Ciągi ASCII można reprezentować według tablic niepodpisanych bajtów, wpisz `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="535e1-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="535e1-155">Sufiks `B` można dodać do literału ciągu, aby wskazać, że jest to ciąg ASCII.</span><span class="sxs-lookup"><span data-stu-id="535e1-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="535e1-156">Literały ciągu ASCII używane z tablicami bajtowymi obsługują te same sekwencje ucieczki co ciągi Unicode, z wyjątkiem sekwencji unikowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="535e1-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="535e1-157">Operatory ciągów</span><span class="sxs-lookup"><span data-stu-id="535e1-157">String Operators</span></span>

<span data-ttu-id="535e1-158">Operator `+` może służyć do łączenia ciągów, zachowując zgodność z funkcjami obsługi ciągów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="535e1-158">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="535e1-159">Poniższy przykład ilustruje łączenie ciągów.</span><span class="sxs-lookup"><span data-stu-id="535e1-159">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="535e1-160">Klasa ciągu</span><span class="sxs-lookup"><span data-stu-id="535e1-160">String Class</span></span>

<span data-ttu-id="535e1-161">Ponieważ typ ciągu w języku F# `System.String` jest faktycznie `System.String` typem .NET Framework, wszystkie elementy członkowskie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="535e1-161">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="535e1-162">Obejmuje to `+` operator, który jest używany do łączenia ciągów, `Length` właściwości i `Chars` właściwości, która zwraca ciąg jako tablicę znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="535e1-162">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="535e1-163">Aby uzyskać więcej informacji `System.String`na temat ciągów, zobacz .</span><span class="sxs-lookup"><span data-stu-id="535e1-163">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="535e1-164">Za pomocą `Chars` właściwości `System.String`, można uzyskać dostęp do poszczególnych znaków w ciągu, określając indeks, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="535e1-164">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="535e1-165">Moduł ciągów</span><span class="sxs-lookup"><span data-stu-id="535e1-165">String Module</span></span>

<span data-ttu-id="535e1-166">Dodatkowe funkcje obsługi ciągów znajduje `String` się `FSharp.Core` w module w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="535e1-166">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="535e1-167">Aby uzyskać więcej informacji, zobacz [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="535e1-167">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="535e1-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="535e1-168">See also</span></span>

- [<span data-ttu-id="535e1-169">Odwołanie do języka F#</span><span class="sxs-lookup"><span data-stu-id="535e1-169">F# Language Reference</span></span>](index.md)
