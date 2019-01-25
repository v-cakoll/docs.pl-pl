---
title: Znaki typu
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: a469a08ebadd77d5abbfa95b270784c9ef534691
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734873"
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="86cab-102">Wpisywanie znaków (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86cab-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="86cab-103">Oprócz określenia typu danych w instrukcji deklaracji, można wymusić typ danych niektórych elementów programowania za pomocą *wpisz znak*.</span><span class="sxs-lookup"><span data-stu-id="86cab-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="86cab-104">Znak typu natychmiast postępuj zgodnie z elementu, bez znaków pośredniczące wszelkiego rodzaju.</span><span class="sxs-lookup"><span data-stu-id="86cab-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="86cab-105">Znak typu nie jest częścią nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="86cab-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="86cab-106">Element zdefiniowane przy użyciu znaku typu mogą być przywoływane bez znaku typu.</span><span class="sxs-lookup"><span data-stu-id="86cab-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="86cab-107">Znaki typu identyfikator</span><span class="sxs-lookup"><span data-stu-id="86cab-107">Identifier type characters</span></span>

<span data-ttu-id="86cab-108">Visual Basic dostarcza zestaw *znaki typu identyfikator* , można użyć w deklaracji, aby określić typ danych zmiennej lub stała.</span><span class="sxs-lookup"><span data-stu-id="86cab-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="86cab-109">W poniższej tabeli przedstawiono znaki typu identyfikator dostępna wraz z przykładami użycia.</span><span class="sxs-lookup"><span data-stu-id="86cab-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="86cab-110">Znak typu identyfikator</span><span class="sxs-lookup"><span data-stu-id="86cab-110">Identifier type character</span></span>|<span data-ttu-id="86cab-111">Typ danych</span><span class="sxs-lookup"><span data-stu-id="86cab-111">Data type</span></span>|<span data-ttu-id="86cab-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="86cab-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="86cab-113">Znaki typu identyfikator, nie istnieje dla `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, lub `UShort` typy danych, ani złożone typy danych takich jak tablice lub struktury.</span><span class="sxs-lookup"><span data-stu-id="86cab-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="86cab-114">W niektórych przypadkach można dołączyć `$` znaku do funkcji języka Visual Basic, na przykład `Left$` zamiast `Left`w celu uzyskania wartości zwracanego typu `String`.</span><span class="sxs-lookup"><span data-stu-id="86cab-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="86cab-115">We wszystkich przypadkach znak typu identyfikator natychmiast postępuj według nazwy identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="86cab-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="86cab-116">Znaki literalne</span><span class="sxs-lookup"><span data-stu-id="86cab-116">Literal type characters</span></span>

<span data-ttu-id="86cab-117">A *literału* tekstowa reprezentacja wartości określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="86cab-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="86cab-118">Domyślne typy literału</span><span class="sxs-lookup"><span data-stu-id="86cab-118">Default literal types</span></span>

<span data-ttu-id="86cab-119">Formularz literału pojawia się w kodzie zazwyczaj określa jego typu danych.</span><span class="sxs-lookup"><span data-stu-id="86cab-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="86cab-120">W poniższej tabeli przedstawiono te domyślne typy.</span><span class="sxs-lookup"><span data-stu-id="86cab-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="86cab-121">Postaci tekstowej literału</span><span class="sxs-lookup"><span data-stu-id="86cab-121">Textual form of literal</span></span>|<span data-ttu-id="86cab-122">Domyślny typ danych</span><span class="sxs-lookup"><span data-stu-id="86cab-122">Default data type</span></span>|<span data-ttu-id="86cab-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="86cab-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="86cab-124">Numeryczne, nie ułamkową część</span><span class="sxs-lookup"><span data-stu-id="86cab-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="86cab-125">Numeryczne, nie ułamkową część, zbyt duże, aby `Integer`</span><span class="sxs-lookup"><span data-stu-id="86cab-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="86cab-126">Numeryczne, ułamkową część</span><span class="sxs-lookup"><span data-stu-id="86cab-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="86cab-127">Ujęta w znaki podwójnego cudzysłowu</span><span class="sxs-lookup"><span data-stu-id="86cab-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="86cab-128">Ujęty w znaki liczby</span><span class="sxs-lookup"><span data-stu-id="86cab-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="86cab-129">Wymuszone typy literałów</span><span class="sxs-lookup"><span data-stu-id="86cab-129">Forced literal types</span></span>

<span data-ttu-id="86cab-130">Visual Basic dostarcza zestaw *znaki literalne*, którym można wymusić literału z nich przejmować typu danych innym niż jego formularza wskazuje.</span><span class="sxs-lookup"><span data-stu-id="86cab-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="86cab-131">Można to zrobić, dodając znak na końcu literału.</span><span class="sxs-lookup"><span data-stu-id="86cab-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="86cab-132">W poniższej tabeli przedstawiono znaków dostępne literalne wraz z przykładami użycia.</span><span class="sxs-lookup"><span data-stu-id="86cab-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="86cab-133">Znak literalny typu</span><span class="sxs-lookup"><span data-stu-id="86cab-133">Literal type character</span></span>|<span data-ttu-id="86cab-134">Typ danych</span><span class="sxs-lookup"><span data-stu-id="86cab-134">Data type</span></span>|<span data-ttu-id="86cab-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="86cab-135">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="86cab-136">Znaki literalne typu, nie istnieje dla `Boolean`, `Byte`, `Date`, `Object`, `SByte`, lub `String` typów danych lub dowolnego złożone typy danych takich jak tablice lub struktury.</span><span class="sxs-lookup"><span data-stu-id="86cab-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="86cab-137">Literały można również użyć znaki typu identyfikator (`%`, `&`, `@`, `!`, `#`, `$`), jak zmienne, stałe i wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="86cab-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="86cab-138">Jednak literału typu znaków (`S`, `I`, `L`, `D`, `F`, `R`, `C`) mogą być używane tylko z literałów.</span><span class="sxs-lookup"><span data-stu-id="86cab-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="86cab-139">We wszystkich przypadkach znak literalny typu musi bezpośrednio po wartości literału.</span><span class="sxs-lookup"><span data-stu-id="86cab-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="86cab-140">Literały, binarne, ósemkowa i szesnastkowym</span><span class="sxs-lookup"><span data-stu-id="86cab-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="86cab-141">Kompilator interpretuje zwykle literał liczby całkowitej w układzie dziesiętny (podstawa 10).</span><span class="sxs-lookup"><span data-stu-id="86cab-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="86cab-142">Można również zdefiniować literał liczby całkowitej jako liczbę szesnastkową (podstawa 16) `&H` prefiksu jako liczbę plik binarny (podstawa 2) `&B` prefiksu oraz liczbę ósemkową (podstawa 8) numeru `&O` prefiks.</span><span class="sxs-lookup"><span data-stu-id="86cab-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="86cab-143">Cyfr, które należy wykonać prefiks musi być odpowiednia dla systemu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="86cab-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="86cab-144">W poniższej tabeli przedstawiono to.</span><span class="sxs-lookup"><span data-stu-id="86cab-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="86cab-145">Numer podstawowy</span><span class="sxs-lookup"><span data-stu-id="86cab-145">Number base</span></span>|<span data-ttu-id="86cab-146">Prefiks</span><span class="sxs-lookup"><span data-stu-id="86cab-146">Prefix</span></span>|<span data-ttu-id="86cab-147">Wartości jednocyfrowe prawidłowe</span><span class="sxs-lookup"><span data-stu-id="86cab-147">Valid digit values</span></span>|<span data-ttu-id="86cab-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="86cab-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="86cab-149">Szesnastkową (podstawa 16)</span><span class="sxs-lookup"><span data-stu-id="86cab-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="86cab-150">0-9 i A-F</span><span class="sxs-lookup"><span data-stu-id="86cab-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="86cab-151">Plik binarny (podstawa 2)</span><span class="sxs-lookup"><span data-stu-id="86cab-151">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="86cab-152">0-1</span><span class="sxs-lookup"><span data-stu-id="86cab-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="86cab-153">Octal (podstawa 8)</span><span class="sxs-lookup"><span data-stu-id="86cab-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="86cab-154">0-7</span><span class="sxs-lookup"><span data-stu-id="86cab-154">0-7</span></span>|`&O77`|

<span data-ttu-id="86cab-155">Począwszy od 2017 Visual Basic można użyć znaku podkreślenia (`_`) jako separator grup, aby zwiększyć czytelność literał typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="86cab-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="86cab-156">W poniższym przykładzie użyto `_` znaku, aby pogrupować dane binarne literału w grupy 8-bitowych:</span><span class="sxs-lookup"><span data-stu-id="86cab-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="86cab-157">Możesz wykonać prefiksem właściwość literal o znak literalny typu.</span><span class="sxs-lookup"><span data-stu-id="86cab-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="86cab-158">Poniższy przykład przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="86cab-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="86cab-159">W poprzednim przykładzie `counter` ma wartość dziesiętną od -32768, i `flags` ma wartość dziesiętna +32768.</span><span class="sxs-lookup"><span data-stu-id="86cab-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="86cab-160">Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="86cab-160">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="86cab-161">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86cab-161">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="86cab-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86cab-162">See also</span></span>

- [<span data-ttu-id="86cab-163">Typy danych</span><span class="sxs-lookup"><span data-stu-id="86cab-163">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="86cab-164">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="86cab-164">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="86cab-165">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="86cab-165">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="86cab-166">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86cab-166">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="86cab-167">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="86cab-167">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="86cab-168">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="86cab-168">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="86cab-169">Typy danych</span><span class="sxs-lookup"><span data-stu-id="86cab-169">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
