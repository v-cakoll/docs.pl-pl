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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9262c57c5773b947f18fd9e8cf9087bb8e02de7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="type-characters-visual-basic"></a>Wpisz znaki (Visual Basic)

Oprócz określenia typu danych w instrukcji deklaracji, można wymusić na typ danych niektórych elementów programowania o *znaku typu*. Znak typu musi występować zaraz po elemencie, bez znaków pośredniczące dowolnego rodzaju.

Znaku typu nie jest częścią nazwy elementu. Element zdefiniowany ze znakiem typu można odwoływać się bez znaku typu.

## <a name="identifier-type-characters"></a>Znaki typu identyfikator

Visual Basic dostarcza zestaw *znaki typu identyfikator* czy można użyć w deklaracji, aby określić typ danych zmiennej lub stała. W poniższej tabeli przedstawiono znaki typu identyfikator dostępne z przykładem użycia.
  
|Znak typu identyfikator|Typ danych|Przykład|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Znaki typu identyfikator, nie istnieje dla `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, lub `UShort` typy danych ani złożone typy danych, takich jak tablice lub struktury.

W niektórych przypadkach możesz dołączyć `$` znak funkcji języka Visual Basic, na przykład `Left$` zamiast `Left`, aby uzyskać zwrócona wartość typu `String`.

We wszystkich przypadkach znak typu Identyfikator musi występować zaraz po nazwy identyfikatora.

## <a name="literal-type-characters"></a>Znaki literalne

A *literału* tekstowa reprezentacja wartości określonego typu danych.  

### <a name="default-literal-types"></a>Domyślne typy literału

Formularz literału wyświetlaną w kodzie zwykle określa jego typu danych. W poniższej tabeli przedstawiono te typy domyślne.  
  
|Postaci tekstowej literału|Domyślny typ danych|Przykład|  
|-----------------------------|-----------------------|-------------|  
|Numeryczne, nie ułamkowych części|`Integer`|`2147483647`|  
|Numeryczne, nie ułamkowych części, zbyt duży dla `Integer`|`Long`|`2147483648`|  
|Numeryczne, ułamkowych części|`Double`|`1.2`|  
|Ujęta w znaki podwójnego cudzysłowu|`String`|`"A"`|  
|Ujęta w znaki numeru|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Wymuszone typy literału

Visual Basic dostarcza zestaw *znaki literalne*, którym można wymusić literał założenie typu danych innego niż jego formularza wskazuje. W tym dodając znak na końcu literału. W poniższej tabeli przedstawiono znaki literalne dostępne z przykładem użycia.
  
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

Znaki literalne, nie istnieje dla `Boolean`, `Byte`, `Date`, `Object`, `SByte`, lub `String` typy danych, lub dla wszystkich typów danych, takich jak tablice lub struktury.

Literały umożliwia także znaki typu identyfikator (`%`, `&`, `@`, `!`, `#`, `$`), jak można zmienne, stałe i wyrażenia. Jednak literał wpisz znaki (`S`, `I`, `L`, `D`, `F`, `R`, `C`) może być używany tylko z literały.

We wszystkich przypadkach znak literalny typu musi występować zaraz po wartość literału.

## <a name="hexadecimal-binary-and-octal-literals"></a>Literały szesnastkowe binarne i ósemkowe

Kompilator interpretuje zwykle literał całkowity w układzie dziesiętnych (o podstawie 10). Istnieje także możliwość zdefiniowania całkowitą literałów jako liczbę szesnastkową (podstawa 16) z `&H` prefiksu jako dane binarne (podstawa 2) z `&B` prefiksu i jako ósemkowe (podstawa 8) numer `&O` prefiks. Cyfr, które należy wykonać prefiks musi być odpowiednia dla systemu liczbowego. W poniższej tabeli przedstawiono to.  
  
|Podstawowy numer|Prefiks|Wartości prawidłową cyfrą|Przykład|
|-----------------|------------|------------------------|-------------|
|Liczba szesnastkowa (16 podstawowy)|`&H`|0-9 i A-F|`&HFFFF`|
|Dane binarne (podstawa 2)|`&B`|0-1|`&B01111100`|
|Octal (podstawa 8)|`&O`|0-7|`&O77`|

Począwszy od 2017 Visual Basic, można użyć znaku podkreślenia (`_`) jako separator grupy, aby zwiększyć czytelność literał całkowity. W poniższym przykładzie użyto `_` znak do pliku binarnego literału w 8-bitową grup:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Możesz wykonać prefiksem literału z znak literalny typu. W poniższym przykładzie pokazano to.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

W poprzednim przykładzie `counter` ma wartość dziesiętna -32768, i `flags` ma wartość dziesiętna +32768.

Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

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
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
