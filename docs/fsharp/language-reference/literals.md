---
title: Literały (F#)
description: 'Poznaj typy literału w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: f28ca0ae7a0b092bbc039d23625b883faffd241c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="literals"></a>Literały

> [!NOTE]
Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN (na razie).

Ten temat zawiera tabelę, która przedstawia sposób określić typ literału w języku F #.

## <a name="literal-types"></a>Typy literału
W poniższej tabeli przedstawiono typy literału w języku F #. Znaki, które reprezentują cyfr w formacie szesnastkowym nie jest rozróżniana; znaki, które identyfikują typ jest rozróżniana wielkość liter.

|Typ|Opis|Sufiks lub prefiksu|Przykłady|
|----|-----------|----------------|--------|
|sbyte|8-bitową liczbę całkowitą ze znakiem|t|`86y`<br /><br />`0b00000101y`|
|byte|bez znaku 8-bitową liczbą naturalnych|UY|`86uy`<br /><br />`0b00000101uy`|
|Int16|16-bitową liczbę całkowitą ze znakiem|s|`86s`|
|UInt16|niepodpisane 16-bitową liczbę naturalnych|US|`86us`|
|int<br /><br />int32|32-bitowa liczba całkowita|l lub Brak|`86`<br /><br />`86l`|
|uint<br /><br />uint32|niepodpisane 32-bitową liczbą naturalnych|u lub ul|`86u`<br /><br />`86ul`|
|unativeint —|wskaźnik natywny jako wartość bez znaku naturalnych|Wyrejestruj|`0x00002D3Fun`|
|int64|64-bitowa liczba całkowita|L|`86L`|
|uint64|Liczba naturalnego 64-bitowa bez znaku|UL|`86UL`|
|pojedynczy, float32|32-bitowych liczb zmiennoprzecinkowych|F lub f|`4.14F` lub `4.14f`|
|||LF|`0x00000000lf`|
|float; podwójne|64-bitowych liczb zmiennoprzecinkowych|brak|`4.14` lub `2.3E+32` lub `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|innymi reprezentacja 64-bitowa liczba całkowita|I|`9999999999999999999999999999I`|
|decimal|liczbę ułamkową reprezentowane jako punkt stałym lub Liczba wymierna|M lub m|`0.7833M` lub `0.7833m`|
|Char|znak Unicode|brak|`'a'`|
|String|Ciąg w formacie Unicode|brak|`"text\n"`<br /><br />lub<br /><br />`@"c:\filename"`<br /><br />lub<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />lub<br /><br />`"string1" + "string2"`<br /><br />Zobacz też [ciągów](Strings.md).|
|byte|Znaków ASCII|B|`'a'B`|
|byte[]|Ciąg ASCII|B|`"text"B`|
|String lub byte]|ciągu dosłownego wyrażenia|@ prefiksu|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="remarks"></a>Uwagi
Ciągów Unicode może zawierać jawnych kodowania, którą można określić za pomocą `\u` następuje szesnastkowy kod 16-bitowy lub kodowania UTF-32, którą można określić za pomocą `\U` następuje 32-bitowy kod szesnastkowe, który reprezentuje Unicode Para zastępcza.

Począwszy od F # 3.1, można użyć `+` logowanie się łączenie literałów ciągu. Można również użyć operatora testu koniunkcji lub (`|||`) operatora łączenia wyliczenia flag. Na przykład następujący kod jest dozwolony w F # 3.1:

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

Korzystanie z innych operatory bitowe nie jest dozwolona.


## <a name="named-literals"></a>Literały nazwanego
Wartości, które mają być stałymi może być oznaczony przez [literału](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atrybutu. Ten atrybut ma wpływ powoduje wartość ma zostać skompilowana jako stała.

W wyrażeniach dopasowywania do wzorca identyfikatory, które zaczynają się od małych liter zawsze są traktowane jako zmienne, które mają być powiązane, a nie jako literały, dlatego należy zwykle należy używać początkowe wersaliki podczas definiowania literały.

## <a name="integers-in-other-bases"></a>Liczby całkowite w innych bazach

Liczb całkowitych ze znakiem 32-bitowych można również określić za pomocą szesnastkowych, ósemkowe lub binarne `0x`, `0o` lub `0b` odpowiednio prefiksu.

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Podkreślenia w literałach numerycznych

Począwszy od 4.1 F # można oddzielić cyfr znakiem podkreślenia (`_`).

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a>Zobacz też

[Core.literalattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
