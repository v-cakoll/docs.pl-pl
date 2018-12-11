---
title: Sumy rozłączne (F#)
description: Dowiedz się, jak używać F# związków wyróżniających.
ms.date: 05/16/2016
ms.openlocfilehash: f833539f2e31ffc6db4182bdbd2088e6dc2bb2cc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154414"
---
# <a name="discriminated-unions"></a>Sumy rozłączne

Połączenia rozróżniane zapewniają obsługę wartości, które mogą być jednym z wielu przypadków nazwanych, prawdopodobnie każdy z różnych wartości i typów. Połączenia rozróżniane są przydatne w przypadku heterogenicznych danych; dane, które mogą mieć specjalne przypadki, włączając przypadku prawidłowe i błędy; dane, które różni się w typie z jednego wystąpienia i jako alternatywa dla małych obiektów hierarchii. Ponadto rekursywne sumy rozłączne są używane do reprezentowania struktur drzew danych.

## <a name="syntax"></a>Składnia

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Uwagi

Połączenia rozróżniane są podobne do typów połączeń w innych językach, ale istnieją różnice. Jako typ union w języku C++ lub typ wariantu w języku Visual Basic danych przechowywanych w wartości nie zostanie usunięty; może być jednym z kilku opcji distinct. W przeciwieństwie do złożeń w tych innych językach, jednak każda z możliwych opcji otrzymuje *identyfikator przypadku*. Identyfikatory przypadków to nazwy dla różnych możliwych typów wartości, które mogą być obiekty tego typu; wartości są opcjonalne. Jeśli wartości nie są obecne, wielkość liter jest równoważna do wielkości liter w wyliczeniu. Jeśli wartości są obecne, każda wartością może być jedną wartością z określonego typu lub spójną kolekcją, która agreguje wiele pól tych samych lub różnych typów. Poszczególnym polom można nadać nazwę, ale nazwa jest opcjonalna, nawet wtedy, gdy inne pola, w tym samym przypadku są nazwane.

Wartością domyślną jest ułatwień dostępu dla sum rozłącznych `public`.

Na przykład rozważmy następującą deklarację typu kształt.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Powyższy kod deklaruje kształt złożenia dyskryminowanego, który może zawierać wartości dowolnego z trzech przypadków: Prostokąt, okrąg i pryzmat. Każdy przypadek ma inny zestaw pól. Przypadek prostokąt ma dwa o nazwane pola, oba typu `float`, które mają szerokości i długości nazwy. Przypadek okręg ma tylko jedno nazwane pole, promień. Przypadek pryzmat ma trzy pola są dwa (szerokość i wysokość) o nazwie pola. Bez nazwy pól są określane jako pola anonimowe.

Konstruujesz obiekty podając wartości dla pól nazwanych i anonimowych według poniższych przykładów.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Ten kod wskazuje, że możesz użyć nazwanych pól podczas inicjowania lub możesz polegać na określeniu kolejności pól w deklaracji i po prostu Podaj wartości dla każdego pola, z kolei. Wywołanie konstruktora dla `rect` w poprzednim kodzie używa pól nazwanych, ale wywołanie konstruktora dla `circ` używa kolejności. Możesz mieszać pola zamówione i pola nazwane, tak jak w konstrukcji `prism`.

`option` Typu jest proste złożeniem dyskryminowanym w F# podstawowej biblioteki. `option` Typ jest zadeklarowany w następujący sposób.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Powyższy kod określa, że typ `Option` to złożenie dyskryminowane, które posiada dwa przypadki `Some` i `None`. `Some` Przypadek ma skojarzoną wartość, która składa się z jednego pola anonimowego, którego typ jest reprezentowany przez parametr typu `'a`. `None` Przypadek nie ma przypisanej wartości. Ten sposób `option` typ Określa typ ogólny, który ma wartość pewnego typu, lub brak wartości. Typ `Option` ma również alias z małej litery, `option`, czyli więcej często używane.

Identyfikatory przypadków mogą służyć jako konstruktory dla dyskryminowanego typu złożenia. Na przykład, poniższy kod służy do tworzenia wartości `option` typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Identyfikatory przypadków są również używane w wyrażeniach dopasowania do wzorca. W wyrażeniu dopasowania do wzorca identyfikatory są dostarczane dla wartości skojarzonych z indywidualnych przypadkami. Na przykład w poniższym kodzie `x` jest identyfikatorem otrzymującym wartość, która jest skojarzona z `Some` przypadku `option` typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

W wyrażeniach dopasowania do wzorca można użyć nazwanych pól do określenia dopasowań złożenia dyskryminowanego. Dla typu kształt, który został uprzednio zadeklarowany można użyć nazwanych pól, jak w poniższym kodzie pokazano do wyodrębnienia wartości pól.

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

Zazwyczaj identyfikatory przypadków mogą służyć bez kwalifikowania ich nazwą Unii. Jeśli chcesz, aby nazwa zawsze była kwalifikowana nazwą złożenia, można zastosować [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atrybutu do definicji typu złożenia.

### <a name="unwrapping-discriminated-unions"></a>Odkodowywanie sumy rozłączne

W F# sumy rozłączne są często używane w domenie modelowania zawijania jednego typu. To ułatwia wyodrębnić wartości podstawowej za pomocą także dopasowywania do wzorca. Nie należy użyć wyrażenia dopasowania dla jednego przypadku:

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

Poniższy przykład przedstawia to:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

Dopasowywania do wzorca jest też dozwolony bezpośrednio w parametrów funkcji, dzięki czemu można Odkodowywanie jeden przypadek:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Sumy rozłączne

Począwszy od F# 4.1, może również reprezentować sumy rozłączne jako struktury.  Jest to zrobić za pomocą `[<Struct>]` atrybutu.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Ponieważ te są typami wartości i typy referencyjne nie istnieją dodatkowe zagadnienia dotyczące w porównaniu z odwołaniem rekord z wariantami:

1. Zostaną skopiowane jako typów wartości i mogą wywoływać semantyka typów wartości.
2. Nie można używać definicji typu cyklicznego multicase struktury Discriminated Unii.
3. Należy podać unikatowe nazwy przypadków multicase struktury Discriminated Unii.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Używanie dyskryminowanych związków zamiast hierarchii obiektu

Często można użyć złożenia dyskryminowanego jako prostszej alternatywy dla hierarchii małych obiektów. Na przykład następującej sumy rozłączonej można użyć zamiast `Shape` podstawowej klasy, która ma pochodne typy dla okręgu, kwadratu, i tak dalej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Zamiast tego metody wirtualnej do obliczenia powierzchni lub obwodu, która zostałaby użyta w implementacji zorientowanej, można użyć wzorca dopasowania w celu odgałęzienia odpowiednich formuł do obliczania tych ilości. W poniższym przykładzie różne formuły służą do obliczania powierzchni, w zależności od kształtu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Wynik jest następujący:

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Używanie dyskryminowanych związków dla struktur drzewa danych

Połączenia rozróżniane mogą być cykliczne, co oznacza, że samo połączenie mogły zostać uwzględnione w rodzaju jeden lub więcej przypadków. Cykliczne związki dyskryminowane mogą służyć do tworzenia struktur drzewa, które są używane do modelowania wyrażeń w językach programowania. W poniższym kodzie cykliczna Suma rozłączna jest używana do tworzenia struktury drzewa danych binarnych. Złożenie składa się z dwóch przypadków `Node`, który jest węzłem o wartości całkowitej oraz poddrzew lewego i prawego, i `Tip`, który kończy drzewo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

W poprzednim kodzie `resultSumTree` ma wartość 10. Poniższa ilustracja przedstawia strukturę drzewa dla `myTree`.

![Struktura drzewa dla myTree](../media/TreeStructureDiagram.png)

Połączenia rozróżniane działają dobrze, jeśli węzłów w drzewie są heterogeniczne. W poniższym kodzie typ `Expression` reprezentuje drzewo abstrakcyjnej składni wyrażenia w prostym języku programowania, który obsługuje dodawanie i mnożenie liczb i zmiennych. Niektórych przypadki nie są cykliczne i reprezentują liczby (`Number`) lub zmienne (`Variable`). Inne przypadki są cykliczne i reprezentują operacje (`Add` i `Multiply`), gdzie argumenty operacji są również wyrażeniami. `Evaluate` Funkcja używa wyrażenia dopasowania, aby procesu cyklicznie przetwarzać drzewo składni.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Kiedy ten kod jest wykonywany, wartość `result` wynosi 5.

## <a name="common-attributes"></a>Atrybuty wspólne

Następujące atrybuty są często widoczne w połączenia dyskryminowanych:

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
