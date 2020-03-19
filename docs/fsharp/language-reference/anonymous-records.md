---
title: Rekordy anonimowe
description: Dowiedz się, jak używać funkcji tworzenia i używania rekordów anonimowych, funkcji języka, która pomaga w manipulowaniu danymi.
ms.date: 06/12/2019
ms.openlocfilehash: ef3aa8fccdb6ff406542932816e4138040845a59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187492"
---
# <a name="anonymous-records"></a>Rekordy anonimowe

Rekordy anonimowe są proste agregaty nazwanych wartości, które nie muszą być zadeklarowane przed użyciem. Można zadeklarować je jako struktury lub typy odwołań. Są to domyślnie typy odwołań.

## <a name="syntax"></a>Składnia

W poniższych przykładach przedstawiono składnię rekordu anonimowego. Elementy rozdzielone jako `[item]` opcjonalne.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Podstawowy sposób użycia

Rekordy anonimowe są najlepiej traktowane jako typy rekordów F#, które nie muszą być zadeklarowane przed wystąpieniem.

Na przykład w tym miejscu, jak można wchodzić w interakcje z funkcją, która tworzy rekord anonimowy:

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

Poniższy przykład rozwija się na poprzednim `printCircleStats` z funkcją, która przyjmuje rekord anonimowy jako dane wejściowe:

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

Wywołanie `printCircleStats` z dowolnym typem rekordu anonimowego, który nie ma tego samego "kształtu", co typ wejściowy, nie powiedzie się:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Rekordy anonimowe struktury

Rekordy anonimowe można również zdefiniować jako `struct` struktury z opcjonalnym słowem kluczowym. Poniższy przykład rozszerza poprzedni, produkując i zużywając rekord anonimowy struct:

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

### <a name="structness-inference"></a>Wnioskowanie o strukturze

Rekordy anonimowe struct pozwalają również na "wnioskowanie struktury", w `struct` którym nie trzeba określać słowa kluczowego w witrynie wywołania. W tym przykładzie można `struct` elide `printCircleStats`słowa kluczowego podczas wywoływania:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

Odwrotny wzorzec - określając, `struct` gdy typ wejściowy nie jest struktury rekord anonimowy - nie powiedzie się skompilować.

## <a name="embedding-anonymous-records-within-other-types"></a>Osadzanie rekordów anonimowych w innych typach

Warto zadeklarować [dyskryminowane związki zawodowe,](discriminated-unions.md) których sprawy są rekordami. Jeśli jednak dane w rekordach są tego samego typu co unia dyskryminowana, należy zdefiniować wszystkie typy jako wzajemnie cykliczne. Korzystanie z rekordów anonimowych pozwala uniknąć tego ograniczenia. Poniżej przedstawiono przykładowy typ i funkcję, która pasuje do niego:

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

## <a name="copy-and-update-expressions"></a>Kopiowanie i aktualizowanie wyrażeń

Anonimowe rekordy obsługują budowę z [wyrażeniami kopiowania i aktualizacji](copy-and-update-record-expressions.md). Na przykład oto jak można skonstruować nowe wystąpienie rekordu anonimowego, który kopiuje istniejące dane:

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Jednak w przeciwieństwie do nazwanych rekordów rekordy anonimowe umożliwiają konstruowanie zupełnie innych formularzy z wyrażeniami kopiowania i aktualizacji. W powyższym przykładzie jest ten sam anonimowy rekord z poprzedniego przykładu i rozszerza go do nowego rekordu anonimowego:

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Istnieje również możliwość konstruowania rekordów anonimowych z wystąpień nazwanych rekordów:

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Można również kopiować dane do i z dokumentacji i struktury rekordów anonimowych:

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

## <a name="properties-of-anonymous-records"></a>Właściwości rekordów anonimowych

Anonimowe rekordy mają wiele cech, które są niezbędne do pełnego zrozumienia, w jaki sposób mogą być używane.

### <a name="anonymous-records-are-nominal"></a>Anonimowe rekordy są nominalne

Rekordy anonimowe są [typami nominalnymi](https://en.wikipedia.org/wiki/Nominal_type_system). Są one najlepiej traktowane jako nazwane typy [rekordów](records.md) (które są również nominalne), które nie wymagają deklaracji z góry.

Rozważmy następujący przykład z dwóch anonimowych deklaracji rekordu:

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

Wartości `x` `y` i mają różne typy i nie są ze sobą kompatybilne. Nie są one zbywalne i nie są porównywalne. Aby to zilustrować, należy wziąć pod uwagę odpowiednik rekordu o nazwie:

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Nie ma nic z natury różni się o anonimowych rekordów w porównaniu z ich odpowiednikami rekord, gdy dotyczące równoważności typu lub porównania.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Anonimowe zapisy wykorzystują równość strukturalną i porównanie

Podobnie jak typy rekordów, anonimowe rekordy są strukturalnie zbywalne i porównywalne. Jest to prawdą tylko wtedy, gdy wszystkie typy składników obsługują równość i porównanie, na przykład w przypadku typów rekordów. Aby obsługiwać równość lub porównanie, dwa anonimowe rekordy muszą mieć ten sam "kształt".

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Anonimowe rekordy są możliwe do serializacji

Można serializować rekordy anonimowe tak samo, jak w przypadku nazwanych rekordów. Oto przykład za pomocą [Newtonsoft.Json:](https://www.nuget.org/packages/Newtonsoft.Json/)

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Rekordy anonimowe są przydatne do wysyłania lekkich danych przez sieć bez konieczności definiowania domeny dla typów serializowanych/deserializowanych z góry.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Rekordy anonimowe współpracują z typami anonimowymi języka C#

Istnieje możliwość użycia interfejsu API .NET, który wymaga użycia [typów anonimowych języka C#.](../../csharp/programming-guide/classes-and-structs/anonymous-types.md) Typy anonimowe języka C# są trywialne do współdziałania przy użyciu rekordów anonimowych. W poniższym przykładzie pokazano, jak używać rekordów anonimowych do wywoływania przeciążenia [LINQ,](../../csharp/programming-guide/concepts/linq/index.md) które wymaga typu anonimowego:

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

Istnieje wiele innych interfejsów API używanych w całej .NET, które wymagają użycia przekazywania w typie anonimowym. Anonimowe rekordy są narzędziem do pracy z nimi.

## <a name="limitations"></a>Ograniczenia

Anonimowe rekordy mają pewne ograniczenia w ich użyciu. Niektóre z nich są nieodłącznym elementem ich projektu, ale inne są podatne na zmiany.

### <a name="limitations-with-pattern-matching"></a>Ograniczenia z dopasowaniem wzorców

Rekordy anonimowe nie obsługują dopasowywania wzorców, w przeciwieństwie do nazwanych rekordów. Istnieją trzy powody:

1. Wzorzec musiałby uwzględniać każde pole rekordu anonimowego, w przeciwieństwie do nazwanych typów rekordów. Dzieje się tak, ponieważ rekordy anonimowe nie obsługują podtypowania strukturalnego — są to typy nominalne.
2. Ze względu na (1) nie ma możliwości, aby dodatkowe wzorce w wyrażeniu dopasowania wzorca, jak każdy odrębny wzorzec będzie oznaczać inny typ rekordu anonimowego.
3. Ze względu na (3) każdy wzorzec rekordu anonimowego będzie bardziej szczegółowy niż użycie notacji "kropka".

Istnieje sugestia otwartego języka, aby [umożliwić dopasowywanie wzorców w ograniczonych kontekstach.](https://github.com/fsharp/fslang-suggestions/issues/713)

### <a name="limitations-with-mutability"></a>Ograniczenia z zmienność

Obecnie nie jest możliwe zdefiniowanie `mutable` rekordu anonimowego z danymi. Istnieje [sugestia otwartego języka,](https://github.com/fsharp/fslang-suggestions/issues/732) aby umożliwić zmienne dane.

### <a name="limitations-with-struct-anonymous-records"></a>Ograniczenia z rekordami anonimowymi struct

Nie można zadeklarować rekordów anonimowych `IsByRefLike` `IsReadOnly`jako lub . Istnieje [sugestia otwartego](https://github.com/fsharp/fslang-suggestions/issues/712) języka `IsByRefLike` `IsReadOnly` dla i anonimowych rekordów.
