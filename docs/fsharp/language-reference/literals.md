---
title: Literały
description: Dowiedz się więcej o typach literałów w języku F# programowania.
ms.date: 06/28/2019
ms.openlocfilehash: 9792a24ac28eb402e35e78574cd6a2bf9526734d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041032"
---
# <a name="literals"></a>Literały

> [!NOTE]
> Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN (dla tej pory).

Ten temat zawiera tabelę, w której pokazano, jak określić typ literału w F#.

## <a name="literal-types"></a>Typy literałów

W poniższej tabeli przedstawiono typy literałów w F#. Znaki reprezentujące cyfry w notacji szesnastkowej nie uwzględniają wielkości liter. w znakach identyfikujących typ rozróżniana jest wielkość liter.

|Typ|Opis|Sufiks lub prefiks|Przykłady|
|----|-----------|----------------|--------|
|sbyte|8-bitowa liczba całkowita ze znakiem|t|`86y`<br /><br />`0b00000101y`|
|byte|8-bitowa niepodpisana liczba naturalna|uy|`86uy`<br /><br />`0b00000101uy`|
|Int16|16-bitowa liczba całkowita ze znakiem|s|`86s`|
|UInt16|16-bitowa liczba naturalna bez znaku|Prześlij|`86us`|
|int<br /><br />Elementem|32-bitowa liczba całkowita|l lub brak|`86`<br /><br />`86l`|
|uint<br /><br />równ|niepodpisany 32-bit liczby naturalnej|u lub ul|`86u`<br /><br />`86ul`|
|nativeint —|natywny wskaźnik do podpisanej liczby naturalnej|n|`123n`|
|unativeint —|natywny wskaźnik jako niepodpisany numer naturalny|odinstalować|`0x00002D3Fun`|
|Int64|64-bitowa liczba całkowita|L|`86L`|
|UInt64|niepodpisany 64-bit liczby naturalnej|UL|`86UL`|
|Single, float32|32-bitowa liczba zmiennoprzecinkowa|F lub f|`4.14F` lub `4.14f`|
|||wiersza|`0x00000000lf`|
|float Double|64-bitowa liczba zmiennoprzecinkowa|brak|`4.14` lub `2.3E+32` lub `2.3e+32`|
|||WIERSZA|`0x0000000000000000LF`|
|bigint|Liczba całkowita nieograniczona do 64-bitowej reprezentacji|I|`9999999999999999999999999999I`|
|decimal|Liczba ułamkowa reprezentowana jako stały punkt lub liczba wymierna|M lub m|`0.7833M` lub `0.7833m`|
|Char|znak Unicode|brak|`'a'` lub `'\u0061'`|
|String|Ciąg Unicode|brak|`"text\n"`<br /><br />lub<br /><br />`@"c:\filename"`<br /><br />lub<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />lub<br /><br />`"string1" + "string2"`<br /><br />Zobacz również [ciągi](Strings.md).|
|byte|Znak ASCII|B|`'a'B`|
|Byte []|Ciąg ASCII|B|`"text"B`|
|Ciąg lub Byte []|ciąg Verbatim|@ prefix|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="named-literals"></a>Nazwane literały

Wartości, które mają być stałymi, mogą być oznaczone atrybutem [literału](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) . Ten atrybut ma wpływ na sposób kompilowania wartości jako stałej.

W wyrażeniach dopasowania wzorców identyfikatory zaczynające się od małych liter są zawsze traktowane jako zmienne do powiązania, a nie jako literały, więc zazwyczaj należy używać początkowych wersalików podczas definiowania literałów.

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a>Uwagi

Ciągi Unicode mogą zawierać jawne kodowania, które można określić przy użyciu `\u`, po którym następuje 16-bitowy kod szesnastkowy (0000-FFFF) lub kodowanie UTF-32, które można określić przy użyciu `\U`, a następnie kod szesnastkowy 32-bitowy, który reprezentuje dowolny Unicode punkt kodu (00000000-0010FFFF).

Użycie innych operatorów bitowych innych niż `|||` nie jest dozwolone.

## <a name="integers-in-other-bases"></a>Liczby całkowite w innych bazach

Podpisane 32-bitowe liczby całkowite można także określić w formacie szesnastkowym, ósemkowym lub binarnym przy użyciu odpowiednio prefiksu `0x`, `0o` lub `0b`.

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Znaki podkreślenia w literałach numerycznych

Możesz oddzielić cyfry znakiem podkreślenia (`_`).

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>Zobacz także

- [Core. LiteralAttribute — Klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
