---
title: Wzorce aktywne (F#)
description: 'Dowiedz się, jak użyć aktywne wzorce, aby zdefiniować nazwany partycji, które należy podzielić danych wejściowych w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: b8c3270b1efbeb3495ac69bf1217fddf8a5a73e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="active-patterns"></a>Wzorce aktywne

*Wzorce aktywne* umożliwiają zdefiniowanie nazwanego partycji, które należy podzielić danych wejściowych, dzięki czemu można używać tych nazw we wzorcu zgodnego z wyrażeniem, tak jak w przypadku Unii rozłącznej. Wzorce aktywne umożliwia dekompozycji danych w sposób dostosowany dla każdej partycji.


## <a name="syntax"></a>Składnia

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>Uwagi
W poprzednich składni identyfikatory są nazwy partycji danych wejściowych, która jest reprezentowana przez *argumenty*, lub innymi słowy, nazwy dla podzbiorów zestawu wszystkie wartości argumentów. W definicji — aktywny wzorzec może być do siedmiu partycji. *Wyrażenie* opisuje formularza, do którego próba dekompozycji danych. Definicja — aktywny wzorzec umożliwia definiowanie zasady określające, który partycji o nazwie wartości podanej jako argumenty należą do. (| A |) symbole są określane jako *klipy bananów* i została wywołana funkcja utworzone przez tego typu powiązania let *aktywny aparat rozpoznawania*.

Na przykład należy wziąć pod uwagę następujące aktywny wzorzec z nieprawidłowym argumentem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Aktywny wzorzec można użyć we wzorcu zgodnego wyrażeniem, jak w poniższym przykładzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Dane wyjściowe tego programu jest następujący:

```
7 is odd
11 is odd
32 is even
```

Inny użycie aktywne wzorce jest próba dekompozycji typy danych na wiele sposobów, na przykład w przypadku tych samych danych różne reprezentacje możliwe. Na przykład `Color` obiektu może być rozłożone na reprezentacja RGB lub reprezentacja HSB.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Dane wyjściowe programu powyżej jest następujący:

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

W połączeniu sposobów przy użyciu aktywne wzorce pozwala na partycji i Rozłóż dane na odpowiednie formularza i wykonaj odpowiednią obliczenia na odpowiednie dane w postaci najbardziej odpowiednim obliczenia.

Wyrażenia dopasowania wzorca wynikowe Włącz dane są zapisywane w wygodny sposób, który jest bardzo do odczytu, znacznie uproszczenie rozgałęzianie złożonych i kod analizy danych.


## <a name="partial-active-patterns"></a>Częściowe aktywne wzorce
Czasami trzeba tylko część obszaru wejściowego podzielić na partycje. W takim przypadku zestaw z częściowa wzorców zapisu w sytuacji, z których zgodne niektórych danych wejściowych, ale nie pasuje do innych danych wejściowych. Wzorce aktywne, które nie zawsze utworzyć wartość są nazywane *częściowe aktywne wzorce*; mają wartości zwracanej, który jest typem opcji. Aby zdefiniować częściowe aktywny wzorzec, należy użyć symbolu wieloznacznego (_) na końcu listy wzorców wewnątrz klipy bananów. Poniższy kod ilustruje korzystanie z częściowa aktywny wzorzec.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Dane wyjściowe w poprzednim przykładzie ma następującą składnię:

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Korzystając z częściowa aktywne wzorce, czasami poszczególnych opcji mogą być rozłączne lub wykluczają się wzajemnie, ale nie muszą być. W poniższym przykładzie kwadratowe wzorzec i wzorzec modułu nie są rozłączne, ponieważ niektóre liczby są kwadratów i modułów, takich jak 64. Następujący program drukowania wszystkich liczb całkowitych do 1000000 zarówno kwadratów i modułów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

Wynik jest następujący:

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
Wzorce aktywne zawsze wykonać co najmniej jednego argumentu dla elementu filtrowanego, ale potrwać również dodatkowe argumenty w takim przypadku nazwa *sparametryzowane — aktywny wzorzec* ma zastosowanie. Zezwalaj na dodatkowe argumenty ogólne wzorzec być specjalizowany. Wzorce aktywne, które często analizowanie ciągów za pomocą wyrażeń regularnych zawierają na przykład wyrażenia regularnego jako dodatkowy parametr, zgodnie z poniższym kodem, który także używa częściowe aktywny wzorzec `Integer` zdefiniowane w poprzednim przykładzie kodu. W tym przykładzie Aby dostosować ogólny ParseRegex — aktywny wzorzec podane są ciągów, które używają wyrażeń regularnych dla różnych formatów daty. Liczba całkowita — aktywny wzorzec jest używana do konwertowania podciągów do liczb całkowitych, które mogą zostać przekazane do konstruktora elementu DateTime.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Dane wyjściowe poprzedniego kodu jest następujący:

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Aktywne wzorce nie są ograniczone tylko do wzorca dopasowania wyrażenia, można również użyć na let — powiązania.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Dane wyjściowe poprzedniego kodu jest następujący:

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Wyrażenia dopasowania](match-expressions.md)

