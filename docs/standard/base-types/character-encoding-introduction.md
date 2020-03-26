---
title: Wprowadzenie do kodowania znaków w .NET
description: Dowiedz się więcej o kodowaniu i dekodowaniu znaków w .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 34b1577f8bcea80c1f41b6f9605bf47d132fdb4f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134445"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="e7ee1-103">Kodowanie znaków w .NET</span><span class="sxs-lookup"><span data-stu-id="e7ee1-103">Character encoding in .NET</span></span>

<span data-ttu-id="e7ee1-104">Ten artykuł zawiera wprowadzenie do systemów kodowania znaków, które są używane przez .NET.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="e7ee1-105">W artykule <xref:System.String>wyjaśniono, jak , <xref:System.Char>, <xref:System.Text.Rune>i <xref:System.Globalization.StringInfo> typy działają z Unicode, UTF-16 i UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="e7ee1-106">Termin *znak* jest używany tutaj w ogólnym znaczeniu *tego, co czytelnik postrzega jako pojedynczy element wyświetlania*.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="e7ee1-107">Typowymi przykładami są litera "a", symbol "@" i emoji " ".🐂</span><span class="sxs-lookup"><span data-stu-id="e7ee1-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="e7ee1-108">Czasami to, co wygląda jak jeden znak, składa się z wielu niezależnych elementów wyświetlania, jak wyjaśnia sekcja na [klastrach grafem.](#grapheme-clusters)</span><span class="sxs-lookup"><span data-stu-id="e7ee1-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="e7ee1-109">Typy ciągów i znaków</span><span class="sxs-lookup"><span data-stu-id="e7ee1-109">The string and char types</span></span>

<span data-ttu-id="e7ee1-110">Wystąpienie klasy [string](xref:System.String) reprezentuje jakiś tekst.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="e7ee1-111">A `string` jest logicznie sekwencji wartości 16-bitowych, z których każdy jest wystąpieniem struktury [char.](xref:System.Char)</span><span class="sxs-lookup"><span data-stu-id="e7ee1-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="e7ee1-112">[Ciąg. Właściwość Length](xref:System.String.Length) zwraca `char` liczbę wystąpień w wystąpieniu. `string`</span><span class="sxs-lookup"><span data-stu-id="e7ee1-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="e7ee1-113">Następująca funkcja przykładu drukuje wartości w notacji szesnastkowej `char` `string`wszystkich wystąpień w:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="e7ee1-114">Przekaż ciąg "Hello" do tej funkcji i otrzymasz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

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

<span data-ttu-id="e7ee1-115">Każdy znak jest reprezentowany `char` przez jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="e7ee1-116">Ten wzorzec odnosi się do większości języków świata.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="e7ee1-117">Na przykład, oto dane wyjściowe dla dwóch chińskich znaków, które brzmią jak *n ho* i oznaczają *Hello:*</span><span class="sxs-lookup"><span data-stu-id="e7ee1-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="e7ee1-118">Jednak w przypadku niektórych języków oraz dla niektórych `char` symboli i emotikonów potrzeba dwóch wystąpień, aby reprezentować pojedynczy znak.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="e7ee1-119">Na przykład porównaj `char` znaki i wystąpienia w słowie, co oznacza *Osage* w języku Osage:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

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

<span data-ttu-id="e7ee1-120">W poprzednim przykładzie każdy znak z wyjątkiem spacji jest reprezentowany przez dwa `char` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="e7ee1-121">Pojedynczy emoji Unicode jest również `char`reprezentowany przez dwa s, jak widać w poniższym przykładzie przedstawiającym emotikony wół:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="e7ee1-122">Te przykłady pokazują, `string.Length`że wartość , która `char` wskazuje liczbę wystąpień, niekoniecznie wskazuje liczbę wyświetlanych znaków.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="e7ee1-123">Pojedyncze `char` wystąpienie samo w sobie nie musi reprezentować znaku.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="e7ee1-124">Pary `char` mapowane na pojedynczy znak są nazywane *parami zastępczymi*.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="e7ee1-125">Aby zrozumieć, jak działają, musisz zrozumieć kodowanie Unicode i UTF-16.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="e7ee1-126">Punkty kodu Unicode</span><span class="sxs-lookup"><span data-stu-id="e7ee1-126">Unicode code points</span></span>

<span data-ttu-id="e7ee1-127">Unicode jest międzynarodowym standardem kodowania do użytku na różnych platformach oraz w różnych językach i skryptach.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="e7ee1-128">Standard Unicode definiuje ponad 1,1 miliona [punktów kodu](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="e7ee1-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="e7ee1-129">Punkt kodu jest wartością całkowitą, która może `U+10FFFF` wynosić od 0 do (dziesiętne 1,114,111).</span><span class="sxs-lookup"><span data-stu-id="e7ee1-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="e7ee1-130">Niektóre punkty kodu są przypisywane do liter, symboli lub emotikonów.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="e7ee1-131">Inne są przypisywane do akcji, które kontrolują sposób wyświetlania tekstu lub znaków, takich jak przechodzenie do nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="e7ee1-132">Wiele punktów kodu nie są jeszcze przypisane.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="e7ee1-133">Oto kilka przykładów przypisań punktów kodu z łączami do wykresów Unicode, w których się pojawiają:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="e7ee1-134">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="e7ee1-134">Decimal</span></span>|<span data-ttu-id="e7ee1-135">Hex</span><span class="sxs-lookup"><span data-stu-id="e7ee1-135">Hex</span></span>       |<span data-ttu-id="e7ee1-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7ee1-136">Example</span></span>|<span data-ttu-id="e7ee1-137">Opis</span><span class="sxs-lookup"><span data-stu-id="e7ee1-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="e7ee1-138">10</span><span class="sxs-lookup"><span data-stu-id="e7ee1-138">10</span></span>     | `U+000A` |<span data-ttu-id="e7ee1-139">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="e7ee1-139">N/A</span></span>| [<span data-ttu-id="e7ee1-140">POSUW LINIOWY</span><span class="sxs-lookup"><span data-stu-id="e7ee1-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="e7ee1-141">65</span><span class="sxs-lookup"><span data-stu-id="e7ee1-141">65</span></span>     | `U+0061` | <span data-ttu-id="e7ee1-142">a</span><span class="sxs-lookup"><span data-stu-id="e7ee1-142">a</span></span> | [<span data-ttu-id="e7ee1-143">ŁACIŃSKA MAŁA LITERA A</span><span class="sxs-lookup"><span data-stu-id="e7ee1-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="e7ee1-144">562</span><span class="sxs-lookup"><span data-stu-id="e7ee1-144">562</span></span>    | `U+0232` | <span data-ttu-id="e7ee1-145">z o.o.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-145">Ȳ</span></span> | [<span data-ttu-id="e7ee1-146">WIELKA LITERA Y Z MACRONEM</span><span class="sxs-lookup"><span data-stu-id="e7ee1-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="e7ee1-147">68,675</span><span class="sxs-lookup"><span data-stu-id="e7ee1-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="e7ee1-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="e7ee1-148">𐱃</span></span> | [<span data-ttu-id="e7ee1-149">STARY LIST TURECKI ORKHON W</span><span class="sxs-lookup"><span data-stu-id="e7ee1-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="e7ee1-150">127,801</span><span class="sxs-lookup"><span data-stu-id="e7ee1-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="e7ee1-151">🌹</span><span class="sxs-lookup"><span data-stu-id="e7ee1-151">🌹</span></span> | [<span data-ttu-id="e7ee1-152">RÓŻA emoji</span><span class="sxs-lookup"><span data-stu-id="e7ee1-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="e7ee1-153">Punkty kodu są zwyczajowo określane przy użyciu `U+xxxx`składni , gdzie `xxxx` jest wartością całkowitą zakodowaną przez szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="e7ee1-154">W pełnym zakresie punktów kodu znajdują się dwa podzakresy:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="e7ee1-155">**Podstawowa płaszczyzna wielojęzyczna (BMP)** w zakresie `U+0000..U+FFFF`.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="e7ee1-156">Ten 16-bitowy zakres zapewnia 65 536 punktów kodu, co wystarcza na pokrycie większości światowych systemów pisania.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="e7ee1-157">**Dodatkowe punkty kodu** w `U+10000..U+10FFFF`zakresie .</span><span class="sxs-lookup"><span data-stu-id="e7ee1-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="e7ee1-158">Ten zakres 21-bitowy zapewnia ponad milion dodatkowych punktów kodu, które mogą być używane w mniej znanych językach i innych celach, takich jak emotikony.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="e7ee1-159">Na poniższym diagramie przedstawiono relację między BMP a dodatkowymi punktami kodu.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP i dodatkowe punkty kodowe":::

## <a name="utf-16-code-units"></a><span data-ttu-id="e7ee1-161">Jednostki kodu UTF-16</span><span class="sxs-lookup"><span data-stu-id="e7ee1-161">UTF-16 code units</span></span>

<span data-ttu-id="e7ee1-162">16-bitowy format transformacji Unicode[(UTF-16)](https://www.unicode.org/faq/utf_bom.html#UTF16)to system kodowania znaków, który używa 16-bitowych *jednostek kodu* do reprezentowania punktów kodu Unicode.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="e7ee1-163">Program .NET używa utf-16 do zakodowania tekstu w pliku `string`.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="e7ee1-164">Wystąpienie `char` reprezentuje jednostkę kodu 16-bitowego.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="e7ee1-165">Pojedyncza 16-bitowa jednostka kodu może reprezentować dowolny punkt kodu w 16-bitowym zakresie podstawowej płaszczyzny wielojęzycznej.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="e7ee1-166">Ale dla punktu kodu w zakresie `char` uzupełniającym potrzebne są dwa wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="e7ee1-167">Pary zastępcze</span><span class="sxs-lookup"><span data-stu-id="e7ee1-167">Surrogate pairs</span></span>

<span data-ttu-id="e7ee1-168">Translacja dwóch 16-bitowych wartości na pojedynczą wartość 21-bitową jest ułatwiona `U+D800` `U+DFFF` przez specjalny zakres zwany *punktami kodu zastępczego*, od (dziesiętne 55 296 do 57 343), włącznie.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="e7ee1-169">Na poniższym diagramie przedstawiono relację między BMP i zastępczych punktów kodu.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP i zastępcze punkty kodu":::

<span data-ttu-id="e7ee1-171">Gdy po *wysokim zastępczym* punkcie kodu (`U+D800..U+DBFF`) natychmiast`U+DC00..U+DFFF`następuje niski punkt kodu *zastępczego* ( ), para jest interpretowana jako dodatkowy punkt kodu przy użyciu następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="e7ee1-172">Oto ta sama formuła z notacją dziesiętną:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="e7ee1-173">*Wysoki* punkt kodu zastępczego nie ma wyższej wartości liczbowej niż *niski* punkt kodu zastępczego.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="e7ee1-174">Wysoki punkt kodu zastępczego jest nazywany "wysokim", ponieważ jest używany do obliczania wyższego rzędu 11 bitów pełnego zakresu punktów kodu 21-bitowego.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="e7ee1-175">Niski punkt kodu zastępczego jest używany do obliczania niższego rzędu 10 bitów.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="e7ee1-176">Na przykład rzeczywisty punkt kodu, który `0xD83C` odpowiada `0xDF39` parze zastępczej i jest obliczany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="e7ee1-177">Oto te same obliczenia przy użyciu notacji dziesiętnej:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="e7ee1-178">W poprzednim przykładzie `"\ud83c\udf39"` pokazano, że jest UTF-16 kodowania punktu `U+1F339 ROSE ('🌹')` kodu wspomniano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="e7ee1-179">Wartości skalarne Unicode</span><span class="sxs-lookup"><span data-stu-id="e7ee1-179">Unicode scalar values</span></span>

<span data-ttu-id="e7ee1-180">Termin [Wartość skalarna Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) odnosi się do wszystkich punktów kodu innych niż punkty kodu zastępczego.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="e7ee1-181">Innymi słowy wartość skalarna jest dowolnym punktem kodu, który jest przypisany znak lub może być przypisany znak w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="e7ee1-182">"Znak" odnosi się tutaj do wszystkiego, co można przypisać do punktu kodu, który zawiera takie rzeczy, jak akcje, które kontrolują sposób wyświetlania tekstu lub znaków.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="e7ee1-183">Na poniższym diagramie przedstawiono skalarne punkty kodu wartości.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Wartości skalarne":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a><span data-ttu-id="e7ee1-185">Typ Rune jako wartość skalarna</span><span class="sxs-lookup"><span data-stu-id="e7ee1-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="e7ee1-186">Począwszy od .NET Core 3.0, <xref:System.Text.Rune?displayProperty=fullName> typ reprezentuje wartość skalarną Unicode.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="e7ee1-187">**`Rune`nie jest dostępna w programach .NET Core 2.x lub .NET Framework 4.x.**</span><span class="sxs-lookup"><span data-stu-id="e7ee1-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="e7ee1-188">Konstruktory `Rune` sprawdzają, czy wynikowe wystąpienie jest prawidłową wartością skalarną Unicode, w przeciwnym razie zgłaszają wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="e7ee1-189">Poniższy przykład pokazuje kod, `Rune` który pomyślnie wystąpienia wystąpień, ponieważ dane wejściowe reprezentuje prawidłowe wartości skalarne:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="e7ee1-190">Poniższy przykład zgłasza wyjątek, ponieważ punkt kodu znajduje się w zakresie zastępczym i nie jest częścią pary zastępczej:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="e7ee1-191">Poniższy przykład zgłasza wyjątek, ponieważ punkt kodu wykracza poza zakres uzupełniający:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Rune<span data-ttu-id="e7ee1-192">przykład użycia: zmiana litery</span><span class="sxs-lookup"><span data-stu-id="e7ee1-192"> usage example: changing letter case</span></span>

<span data-ttu-id="e7ee1-193">Interfejs API, `char` który przyjmuje i zakłada, że pracuje z punktem kodu, który `char` jest wartością skalarną, nie działa poprawnie, jeśli jest z pary zastępczej.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="e7ee1-194">Rozważmy na przykład następującą <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> metodę, która wywołuje każdą char w: string</span><span class="sxs-lookup"><span data-stu-id="e7ee1-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="e7ee1-195">`input` string Jeśli zawiera literę Deseret `er` (`𐑉`), ten kod nie konwertuje`𐐡`go na wielkie litery ( ).</span><span class="sxs-lookup"><span data-stu-id="e7ee1-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="e7ee1-196">Kod wywołuje `char.ToUpperInvariant` oddzielnie dla każdego `U+D801` zastępczego punktu kodu i `U+DC49`.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="e7ee1-197">Ale `U+D801` nie ma wystarczającej ilości informacji, aby zidentyfikować je `char.ToUpperInvariant` jako małe litery, więc pozostawia go w spokoju.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="e7ee1-198">I radzi `U+DC49` sobie w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="e7ee1-199">W rezultacie małe litery "♡" w literach `input` string nie są konwertowane na wielkie litery .-."</span><span class="sxs-lookup"><span data-stu-id="e7ee1-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="e7ee1-200">Oto dwie opcje poprawnej string konwersji liter na wielkie litery:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="e7ee1-201"><xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> Wezwiej string dane wejściowe, a nie iteracyjne `char`-by-`char`.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="e7ee1-202">Metoda `string.ToUpperInvariant` ma dostęp do obu części każdej pary zastępczej, dzięki czemu może obsługiwać wszystkie punkty kodu Unicode poprawnie.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="e7ee1-203">Iteracji za pośrednictwem wartości skalarnych Unicode jako `Rune` wystąpień zamiast `char` wystąpień, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="e7ee1-204">Ponieważ `Rune` wystąpienie jest prawidłową wartością skalarną Unicode, może być przekazywana do interfejsów API, które oczekują, że będą działać na wartości skalarnej.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="e7ee1-205">Na przykład <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> wywołanie, jak pokazano w poniższym przykładzie daje poprawne wyniki:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a><span data-ttu-id="e7ee1-206">Inne Rune interfejsy API</span><span class="sxs-lookup"><span data-stu-id="e7ee1-206">Other Rune APIs</span></span>

<span data-ttu-id="e7ee1-207">Typ `Rune` udostępnia analogi wielu interfejsów `char` API.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="e7ee1-208">Na przykład następujące metody dublowania statycznych `char` interfejsów API na typ:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="e7ee1-209">Aby uzyskać surową wartość `Rune` skalarną <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> z wystąpienia, należy użyć właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="e7ee1-210">Aby przekonwertować `Rune` wystąpienie `char`z <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> powrotem <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> do sekwencji s, użyj lub metody.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="e7ee1-211">Ponieważ każda wartość skalarna Unicode `char` jest reprezentowana przez `Rune` parę pojedynczą lub zastępczą, `char` każde wystąpienie może być reprezentowane przez co najwyżej 2 wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="e7ee1-212">Użyj, <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> aby `char` zobaczyć, ile wystąpień `Rune` są wymagane do reprezentowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="e7ee1-213">Aby uzyskać więcej informacji `Rune` na temat typu .NET, zobacz [ `Rune` odwołanie do interfejsu API](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="e7ee1-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="e7ee1-214">Klastry grafeme</span><span class="sxs-lookup"><span data-stu-id="e7ee1-214">Grapheme clusters</span></span>

<span data-ttu-id="e7ee1-215">To, co wygląda jak jeden znak, może wynikać z połączenia wielu punktów kodu, więc bardziej opisowym terminem, który jest często używany zamiast "znaku", jest [klaster grafem](https://www.unicode.org/glossary/#grapheme_cluster).</span><span class="sxs-lookup"><span data-stu-id="e7ee1-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="e7ee1-216">Równoważnym terminem w .NET jest [element tekstowy](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="e7ee1-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="e7ee1-217">Rozważmy `string` wystąpienia "a", "á".</span><span class="sxs-lookup"><span data-stu-id="e7ee1-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="e7ee1-218">"á" i`👩🏽‍🚒`" ".</span><span class="sxs-lookup"><span data-stu-id="e7ee1-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="e7ee1-219">Jeśli system operacyjny obsługuje je zgodnie z normą Unicode, każde z tych `string` wystąpień jest wyświetlane jako pojedynczy element tekstowy lub klaster grafem.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="e7ee1-220">Ale dwa ostatnie są reprezentowane przez więcej niż jeden punkt kodu wartości skalarnej.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="e7ee1-221">"a" string jest reprezentowana przez jedną wartość `char` skalarną i zawiera jedno wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="e7ee1-222">"á" string jest reprezentowana przez jedną wartość `char` skalarną i zawiera jedno wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* <span data-ttu-id="e7ee1-223">string "á" wygląda tak samo jak "á", ale jest reprezentowana `char` przez dwie wartości skalarne i zawiera dwa wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="e7ee1-224">Na koniec string "`👩🏽‍🚒`" jest reprezentowany przez cztery `char` wartości skalarne i zawiera siedem wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="e7ee1-225">`U+1F469 WOMAN`(zakres dodatkowy, wymaga pary zastępczej)</span><span class="sxs-lookup"><span data-stu-id="e7ee1-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="e7ee1-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(zakres dodatkowy, wymaga pary zastępczej)</span><span class="sxs-lookup"><span data-stu-id="e7ee1-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="e7ee1-227">`U+1F692 FIRE ENGINE`(zakres dodatkowy, wymaga pary zastępczej)</span><span class="sxs-lookup"><span data-stu-id="e7ee1-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="e7ee1-228">W niektórych z powyższych przykładów , takich jak modyfikator akcentu łączącego lub modyfikator odcienia karnacji, punkt kodu nie jest wyświetlany jako element autonomiczny na ekranie.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="e7ee1-229">Przeciwnie służy do modyfikowania wyglądu elementu tekstowego, który przyszedł przed nim.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="e7ee1-230">Te przykłady pokazują, że może potrwać wiele wartości skalarnych, aby uzupełnić to, co myślimy o jako pojedynczy "znak" lub "klaster grafeme".</span><span class="sxs-lookup"><span data-stu-id="e7ee1-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="e7ee1-231">Aby wyliczyć klastry grafeme `string`, <xref:System.Globalization.StringInfo> użyj klasy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="e7ee1-232">Jeśli znasz program Swift, typ `StringInfo` .NET jest koncepcyjnie podobny do [ `character` typu Swift.](https://developer.apple.com/documentation/swift/character)</span><span class="sxs-lookup"><span data-stu-id="e7ee1-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a><span data-ttu-id="e7ee1-233">Przykład: charliczba Rune, i wystąpienia elementów tekstowych</span><span class="sxs-lookup"><span data-stu-id="e7ee1-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="e7ee1-234">W interfejsach API platformy .NET klaster grafemowy jest nazywany *elementem tekstowym*.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="e7ee1-235">Poniższa metoda pokazuje różnice `char` `Rune`między wystąpieniami elementu tekstowego i tekstowymi `string`w :</span><span class="sxs-lookup"><span data-stu-id="e7ee1-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="e7ee1-236">Jeśli ten kod zostanie uruchomiony w programach .NET Framework lub .NET Core 3.1 lub wcześniejszych, liczba elementów tekstowych dla emoji zostanie wyświetlony `4`.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="e7ee1-237">Wynika to z błędu `StringInfo` w klasie, który jest naprawiony w .NET 5.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-opno-locstring-instances"></a><span data-ttu-id="e7ee1-238">Przykład: dzielenie string wystąpień</span><span class="sxs-lookup"><span data-stu-id="e7ee1-238">Example: splitting string instances</span></span>

<span data-ttu-id="e7ee1-239">Podczas dzielenia `string` wystąpień należy unikać dzielenia par zastępczych i klastrów grafem.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="e7ee1-240">Rozważmy następujący przykład nieprawidłowego kodu, który zamierza wstawić podziały wiersza co 10 znaków w : string</span><span class="sxs-lookup"><span data-stu-id="e7ee1-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="e7ee1-241">Ponieważ ten kod wylicza `char` wystąpienia, para zastępcza, która dzieje`char` się osieroconych 10-granica zostanie podzielona i nowywierek między nimi.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="e7ee1-242">To wstawianie wprowadza uszkodzenie danych, ponieważ zastępcze punkty kodu mają znaczenie tylko jako pary.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="e7ee1-243">Możliwość uszkodzenia danych nie jest eliminowana, jeśli `Rune` wyliczasz wystąpienia (wartości skalarne) zamiast wystąpień. `char`</span><span class="sxs-lookup"><span data-stu-id="e7ee1-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="e7ee1-244">Zestaw wystąpień `Rune` może stanowić klaster grafem, który przecina`char` granicę 10.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="e7ee1-245">Jeśli zestaw klastra grafemu jest podzielony, nie można go poprawnie zinterpretować.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="e7ee1-246">Lepszym rozwiązaniem jest przerwanie string klastrów grafeme lub elementów tekstowych, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="e7ee1-247">Jak wspomniano wcześniej, jednak w implementacjach .NET innych `StringInfo` niż .NET 5, klasa może obsługiwać niektóre klastry grafeme niepoprawnie.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="e7ee1-248">UTF-8 i UTF-32</span><span class="sxs-lookup"><span data-stu-id="e7ee1-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="e7ee1-249">Poprzednie sekcje koncentruje się na UTF-16, ponieważ to, co `string` .NET używa do kodowania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="e7ee1-250">Istnieją inne systemy kodowania dla Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) i [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span><span class="sxs-lookup"><span data-stu-id="e7ee1-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="e7ee1-251">Kodowania te używają jednostek kodu 8-bitowego i jednostek kodu 32-bitowego, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="e7ee1-252">Podobnie jak UTF-16, UTF-8 wymaga wielu jednostek kodu do reprezentowania niektórych wartości skalarnych Unicode.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="e7ee1-253">UTF-32 może reprezentować dowolną wartość skalarną w pojedynczej jednostce kodu 32-bitowego.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="e7ee1-254">Oto kilka przykładów pokazujących, jak ten sam punkt kodu Unicode jest reprezentowany w każdym z tych trzech systemów kodowania Unicode:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

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

<span data-ttu-id="e7ee1-255">Jak wspomniano wcześniej, pojedyncza jednostka kodu UTF-16 z [pary zastępczej](#surrogate-pairs) jest bez znaczenia sama w sobie.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="e7ee1-256">W ten sam sposób pojedyncza jednostka kodu UTF-8 jest sama w sobie bez znaczenia, jeśli jest w sekwencji dwóch, trzech lub czterech używanych do obliczania wartości skalarnej.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="e7ee1-257">Endianness (Endianness)</span><span class="sxs-lookup"><span data-stu-id="e7ee1-257">Endianness</span></span>

<span data-ttu-id="e7ee1-258">W .NET jednostki kodu UTF-16 string są przechowywane w ciągłej pamięci jako sekwencja 16-bitowych liczby całkowite (wystąpień).`char`</span><span class="sxs-lookup"><span data-stu-id="e7ee1-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="e7ee1-259">Bity poszczególnych jednostek kodu są określone zgodnie z [endianness](https://en.wikipedia.org/wiki/Endianness) bieżącej architektury.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="e7ee1-260">Na architekturze mało endian, string składający się z punktów `[ D801 DCCC ]` kodu UTF-16 będzie `[ 0x01, 0xD8, 0xCC, 0xDC ]`określone w pamięci jako bajty .</span><span class="sxs-lookup"><span data-stu-id="e7ee1-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="e7ee1-261">Na architekturze big-endian, że to samo string będzie `[ 0xD8, 0x01, 0xDC, 0xCC ]`określone w pamięci jako bajty .</span><span class="sxs-lookup"><span data-stu-id="e7ee1-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="e7ee1-262">Systemy komputerowe, które komunikują się ze sobą, muszą uzgodnić reprezentację danych przecinających przewód.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="e7ee1-263">Większość protokołów sieciowych używa UTF-8 jako standardu podczas przesyłania tekstu, częściowo w celu uniknięcia problemów, które mogą wynikać z komunikacji maszyny wielkofemiańskiego z maszyną małotuzyjną.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="e7ee1-264">Składający string się z punktów `[ F0 90 93 8C ]` kodu UTF-8 zawsze będą `[ 0xF0, 0x90, 0x93, 0x8C ]` reprezentowane jako bajty, niezależnie od endianness.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="e7ee1-265">Aby użyć UTF-8 do przesyłania tekstu, aplikacje .NET często używają kodu, takiego jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="e7ee1-266">W poprzednim przykładzie metoda [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) dekoduje UTF-16 `string` z powrotem do serii wartości skalarnych Unicode, a następnie ponownie koduje te wartości `byte` skalarne w UTF-8 i umieszcza wynikową sekwencję w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="e7ee1-267">Metoda [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) wykonuje odwrotną transformację, konwertując `byte` tablicę UTF-8 `string`na UTF-16 .</span><span class="sxs-lookup"><span data-stu-id="e7ee1-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="e7ee1-268">Ponieważ UTF-8 jest powszechne w Internecie, może być kuszące, aby odczytać surowe bajty z przewodu i traktować dane tak, jakby to było UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="e7ee1-269">Należy jednak sprawdzić, czy jest on rzeczywiście dobrze uformowany.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="e7ee1-270">Złośliwy klient może przesłać źle sformułowane UTF-8 do usługi.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="e7ee1-271">Jeśli działasz na tych danych tak, jakby były dobrze sformułowane, może to spowodować błędy lub luki w zabezpieczeniach w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="e7ee1-272">Aby sprawdzić poprawność danych UTF-8, `Encoding.UTF8.GetString`można użyć metody, takiej jak , `string`która będzie przeprowadzać sprawdzanie poprawności podczas konwertowania danych przychodzących na plik .</span><span class="sxs-lookup"><span data-stu-id="e7ee1-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="e7ee1-273">Dobrze uformowane kodowanie</span><span class="sxs-lookup"><span data-stu-id="e7ee1-273">Well-formed encoding</span></span>

<span data-ttu-id="e7ee1-274">Dobrze sformułowane kodowanie Unicode string jest jednostkami kodu, które mogą być dekodowane jednoznacznie i bez błędu w sekwencji wartości skalarnych Unicode.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="e7ee1-275">Dobrze uformowane dane mogą być transkodowane swobodnie tam iz powrotem między UTF-8, UTF-16 i UTF-32.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="e7ee1-276">Pytanie, czy sekwencja kodowania jest dobrze sformułowana, czy nie, nie jest związane z endianness architektury maszyny.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="e7ee1-277">Źle ukształtowana sekwencja UTF-8 jest źle uformowana w ten sam sposób zarówno na maszynach big-endian, jak i mało endiańskich.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="e7ee1-278">Oto kilka przykładów źle sformułowanych kodowania:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="e7ee1-279">W UTF-8 sekwencja `[ 6C C2 61 ]` jest źle `C2` sformułowana, `61`ponieważ nie można następować po .</span><span class="sxs-lookup"><span data-stu-id="e7ee1-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="e7ee1-280">`[ DC00 DD00 ]` W UTF-16 sekwencja (lub w języku string `"\udc00\udd00"`C#,) jest źle `DC00` sformułowana, ponieważ `DD00`nie można następować po niskim surogatem.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="e7ee1-281">W UTF-32 sekwencja `[ 0011ABCD ]` jest źle `0011ABCD` sformułowana, ponieważ znajduje się poza zakresem wartości skalarnych Unicode.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="e7ee1-282">W .NET `string` wystąpienia prawie zawsze zawierają dobrze sformułowane dane UTF-16, ale nie jest to gwarantowane.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="e7ee1-283">Poniższe przykłady pokazują prawidłowy kod języka C#, który tworzy `string` źle sformułowane dane UTF-16 w wystąpieniach.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="e7ee1-284">Źle sformułowany dosłowny:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="e7ee1-285">Podciąg, który dzieli parę zastępczą:</span><span class="sxs-lookup"><span data-stu-id="e7ee1-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="e7ee1-286">Interfejsy API [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) jak nigdy `string` nie zwracają źle sformułowane wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="e7ee1-287">`Encoding.GetString`i `Encoding.GetBytes` metody wykrywają źle sformułowane sekwencje w danych wejściowych i wykonują podstawienie znaków podczas generowania danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="e7ee1-288">Na przykład [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) jeśli widzi bajt non-ASCII w danych wejściowych (poza zakresem U + 0000..U + 007F), wstawia '?' do zwróconego `string` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="e7ee1-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)zastępuje źle sformułowane sekwencje UTF-8 `U+FFFD REPLACEMENT CHARACTER ('�')` `string` w zwróconym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="e7ee1-290">Aby uzyskać więcej informacji, zobacz [Standard Unicode](https://www.unicode.org/versions/latest/), Sekcje 5.22 i 3.9.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="e7ee1-291">Wbudowane klasy `Encoding` można również skonfigurować, aby zgłosić wyjątek, a nie wykonywać podstawienia znaków, gdy nieuformowane sekwencje są widoczne.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="e7ee1-292">Takie podejście jest często używane w aplikacjach wrażliwych na zabezpieczenia, gdzie podstawianie znaków może być nie do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="e7ee1-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="e7ee1-293">Aby uzyskać informacje dotyczące używania `Encoding` wbudowanych klas, zobacz [Jak używać klas kodowania znaków w .NET](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee1-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e7ee1-294">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7ee1-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="e7ee1-295">Globalizacja i lokalizacja</span><span class="sxs-lookup"><span data-stu-id="e7ee1-295">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
