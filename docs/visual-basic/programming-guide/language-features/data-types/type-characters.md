---
title: Znaki typu
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bd017db40fc28c78e960a889947cc7323e3e156
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="91c11-102">Wpisz znaki (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91c11-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="91c11-103">Oprócz określenia typu danych w instrukcji deklaracji, można wymusić na typ danych niektórych elementów programowania o *znaku typu*.</span><span class="sxs-lookup"><span data-stu-id="91c11-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="91c11-104">Znak typu musi występować zaraz po elemencie, bez znaków pośredniczące dowolnego rodzaju.</span><span class="sxs-lookup"><span data-stu-id="91c11-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="91c11-105">Znaku typu nie jest częścią nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="91c11-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="91c11-106">Element zdefiniowany ze znakiem typu można odwoływać się bez znaku typu.</span><span class="sxs-lookup"><span data-stu-id="91c11-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="91c11-107">Znaki typu identyfikator</span><span class="sxs-lookup"><span data-stu-id="91c11-107">Identifier type characters</span></span>

<span data-ttu-id="91c11-108">Visual Basic dostarcza zestaw *znaki typu identyfikator* czy można użyć w deklaracji, aby określić typ danych zmiennej lub stała.</span><span class="sxs-lookup"><span data-stu-id="91c11-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="91c11-109">W poniższej tabeli przedstawiono znaki typu identyfikator dostępne z przykładem użycia.</span><span class="sxs-lookup"><span data-stu-id="91c11-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="91c11-110">Znak typu identyfikator</span><span class="sxs-lookup"><span data-stu-id="91c11-110">Identifier type character</span></span>|<span data-ttu-id="91c11-111">Typ danych</span><span class="sxs-lookup"><span data-stu-id="91c11-111">Data type</span></span>|<span data-ttu-id="91c11-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="91c11-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="91c11-113">Znaki typu identyfikator, nie istnieje dla `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, lub `UShort` typy danych ani złożone typy danych, takich jak tablice lub struktury.</span><span class="sxs-lookup"><span data-stu-id="91c11-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="91c11-114">W niektórych przypadkach możesz dołączyć `$` znak funkcji języka Visual Basic, na przykład `Left$` zamiast `Left`, aby uzyskać zwrócona wartość typu `String`.</span><span class="sxs-lookup"><span data-stu-id="91c11-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="91c11-115">We wszystkich przypadkach znak typu Identyfikator musi występować zaraz po nazwy identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="91c11-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="91c11-116">Znaki literalne</span><span class="sxs-lookup"><span data-stu-id="91c11-116">Literal type characters</span></span>

<span data-ttu-id="91c11-117">A *literału* tekstowa reprezentacja wartości określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="91c11-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="91c11-118">Domyślne typy literału</span><span class="sxs-lookup"><span data-stu-id="91c11-118">Default literal types</span></span>

<span data-ttu-id="91c11-119">Formularz literału wyświetlaną w kodzie zwykle określa jego typu danych.</span><span class="sxs-lookup"><span data-stu-id="91c11-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="91c11-120">W poniższej tabeli przedstawiono te typy domyślne.</span><span class="sxs-lookup"><span data-stu-id="91c11-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="91c11-121">Postaci tekstowej literału</span><span class="sxs-lookup"><span data-stu-id="91c11-121">Textual form of literal</span></span>|<span data-ttu-id="91c11-122">Domyślny typ danych</span><span class="sxs-lookup"><span data-stu-id="91c11-122">Default data type</span></span>|<span data-ttu-id="91c11-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="91c11-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="91c11-124">Numeryczne, nie ułamkowych części</span><span class="sxs-lookup"><span data-stu-id="91c11-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="91c11-125">Numeryczne, nie ułamkowych części, zbyt duży dla`Integer`</span><span class="sxs-lookup"><span data-stu-id="91c11-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="91c11-126">Numeryczne, ułamkowych części</span><span class="sxs-lookup"><span data-stu-id="91c11-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="91c11-127">Ujęta w znaki podwójnego cudzysłowu</span><span class="sxs-lookup"><span data-stu-id="91c11-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="91c11-128">Ujęta w znaki numeru</span><span class="sxs-lookup"><span data-stu-id="91c11-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="91c11-129">Wymuszone typy literału</span><span class="sxs-lookup"><span data-stu-id="91c11-129">Forced literal types</span></span>

<span data-ttu-id="91c11-130">Visual Basic dostarcza zestaw *znaki literalne*, którym można wymusić literał założenie typu danych innego niż jego formularza wskazuje.</span><span class="sxs-lookup"><span data-stu-id="91c11-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="91c11-131">W tym dodając znak na końcu literału.</span><span class="sxs-lookup"><span data-stu-id="91c11-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="91c11-132">W poniższej tabeli przedstawiono znaki literalne dostępne z przykładem użycia.</span><span class="sxs-lookup"><span data-stu-id="91c11-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="91c11-133">Znak literalny typu</span><span class="sxs-lookup"><span data-stu-id="91c11-133">Literal type character</span></span>|<span data-ttu-id="91c11-134">Typ danych</span><span class="sxs-lookup"><span data-stu-id="91c11-134">Data type</span></span>|<span data-ttu-id="91c11-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="91c11-135">Example</span></span>|  
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

<span data-ttu-id="91c11-136">Znaki literalne, nie istnieje dla `Boolean`, `Byte`, `Date`, `Object`, `SByte`, lub `String` typy danych, lub dla wszystkich typów danych, takich jak tablice lub struktury.</span><span class="sxs-lookup"><span data-stu-id="91c11-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="91c11-137">Literały umożliwia także znaki typu identyfikator (`%`, `&`, `@`, `!`, `#`, `$`), jak można zmienne, stałe i wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="91c11-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="91c11-138">Jednak literał wpisz znaki (`S`, `I`, `L`, `D`, `F`, `R`, `C`) może być używany tylko z literały.</span><span class="sxs-lookup"><span data-stu-id="91c11-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="91c11-139">We wszystkich przypadkach znak literalny typu musi występować zaraz po wartość literału.</span><span class="sxs-lookup"><span data-stu-id="91c11-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="91c11-140">Literały szesnastkowe binarne i ósemkowe</span><span class="sxs-lookup"><span data-stu-id="91c11-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="91c11-141">Kompilator interpretuje zwykle literał całkowity w układzie dziesiętnych (o podstawie 10).</span><span class="sxs-lookup"><span data-stu-id="91c11-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="91c11-142">Istnieje także możliwość zdefiniowania całkowitą literałów jako liczbę szesnastkową (podstawa 16) z `&H` prefiksu jako dane binarne (podstawa 2) z `&B` prefiksu i jako ósemkowe (podstawa 8) numer `&O` prefiks.</span><span class="sxs-lookup"><span data-stu-id="91c11-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="91c11-143">Cyfr, które należy wykonać prefiks musi być odpowiednia dla systemu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="91c11-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="91c11-144">W poniższej tabeli przedstawiono to.</span><span class="sxs-lookup"><span data-stu-id="91c11-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="91c11-145">Podstawowy numer</span><span class="sxs-lookup"><span data-stu-id="91c11-145">Number base</span></span>|<span data-ttu-id="91c11-146">Prefiks</span><span class="sxs-lookup"><span data-stu-id="91c11-146">Prefix</span></span>|<span data-ttu-id="91c11-147">Wartości prawidłową cyfrą</span><span class="sxs-lookup"><span data-stu-id="91c11-147">Valid digit values</span></span>|<span data-ttu-id="91c11-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="91c11-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="91c11-149">Liczba szesnastkowa (16 podstawowy)</span><span class="sxs-lookup"><span data-stu-id="91c11-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="91c11-150">0-9 i A-F</span><span class="sxs-lookup"><span data-stu-id="91c11-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="91c11-151">Dane binarne (podstawa 2)</span><span class="sxs-lookup"><span data-stu-id="91c11-151">Binary (base 2)</span></span>|`0B`|<span data-ttu-id="91c11-152">0-1</span><span class="sxs-lookup"><span data-stu-id="91c11-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="91c11-153">Octal (podstawa 8)</span><span class="sxs-lookup"><span data-stu-id="91c11-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="91c11-154">0-7</span><span class="sxs-lookup"><span data-stu-id="91c11-154">0-7</span></span>|`&O77`|

<span data-ttu-id="91c11-155">Począwszy od 2017 Visual Basic, można użyć znaku podkreślenia (`_`) jako separator grupy, aby zwiększyć czytelność literał całkowity.</span><span class="sxs-lookup"><span data-stu-id="91c11-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="91c11-156">W poniższym przykładzie użyto `_` znak do pliku binarnego literału w 8-bitową grup:</span><span class="sxs-lookup"><span data-stu-id="91c11-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="91c11-157">Możesz wykonać prefiksem literału z znak literalny typu.</span><span class="sxs-lookup"><span data-stu-id="91c11-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="91c11-158">W poniższym przykładzie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="91c11-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="91c11-159">W poprzednim przykładzie `counter` ma wartość dziesiętna -32768, i `flags` ma wartość dziesiętna +32768.</span><span class="sxs-lookup"><span data-stu-id="91c11-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

## <a name="see-also"></a><span data-ttu-id="91c11-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91c11-160">See Also</span></span>

 [<span data-ttu-id="91c11-161">Typy danych</span><span class="sxs-lookup"><span data-stu-id="91c11-161">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="91c11-162">Podstawowe typy danych</span><span class="sxs-lookup"><span data-stu-id="91c11-162">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="91c11-163">Typy wartości i typy referencyjne</span><span class="sxs-lookup"><span data-stu-id="91c11-163">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="91c11-164">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91c11-164">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="91c11-165">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="91c11-165">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="91c11-166">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="91c11-166">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="91c11-167">Typy danych</span><span class="sxs-lookup"><span data-stu-id="91c11-167">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
