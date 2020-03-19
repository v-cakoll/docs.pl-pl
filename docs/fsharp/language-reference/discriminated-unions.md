---
title: Sumy rozłączne
description: Dowiedz się, jak używać związków dyskryminowanych f#.
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400219"
---
# <a name="discriminated-unions"></a>Sumy rozłączne

Dyskryminowane związki zapewniają obsługę wartości, które mogą być jednym z wielu nazwanych przypadków, ewentualnie każdy z różnych wartości i typów. Dyskryminowane związki zawodowe są przydatne w przypadku danych heterogenicznych; dane, które mogą mieć szczególne przypadki, w tym ważne i przypadki błędów; danych, które różnią się w zależności od typu; i jako alternatywa dla hierarchii małych obiektów. Ponadto rekurencyjne związki dyskryminowane są używane do reprezentowania struktur danych drzewa.

## <a name="syntax"></a>Składnia

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Uwagi

Związki dyskryminowane są podobne do typów związków w innych językach, ale istnieją różnice. Podobnie jak w przypadku typu unii w języku C++ lub typu wariantu w języku Visual Basic, dane przechowywane w wartości nie jest ustalona; może to być jedna z kilku różnych opcji. W przeciwieństwie do związków zawodowych w tych innych językach, jednak każda z możliwych opcji otrzymuje *identyfikator sprawy*. Identyfikatory przypadków są nazwy dla różnych możliwych typów wartości, które mogą być obiekty tego typu; wartości są opcjonalne. Jeśli wartości nie są obecne, sprawa jest równoważna przypadku wyliczenia. Jeśli wartości są obecne, każda wartość może być pojedynczą wartością określonego typu lub krotką, która agreguje wiele pól tego samego lub różnych typów. Można nadać poszczególne pola nazwę, ale nazwa jest opcjonalna, nawet jeśli inne pola w tym samym przypadku są nazwane.

Dostępność dla związków dyskryminowanych `public`domyślnie .

Rozważmy na przykład następującą deklarację typu Shape.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Poprzedni kod deklaruje rozróżniony kształt unii, który może mieć wartości dowolnego z trzech przypadków: Prostokąt, Okrąg i Pryzmat. Każdy przypadek ma inny zestaw pól. Prostokąt ma dwa pola o nazwie, `float`oba typu , które mają szerokość i długość nazw. Przypadek Circle ma tylko jedno nazwane pole, promień. Przypadek Pryzmat ma trzy pola, z których dwa (szerokość i wysokość) są nazywane polami. Pola bez nazwy są nazywane polami anonimowymi.

Obiekty można konstruować, podając wartości dla nazwanych i anonimowych pól zgodnie z poniższymi przykładami.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Ten kod pokazuje, że można użyć nazwanych pól w inicjalizacji lub można polegać na kolejności pól w deklaracji i po prostu podać wartości dla każdego pola po kolei. Wywołanie konstruktora `rect` w poprzednim kodzie używa nazwanych `circ` pól, ale wywołanie konstruktora używa kolejności. Można mieszać uporządkowane pola i pola nazwane, tak `prism`jak w przypadku konstrukcji .

Typ `option` jest prostą, dyskryminowaną uniią w bibliotece podstawowej F#. Typ `option` jest zadeklarowany w następujący sposób.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Poprzedni kod określa, że `Option` typ jest związkiem dyskryminowanym, `None`który ma dwa przypadki i `Some` . Sprawa `Some` ma skojarzoną wartość, która składa się z jednego `'a`pola anonimowego, którego typ jest reprezentowany przez parametr type . Sprawa `None` nie ma skojarzonej wartości. W `option` związku z tym typ określa typ ogólny, który ma wartość pewnego typu lub nie ma wartości. Typ `Option` ma również alias typu `option`małych liter, który jest powszechnie używany.

Identyfikatory przypadków mogą być używane jako konstruktory dla typu unii dyskryminowanych. Na przykład następujący kod jest używany do `option` tworzenia wartości typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Identyfikatory przypadków są również używane w wyrażeniach dopasowania wzorca. W wyrażeniu dopasowania wzorca identyfikatory są dostarczane dla wartości skojarzonych z poszczególnych przypadków. Na przykład w poniższym `x` kodzie jest identyfikator biorąc pod `Some` uwagę wartość, która jest skojarzona ze sprawą `option` typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

W wyrażeniach dopasowania wzorca można użyć nazwanych pól do określania dopasowanych dopasowań unii dyskryminowanych. Dla typu Kształt, który został zadeklarowany wcześniej, można użyć nazwanych pól, jak pokazano w poniższym kodzie, aby wyodrębnić wartości pól.

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

Zwykle identyfikatory sprawy mogą być używane bez kwalifikowania ich nazwą związku. Jeśli chcesz, aby nazwa była zawsze kwalifikowana przy użyciu nazwy unii, można zastosować [requirequalifiedaccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) atrybut do definicji typu unii.

### <a name="unwrapping-discriminated-unions"></a>Rozpakowywanie dyskryminowanych związków

W F# Dyskryminowane związki są często używane w modelowaniu domeny do zawijania pojedynczego typu. Łatwo jest wyodrębnić wartość podstawową poprzez dopasowanie wzorca, jak również. Nie musisz używać wyrażenia dopasowania dla pojedynczego przypadku:

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

Poniższy przykład pokazuje to:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

Dopasowywanie wzorców jest również dozwolone bezpośrednio w parametrach funkcji, dzięki czemu można rozpakować tam pojedynczy przypadek:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Związki dyskryminowane struct

Związki dyskryminowane można również reprezentować jako struktury.  Odbywa się to `[<Struct>]` za pomocą atrybutu.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Ponieważ są to typy wartości, a nie typy odwołań, istnieją dodatkowe zagadnienia w porównaniu z odwołaniami dyskryminowane związki:

1. Są one kopiowane jako typy wartości i mają semantyki typu wartości.
2. Nie można użyć definicji typu cyklicznego z wieloliterową strukturą Unii dyskryminowanej.
3. Należy podać unikatowe nazwy przypadków dla wieloliterowej struktury Unii dyskryminowanej.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Używanie związków dyskryminowanych zamiast hierarchii obiektów

Często można użyć unii dyskryminowanej jako prostszą alternatywę dla hierarchii małych obiektów. Na przykład następujące unii dyskryminowanej może służyć `Shape` zamiast klasy podstawowej, która ma pochodne typy dla okręgu, kwadratu i tak dalej.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Zamiast metody wirtualnej do obliczania obszaru lub obwodu, jak można użyć w implementacji obiektowej, można użyć dopasowania wzorca do gałęzi do odpowiednich formuł do obliczenia tych ilości. W poniższym przykładzie różne formuły są używane do obliczania obszaru, w zależności od kształtu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Wynik jest następujący:

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Używanie zniechęconych związków dla struktur danych drzewa

Dyskryminowane związki zawodowe mogą być rekurencyjne, co oznacza, że sam związek może zostać włączony do rodzaju jednego lub więcej przypadków. Rekurencyjne związki dyskryminowane mogą służyć do tworzenia struktur drzewa, które są używane do modelowania wyrażeń w językach programowania. W poniższym kodzie rekurencyjne jednych z unii dyskryminaciajest używany do tworzenia struktury danych drzewa binarnego. Unia składa się z `Node`dwóch przypadków, , który jest węzłem z wartością `Tip`całkowitą i lewym i prawym poddrzewa, i , który kończy drzewo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

W poprzednim kodzie `resultSumTree` ma wartość 10. Na poniższej ilustracji `myTree`przedstawiono strukturę drzewa dla .

![Diagram, który pokazuje strukturę drzewa dla myTree.](../media/discriminated-unions/tree-structure-mytree.png)

Dyskryminowane związki działają dobrze, jeśli węzły w drzewie są heterogeniczne. W poniższym kodzie `Expression` typ reprezentuje abstrakcyjne drzewo składni wyrażenia w prostym języku programowania, który obsługuje dodawanie i mnożenie liczb i zmiennych. Niektóre sprawy związkowe nie są rekurencyjne`Number`i reprezentują liczby`Variable`( ) lub zmienne ( ). Inne przypadki są rekurencyjne i`Add` reprezentują `Multiply`operacje ( i ), gdzie operandy są również wyrażenia. Funkcja `Evaluate` używa wyrażenia dopasowania do rekurencyjnego przetwarzania drzewa składni.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Po wykonaniu tego kodu wartość `result` to 5.

## <a name="members"></a>Elementy członkowskie

Możliwe jest zdefiniowanie członków na dyskryminowanych związkach. W poniższym przykładzie pokazano, jak zdefiniować właściwość i zaimplementować interfejs:

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a>Typowe atrybuty

Następujące atrybuty są powszechnie postrzegane w dyskryminowanych związków:

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka F#](index.md)
