---
title: Wprowadzenie do kodowania znaków w programie .NET
description: Informacje o kodowaniu i dekodowanie znaków w programie .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 1b6ec6a7275408d4a8061c0de92cdf6e82dd533a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288046"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="fdd39-103">Kodowanie znaków na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="fdd39-103">Character encoding in .NET</span></span>

<span data-ttu-id="fdd39-104">Ten artykuł zawiera wprowadzenie do systemów kodowania znaków, które są używane przez platformę .NET.</span><span class="sxs-lookup"><span data-stu-id="fdd39-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="fdd39-105">W tym artykule wyjaśniono <xref:System.String> , jak,, <xref:System.Char> <xref:System.Text.Rune> i <xref:System.Globalization.StringInfo> typy działają z Unicode, UTF-16 i UTF-8.</span><span class="sxs-lookup"><span data-stu-id="fdd39-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="fdd39-106">Ten *znak* jest używany w tym miejscu w ogólnym sensie, *co czytnik jest postrzegany jako pojedynczy element wyświetlania*.</span><span class="sxs-lookup"><span data-stu-id="fdd39-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="fdd39-107">Typowe przykłady to litera "a", symbol "@" i Emoji " 🐂 ".</span><span class="sxs-lookup"><span data-stu-id="fdd39-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="fdd39-108">Czasami wygląda na to, że jeden znak jest w rzeczywistości składający się z wielu niezależnych elementów wyświetlanych, ponieważ sekcja w [klastrach Grapheme](#grapheme-clusters) objaśnia.</span><span class="sxs-lookup"><span data-stu-id="fdd39-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="fdd39-109">stringTypy i char</span><span class="sxs-lookup"><span data-stu-id="fdd39-109">The string and char types</span></span>

<span data-ttu-id="fdd39-110">Wystąpienie [string](xref:System.String) klasy reprezentuje jakiś tekst.</span><span class="sxs-lookup"><span data-stu-id="fdd39-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="fdd39-111">A `string` jest logicznie sekwencją wartości 16-bitowych, z których każdy jest wystąpieniem [char](xref:System.Char) struktury.</span><span class="sxs-lookup"><span data-stu-id="fdd39-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="fdd39-112">[ string . Właściwość length](xref:System.String.Length) zwraca liczbę `char` wystąpień w `string` wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="fdd39-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="fdd39-113">Poniższa funkcja Przykładowa drukuje wartości w notacji szesnastkowej wszystkich `char` wystąpień w `string` :</span><span class="sxs-lookup"><span data-stu-id="fdd39-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="fdd39-114">Przekaż string "Hello" do tej funkcji i uzyskasz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="fdd39-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

<span data-ttu-id="fdd39-115">Każdy znak jest reprezentowany przez pojedynczą `char` wartość.</span><span class="sxs-lookup"><span data-stu-id="fdd39-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="fdd39-116">Ten wzorzec ma wartość true w przypadku większości języków świata.</span><span class="sxs-lookup"><span data-stu-id="fdd39-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="fdd39-117">Na przykład poniżej przedstawiono dane wyjściowe dla dwóch znaków chińskich, takich jak *nǐ hǎo* i średnia *Hello*:</span><span class="sxs-lookup"><span data-stu-id="fdd39-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="fdd39-118">Jednak w przypadku niektórych języków i dla niektórych symboli i Emoji `char` do reprezentowania pojedynczego znaku przyjmuje się dwa wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fdd39-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="fdd39-119">Na przykład Porównaj znaki i `char` wystąpienia w wyrazie oznaczające *Osage* w języku Osage:</span><span class="sxs-lookup"><span data-stu-id="fdd39-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

<span data-ttu-id="fdd39-120">W poprzednim przykładzie każdy znak z wyjątkiem miejsca jest reprezentowany przez dwa `char` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fdd39-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="fdd39-121">Pojedynczy emoji Unicode jest również reprezentowany przez dwa `char` s, jak pokazano w poniższym przykładzie pokazujący OX-emoji:</span><span class="sxs-lookup"><span data-stu-id="fdd39-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="fdd39-122">Te przykłady pokazują, że wartość `string.Length` , która wskazuje liczbę `char` wystąpień, nie musi wskazywać liczby wyświetlanych znaków.</span><span class="sxs-lookup"><span data-stu-id="fdd39-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="fdd39-123">Pojedyncze `char` wystąpienie przez siebie nie musi reprezentować znaku.</span><span class="sxs-lookup"><span data-stu-id="fdd39-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="fdd39-124">`char`Pary, które są mapowane na pojedynczy znak, są nazywane *parami surogatów*.</span><span class="sxs-lookup"><span data-stu-id="fdd39-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="fdd39-125">Aby zrozumieć, jak działają, należy zrozumieć kodowanie Unicode i UTF-16.</span><span class="sxs-lookup"><span data-stu-id="fdd39-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="fdd39-126">Punkty kodu Unicode</span><span class="sxs-lookup"><span data-stu-id="fdd39-126">Unicode code points</span></span>

<span data-ttu-id="fdd39-127">Unicode jest międzynarodowym standardem kodowania do użycia na różnych platformach i w różnych językach i skryptach.</span><span class="sxs-lookup"><span data-stu-id="fdd39-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="fdd39-128">Standard Unicode definiuje ponad 1 100 000 [punktów kodów](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="fdd39-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="fdd39-129">Punkt kodu jest wartością całkowitą, która może być z zakresu od 0 do `U+10FFFF` (dziesiętne 1 114 111).</span><span class="sxs-lookup"><span data-stu-id="fdd39-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="fdd39-130">Niektóre punkty kodu są przypisywane do liter, symboli lub emoji.</span><span class="sxs-lookup"><span data-stu-id="fdd39-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="fdd39-131">Inne są przypisane do akcji kontrolujących sposób wyświetlania tekstu lub znaków, na przykład z wyprzedzeniem do nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="fdd39-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="fdd39-132">Wiele punktów kodowych nie jest jeszcze przypisanych.</span><span class="sxs-lookup"><span data-stu-id="fdd39-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="fdd39-133">Poniżej przedstawiono kilka przykładów przypisań punktów kodu z linkami do wykresów Unicode, w których są one wyświetlane:</span><span class="sxs-lookup"><span data-stu-id="fdd39-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="fdd39-134">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="fdd39-134">Decimal</span></span>|<span data-ttu-id="fdd39-135">Hex</span><span class="sxs-lookup"><span data-stu-id="fdd39-135">Hex</span></span>       |<span data-ttu-id="fdd39-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="fdd39-136">Example</span></span>|<span data-ttu-id="fdd39-137">Opis</span><span class="sxs-lookup"><span data-stu-id="fdd39-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="fdd39-138">10</span><span class="sxs-lookup"><span data-stu-id="fdd39-138">10</span></span>     | `U+000A` |<span data-ttu-id="fdd39-139">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="fdd39-139">N/A</span></span>| [<span data-ttu-id="fdd39-140">KANAŁ INFORMACYJNY WIERSZA</span><span class="sxs-lookup"><span data-stu-id="fdd39-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="fdd39-141">65</span><span class="sxs-lookup"><span data-stu-id="fdd39-141">65</span></span>     | `U+0061` | <span data-ttu-id="fdd39-142">a</span><span class="sxs-lookup"><span data-stu-id="fdd39-142">a</span></span> | [<span data-ttu-id="fdd39-143">MAŁA LITERA A</span><span class="sxs-lookup"><span data-stu-id="fdd39-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="fdd39-144">562</span><span class="sxs-lookup"><span data-stu-id="fdd39-144">562</span></span>    | `U+0232` | <span data-ttu-id="fdd39-145">Ȳ</span><span class="sxs-lookup"><span data-stu-id="fdd39-145">Ȳ</span></span> | [<span data-ttu-id="fdd39-146">WIELKA LITERA Y Z MACRON</span><span class="sxs-lookup"><span data-stu-id="fdd39-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="fdd39-147">68 675</span><span class="sxs-lookup"><span data-stu-id="fdd39-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="fdd39-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="fdd39-148">𐱃</span></span> | [<span data-ttu-id="fdd39-149">STARY TURKIC LETTER ORKHON NA</span><span class="sxs-lookup"><span data-stu-id="fdd39-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="fdd39-150">127 801</span><span class="sxs-lookup"><span data-stu-id="fdd39-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="fdd39-151">🌹</span><span class="sxs-lookup"><span data-stu-id="fdd39-151">🌹</span></span> | [<span data-ttu-id="fdd39-152">RÓŻAny emoji</span><span class="sxs-lookup"><span data-stu-id="fdd39-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="fdd39-153">Punkty kodu są zwykle określane przy użyciu składni `U+xxxx` , gdzie `xxxx` jest wartością całkowitą zakodowaną szesnastkowo.</span><span class="sxs-lookup"><span data-stu-id="fdd39-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="fdd39-154">W całym zakresie punktów kodu istnieją dwa podzakresy:</span><span class="sxs-lookup"><span data-stu-id="fdd39-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="fdd39-155">**Podstawowa płaszczyzna wielojęzyczna (BMP)** w zakresie `U+0000..U+FFFF` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="fdd39-156">Ten 16-bitowy zakres zapewnia 65 536 punktów kodów, wystarczających do pokrycia większości systemów pisania na świecie.</span><span class="sxs-lookup"><span data-stu-id="fdd39-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="fdd39-157">**Dodatkowe punkty kodu** z zakresu `U+10000..U+10FFFF` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="fdd39-158">Ten 21-bitowy zakres oferuje ponad milion dodatkowych punktów kodu, które mogą być używane dla mniej dobrze znanych języków i innych celów, takich jak emoji.</span><span class="sxs-lookup"><span data-stu-id="fdd39-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="fdd39-159">Na poniższym diagramie przedstawiono relację między BMP i dodatkowymi punktami kodu.</span><span class="sxs-lookup"><span data-stu-id="fdd39-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP i dodatkowe punkty kodów":::

## <a name="utf-16-code-units"></a><span data-ttu-id="fdd39-161">Jednostki kodu UTF-16</span><span class="sxs-lookup"><span data-stu-id="fdd39-161">UTF-16 code units</span></span>

<span data-ttu-id="fdd39-162">16-bitowy format transformacji Unicode ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) to system kodowania znaków, który używa 16-bitowych *jednostek kodu* do reprezentowania punktów kodu Unicode.</span><span class="sxs-lookup"><span data-stu-id="fdd39-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="fdd39-163">.NET używa kodowania UTF-16, aby zakodować tekst w `string` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="fdd39-164">`char`Wystąpienie reprezentuje jednostkę kodu 16-bitowego.</span><span class="sxs-lookup"><span data-stu-id="fdd39-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="fdd39-165">Pojedyncza jednostka kodowa 16-bitowa może reprezentować dowolny punkt kodu w 16-bitowym zakresie podstawowej płaszczyzny wielojęzycznej.</span><span class="sxs-lookup"><span data-stu-id="fdd39-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="fdd39-166">Jednak w przypadku punktu kodu w dodatkowych zakresach `char` są potrzeby dwa wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fdd39-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="fdd39-167">Pary zastępcze</span><span class="sxs-lookup"><span data-stu-id="fdd39-167">Surrogate pairs</span></span>

<span data-ttu-id="fdd39-168">Tłumaczenie wartości 2 16-bitowych na pojedynczą wartość 21-bitową jest obsługiwane przez specjalny zakres nazywany *surogatami punktów kodu*od `U+D800` do `U+DFFF` (dziesiętne 55 296 do 57 343) włącznie.</span><span class="sxs-lookup"><span data-stu-id="fdd39-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="fdd39-169">Na poniższym diagramie przedstawiono relację między kodem BMP i surogatem.</span><span class="sxs-lookup"><span data-stu-id="fdd39-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP i Surogat — punkty kodu":::

<span data-ttu-id="fdd39-171">Gdy do *górnego* punktu kodowego ( `U+D800..U+DBFF` ) bezpośrednio następuje *dolny* punkt kodowy ( `U+DC00..U+DFFF` ), para jest interpretowana jako dodatkowy punkt kodu przy użyciu następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="fdd39-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="fdd39-172">W tej samej formule jest używana notacja dziesiętna:</span><span class="sxs-lookup"><span data-stu-id="fdd39-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="fdd39-173">*Górny* punkt kodu wieloskładnikowego nie ma wyższej wartości liczbowej niż *dolny* punkt kodowy.</span><span class="sxs-lookup"><span data-stu-id="fdd39-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="fdd39-174">Górny punkt kodowy jest nazywany "wysoki", ponieważ jest używany do obliczania wyższej liczby 11 bitów pełnego zakresu kodów 21-bitowego.</span><span class="sxs-lookup"><span data-stu-id="fdd39-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="fdd39-175">Dolny punkt kodowy jest używany do obliczania 10 bitów o mniejszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="fdd39-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="fdd39-176">Na przykład rzeczywisty punkt kodu, który odnosi się do pary zastępczej `0xD83C` i `0xDF39` jest obliczany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="fdd39-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="fdd39-177">To samo obliczenie przy użyciu notacji dziesiętnej:</span><span class="sxs-lookup"><span data-stu-id="fdd39-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="fdd39-178">Powyższy przykład pokazuje, że `"\ud83c\udf39"` jest kodowanie UTF-16 `U+1F339 ROSE ('🌹')` powyżej wymienionego powyżej.</span><span class="sxs-lookup"><span data-stu-id="fdd39-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="fdd39-179">Wartości skalarne Unicode</span><span class="sxs-lookup"><span data-stu-id="fdd39-179">Unicode scalar values</span></span>

<span data-ttu-id="fdd39-180">Wyrażenie " [wartość skalarna Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) " odnosi się do wszystkich punktów kodu innych niż punkty zastępcze kodu.</span><span class="sxs-lookup"><span data-stu-id="fdd39-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="fdd39-181">Innymi słowy, wartość skalarna to dowolny punkt kodu, do którego przypisano znak lub można przypisać znak w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="fdd39-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="fdd39-182">"Znak" odnosi się do wszystkich elementów, które można przypisać do punktu kodu, co obejmuje takie czynności jak akcje kontrolujące sposób wyświetlania tekstu lub znaków.</span><span class="sxs-lookup"><span data-stu-id="fdd39-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="fdd39-183">Na poniższym diagramie przedstawiono punkty kodów wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="fdd39-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Wartości skalarne":::

### <a name="the-rune-type-as-a-scalar-value"></a><span data-ttu-id="fdd39-185">RuneTyp jako wartość skalarną</span><span class="sxs-lookup"><span data-stu-id="fdd39-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="fdd39-186">Począwszy od platformy .NET Core 3,0, <xref:System.Text.Rune?displayProperty=fullName> Typ reprezentuje wartość skalarną Unicode.</span><span class="sxs-lookup"><span data-stu-id="fdd39-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="fdd39-187">**`Rune`Program nie jest dostępny w programie .NET Core 2. x lub .NET Framework 4. x.**</span><span class="sxs-lookup"><span data-stu-id="fdd39-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="fdd39-188">`Rune`Konstruktory weryfikują, że wystąpienie wyniku jest prawidłową wartością skalarną Unicode, w przeciwnym razie zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="fdd39-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="fdd39-189">Poniższy przykład pokazuje kod, który pomyślnie tworzy wystąpienia `Rune` wystąpień, ponieważ dane wejściowe reprezentują prawidłowe wartości skalarne:</span><span class="sxs-lookup"><span data-stu-id="fdd39-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="fdd39-190">Poniższy przykład zgłasza wyjątek, ponieważ punkt kodu znajduje się w zakresie surogatu i nie jest częścią pary dwuskładnikowej:</span><span class="sxs-lookup"><span data-stu-id="fdd39-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="fdd39-191">Poniższy przykład zgłasza wyjątek, ponieważ punkt kodu znajduje się poza dodatkowym zakresem:</span><span class="sxs-lookup"><span data-stu-id="fdd39-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="rune-usage-example-changing-letter-case"></a>Rune<span data-ttu-id="fdd39-192">przykład użycia: zmiana wielkości liter</span><span class="sxs-lookup"><span data-stu-id="fdd39-192"> usage example: changing letter case</span></span>

<span data-ttu-id="fdd39-193">Interfejs API, który przyjmuje `char` i zakłada, że pracuje z punktem kodu, który jest wartością skalarną, nie działa poprawnie, jeśli `char` pochodzi z pary zastępczej.</span><span class="sxs-lookup"><span data-stu-id="fdd39-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="fdd39-194">Rozważmy na przykład następującą metodę, która wywołuje <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> na każdym z char string :</span><span class="sxs-lookup"><span data-stu-id="fdd39-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="fdd39-195">Jeśli `input` string zawiera małą literę Deseret `er` ( `𐑉` ), ten kod nie przekonwertuje go na wielkie litery ( `𐐡` ).</span><span class="sxs-lookup"><span data-stu-id="fdd39-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="fdd39-196">Kod jest wywoływany `char.ToUpperInvariant` oddzielnie w każdym punkcie kodu zastępczego `U+D801` i `U+DC49` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="fdd39-197">Ale `U+D801` nie ma wystarczających informacji, aby zidentyfikować je jako małą literę, więc `char.ToUpperInvariant` pozostawia ją samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="fdd39-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="fdd39-198">Obsługuje to ten `U+DC49` sam sposób.</span><span class="sxs-lookup"><span data-stu-id="fdd39-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="fdd39-199">Wynikiem jest to, że małe litery "𐑉" w `input` string nie są konwertowane na wielkie litery "𐑉".</span><span class="sxs-lookup"><span data-stu-id="fdd39-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="fdd39-200">Poniżej przedstawiono dwie opcje prawidłowej konwersji string na wielkie litery:</span><span class="sxs-lookup"><span data-stu-id="fdd39-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="fdd39-201">Wywołania <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> na wejściu string zamiast Iterowanie `char` przez- `char` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="fdd39-202">`string.ToUpperInvariant`Metoda ma dostęp do obu części każdej pary surogatów, więc może prawidłowo obsługiwać wszystkie punkty kodu Unicode.</span><span class="sxs-lookup"><span data-stu-id="fdd39-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="fdd39-203">Wykonaj iterację przez wartości skalarne Unicode jako `Rune` wystąpienia `char` , a nie wystąpienia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fdd39-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="fdd39-204">Ponieważ `Rune` wystąpienie jest prawidłową wartością skalarną Unicode, można je przesłać do interfejsów API, które oczekują na wartość skalarną.</span><span class="sxs-lookup"><span data-stu-id="fdd39-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="fdd39-205">Na przykład wywoływanie, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> jak pokazano w poniższym przykładzie, daje poprawne wyniki:</span><span class="sxs-lookup"><span data-stu-id="fdd39-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-rune-apis"></a><span data-ttu-id="fdd39-206">Inne Rune interfejsy API</span><span class="sxs-lookup"><span data-stu-id="fdd39-206">Other Rune APIs</span></span>

<span data-ttu-id="fdd39-207">`Rune`Typ uwidacznia analogowe wiele `char` interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="fdd39-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="fdd39-208">Na przykład następujące metody dublowania statycznych interfejsów API w `char` typie:</span><span class="sxs-lookup"><span data-stu-id="fdd39-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="fdd39-209">Aby pobrać nieprzetworzoną wartość skalarną z `Rune` wystąpienia, użyj <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fdd39-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="fdd39-210">Aby skonwertować `Rune` wystąpienie z powrotem do sekwencji `char` s, użyj <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> metody lub.</span><span class="sxs-lookup"><span data-stu-id="fdd39-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="fdd39-211">Ponieważ każda wartość skalarna Unicode jest możliwa do zaprezentowania przez pojedynczą `char` lub dwuskładnikową parę, każde `Rune` wystąpienie może być reprezentowane przez co najwyżej 2 `char` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fdd39-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="fdd39-212">Użyj <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> , aby zobaczyć, ile `char` wystąpień jest wymaganych do reprezentowania `Rune` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fdd39-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="fdd39-213">Aby uzyskać więcej informacji na temat `Rune` typu .NET, zobacz [ `Rune` Dokumentacja interfejsu API](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="fdd39-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="fdd39-214">Klastry Grapheme</span><span class="sxs-lookup"><span data-stu-id="fdd39-214">Grapheme clusters</span></span>

<span data-ttu-id="fdd39-215">Wygląda na to, że jeden znak może wynikać z kombinacji wielu punktów kodowych, więc bardziej opisowy termin, który jest często używany zamiast "Character", to [Grapheme klastra](https://www.unicode.org/glossary/#grapheme_cluster).</span><span class="sxs-lookup"><span data-stu-id="fdd39-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="fdd39-216">Odpowiedni termin w programie .NET to [element tekstowy](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="fdd39-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="fdd39-217">Rozważ `string` wystąpienia "a", "o".</span><span class="sxs-lookup"><span data-stu-id="fdd39-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="fdd39-218">"i" `👩🏽‍🚒` ".</span><span class="sxs-lookup"><span data-stu-id="fdd39-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="fdd39-219">Jeśli system operacyjny obsługuje je zgodnie z definicją standardu Unicode, każde z tych `string` wystąpień jest wyświetlane jako pojedynczy element tekstowy lub klaster Grapheme.</span><span class="sxs-lookup"><span data-stu-id="fdd39-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="fdd39-220">Jednak ostatnie dwa są reprezentowane przez więcej niż jeden punkt kodu wartości skalarnej.</span><span class="sxs-lookup"><span data-stu-id="fdd39-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="fdd39-221">string"A" jest reprezentowane przez jedną wartość skalarną i zawiera jedno `char` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="fdd39-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="fdd39-222">"I" string jest reprezentowane przez jedną wartość skalarną i zawiera jedno `char` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="fdd39-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="fdd39-223">string"A" wygląda tak samo jak "", ale jest reprezentowane przez dwie wartości skalarne i zawiera dwa `char` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fdd39-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="fdd39-224">Na koniec string " `👩🏽‍🚒` " jest reprezentowane przez cztery wartości skalarne i zawiera siedem `char` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="fdd39-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="fdd39-225">`U+1F469 WOMAN`(zakres dodatkowy, wymaga pary dwuskładnikowej)</span><span class="sxs-lookup"><span data-stu-id="fdd39-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="fdd39-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(zakres dodatkowy, wymaga pary dwuskładnikowej)</span><span class="sxs-lookup"><span data-stu-id="fdd39-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="fdd39-227">`U+1F692 FIRE ENGINE`(zakres dodatkowy, wymaga pary dwuskładnikowej)</span><span class="sxs-lookup"><span data-stu-id="fdd39-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="fdd39-228">W niektórych z powyższych przykładów — takich jak modyfikator łączenia akcentu lub modyfikator odcienia skórki — punkt kodu nie jest wyświetlany jako element autonomiczny na ekranie.</span><span class="sxs-lookup"><span data-stu-id="fdd39-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="fdd39-229">Zamiast tego służy do modyfikowania wyglądu elementu tekstowego, który został wcześniej dołączony.</span><span class="sxs-lookup"><span data-stu-id="fdd39-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="fdd39-230">Te przykłady pokazują, że może przyjmować wiele wartości skalarnych, aby określić, co myślisz jako pojedynczy "znak" lub "klaster Grapheme".</span><span class="sxs-lookup"><span data-stu-id="fdd39-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="fdd39-231">Aby wyliczyć klastry Grapheme z `string` , należy użyć <xref:System.Globalization.StringInfo> klasy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fdd39-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="fdd39-232">Jeśli znasz język SWIFT, `StringInfo` Typ .NET jest koncepcyjnie podobny do [ `character` typu SWIFT](https://developer.apple.com/documentation/swift/character).</span><span class="sxs-lookup"><span data-stu-id="fdd39-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-char-rune-and-text-element-instances"></a><span data-ttu-id="fdd39-233">Przykład: liczba char , Rune i wystąpienia elementu tekstowego</span><span class="sxs-lookup"><span data-stu-id="fdd39-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="fdd39-234">W interfejsach API platformy .NET klaster Grapheme jest nazywany *elementem tekstowym*.</span><span class="sxs-lookup"><span data-stu-id="fdd39-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="fdd39-235">Poniższa metoda pokazuje różnice między elementami `char` , `Rune` i wystąpieniami elementów tekstu w `string` :</span><span class="sxs-lookup"><span data-stu-id="fdd39-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="fdd39-236">W przypadku uruchomienia tego kodu w .NET Framework lub .NET Core 3,1 lub starszym liczba elementów tekstowych dla znaku emoji zostanie wyświetlona `4` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="fdd39-237">Jest to spowodowane usterką w `StringInfo` klasie, która została naprawiona w programie .NET 5.</span><span class="sxs-lookup"><span data-stu-id="fdd39-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-string-instances"></a><span data-ttu-id="fdd39-238">Przykład: dzielenie string wystąpień</span><span class="sxs-lookup"><span data-stu-id="fdd39-238">Example: splitting string instances</span></span>

<span data-ttu-id="fdd39-239">Podczas dzielenia `string` wystąpień należy unikać dzielenia pary zastępczych i klastrów Grapheme.</span><span class="sxs-lookup"><span data-stu-id="fdd39-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="fdd39-240">Rozważmy następujący przykład nieprawidłowego kodu, który zamierza wstawiać podziały wierszy co 10 znaków w string :</span><span class="sxs-lookup"><span data-stu-id="fdd39-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="fdd39-241">Ponieważ ten kod wylicza `char` wystąpienia, para dwuskładnikowa, która ma miejsce na obramowanie międzystrefowe, `char` zostanie podzielona i zostanie dodany nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="fdd39-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="fdd39-242">W tym wstawieniu wprowadzono uszkodzenia danych, ponieważ punkty kodu surogatu są istotne tylko jako pary.</span><span class="sxs-lookup"><span data-stu-id="fdd39-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="fdd39-243">Potencjalne uszkodzenie danych nie jest eliminowane w przypadku wyliczania `Rune` wystąpień (wartości skalarnych) zamiast `char` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="fdd39-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="fdd39-244">Zestaw `Rune` wystąpień może utworzyć klaster Grapheme, który ma międzystrefę 10 `char` granic.</span><span class="sxs-lookup"><span data-stu-id="fdd39-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="fdd39-245">Jeśli zestaw klastrów Grapheme jest podzielony, nie można go poprawnie zinterpretować.</span><span class="sxs-lookup"><span data-stu-id="fdd39-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="fdd39-246">Lepszym rozwiązaniem jest przerwanie string przez zliczanie klastrów Grapheme lub elementów tekstowych, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fdd39-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="fdd39-247">Jak wspomniano wcześniej, jednak w implementacjach platformy .NET innej niż .NET 5 `StringInfo` Klasa może nieprawidłowo obsłużyć niektóre klastry Grapheme.</span><span class="sxs-lookup"><span data-stu-id="fdd39-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="fdd39-248">UTF-8 i UTF-32</span><span class="sxs-lookup"><span data-stu-id="fdd39-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="fdd39-249">Poprzednie sekcje skupiające się na kodowaniu UTF-16, ponieważ są używane przez platformę .NET do kodowania `string` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="fdd39-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="fdd39-250">Istnieją inne systemy kodowania dla standardu Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) i [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span><span class="sxs-lookup"><span data-stu-id="fdd39-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="fdd39-251">Te kodowania wykorzystują odpowiednio 8-bitowe jednostki kodu i 32-bitowe jednostki kodu.</span><span class="sxs-lookup"><span data-stu-id="fdd39-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="fdd39-252">Podobnie jak w przypadku UTF-16, UTF-8 wymaga wielu jednostek kodu do reprezentowania niektórych wartości skalarnych Unicode.</span><span class="sxs-lookup"><span data-stu-id="fdd39-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="fdd39-253">Kodowanie UTF-32 może reprezentować dowolną wartość skalarną w jednej jednostce kodu 32-bitowej.</span><span class="sxs-lookup"><span data-stu-id="fdd39-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="fdd39-254">Poniżej przedstawiono kilka przykładów przedstawiających sposób reprezentowania tego samego punktu kodu Unicode w każdym z tych trzech systemów kodowania Unicode:</span><span class="sxs-lookup"><span data-stu-id="fdd39-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

<span data-ttu-id="fdd39-255">Jak wspomniano wcześniej, pojedyncza jednostka kodu UTF-16 z [pary zastępczej](#surrogate-pairs) jest bezproblemowa.</span><span class="sxs-lookup"><span data-stu-id="fdd39-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="fdd39-256">W ten sam sposób pojedyncza jednostka kodu UTF-8 jest bezużyteczne, jeśli jest w sekwencji dwóch, trzech lub czterech używanych do obliczania wartości skalarnej.</span><span class="sxs-lookup"><span data-stu-id="fdd39-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="fdd39-257">Endian</span><span class="sxs-lookup"><span data-stu-id="fdd39-257">Endianness</span></span>

<span data-ttu-id="fdd39-258">W programie .NET jednostki kodu UTF-16 string są przechowywane w ciągłej pamięci jako sekwencja 16-bitowych liczb całkowitych ( `char` wystąpień).</span><span class="sxs-lookup"><span data-stu-id="fdd39-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="fdd39-259">Bity poszczególnych jednostek kodu są ustalane w zależności od liczby [bajtów](https://en.wikipedia.org/wiki/Endianness) bieżącej architektury.</span><span class="sxs-lookup"><span data-stu-id="fdd39-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="fdd39-260">W przypadku architektury little-endian string złożone z punktów kodu UTF-16 `[ D801 DCCC ]` zostałyby ustalone w pamięci jako bajty `[ 0x01, 0xD8, 0xCC, 0xDC ]` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="fdd39-261">W przypadku architektury big-endian string można ją określić w pamięci jako bajty `[ 0xD8, 0x01, 0xDC, 0xCC ]` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="fdd39-262">Systemy komputerowe, które komunikują się ze sobą, muszą wyrazić zgodę na reprezentację danych przekraczających sieć.</span><span class="sxs-lookup"><span data-stu-id="fdd39-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="fdd39-263">Większość protokołów sieciowych używa kodowania UTF-8 jako standard podczas przesyłania tekstu, częściowo, aby uniknąć problemów, które mogą wynikać z komputera z dużą liczbą bajtów, komunikując się z komputerem o małej przepustowości.</span><span class="sxs-lookup"><span data-stu-id="fdd39-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="fdd39-264">stringSkładowe składające się z punktów kodu UTF-8 `[ F0 90 93 8C ]` będą zawsze reprezentowane jako bajty, `[ 0xF0, 0x90, 0x93, 0x8C ]` niezależnie od liczby bajtów.</span><span class="sxs-lookup"><span data-stu-id="fdd39-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="fdd39-265">Aby użyć UTF-8 do przesyłania tekstu, aplikacje .NET często używają kodu, takiego jak Poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="fdd39-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="fdd39-266">W poprzednim przykładzie metoda [Encoding. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) dekoduje kod UTF-16 `string` do serii wartości skalarnych Unicode, a następnie ponownie koduje te wartości skalarne na UTF-8 i umieszcza wyniki sekwencji w `byte` tablicy.</span><span class="sxs-lookup"><span data-stu-id="fdd39-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="fdd39-267">Metoda [Encoding. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) wykonuje odwrotną transformację, konwertując tablicę UTF-8 `byte` na UTF-16 `string` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="fdd39-268">Ponieważ UTF-8 jest commonplace w Internecie, może być skłonny do odczytu nieprzetworzonych bajtów z sieci i do traktowania danych, tak jakby była to UTF-8.</span><span class="sxs-lookup"><span data-stu-id="fdd39-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="fdd39-269">Należy jednak sprawdzić, czy jest on rzeczywiście poprawnie sformułowany.</span><span class="sxs-lookup"><span data-stu-id="fdd39-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="fdd39-270">Złośliwy klient może przesłać do usługi źle sformułowany format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="fdd39-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="fdd39-271">Jeśli te dane są używane w taki sposób, jakby były poprawnie sformułowane, może to spowodować błędy lub luki w zabezpieczeniach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fdd39-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="fdd39-272">Aby sprawdzić poprawność danych UTF-8, można użyć metody takiej jak `Encoding.UTF8.GetString` , która przeprowadza walidację podczas konwertowania danych przychodzących na `string` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="fdd39-273">Poprawnie sformułowane kodowanie</span><span class="sxs-lookup"><span data-stu-id="fdd39-273">Well-formed encoding</span></span>

<span data-ttu-id="fdd39-274">Poprawnie sformułowane kodowanie Unicode to string jednostki kodu, które można zdekodować w sposób niejednoznaczny i bez błędu do sekwencji wartości skalarnych Unicode.</span><span class="sxs-lookup"><span data-stu-id="fdd39-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="fdd39-275">Poprawnie sformułowane dane można transkodować bez ograniczeń i z powrotem między UTF-8, UTF-16 i UTF-32.</span><span class="sxs-lookup"><span data-stu-id="fdd39-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="fdd39-276">Pytanie, czy sekwencja kodowania jest poprawnie sformułowana, czy nie jest niezwiązana z przydziałami architektury maszyny.</span><span class="sxs-lookup"><span data-stu-id="fdd39-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="fdd39-277">Nieprawidłowo sformułowana sekwencja UTF-8 jest źle sformułowana w taki sam sposób na maszynach big-endian i little-endian.</span><span class="sxs-lookup"><span data-stu-id="fdd39-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="fdd39-278">Poniżej przedstawiono kilka przykładów niewłaściwie sformułowanych kodowań:</span><span class="sxs-lookup"><span data-stu-id="fdd39-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="fdd39-279">W UTF-8 sekwencja `[ 6C C2 61 ]` jest źle sformułowana, ponieważ `C2` nie może następować po niej `61` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="fdd39-280">W UTF-16, sekwencja `[ DC00 DD00 ]` (lub, w języku C#, string `"\udc00\udd00"` ) jest źle sformułowana, ponieważ dolny Surogat `DC00` nie może następować po drugim dolnym surogatie `DD00` .</span><span class="sxs-lookup"><span data-stu-id="fdd39-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="fdd39-281">W UTF-32 sekwencja `[ 0011ABCD ]` jest źle sformułowana, ponieważ `0011ABCD` znajduje się poza zakresem wartości skalarnych Unicode.</span><span class="sxs-lookup"><span data-stu-id="fdd39-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="fdd39-282">W programie .NET `string` wystąpienia prawie zawsze zawierają poprawnie sformułowane dane UTF-16, ale nie są one gwarantowane.</span><span class="sxs-lookup"><span data-stu-id="fdd39-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="fdd39-283">W poniższych przykładach pokazano prawidłowy kod w języku C#, który tworzy nieprawidłowo sformułowane dane UTF-16 w `string` wystąpieniach.</span><span class="sxs-lookup"><span data-stu-id="fdd39-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="fdd39-284">Nieprawidłowo sformułowany literał:</span><span class="sxs-lookup"><span data-stu-id="fdd39-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="fdd39-285">Podciąg dzielący parę zastępczą:</span><span class="sxs-lookup"><span data-stu-id="fdd39-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="fdd39-286">Interfejsy API, takie jak [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) nigdy nie zwracają źle sformułowane `string` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fdd39-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="fdd39-287">`Encoding.GetString``Encoding.GetBytes`metody i wykrywają źle sformułowane sekwencje w danych wejściowych i wykonują podstawienie znaków podczas generowania danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fdd39-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="fdd39-288">Jeśli na przykład [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) w danych wejściowych zostanie wyświetlony bajt inny niż ASCII (poza zakresem u + 0000.. u + 007F), wstawiany jest znak "?" w zwracanym `string` wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="fdd39-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="fdd39-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)zamienia źle sformułowane sekwencje UTF-8 z `U+FFFD REPLACEMENT CHARACTER ('�')` w zwracanym `string` wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="fdd39-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="fdd39-290">Aby uzyskać więcej informacji, zobacz [standard Unicode](https://www.unicode.org/versions/latest/), sekcje 5,22 i 3,9.</span><span class="sxs-lookup"><span data-stu-id="fdd39-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="fdd39-291">Wbudowane `Encoding` klasy można również skonfigurować w taki sposób, aby zgłaszać wyjątek, a nie wykonywać podstawienia znaków, gdy widoczne są źle sformułowane sekwencje.</span><span class="sxs-lookup"><span data-stu-id="fdd39-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="fdd39-292">Takie podejście jest często stosowane w aplikacjach z uwzględnieniem zabezpieczeń, w których podstawienie znaków może nie być akceptowalne.</span><span class="sxs-lookup"><span data-stu-id="fdd39-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="fdd39-293">Aby uzyskać informacje o sposobach korzystania z wbudowanych `Encoding` klas, zobacz [jak używać klas kodowania znaków w programie .NET](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="fdd39-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fdd39-294">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdd39-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="fdd39-295">Globalizacja i lokalizacja</span><span class="sxs-lookup"><span data-stu-id="fdd39-295">Globalization and Localization</span></span>](../globalization-localization/index.md)
