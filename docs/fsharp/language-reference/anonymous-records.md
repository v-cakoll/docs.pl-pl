---
title: Rekordy anonimowe
description: Dowiedz się, jak używać konstrukcji i rekordów anonimowe, funkcji języka, która może ułatwić realizację manipulacji danymi.
ms.date: 06/12/2019
ms.openlocfilehash: e576210d4fb76ccfd09f8feb157ef4542aa94ccf
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041795"
---
# <a name="anonymous-records"></a>Rekordy anonimowe

Anonimowe rekordy są prostych wartości zagregowanych nazwanych wartości, które nie muszą być zadeklarowana przed użyciem. Można zadeklarować je jako typy struktur lub odwołania. Są one domyślnie typami odwołań.

## <a name="syntax"></a>Składnia

W poniższych przykładach pokazano składnię anonimowe rekordu. Elementów rozdzielonych jako `[item]` są opcjonalne.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Podstawowe użycia

Anonimowe rekordy są najlepiej uważane za F# typy, które nie muszą być zadeklarowany przed wystąpienia rekordów.

Na przykład w tym miejscu w jaki sposób możesz wchodzić w interakcje przy użyciu funkcji daje rekord anonimowy:

```fsharp

open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Poniższy przykład rozszerza poprzedni z `printCircleStats` funkcji, która przyjmuje rekord anonimowe jako dane wejściowe:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let printCircleStats r (stats: {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

Wywoływanie `printCircleStats` za pomocą anonimowy typ rekordu, który nie ma tego samego "kształt", jako typ danych wejściowych nie będzie można skompilować:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Struktury anonimowe rekordów

Rekordy anonimowe, również mogą być definiowane jako struktury z opcjonalnym `struct` — słowo kluczowe. Poniższy przykład rozszerza poprzedni przez tworzenie i korzystanie z rekordu struktury anonimowe:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    // Note that the keyword comes before the '{| |}' brace pair
    struct {| Area = a; Circumference = c; Diameter = d |}

// the 'struct' keyword also comes before the '{| |}' brace pair when declaring the parameter type
let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

### <a name="structness-inference"></a>Wnioskowanie Structness

Struktury anonimowe rekordów pozwalają również "structness wnioskowania" gdzie nie należy określić `struct` — słowo kluczowe w witrynie wywołania. W tym przykładzie elide `struct` — słowo kluczowe podczas wywoływania `printCircleStats`:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

Odwrotnej wzorca — określanie `struct` gdy typ danych wejściowych nie jest rekordem anonimowa struktura - zakończy się niepowodzeniem do skompilowania.

## <a name="embedding-anonymous-records-within-other-types"></a>Osadzanie anonimowe rekordy w ramach innych typów

Jest przydatne do deklarowania [rekord z wariantami](discriminated-unions.md) którego przypadki są rekordy. Ale jeśli dane w rekordach są tego samego typu co złożenia dyskryminowanego, należy zdefiniować wszystkie typy jako wzajemnie cykliczne. Przy użyciu anonimowego rekordów pozwala uniknąć tego ograniczenia. Poniżej znajduje się przykład typ i funkcję ten wzorzec dopasowuje się nad nią:

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named for Manager and Executive would require mutually recursive definitions.
type Employee =
    | Engineer of FullName
    | Manager of {| Name: FullName; Reports: Employee list |}
    | Executive of {| Name: FullName; Reports: Employee list; Assistant: Employee |}

let getFirstName e =
    match e with
    | Engineer fullName -> fullName.FirstName
    | Manager m -> m.Name.FirstName
    | Executive ex -> ex.Name.FirstName
```

## <a name="copy-and-update-expressions"></a>Kopiuj i Aktualizuj wyrażeń

Konstrukcja z obsługą rekordów anonimowe [Kopiuj i Aktualizuj wyrażenia](copy-and-update-record-expressions.md). Na przykład Oto, jak można utworzyć nowe wystąpienie klasy anonimowe rekord, który kopiuje istniejącą jednostkowego danych:

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Jednak w przeciwieństwie do rekordów o nazwie rekordów anonimowe umożliwiają konstruowania całkowicie różne formy z kopią i aktualizacja wyrażeń. W przykładzie poniżej ma ten sam rekord anonimowego z poprzedniego przykładu i rozszerza ją na nowy rekord anonimowy:

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Istnieje również możliwość konstruowania anonimowe rekordy z wystąpienia nazwanego rekordy:

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Można także skopiować dane do i z odwołania i struktury anonimowe rekordów:

```fsharp
// Copy data from a reference record into a struct anonymous record
type R1 = { X: int }
let r1 = { X = 1 }

let data1 = struct {| r1 with Y = 1 |}

// Copy data from a struct record into a reference anonymous record
[<Struct>]
type R2 = { X: int }
let r2 = { X = 1 }

let data2 = {| r1 with Y = 1 |}

// Copy the reference anonymous record data into a struct anonymous record
let data3 = struct {| data2 with Z = r2.X |}
```

## <a name="properties-of-anonymous-records"></a>Właściwości anonimowych rekordów

Anonimowe rekordy mają cechy, które są niezbędne do pełnego zrozumienia, jak mogą być używane.

### <a name="anonymous-records-are-nominal"></a>Anonimowe rekordy, które są nominalna

Anonimowe rekordy, które są [nominalna typy](https://en.wikipedia.org/wiki/Nominal_type_system). Są one najlepszym myślenia jako o nazwie [rekordu](records.md) typy (które są również nominalna), które nie wymagają ponoszenia deklaracji.

Rozważmy następujący przykład za pomocą dwie deklaracje anonimowe rekord:

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

`x` i `y` wartości mają różne typy i nie są zgodne ze sobą. Nie są one equatable i nie są porównywalne. Aby zilustrować ten problem, należy wziąć pod uwagę rekord o nazwie równoważne:

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Nie ma żadnych założenia dotyczące anonimowe rekordów w porównaniu z ich odpowiedniki o nazwie rekordu, gdy dotyczące równoważności typu lub porównywania.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Anonimowe rekordów, użyj strukturalnej równości i porównania

Podobnie jak typy rekordów anonimowe rekordy są strukturalnie equatable i porównywalne. To jest wartość true, jeśli wszystkie typy składowych obsługują równości i porównanie, takie jak przy użyciu typów rekordów. Do obsługi równości lub porównywania, dwa rekordy anonimowe musi mieć ten sam "kształt".

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Anonimowe rekordy, które są możliwe do serializacji

Podobnie jak rekordów o nazwie może wykonywać serializację anonimowe rekordów. Oto przykład za pomocą [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Anonimowe rekordy są przydatne do wysyłania danych uproszczone przez sieć bez konieczności zdefiniować domeny na potrzeby serializacji/deserializacji typów na początku.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Anonimowe rekordów współdziałać z C# typy anonimowe

Można użyć interfejsu API platformy .NET, która wymaga użycia [ C# typy anonimowe](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). C#typy anonimowe są proste do współdziałania z usługami przy użyciu anonimowego rekordów. Poniższy przykład pokazuje, jak użyć do nawiązania połączenia anonimowego rekordów [LINQ](../../csharp/programming-guide/concepts/linq/index.md) przeciążenia, które wymaga typu anonimowego:

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

Istnieje wiele innych interfejsów API używane w całej platformy .NET, które wymagają użycia przekazywanie w typu anonimowego. Anonimowe rekordy są narzędziem do pracy z nimi.

## <a name="limitations"></a>Ograniczenia

Anonimowe rekordy mają pewne ograniczenia ich użycia. Niektóre są wbudowane w swoich konstrukcjach, ale inne nadającymi się do zmiany.

### <a name="limitations-with-pattern-matching"></a>Ograniczenia dotyczące dopasowywania do wzorca

Anonimowe rekordów nie obsługuje dopasowywania do wzorca, w przeciwieństwie do rekordów o nazwie. Istnieją trzy powody:

1. Wzorzec musi uwzględnić wszystkie pola rekordu anonimowe, w przeciwieństwie do typów rekordów o nazwie. Jest to spowodowane rekordów anonimowe nie obsługują strukturalnych subtyping — są one nominalna typów.
2. Ze względu na (1) istnieje możliwość mają dodatkowe wzorców w wyrażeniu dopasowania wzorca każdy wzorzec distinct oznaczałoby inny anonimowy typ rekordu.
3. Ze względu na [3] wszelkie wzorzec anonimowe rekordu byłoby pełniejszą niż użycie "kropkowej".

Brak sugestii języka otwarte do [umożliwia dopasowanie do wzorca w ograniczone konteksty](https://github.com/fsharp/fslang-suggestions/issues/713).

### <a name="limitations-with-mutability"></a>Ograniczenia dotyczące zmienność

Nie jest obecnie można zdefiniować anonimowe rekord z `mutable` danych. Brak [Otwórz sugestii języka](https://github.com/fsharp/fslang-suggestions/issues/732) umożliwia mutable danych.

### <a name="limitations-with-struct-anonymous-records"></a>Ograniczenia dotyczące struktury anonimowe rekordów

Nie jest możliwe zadeklarować struktury anonimowe rekordy jako `IsByRefLike` lub `IsReadOnly`. Brak [Otwórz sugestii języka](https://github.com/fsharp/fslang-suggestions/issues/712) do dla `IsByRefLike` i `IsReadOnly` anonimowe rekordów.
