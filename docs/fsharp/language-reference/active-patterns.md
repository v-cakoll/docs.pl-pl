---
title: Wzorce aktywne
description: 'Dowiedz się, jak używać aktywnych wzorców do definiowania nazwanych partycji, które dzielą dane wejściowe w języku programowania języka F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 7b6da38baa35f30ae6de8a930be60a4e4fc0fc0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493895"
---
# <a name="active-patterns"></a>Wzorce aktywne

*Aktywne wzorce* umożliwiają zdefiniowanie nazwanych partycji, które dzielą dane wejściowe, dzięki czemu można używać tych nazw w wyrażeniu dopasowania wzorca tak samo jak w przypadku Unii rozłącznych. Przy użyciu aktywnych wzorców można rozkładać dane w dostosowany sposób dla każdej partycji.

## <a name="syntax"></a>Składnia

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch = expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni identyfikatory są nazwami dla partycji danych wejściowych, które są reprezentowane przez *argumenty*lub, innymi słowy, nazwy podzestawów zestawu wszystkich wartości argumentów. W definicji aktywnego wzorca może istnieć maksymalnie siedem partycji. *Wyrażenie* opisuje formularz, w którym mają zostać rozdzielone dane. Możesz użyć aktywnej definicji wzorca, aby zdefiniować reguły określania, które z nazwanych partycji są wartościami podaną jako argumenty należą do. Symbole (| i |) są określane jako *klipy bananów* , a funkcja utworzona przez ten typ powiązania Let jest nazywana *aktywnym aparatem rozpoznawania*.

Na przykład rozważmy następujący Aktywny wzorzec z argumentem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Możesz użyć aktywnego wzorca w wyrażeniu dopasowania do wzorca, jak w poniższym przykładzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Dane wyjściowe tego programu są następujące:

```console
7 is odd
11 is odd
32 is even
```

Innym sposobem użycia aktywnych wzorców jest rozkład typów danych na wiele sposobów, na przykład wtedy, gdy te same dane podstawowe mają różne możliwe reprezentacje. Na przykład `Color` obiekt może zostać rozłożony na reprezentację RGB lub reprezentację HSB.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Dane wyjściowe powyższego programu są następujące:

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

W połączeniu te dwa sposoby używania aktywnych wzorców umożliwiają partycjonowanie i rozdzielenie danych na odpowiedni formularz i wykonanie odpowiednich obliczeń na odpowiednich danych w formularzu najbardziej wygodnym do obliczenia.

Wyrażenia zgodne z wzorcem umożliwiają zapisywanie danych w wygodny sposób, który jest bardzo czytelny, co znacznie upraszcza tworzenie rozgałęzień i kodu analizy danych.

## <a name="partial-active-patterns"></a>Częściowe aktywne wzorce

Czasami należy podzielić tylko część przestrzeni wejściowej. W takim przypadku należy napisać zestaw częściowych wzorców, z których każdy jest zgodny z niektórymi danymi wejściowymi, ale nie może dopasować innych danych wejściowych. Aktywne wzorce, które nie zawsze generują wartość, są nazywane *częściowymi wzorcami aktywnymi*; mają one wartość zwracaną, która jest typem opcji. Aby zdefiniować częściowy Aktywny wzorzec, należy użyć symbolu wieloznacznego ( \_ ) na końcu listy wzorców wewnątrz klipów bananów. Poniższy kod ilustruje użycie części aktywnego wzorca.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

W poprzednim przykładzie przedstawiono dane wyjściowe poniższego przykładu:

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

W przypadku używania częściowych aktywnych wzorców czasami poszczególne opcje mogą być rozłączne lub wykluczane wzajemnie, ale nie muszą być. W poniższym przykładzie, kwadrat wzorca i moduł wzorca nie są rozłączane, ponieważ niektóre liczby są kwadratami i modułami, takimi jak 64. Poniższy program używa wzorca i do łączenia wzorców kwadratowych i sześcianu. Drukuje wszystkie liczby całkowite o wartości do 1000, które są zarówno kwadratami, jak i modułami, a także tymi, które są tylko modułami.

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

Aktywne wzorce zawsze przyjmują co najmniej jeden argument dla elementu, który jest dopasowywany, ale mogą również przyjmować dodatkowe argumenty, w tym przypadku ma zastosowanie nazwa *sparametryzowanego wzorca* . Dodatkowe argumenty umożliwiają użycie ogólnego wzorca. Na przykład aktywne wzorce używające wyrażeń regularnych do analizowania ciągów często zawierają wyrażenie regularne jako dodatkowy parametr, jak w poniższym kodzie, który używa również części aktywnego wzorca `Integer` zdefiniowanego w poprzednim przykładzie kodu. W tym przykładzie ciągi, które używają wyrażeń regularnych dla różnych formatów daty, są przyznawane w celu dostosowania ogólnego wzorca ParseRegex. Aktywny wzorzec w liczbie całkowitej służy do konwertowania dopasowanych ciągów do liczb całkowitych, które mogą być przesyłane do konstruktora DateTime.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Dane wyjściowe poprzedniego kodu są następujące:

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Aktywne wzorce nie są ograniczone tylko do wyrażeń dopasowania wzorca, ale można ich używać również na potrzeby powiązań.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Dane wyjściowe poprzedniego kodu są następujące:

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F #](index.md)
- [Wyrażenia dopasowania](match-expressions.md)
