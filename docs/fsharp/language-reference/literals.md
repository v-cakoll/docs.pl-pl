---
title: Literały
description: Dowiedz się więcej o typy literałów w F# języka programowania.
ms.date: 06/08/2019
ms.openlocfilehash: 93329cd868ff7a2daaffa1b87ba838bbbc98015c
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816234"
---
# <a name="literals"></a>Literały

> [!NOTE]
> Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN (na razie).

Ten temat zawiera tabelę, która pokazuje sposób określania rodzaju literału w F#.

## <a name="literal-types"></a>Typy literałów

W poniższej tabeli przedstawiono typy literałów w F#. Znaki, które reprezentują cyfr w zapisie szesnastkowym nie jest rozróżniana wielkość liter; znaki, które identyfikują typ jest rozróżniana wielkość liter.

|Typ|Opis|Prefiks lub sufiks|Przykłady|
|----|-----------|----------------|--------|
|sbyte|8-bitową liczbę całkowitą ze znakiem|t|`86y`<br /><br />`0b00000101y`|
|byte|niepodpisane 8-bitowa liczba naturalna|UY|`86uy`<br /><br />`0b00000101uy`|
|Int16|16-bitową liczbę całkowitą ze znakiem|s|`86s`|
|UInt16|Liczba naturalna bez znaku 16-bitowych|us|`86us`|
|int<br /><br />int32|32-bitowa liczba całkowita ze znakiem|l lub Brak|`86`<br /><br />`86l`|
|uint<br /><br />uint32|niepodpisane 32-bitowa liczba naturalna|u lub ul|`86u`<br /><br />`86ul`|
|nativeint —|wskaźnik natywny podpisem numer naturalnym|n|`123n`|
|unativeint —|wskaźnik natywny jako liczba naturalna bez znaku|NZ|`0x00002D3Fun`|
|int64|64-bitowa liczba całkowita ze znakiem|L|`86L`|
|uint64|niepodpisane 64-bitowa liczba naturalna|UL|`86UL`|
|pojedynczy, float32|32-bitowych liczb zmiennoprzecinkowych|F lub f|`4.14F` lub `4.14f`|
|||lf|`0x00000000lf`|
|float; podwójne|64-bitowych liczb zmiennoprzecinkowych|brak|`4.14` lub `2.3E+32` lub `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|Liczba całkowita nie ogranicza się do reprezentacja 64-bitowa|I|`9999999999999999999999999999I`|
|decimal|liczba ułamkowa reprezentowana jako stały punktu lub Liczba wymierna|M lub m|`0.7833M` lub `0.7833m`|
|Char|znak Unicode|brak|`'a'`|
|String|Ciąg Unicode|brak|`"text\n"`<br /><br />lub<br /><br />`@"c:\filename"`<br /><br />lub<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />lub<br /><br />`"string1" + "string2"`<br /><br />Zobacz też [ciągi](Strings.md).|
|byte|Znak ASCII|B|`'a'B`|
|byte[]|Ciąg ASCII|B|`"text"B`|
|Ciąg lub bajt]|Ciąg Verbatim|@ prefiksu|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="named-literals"></a>Nazwane literały

Wartości, które mają być stałymi mogą być oznaczone [literału](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atrybutu. Ten atrybut jest w stanie sprawić, że wartość zostanie skompilowana jako stała.

W wyrażeniach dopasowania do wzorca identyfikatory, które zaczynają się od małych liter są zawsze traktowane jako zmienne do powiązania, a nie jako literały, więc należy generalnie używać początkowych wielkich liter podczas definiowania literałów.

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

Ciągi Unicode mogą zawierać jawne kodowania, które można określić za pomocą `\u` następuje 16-bitowych kodów szesnastkowych lub kodowania UTF-32, które można określić za pomocą `\U` następuje kod szesnastkowy 32-bitowy, który reprezentuje Unicode Para zastępcza.

Używanie innych operatorów bitowych inne niż `|||` nie jest dozwolone.

## <a name="integers-in-other-bases"></a>Liczby całkowite w innych bazach

Liczby całkowite ze znakiem 32-bitowych można również określić szesnastkową, ósemkowej lub binarny przy użyciu `0x`, `0o` lub `0b` odpowiednio prefiksu.

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Podkreślenia w literałach numerycznych

Możesz oddzielić cyfr znaku podkreślenia (`_`).

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>Zobacz także

- [Core.literalattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
