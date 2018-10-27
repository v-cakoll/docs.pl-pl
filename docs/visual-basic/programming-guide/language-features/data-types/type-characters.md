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
ms.openlocfilehash: 1922282ece4dd90c8f55c8dea20ef2866d8b357c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181404"
---
# <a name="type-characters-visual-basic"></a>Wpisywanie znaków (Visual Basic)

Oprócz określenia typu danych w instrukcji deklaracji, można wymusić typ danych niektórych elementów programowania za pomocą *wpisz znak*. Znak typu natychmiast postępuj zgodnie z elementu, bez znaków pośredniczące wszelkiego rodzaju.

Znak typu nie jest częścią nazwy elementu. Element zdefiniowane przy użyciu znaku typu mogą być przywoływane bez znaku typu.

## <a name="identifier-type-characters"></a>Znaki typu identyfikator

Visual Basic dostarcza zestaw *znaki typu identyfikator* , można użyć w deklaracji, aby określić typ danych zmiennej lub stała. W poniższej tabeli przedstawiono znaki typu identyfikator dostępna wraz z przykładami użycia.
  
|Znak typu identyfikator|Typ danych|Przykład|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Znaki typu identyfikator, nie istnieje dla `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, lub `UShort` typy danych, ani złożone typy danych takich jak tablice lub struktury.

W niektórych przypadkach można dołączyć `$` znaku do funkcji języka Visual Basic, na przykład `Left$` zamiast `Left`w celu uzyskania wartości zwracanego typu `String`.

We wszystkich przypadkach znak typu identyfikator natychmiast postępuj według nazwy identyfikatora.

## <a name="literal-type-characters"></a>Znaki literalne

A *literału* tekstowa reprezentacja wartości określonego typu danych.  

### <a name="default-literal-types"></a>Domyślne typy literału

Formularz literału pojawia się w kodzie zazwyczaj określa jego typu danych. W poniższej tabeli przedstawiono te domyślne typy.  
  
|Postaci tekstowej literału|Domyślny typ danych|Przykład|  
|-----------------------------|-----------------------|-------------|  
|Numeryczne, nie ułamkową część|`Integer`|`2147483647`|  
|Numeryczne, nie ułamkową część, zbyt duże, aby `Integer`|`Long`|`2147483648`|  
|Numeryczne, ułamkową część|`Double`|`1.2`|  
|Ujęta w znaki podwójnego cudzysłowu|`String`|`"A"`|  
|Ujęty w znaki liczby|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Wymuszone typy literałów

Visual Basic dostarcza zestaw *znaki literalne*, którym można wymusić literału z nich przejmować typu danych innym niż jego formularza wskazuje. Można to zrobić, dodając znak na końcu literału. W poniższej tabeli przedstawiono znaków dostępne literalne wraz z przykładami użycia.
  
|Znak literalny typu|Typ danych|Przykład|  
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

Znaki literalne typu, nie istnieje dla `Boolean`, `Byte`, `Date`, `Object`, `SByte`, lub `String` typów danych lub dowolnego złożone typy danych takich jak tablice lub struktury.

Literały można również użyć znaki typu identyfikator (`%`, `&`, `@`, `!`, `#`, `$`), jak zmienne, stałe i wyrażeń. Jednak literału typu znaków (`S`, `I`, `L`, `D`, `F`, `R`, `C`) mogą być używane tylko z literałów.

We wszystkich przypadkach znak literalny typu musi bezpośrednio po wartości literału.

## <a name="hexadecimal-binary-and-octal-literals"></a>Literały, binarne, ósemkowa i szesnastkowym

Kompilator interpretuje zwykle literał liczby całkowitej w układzie dziesiętny (podstawa 10). Można również zdefiniować literał liczby całkowitej jako liczbę szesnastkową (podstawa 16) `&H` prefiksu jako liczbę plik binarny (podstawa 2) `&B` prefiksu oraz liczbę ósemkową (podstawa 8) numeru `&O` prefiks. Cyfr, które należy wykonać prefiks musi być odpowiednia dla systemu liczbowego. W poniższej tabeli przedstawiono to.  
  
|Numer podstawowy|Prefiks|Wartości jednocyfrowe prawidłowe|Przykład|
|-----------------|------------|------------------------|-------------|
|Szesnastkową (podstawa 16)|`&H`|0-9 i A-F|`&HFFFF`|
|Plik binarny (podstawa 2)|`&B`|0-1|`&B01111100`|
|Octal (podstawa 8)|`&O`|0-7|`&O77`|

Począwszy od 2017 Visual Basic można użyć znaku podkreślenia (`_`) jako separator grup, aby zwiększyć czytelność literał typu całkowitego. W poniższym przykładzie użyto `_` znaku, aby pogrupować dane binarne literału w grupy 8-bitowych:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Możesz wykonać prefiksem właściwość literal o znak literalny typu. Poniższy przykład przedstawia to.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

W poprzednim przykładzie `counter` ma wartość dziesiętną od -32768, i `flags` ma wartość dziesiętna +32768.

Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Zobacz też

 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
