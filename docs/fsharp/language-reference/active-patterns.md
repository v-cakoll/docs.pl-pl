---
title: Wzorce aktywne (F#)
description: 'Dowiedz się, jak zdefiniować nazwanych partycji, które należy podzielić dane wejściowe w języku programowania F # przy użyciu wzorców.'
ms.date: 05/16/2016
ms.openlocfilehash: 4fb7d3e2b9c7e6f1c1ed9d64a47728c7f40017c8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108965"
---
# <a name="active-patterns"></a>Wzorce aktywne

*Wzorce aktywne* umożliwiają definiowanie nazwanych partycji, które należy podzielić dane wejściowe, dzięki czemu można używać tych nazw w wyrażeniu dopasowania, tak jak w przypadku złożenia dyskryminowanego do wzorca. Wzorce aktywne służy do rozkładania danych w sposób dostosowany dla każdej partycji.

## <a name="syntax"></a>Składnia

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni identyfikatory są nazwy partycji danych wejściowych, który jest reprezentowany przez *argumenty*, lub innymi słowy, nazwy dla podzbiorów zbiór wszystkich wartości argumentów. W definicji — aktywny wzorzec może być maksymalnie siedem partycji. *Wyrażenie* opisuje formularza, w którym do rozkładania danych. Definicja — aktywny wzorzec można użyć do zdefiniowania reguł do określania, której partycji nazwanej wartości podanej jako argumenty należą do. (| I |) symbole są określane jako *klipy banany* i jest wywoływana funkcja utworzone przez tego typu powiązania let *active rozpoznawania*.

Na przykład należy wziąć pod uwagę następujące aktywny wzorzec z nieprawidłowym argumentem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Aktywny wzorzec można użyć w wyrażeniu, jak w poniższym przykładzie dopasowania do wzorca.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Dane wyjściowe tego programu jest następująca:

```
7 is odd
11 is odd
32 is even
```

Innym zastosowaniem wzorców jest do rozkładania typy danych na wiele sposobów, na przykład w przypadku tych samych danych bazowych różne reprezentacje to możliwe. Na przykład `Color` obiekt może być rozłożone na reprezentację w postaci RGB lub reprezentację w postaci HSB.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Dane wyjściowe programu powyżej jest następująca:

```
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

W połączeniu te dwa sposoby używania wzorców pozwalają na partycji i rozkładania danych do odpowiedniej postaci i wykonać odpowiednie obliczeń na odpowiednie dane w postaci najbardziej odpowiednim obliczeń.

Wyrażenia dopasowania wzorca wynikowe Włącz dane są zapisywane w wygodny sposób, który jest bardzo czytelny, znaczne uproszczenie złożonych tworzenia rozgałęzień i kod analizy danych.

## <a name="partial-active-patterns"></a>Wzorce aktywne częściowe

Czasami musisz partycji tylko część obszaru danych wejściowych. W takim przypadku można zapisać zestawu częściowego wzorców, z nich odnosić się do niektórych danych wejściowych, ale nie można dopasować pozostałych danych wejściowych. Aktywne wzorce, które nie zawsze daje wartość są nazywane *częściowe wzorców*; mają zwracanej wartości, która jest typem opcji. Aby zdefiniować częściowe — aktywny wzorzec, należy użyć symbolu wieloznacznego (\_) na końcu listy wzorców wewnątrz klipów banany. Poniższy kod ilustruje sposób korzystania z częściowego — aktywny wzorzec.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Dane wyjściowe poprzedniego przykładu, jest następujący:

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Korzystając z częściowego wzorców, czasami poszczególne opcje mogą być rozłączne lub wzajemnie się wykluczają, ale nie muszą być. W poniższym przykładzie kwadrat wzorca i wzorzec modułu nie są rozłączne, ponieważ niektóre numery kwadratów i modułów, takich jak 64. Następujący program drukowania wszystkich liczb całkowitych do 1000000, które są zarówno kwadratów i moduły.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

Dane wyjściowe wyglądają następująco:

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a>Wzorce aktywne sparametryzowane

Wzorce aktywne zawsze uruchomić co najmniej jednego argumentu dla elementu są dopasowywane, ale potrwać dodatkowych argumentów, w tym przypadku nazwa *sparametryzowanego — aktywny wzorzec* ma zastosowanie. Dodatkowe argumenty zezwala na ogólny wzorzec można wyspecjalizować. Na przykład wzorców, które używają wyrażeń regularnych do analizowania ciągów często zawierają wyrażenia regularnego jako dodatkowego parametru, zgodnie z poniższym kodem, który także używa częściowe — aktywny wzorzec `Integer` zdefiniowane w poprzednim przykładzie kodu. W tym przykładzie podane są ciągów, które używają wyrażeń regularnych dla różnych formatów daty, aby dostosować ogólny ParseRegex — aktywny wzorzec. Liczba całkowita — aktywny wzorzec służy do konwertowania ciągów dopasowane do liczb całkowitych, które mogą być przekazywane do konstruktora daty/godziny.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Dane wyjściowe poprzedniego kodu jest następująca:

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Wzorce aktywne nie są ograniczone tylko do wyrażenia dopasowania do wzorca, można również użyć na let — powiązania.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Dane wyjściowe poprzedniego kodu jest następująca:

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Wyrażenia dopasowania](match-expressions.md)
