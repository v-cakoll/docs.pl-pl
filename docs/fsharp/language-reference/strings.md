---
title: Ciągi
description: Dowiedz się, jak F# typu "string" reprezentuje niezmienny tekst jako sekwencja znaków Unicode.
ms.date: 05/16/2016
ms.openlocfilehash: 5b55b0c87b6636346677b973e093e7bcba324e98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755353"
---
# <a name="strings"></a><span data-ttu-id="08720-103">Ciągi</span><span class="sxs-lookup"><span data-stu-id="08720-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="08720-104">Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="08720-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="08720-105">Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="08720-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="08720-106">`string` Typu reprezentuje niezmienny tekst jako sekwencja znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="08720-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="08720-107">`string` jest aliasem dla `System.String` w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08720-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="08720-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08720-108">Remarks</span></span>

<span data-ttu-id="08720-109">Literały ciągów są rozdzielone znakiem cudzysłowu (").</span><span class="sxs-lookup"><span data-stu-id="08720-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="08720-110">Znak ukośnika odwrotnego ( \\ ) jest używany do kodowania niektórych znaków specjalnych.</span><span class="sxs-lookup"><span data-stu-id="08720-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="08720-111">Ukośnik odwrotny i następny znak razem są określane jako *sekwencji unikowej*.</span><span class="sxs-lookup"><span data-stu-id="08720-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="08720-112">Obsługiwane w sekwencjach specjalnych F# literały ciągów są wyświetlane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="08720-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="08720-113">Znak</span><span class="sxs-lookup"><span data-stu-id="08720-113">Character</span></span>|<span data-ttu-id="08720-114">Sekwencja unikowa</span><span class="sxs-lookup"><span data-stu-id="08720-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="08720-115">Backspace</span><span class="sxs-lookup"><span data-stu-id="08720-115">Backspace</span></span>|`\b`|
|<span data-ttu-id="08720-116">nowy wiersz</span><span class="sxs-lookup"><span data-stu-id="08720-116">Newline</span></span>|`\n`|
|<span data-ttu-id="08720-117">Powrót karetki</span><span class="sxs-lookup"><span data-stu-id="08720-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="08720-118">Tab</span><span class="sxs-lookup"><span data-stu-id="08720-118">Tab</span></span>|`\t`|
|<span data-ttu-id="08720-119">Ukośnik odwrotny</span><span class="sxs-lookup"><span data-stu-id="08720-119">Backslash</span></span>|`\\`|
|<span data-ttu-id="08720-120">Znak cudzysłowu</span><span class="sxs-lookup"><span data-stu-id="08720-120">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="08720-121">Apostrof</span><span class="sxs-lookup"><span data-stu-id="08720-121">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="08720-122">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="08720-122">Unicode character</span></span>|<span data-ttu-id="08720-123">`\uXXXX` lub `\UXXXX` (gdzie `X` wskazuje cyfra szesnastkowa)</span><span class="sxs-lookup"><span data-stu-id="08720-123">`\uXXXX` or `\UXXXX` (where `X` indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="08720-124">Jeśli poprzedzone symbolem @ literał jest ciąg verbatim.</span><span class="sxs-lookup"><span data-stu-id="08720-124">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="08720-125">Oznacza to, że wszelkie sekwencje ucieczki są ignorowane, z tą różnicą, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="08720-125">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="08720-126">Ponadto ciąg mogą być ujęte w cudzysłowy Potrójna.</span><span class="sxs-lookup"><span data-stu-id="08720-126">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="08720-127">W takim przypadku wszystkie sekwencje ucieczki są ignorowane, w tym znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="08720-127">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="08720-128">Aby określić ciąg, który zawiera osadzony jako ciąg, możesz użyć ciąg verbatim lub ciąg potrójnych cudzysłowach.</span><span class="sxs-lookup"><span data-stu-id="08720-128">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="08720-129">Jeśli używasz ciąg verbatim, należy określić dwa znaki cudzysłowu do wskazania znak pojedynczego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="08720-129">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="08720-130">Użycie ciągu potrójnych cudzysłowach, można użyć znaków pojedynczego cudzysłowu, bez nich przeanalizowany jako końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="08720-130">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="08720-131">Ta technika może być przydatne podczas pracy z XML lub innych struktur, które zawierają osadzone znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="08720-131">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="08720-132">W kodzie ciągów zawierających podziały wierszy są akceptowane i podziałów wiersza są interpretowane dosłownie jako tabulacji, chyba że znak ukośnika odwrotnego jest ostatni znak przed podziału wiersza.</span><span class="sxs-lookup"><span data-stu-id="08720-132">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="08720-133">Spacja wiodąca w następnym wierszu jest ignorowana, gdy jest używany znak ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="08720-133">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="08720-134">Poniższy kod tworzy ciąg `str1` wartością `"abc\ndef"` i ciąg `str2` wartością `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="08720-134">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="08720-135">Można uzyskać dostęp do poszczególnych znaków w ciągu za pomocą składni tablicy w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="08720-135">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="08720-136">Dane wyjściowe są `b`.</span><span class="sxs-lookup"><span data-stu-id="08720-136">The output is `b`.</span></span>

<span data-ttu-id="08720-137">Lub wyodrębnić podciągi przy użyciu składni wycinek tablicy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="08720-137">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="08720-138">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="08720-138">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="08720-139">Ciągi ASCII mogą być reprezentowane przez tablice bajtów bez znaku, wpisz `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="08720-139">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="08720-140">Dodaj sufiks `B` z ciągiem literału, aby wskazać, że ciąg ASCII.</span><span class="sxs-lookup"><span data-stu-id="08720-140">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="08720-141">Literały ciągów znaków ASCII używany z tablic bajtowych obsługują ten sam sekwencje ucieczki jako ciągi znaków Unicode, z wyjątkiem sekwencje unikowe Unicode.</span><span class="sxs-lookup"><span data-stu-id="08720-141">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="08720-142">Operatory ciągów</span><span class="sxs-lookup"><span data-stu-id="08720-142">String Operators</span></span>

<span data-ttu-id="08720-143">Istnieją dwa sposoby łączenia ciągów: za pomocą `+` operatora lub za pomocą `^` operatora.</span><span class="sxs-lookup"><span data-stu-id="08720-143">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="08720-144">`+` Operator zachowuje zgodność z obsługi funkcji ciągów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08720-144">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="08720-145">Poniższy przykład ilustruje ciągów.</span><span class="sxs-lookup"><span data-stu-id="08720-145">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="08720-146">Klasa String</span><span class="sxs-lookup"><span data-stu-id="08720-146">String Class</span></span>

<span data-ttu-id="08720-147">Ponieważ wpisać ciąg F# jest faktycznie .NET Framework `System.String` wpisz wszystkie `System.String` składowe są dostępne.</span><span class="sxs-lookup"><span data-stu-id="08720-147">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="08720-148">Obejmuje to `+` operatora, który jest używany do łączenia ciągów, `Length` właściwości i `Chars` właściwość, która zwraca ciąg w postaci tablicy znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="08720-148">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="08720-149">Aby uzyskać więcej informacji na temat ciągów, zobacz `System.String`.</span><span class="sxs-lookup"><span data-stu-id="08720-149">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="08720-150">Za pomocą `Chars` właściwość `System.String`, dostęp do poszczególnych znaków w ciągu, określając indeksu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="08720-150">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="08720-151">Parametry modułu</span><span class="sxs-lookup"><span data-stu-id="08720-151">String Module</span></span>

<span data-ttu-id="08720-152">Dodatkowe funkcje obsługi ciągu znajduje się w `String` modułu w `FSharp.Core` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="08720-152">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="08720-153">Aby uzyskać więcej informacji, zobacz [Core.String — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="08720-153">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="08720-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08720-154">See also</span></span>

- [<span data-ttu-id="08720-155">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="08720-155">F# Language Reference</span></span>](index.md)