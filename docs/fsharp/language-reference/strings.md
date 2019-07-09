---
title: Ciągi
description: Dowiedz się, jak F# typu "string" reprezentuje niezmienny tekst jako sekwencja znaków Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: ec895723cc6d21a701a27b5d70d053bb681ce2b3
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660598"
---
# <a name="strings"></a><span data-ttu-id="594a8-103">Ciągi</span><span class="sxs-lookup"><span data-stu-id="594a8-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="594a8-104">Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="594a8-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="594a8-105">Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="594a8-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="594a8-106">`string` Typu reprezentuje niezmienny tekst jako sekwencja znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="594a8-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="594a8-107">`string` jest aliasem dla `System.String` w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="594a8-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="594a8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="594a8-108">Remarks</span></span>

<span data-ttu-id="594a8-109">Literały ciągów są rozdzielone znakiem cudzysłowu (").</span><span class="sxs-lookup"><span data-stu-id="594a8-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="594a8-110">Znak ukośnika odwrotnego ( \\ ) jest używany do kodowania niektórych znaków specjalnych.</span><span class="sxs-lookup"><span data-stu-id="594a8-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="594a8-111">Ukośnik odwrotny i następny znak razem są określane jako *sekwencji unikowej*.</span><span class="sxs-lookup"><span data-stu-id="594a8-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="594a8-112">Obsługiwane w sekwencjach specjalnych F# literały ciągów są wyświetlane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="594a8-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="594a8-113">Znak</span><span class="sxs-lookup"><span data-stu-id="594a8-113">Character</span></span>|<span data-ttu-id="594a8-114">Sekwencja unikowa</span><span class="sxs-lookup"><span data-stu-id="594a8-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="594a8-115">Alerty</span><span class="sxs-lookup"><span data-stu-id="594a8-115">Alert</span></span>|`\a`|
|<span data-ttu-id="594a8-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="594a8-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="594a8-117">Wysuw strony</span><span class="sxs-lookup"><span data-stu-id="594a8-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="594a8-118">nowy wiersz</span><span class="sxs-lookup"><span data-stu-id="594a8-118">Newline</span></span>|`\n`|
|<span data-ttu-id="594a8-119">Powrót karetki</span><span class="sxs-lookup"><span data-stu-id="594a8-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="594a8-120">Tab</span><span class="sxs-lookup"><span data-stu-id="594a8-120">Tab</span></span>|`\t`|
|<span data-ttu-id="594a8-121">tabulator pionowy</span><span class="sxs-lookup"><span data-stu-id="594a8-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="594a8-122">Ukośnik odwrotny</span><span class="sxs-lookup"><span data-stu-id="594a8-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="594a8-123">Znak cudzysłowu</span><span class="sxs-lookup"><span data-stu-id="594a8-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="594a8-124">Apostrof</span><span class="sxs-lookup"><span data-stu-id="594a8-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="594a8-125">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="594a8-125">Unicode character</span></span>|<span data-ttu-id="594a8-126">`\DDD` (gdzie `D` wskazuje wartości dziesiętnej cyfrę; zakres 000 - 255; na przykład `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="594a8-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="594a8-127">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="594a8-127">Unicode character</span></span>|<span data-ttu-id="594a8-128">`\xHH` (gdzie `H` wskazuje cyfra szesnastkowa; zakres 00 - FF; na przykład `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="594a8-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="594a8-129">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="594a8-129">Unicode character</span></span>|<span data-ttu-id="594a8-130">`\uHHHH` (UTF-16) (gdzie `H` wskazuje cyfra szesnastkowa; zakres 0000 – FFFF;  na przykład `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="594a8-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="594a8-131">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="594a8-131">Unicode character</span></span>|<span data-ttu-id="594a8-132">`\U00HHHHHH` (UTF-32) (gdzie `H` wskazuje cyfra szesnastkowa; zakres 000000 - 10FFFF;  na przykład `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="594a8-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="594a8-133">`\DDD` Sekwencja unikowa to Notacja dziesiętna, a nie ósemkowy podobnie jak w innych językach.</span><span class="sxs-lookup"><span data-stu-id="594a8-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="594a8-134">W związku z tym, cyfr `8` i `9` są prawidłowe oraz sekwencję `\032` reprezentuje spację (U + 0020), byłoby tego samego punktu kodu w notacji ósemkowej `\040`.</span><span class="sxs-lookup"><span data-stu-id="594a8-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="594a8-135">Jest ograniczone do zakresu od 0 - 255 (0xFF) `\DDD` i `\x` sekwencje ucieczki są faktycznymi [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) znak zestawu, ponieważ odpowiadający 256 pierwszych punkty kodowe Unicode.</span><span class="sxs-lookup"><span data-stu-id="594a8-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="594a8-136">Jeśli poprzedzone symbolem @ literał jest ciąg verbatim.</span><span class="sxs-lookup"><span data-stu-id="594a8-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="594a8-137">Oznacza to, że wszelkie sekwencje ucieczki są ignorowane, z tą różnicą, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="594a8-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="594a8-138">Ponadto ciąg mogą być ujęte w cudzysłowy Potrójna.</span><span class="sxs-lookup"><span data-stu-id="594a8-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="594a8-139">W takim przypadku wszystkie sekwencje ucieczki są ignorowane, w tym znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="594a8-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="594a8-140">Aby określić ciąg, który zawiera osadzony jako ciąg, możesz użyć ciąg verbatim lub ciąg potrójnych cudzysłowach.</span><span class="sxs-lookup"><span data-stu-id="594a8-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="594a8-141">Jeśli używasz ciąg verbatim, należy określić dwa znaki cudzysłowu do wskazania znak pojedynczego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="594a8-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="594a8-142">Użycie ciągu potrójnych cudzysłowach, można użyć znaków pojedynczego cudzysłowu, bez nich przeanalizowany jako końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="594a8-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="594a8-143">Ta technika może być przydatne podczas pracy z XML lub innych struktur, które zawierają osadzone znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="594a8-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="594a8-144">W kodzie ciągów zawierających podziały wierszy są akceptowane i podziałów wiersza są interpretowane dosłownie jako tabulacji, chyba że znak ukośnika odwrotnego jest ostatni znak przed podziału wiersza.</span><span class="sxs-lookup"><span data-stu-id="594a8-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="594a8-145">Spacja wiodąca w następnym wierszu jest ignorowana, gdy jest używany znak ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="594a8-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="594a8-146">Poniższy kod tworzy ciąg `str1` wartością `"abc\ndef"` i ciąg `str2` wartością `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="594a8-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="594a8-147">Można uzyskać dostęp do poszczególnych znaków w ciągu za pomocą składni tablicy w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="594a8-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="594a8-148">Dane wyjściowe są `b`.</span><span class="sxs-lookup"><span data-stu-id="594a8-148">The output is `b`.</span></span>

<span data-ttu-id="594a8-149">Lub wyodrębnić podciągi przy użyciu składni wycinek tablicy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="594a8-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="594a8-150">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="594a8-150">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="594a8-151">Ciągi ASCII mogą być reprezentowane przez tablice bajtów bez znaku, wpisz `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="594a8-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="594a8-152">Dodaj sufiks `B` z ciągiem literału, aby wskazać, że ciąg ASCII.</span><span class="sxs-lookup"><span data-stu-id="594a8-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="594a8-153">Literały ciągów znaków ASCII używany z tablic bajtowych obsługują ten sam sekwencje ucieczki jako ciągi znaków Unicode, z wyjątkiem sekwencje unikowe Unicode.</span><span class="sxs-lookup"><span data-stu-id="594a8-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="594a8-154">Operatory ciągów</span><span class="sxs-lookup"><span data-stu-id="594a8-154">String Operators</span></span>

<span data-ttu-id="594a8-155">Istnieją dwa sposoby łączenia ciągów: za pomocą `+` operatora lub za pomocą `^` operatora.</span><span class="sxs-lookup"><span data-stu-id="594a8-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="594a8-156">`+` Operator zachowuje zgodność z obsługi funkcji ciągów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="594a8-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="594a8-157">Poniższy przykład ilustruje ciągów.</span><span class="sxs-lookup"><span data-stu-id="594a8-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="594a8-158">Klasa String</span><span class="sxs-lookup"><span data-stu-id="594a8-158">String Class</span></span>

<span data-ttu-id="594a8-159">Ponieważ wpisać ciąg F# jest faktycznie .NET Framework `System.String` wpisz wszystkie `System.String` składowe są dostępne.</span><span class="sxs-lookup"><span data-stu-id="594a8-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="594a8-160">Obejmuje to `+` operatora, który jest używany do łączenia ciągów, `Length` właściwości i `Chars` właściwość, która zwraca ciąg w postaci tablicy znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="594a8-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="594a8-161">Aby uzyskać więcej informacji na temat ciągów, zobacz `System.String`.</span><span class="sxs-lookup"><span data-stu-id="594a8-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="594a8-162">Za pomocą `Chars` właściwość `System.String`, dostęp do poszczególnych znaków w ciągu, określając indeksu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="594a8-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="594a8-163">Parametry modułu</span><span class="sxs-lookup"><span data-stu-id="594a8-163">String Module</span></span>

<span data-ttu-id="594a8-164">Dodatkowe funkcje obsługi ciągu znajduje się w `String` modułu w `FSharp.Core` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="594a8-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="594a8-165">Aby uzyskać więcej informacji, zobacz [Core.String — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="594a8-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="594a8-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="594a8-166">See also</span></span>

- [<span data-ttu-id="594a8-167">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="594a8-167">F# Language Reference</span></span>](index.md)
