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
ms.openlocfilehash: 628461c8136946dd902c0a52048eee7c516c52cd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352924"
---
# <a name="type-characters-visual-basic"></a>Znaki typu (Visual Basic)

Oprócz określania typu danych w instrukcji deklaracji, można wymusić typ danych niektórych elementów programistycznych *znakami typu*. Znak typu musi występować bezpośrednio po elemencie i nie ma żadnych znaków interwencji żadnego rodzaju.

Znak typu nie jest częścią nazwy elementu. Element zdefiniowany za pomocą znaku typu może być przywoływany bez znaku typu.

## <a name="identifier-type-characters"></a>Znaki typu identyfikatora

Visual Basic dostarcza zestaw *znaków typu identyfikatora* , których można użyć w deklaracji, aby określić typ danych zmiennej lub stałej. W poniższej tabeli przedstawiono znaki dostępnego identyfikatora z przykładami użycia.
  
|Znak typu identyfikatora|Typ danych|Przykład|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Nie istnieją znaki typu identyfikatora dla `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`lub `UShort` typów danych lub dla jakichkolwiek typów danych złożonych, takich jak tablice lub struktury.

W niektórych przypadkach można dołączyć znak `$` do funkcji Visual Basic, na przykład `Left$` zamiast `Left`, aby uzyskać zwracaną wartość typu `String`.

We wszystkich przypadkach znak typu identyfikatora musi występować bezpośrednio po nazwie identyfikatora.

## <a name="literal-type-characters"></a>Znaki typu Literal

*Literał* jest tekstową reprezentacją określonej wartości typu danych.  

### <a name="default-literal-types"></a>Domyślne typy literałów

Postać literału wyświetlanego w kodzie zwykle określa swój typ danych. W poniższej tabeli przedstawiono te typy domyślne.  
  
|Tekstowa postać literału|Domyślny typ danych|Przykład|  
|-----------------------------|-----------------------|-------------|  
|Liczbowa, bez części ułamkowej|`Integer`|`2147483647`|  
|Liczbowa, bez części ułamkowej, zbyt duża dla `Integer`|`Long`|`2147483648`|  
|Liczbowa, ułamkowa część|`Double`|`1.2`|  
|Ujęte w podwójne cudzysłowy|`String`|`"A"`|  
|Ujęte w znaki liczbowe|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Wymuszone typy literałów

Visual Basic dostarcza zestaw *znaków literału*, których można użyć, aby wymusić, że w literale zostanie przyjęty typ danych inny niż ten, który wskazuje. Można to zrobić przez dołączenie znaku do końca literału. W poniższej tabeli przedstawiono dostępne znaki literału z przykładami użycia.
  
|Znak typu literału|Typ danych|Przykład|  
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

Nie istnieją znaki typu literału dla typu danych `Boolean`, `Byte`, `Date`, `Object`, `SByte`lub `String` lub dla dowolnego złożonego typu danych, takiego jak tablice lub struktury.

Literały mogą również używać znaków typu identyfikatora (`%`, `&`, `@`, `!`, `#`, `$`), ponieważ mogą to być zmienne, stałe i wyrażenia. Jednak znaki literału (`S`, `I`, `L`, `D`, `F`, `R`, `C`) mogą być używane tylko z literałami.

We wszystkich przypadkach znak typu literału musi występować bezpośrednio po wartości literału.

## <a name="hexadecimal-binary-and-octal-literals"></a>Literały szesnastkowe, binarne i ósemkowe

Kompilator zwykle interpretuje literał liczby całkowitej, aby znajdować się w systemie dziesiętnym (podstawowy 10). Można również zdefiniować literał liczby całkowitej jako szesnastkową (Base 16) z prefiksem `&H`, jako wartość binarną (podstawową 2) z prefiksem `&B`, a jako ósemkową (bazową 8) liczbę z prefiksem `&O`. Cyfry, które są zgodne z prefiksem, muszą być odpowiednie dla systemu liczbowego. Przedstawiono to w poniższej tabeli.  
  
|Podstawa liczby|prefiks|Prawidłowe wartości cyfry|Przykład|
|-----------------|------------|------------------------|-------------|
|Szesnastkowe (Base 16)|`&H`|0-9 i A-F|`&HFFFF`|
|Binary (baza 2)|`&B`|0-1|`&B01111100`|
|Ósemkowe (podstawa 8)|`&O`|0-7|`&O77`|

Począwszy od Visual Basic 2017, można użyć znaku podkreślenia (`_`) jako separatora grupy, aby zwiększyć czytelność literału całkowitego. Poniższy przykład używa znaku `_`, aby zgrupować literał binarny w grupy 8-bitowe:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Można przestrzegać prefiksu poprzedzonego znakiem typu literału. Poniższy przykład pokazuje.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

W poprzednim przykładzie `counter` ma wartość dziesiętną-32768, a `flags` ma wartość dziesiętną + 32768.

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Na przykład:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Konwersje typów w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
