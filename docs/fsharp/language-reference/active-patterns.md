---
title: Wzorce aktywne
description: Dowiedz się, jak używać aktywnych wzorców do definiowania nazwanych partycji, które dzielą dane wejściowe w języku programowania F#.
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187056"
---
# <a name="active-patterns"></a>Wzorce aktywne

*Aktywne wzorce* umożliwiają definiowanie nazwanych partycji, które dzielą dane wejściowe, dzięki czemu można używać tych nazw w wyrażeniu dopasowania wzorca, tak jak w przypadku unii dyskryminowanej. Za pomocą aktywnych wzorców można rozłożyć dane w sposób dostosowany dla każdej partycji.

## <a name="syntax"></a>Składnia

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni identyfikatory są nazwami partycji danych wejściowych, które są reprezentowane przez *argumenty*lub, innymi słowy, nazwy podzbiorów zestawu wszystkich wartości argumentów. W definicji aktywnego wzorca może być maksymalnie siedem partycji. *Wyrażenie* opisuje formularz, w którym mają być rozkładane dane. Definicja aktywnego wzorca służy do definiowania reguł określania, które z nazwanych partycji należą do wartości podanych jako argumenty. Symbole (| i |) są nazywane *klipsami bananów,* a funkcja utworzona przez ten typ wiązania let jest nazywana *aktywnym aparatem rozpoznawania.*

Na przykład należy wziąć pod uwagę następujący aktywny wzorzec z argumentem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Aktywny wzorzec można użyć w wyrażeniu dopasowania wzorca, jak w poniższym przykładzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Dane wyjściowe tego programu są następujące:

```console
7 is odd
11 is odd
32 is even
```

Innym zastosowaniem aktywnych wzorców jest rozkładanie typów danych na wiele sposobów, na przykład gdy te same dane źródłowe mają różne możliwe reprezentacje. Na przykład `Color` obiekt może być rozłożone na reprezentację RGB lub reprezentacji HSB.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Wyniki powyższego programu są następujące:

```console
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

W połączeniu te dwa sposoby używania aktywnych wzorców umożliwiają partycjonowanie i rozkładanie danych na odpowiedni formularz i wykonywanie odpowiednich obliczeń na odpowiednich danych w formularzu najwygodniejszym do obliczeń.

Wynikowe wyrażenia dopasowania wzorca umożliwiają pisanie danych w wygodny sposób, który jest bardzo czytelny, znacznie upraszczając potencjalnie złożony kod rozgałęzienia i analizy danych.

## <a name="partial-active-patterns"></a>Częściowe aktywne wzorce

Czasami trzeba podzielić tylko część miejsca wejściowego. W takim przypadku należy napisać zestaw częściowych wzorców, z których każdy pasuje do niektórych danych wejściowych, ale nie pasuje do innych danych wejściowych. Aktywne wzorce, które nie zawsze generują wartość, nazywane są *częściowymi aktywnymi wzorcami;* mają wartość zwracaną, która jest typem opcji. Aby zdefiniować częściowy aktywny wzorzec,\_należy użyć symbolu wieloznacznego ( ) na końcu listy wzorów wewnątrz klipów bananów. Poniższy kod ilustruje użycie częściowego aktywnego wzorca.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Dane wyjściowe poprzedniego przykładu są następujące:

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Podczas korzystania z częściowych aktywnych wzorców, czasami poszczególne wybory mogą być rozłączne lub wzajemnie się wykluczają, ale nie muszą być. W poniższym przykładzie wzorzec Kwadrat i wzorzec Cube nie są rozłączne, ponieważ niektóre liczby są zarówno kwadraty i moduły, takich jak 64. Poniższy program używa wzorca AND do łączenia wzorców Kwadrat i Moduł. Drukuje wszystkie liczby całkowite do 1000, które są zarówno kwadraty i kostki, jak również te, które są tylko kostki.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

Wynik jest następujący:

```console
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a>Sparametryzowane aktywne wzorce

Aktywne wzorce zawsze mają co najmniej jeden argument dla elementu, który jest dopasowywany, ale mogą również przyjmować dodatkowe argumenty, w którym to przypadku ma zastosowanie nazwa *sparametryzowana aktywny wzorzec.* Dodatkowe argumenty umożliwiają specjalizację wzorca ogólnego. Na przykład aktywne wzorce, które używają wyrażeń regularnych do analizowanie ciągów, często zawierają wyrażenie regularne jako `Integer` dodatkowy parametr, jak w poniższym kodzie, który używa również częściowego aktywnego wzorca zdefiniowanego w poprzednim przykładzie kodu. W tym przykładzie ciągi, które używają wyrażeń regularnych dla różnych formatów daty są podane w celu dostosowania ogólnego wzorca parseRegex aktywny. Integer aktywny wzorzec jest używany do konwertowania dopasowanych ciągów do liczb całkowitych, które mogą być przekazywane do konstruktora DateTime.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Dane wyjściowe poprzedniego kodu są następujące:

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Aktywne wzorce nie są ograniczone tylko do wyrażenia dopasowania wzorca, można również użyć ich na let-powiązania.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Dane wyjściowe poprzedniego kodu są następujące:

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka F#](index.md)
- [Wyrażenia dopasowania](match-expressions.md)
