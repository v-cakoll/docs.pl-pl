---
title: "Sumy rozłączne (F#)"
description: "Dowiedz się, jak używać F # Suma rozłączna Unii."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e2a011-c785-48c8-859f-79df7f3a0e29
ms.openlocfilehash: b7a02512ce4a63885e771be56f106bc66cc2743e
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="discriminated-unions"></a>Sumy rozłączne

Sumy rozłączne zapewniają obsługę wartości, które może być jedną z liczbą przypadków, prawdopodobnie każde z nich różne wartości i typy. Sumy rozłączne są przydatne w przypadku danych heterogenicznych; dane, które mogą mieć szczególnych przypadkach, w tym nieprawidłowy i w przypadku wystąpienia błędów; dane, które może być różna w typie z jednego wystąpienia i jako alternatywę dla małego obiektu hierarchii. Ponadto suma rozłączna cykliczne unie są używane do reprezentowania struktur danych drzewa.

## <a name="syntax"></a>Składnia

```fsharp
[ attributes ]
type type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]
...
```

## <a name="remarks"></a>Uwagi
Sumy rozłączne są podobne do typów złożenia w innych językach, ale różnią się. Jako typ union w języku C++ lub typ wariantu w języku Visual Basic danych przechowywanych w wartości nie jest stały; może być jedną z kilku różne opcje. W przeciwieństwie do złożenia w tych językach, jednak wszystkich możliwych opcji podano *identyfikator przypadku*. Identyfikatory przypadku są nazwy dla różnych rodzajów wartości, które mogą być obiekty tego typu; wartości są opcjonalne. Jeśli nie podano wartości, że wielkość liter jest odpowiednikiem wariant wyliczenia. Jeśli istnieją wartości, każda wartość albo może być pojedynczą wartość określonego typu lub spójnej kolekcji, który agreguje wiele pól w tych samych lub różnych typów. Począwszy od F # 3.1 pojedyncze pole można podać nazwę, ale nazwa jest opcjonalny, nawet jeśli są nazywane innych pól w przypadku tego samego.

Na przykład należy wziąć pod uwagę następujące deklaracji typu kształtu.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Poprzedni kod deklaruje rozróżnianą Unię kształtu, który może mieć wartości dowolnej z trzech przypadkach: prostokąt, okrąg i biblioteki Prism. Każdej sprawy ma inny zestaw pól. Prostokąt przypadek ma dwa o nazwie pola, zarówno typu `float`, które mają nazwy szerokości i długości. W przypadku okrąg ma tylko jedno pole o nazwie, usługi radius. W przypadku biblioteki Prism ma trzy pola są dwa (szerokość i wysokość) o nazwie pola. Nazwy pól są określane jako pola anonimowego.

Podając wartości w polach nazwane i anonimowe zgodnie z poniższych przykładach utworzymy obiektów.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Ten kod pokazuje, że możesz użyć pola o nazwie inicjowania lub mogą polegać na kolejność pól w deklaracji i z kolei wystarczy podać wartości dla każdego pola. Wywołanie konstruktora dla `rect` w poprzednim kodzie używa pola o nazwie, ale wywołanie konstruktora dla `circ` używa kolejność. Można mieszać uporządkowanych pól i o nazwie pola, tak jak konstrukcji `prism`.

`option` Typ jest proste rozróżnianą Unię biblioteki podstawowej F #. `option` Typ został zadeklarowany w następujący sposób.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Poprzedni kod określa, że typ `Option` jest rozróżnianą Unię z dwóch przypadków `Some` i `None`. `Some` Przypadek ma skojarzoną wartość, która składa się z co najmniej dwa pola anonimowego, którego typ jest reprezentowana przez parametr typu `'a`. `None` Case nie ma skojarzonej wartości. W związku z tym `option` typ określa typu ogólnego, który ma wartość pewien typ lub brak wartości. Typ `Option` ma również alias typu małych `option`, to znaczy więcej często używane.

Identyfikatory przypadku może służyć jako konstruktorów typu Unii rozłącznych. Na przykład poniższy kod służy do tworzenia wartości `option` typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Identyfikatory przypadku są również używane w wyrażeniach dopasowywania do wzorca. We wzorcu zgodnego wyrażeniem identyfikatory są dostępne dla wartości skojarzone z poszczególnych przypadków. Na przykład w poniższym kodzie `x` identyfikator znajduje się wartość, z którym skojarzony jest `Some` przypadku `option` typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

We wzorcu pasujące wyrażeń pola o nazwie służy do określenia dopasowań Unii rozłącznych. Typu, który został wcześniej zadeklarowany jako można użyć pola o nazwie, jak poniższy kod przedstawia wyodrębnianie wartości pól.

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

Identyfikatory przypadku można zwykle bez zakwalifikowanie ich nazwą Unii. Jeśli nazwa zawsze być kwalifikowane nazwą Unii, można zastosować [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atrybutu do definicji typu union.

### <a name="unwrapping-discriminated-unions"></a>Odkodowywanie rozłączne

W F # Suma rozłączna unie są często używane w domenie modelowania zawijania jednego typu. Jest łatwy do wyodrębnienia odpowiednia wartość za pomocą, jak również dopasowanie wzorca. Nie trzeba używać wyrażenie dopasowania dla pojedynczego przypadku:
```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

W poniższym przykładzie pokazano to:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a>Unie Suma rozłączna — struktura

Począwszy od 4.1 F #, może także reprezentować Suma rozłączna unie jako struktury.  Jest to zrobić za pomocą `[<Struct>]` atrybutu.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Ponieważ te są typy wartości i typy referencyjne nie istnieją dodatkowe zagadnienia, w porównaniu z odwołaniem Suma rozłączna unie:

1. Są kopiowane jako typów wartości i mogą wywoływać semantyka typów wartości.
2. Definicja typu rekursywnego nie można używać struktury multicase Discriminated Union.
3. Podaj unikatowe nazwy multicase struktury Discriminated Unii.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Za pomocą rozłączne zamiast hierarchie obiektów
Często służą rozróżnianą Unię prostsze alternatywę do hierarchii małego obiektu. Na przykład można użyć następujących rozróżnianą Unię zamiast `Shape` podstawowa klasa, która ma pochodnych typów koło, kwadratowa itd.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Zamiast tego metody wirtualnej można obliczyć obszar lub obwód, możesz mogą używać w implementację zorientowany obiektowo, możesz użyć wzorzec dopasowany do gałęzi odpowiednie formuły można obliczyć ilości te. W poniższym przykładzie różne formuły są używane do obliczenia obszaru, w zależności od kształtu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Wynik jest następujący:

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Za pomocą rozłączne dla struktur danych drzewa
Sumy rozłączne można cyklicznej, co oznacza, że sam Unii można dołączyć do typu jeden lub więcej przypadków. Cykliczne rozłączne może służyć do tworzenia struktury drzewa, które są używane do wyrażenia modelu w językach programowania. W poniższym kodzie Suma rozłączna cyklicznej union jest używana do tworzenia struktury danych binarnych drzewa. Unia składa się z dwóch przypadków `Node`, który jest węzłem z wartością całkowitą i lewy i prawy poddrzewa, i `Tip`, która kończy drzewa.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

W poprzednim kodzie `resultSumTree` ma wartość 10. Na poniższej ilustracji przedstawiono struktury drzewa `myTree`.

![Struktura drzewa myTree](../media/TreeStructureDiagram.png)

Sumy rozłączne działa również w przypadku węzłów w drzewie heterogenicznych. W poniższym kodzie typ `Expression` reprezentuje drzewa składni abstrakcyjnej wyrażenia w prosty język programowania, który obsługuje dodawanie i mnożenia zmiennych i cyfry. Niektóre przypadków Unii nie są cykliczne i liczby albo (`Number`) lub zmiennych (`Variable`). Zdarza się to cykliczne, stanowiące operacji (`Add` i `Multiply`), gdzie argumenty operacji są również wyrażenia. `Evaluate` Funkcja korzysta z wyrażenia dopasowania do procesu rekursywnie drzewa składni.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Po wykonaniu tego kodu, wartość `result` wynosi 5.

## <a name="common-attributes"></a>Atrybuty wspólne

Następujące atrybuty są zwykle widoczne w rozłączne:

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`(F # 4.1 i nowsze)

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)
