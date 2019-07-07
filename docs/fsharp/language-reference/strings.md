---
title: Ciągi
description: Dowiedz się, jak F# typu "string" reprezentuje niezmienny tekst jako sekwencja znaków Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: b252aef7d7e6e299df8282407198714971e80cd5
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610164"
---
# <a name="strings"></a><span data-ttu-id="8925b-103">Ciągi</span><span class="sxs-lookup"><span data-stu-id="8925b-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="8925b-104">Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="8925b-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="8925b-105">Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="8925b-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="8925b-106">`string` Typu reprezentuje niezmienny tekst jako sekwencja znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="8925b-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="8925b-107">`string` jest aliasem dla `System.String` w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8925b-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="8925b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8925b-108">Remarks</span></span>

<span data-ttu-id="8925b-109">Literały ciągów są rozdzielone znakiem cudzysłowu (").</span><span class="sxs-lookup"><span data-stu-id="8925b-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="8925b-110">Znak ukośnika odwrotnego ( \\ ) jest używany do kodowania niektórych znaków specjalnych.</span><span class="sxs-lookup"><span data-stu-id="8925b-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="8925b-111">Ukośnik odwrotny i następny znak razem są określane jako *sekwencji unikowej*.</span><span class="sxs-lookup"><span data-stu-id="8925b-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="8925b-112">Obsługiwane w sekwencjach specjalnych F# literały ciągów są wyświetlane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="8925b-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="8925b-113">Znak</span><span class="sxs-lookup"><span data-stu-id="8925b-113">Character</span></span>|<span data-ttu-id="8925b-114">Sekwencja unikowa</span><span class="sxs-lookup"><span data-stu-id="8925b-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="8925b-115">Alerty</span><span class="sxs-lookup"><span data-stu-id="8925b-115">Alert</span></span>|`\a`|
|<span data-ttu-id="8925b-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="8925b-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="8925b-117">Wysuw strony</span><span class="sxs-lookup"><span data-stu-id="8925b-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="8925b-118">nowy wiersz</span><span class="sxs-lookup"><span data-stu-id="8925b-118">Newline</span></span>|`\n`|
|<span data-ttu-id="8925b-119">Powrót karetki</span><span class="sxs-lookup"><span data-stu-id="8925b-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="8925b-120">Tab</span><span class="sxs-lookup"><span data-stu-id="8925b-120">Tab</span></span>|`\t`|
|<span data-ttu-id="8925b-121">tabulator pionowy</span><span class="sxs-lookup"><span data-stu-id="8925b-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="8925b-122">Ukośnik odwrotny</span><span class="sxs-lookup"><span data-stu-id="8925b-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="8925b-123">Znak cudzysłowu</span><span class="sxs-lookup"><span data-stu-id="8925b-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="8925b-124">Apostrof</span><span class="sxs-lookup"><span data-stu-id="8925b-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="8925b-125">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="8925b-125">Unicode character</span></span>|<span data-ttu-id="8925b-126">`\DDD` (gdzie `D` wskazuje wartości dziesiętnej cyfrę; zakres 000 - 255; np. `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="8925b-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; e.g. `\231` = "ç")</span></span>|
|<span data-ttu-id="8925b-127">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="8925b-127">Unicode character</span></span>|<span data-ttu-id="8925b-128">`\xHH` (gdzie `H` wskazuje cyfra szesnastkowa; zakres 00 - FF; np. `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="8925b-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; e.g. `\xE7` = "ç")</span></span>|
|<span data-ttu-id="8925b-129">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="8925b-129">Unicode character</span></span>|<span data-ttu-id="8925b-130">`\uHHHH` (UTF-16) (gdzie `H` wskazuje cyfra szesnastkowa; zakres 0000 – FFFF;  np. `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="8925b-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  e.g. `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="8925b-131">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="8925b-131">Unicode character</span></span>|<span data-ttu-id="8925b-132">`\U00HHHHHH` (UTF-32) (gdzie `H` wskazuje cyfra szesnastkowa; zakres 000000 - 10FFFF;  np. `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="8925b-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  e.g. `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="8925b-133">`\DDD` Sekwencja unikowa to Notacja dziesiętna, a nie ósemkowy podobnie jak w innych językach.</span><span class="sxs-lookup"><span data-stu-id="8925b-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="8925b-134">W związku z tym, cyfr `8` i `9` są prawidłowe oraz sekwencję `\032` reprezentuje spację (U + 0020), byłoby tego samego punktu kodu w notacji ósemkowej `\040`.</span><span class="sxs-lookup"><span data-stu-id="8925b-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="8925b-135">Jest ograniczone do zakresu od 0 - 255 (0xFF) `\DDD` i `\x` sekwencje ucieczki są faktycznymi [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) znak zestawu, ponieważ odpowiadający 256 pierwszych punkty kodowe Unicode.</span><span class="sxs-lookup"><span data-stu-id="8925b-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="8925b-136">Jeśli poprzedzone symbolem @ literał jest ciąg verbatim.</span><span class="sxs-lookup"><span data-stu-id="8925b-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="8925b-137">Oznacza to, że wszelkie sekwencje ucieczki są ignorowane, z tą różnicą, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="8925b-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="8925b-138">Ponadto ciąg mogą być ujęte w cudzysłowy Potrójna.</span><span class="sxs-lookup"><span data-stu-id="8925b-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="8925b-139">W takim przypadku wszystkie sekwencje ucieczki są ignorowane, w tym znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="8925b-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="8925b-140">Aby określić ciąg, który zawiera osadzony jako ciąg, możesz użyć ciąg verbatim lub ciąg potrójnych cudzysłowach.</span><span class="sxs-lookup"><span data-stu-id="8925b-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="8925b-141">Jeśli używasz ciąg verbatim, należy określić dwa znaki cudzysłowu do wskazania znak pojedynczego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="8925b-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="8925b-142">Użycie ciągu potrójnych cudzysłowach, można użyć znaków pojedynczego cudzysłowu, bez nich przeanalizowany jako końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="8925b-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="8925b-143">Ta technika może być przydatne podczas pracy z XML lub innych struktur, które zawierają osadzone znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="8925b-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="8925b-144">W kodzie ciągów zawierających podziały wierszy są akceptowane i podziałów wiersza są interpretowane dosłownie jako tabulacji, chyba że znak ukośnika odwrotnego jest ostatni znak przed podziału wiersza.</span><span class="sxs-lookup"><span data-stu-id="8925b-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="8925b-145">Spacja wiodąca w następnym wierszu jest ignorowana, gdy jest używany znak ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8925b-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="8925b-146">Poniższy kod tworzy ciąg `str1` wartością `"abc\ndef"` i ciąg `str2` wartością `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="8925b-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="8925b-147">Można uzyskać dostęp do poszczególnych znaków w ciągu za pomocą składni tablicy w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="8925b-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="8925b-148">Dane wyjściowe są `b`.</span><span class="sxs-lookup"><span data-stu-id="8925b-148">The output is `b`.</span></span>

<span data-ttu-id="8925b-149">Lub wyodrębnić podciągi przy użyciu składni wycinek tablicy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8925b-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="8925b-150">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="8925b-150">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="8925b-151">Ciągi ASCII mogą być reprezentowane przez tablice bajtów bez znaku, wpisz `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="8925b-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="8925b-152">Dodaj sufiks `B` z ciągiem literału, aby wskazać, że ciąg ASCII.</span><span class="sxs-lookup"><span data-stu-id="8925b-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="8925b-153">Literały ciągów znaków ASCII używany z tablic bajtowych obsługują ten sam sekwencje ucieczki jako ciągi znaków Unicode, z wyjątkiem sekwencje unikowe Unicode.</span><span class="sxs-lookup"><span data-stu-id="8925b-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="8925b-154">Operatory ciągów</span><span class="sxs-lookup"><span data-stu-id="8925b-154">String Operators</span></span>

<span data-ttu-id="8925b-155">Istnieją dwa sposoby łączenia ciągów: za pomocą `+` operatora lub za pomocą `^` operatora.</span><span class="sxs-lookup"><span data-stu-id="8925b-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="8925b-156">`+` Operator zachowuje zgodność z obsługi funkcji ciągów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8925b-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="8925b-157">Poniższy przykład ilustruje ciągów.</span><span class="sxs-lookup"><span data-stu-id="8925b-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="8925b-158">Klasa String</span><span class="sxs-lookup"><span data-stu-id="8925b-158">String Class</span></span>

<span data-ttu-id="8925b-159">Ponieważ wpisać ciąg F# jest faktycznie .NET Framework `System.String` wpisz wszystkie `System.String` składowe są dostępne.</span><span class="sxs-lookup"><span data-stu-id="8925b-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="8925b-160">Obejmuje to `+` operatora, który jest używany do łączenia ciągów, `Length` właściwości i `Chars` właściwość, która zwraca ciąg w postaci tablicy znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="8925b-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="8925b-161">Aby uzyskać więcej informacji na temat ciągów, zobacz `System.String`.</span><span class="sxs-lookup"><span data-stu-id="8925b-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="8925b-162">Za pomocą `Chars` właściwość `System.String`, dostęp do poszczególnych znaków w ciągu, określając indeksu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8925b-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="8925b-163">Parametry modułu</span><span class="sxs-lookup"><span data-stu-id="8925b-163">String Module</span></span>

<span data-ttu-id="8925b-164">Dodatkowe funkcje obsługi ciągu znajduje się w `String` modułu w `FSharp.Core` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8925b-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="8925b-165">Aby uzyskać więcej informacji, zobacz [Core.String — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="8925b-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="8925b-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8925b-166">See also</span></span>

- [<span data-ttu-id="8925b-167">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="8925b-167">F# Language Reference</span></span>](index.md)
