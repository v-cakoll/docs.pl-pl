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
# <a name="anonymous-records"></a><span data-ttu-id="e3988-103">Rekordy anonimowe</span><span class="sxs-lookup"><span data-stu-id="e3988-103">Anonymous Records</span></span>

<span data-ttu-id="e3988-104">Rekordy anonimowe są proste agregaty nazwanych wartości, które nie muszą być zadeklarowane przed użyciem.</span><span class="sxs-lookup"><span data-stu-id="e3988-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="e3988-105">Można zadeklarować je jako struktury lub typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="e3988-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="e3988-106">Są to domyślnie typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="e3988-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3988-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3988-107">Syntax</span></span>

<span data-ttu-id="e3988-108">W poniższych przykładach przedstawiono składnię rekordu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="e3988-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="e3988-109">Elementy rozdzielone jako `[item]` opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e3988-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="e3988-110">Podstawowy sposób użycia</span><span class="sxs-lookup"><span data-stu-id="e3988-110">Basic usage</span></span>

<span data-ttu-id="e3988-111">Rekordy anonimowe są najlepiej traktowane jako typy rekordów F#, które nie muszą być zadeklarowane przed wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="e3988-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="e3988-112">Na przykład w tym miejscu, jak można wchodzić w interakcje z funkcją, która tworzy rekord anonimowy:</span><span class="sxs-lookup"><span data-stu-id="e3988-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="e3988-113">Poniższy przykład rozwija się na poprzednim `printCircleStats` z funkcją, która przyjmuje rekord anonimowy jako dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="e3988-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="e3988-114">Wywołanie `printCircleStats` z dowolnym typem rekordu anonimowego, który nie ma tego samego "kształtu", co typ wejściowy, nie powiedzie się:</span><span class="sxs-lookup"><span data-stu-id="e3988-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="e3988-115">Rekordy anonimowe struktury</span><span class="sxs-lookup"><span data-stu-id="e3988-115">Struct anonymous records</span></span>

<span data-ttu-id="e3988-116">Rekordy anonimowe można również zdefiniować jako `struct` struktury z opcjonalnym słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="e3988-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="e3988-117">Poniższy przykład rozszerza poprzedni, produkując i zużywając rekord anonimowy struct:</span><span class="sxs-lookup"><span data-stu-id="e3988-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="e3988-118">Wnioskowanie o strukturze</span><span class="sxs-lookup"><span data-stu-id="e3988-118">Structness inference</span></span>

<span data-ttu-id="e3988-119">Rekordy anonimowe struct pozwalają również na "wnioskowanie struktury", w `struct` którym nie trzeba określać słowa kluczowego w witrynie wywołania.</span><span class="sxs-lookup"><span data-stu-id="e3988-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="e3988-120">W tym przykładzie można `struct` elide `printCircleStats`słowa kluczowego podczas wywoływania:</span><span class="sxs-lookup"><span data-stu-id="e3988-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="e3988-121">Odwrotny wzorzec - określając, `struct` gdy typ wejściowy nie jest struktury rekord anonimowy - nie powiedzie się skompilować.</span><span class="sxs-lookup"><span data-stu-id="e3988-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="e3988-122">Osadzanie rekordów anonimowych w innych typach</span><span class="sxs-lookup"><span data-stu-id="e3988-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="e3988-123">Warto zadeklarować [dyskryminowane związki zawodowe,](discriminated-unions.md) których sprawy są rekordami.</span><span class="sxs-lookup"><span data-stu-id="e3988-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="e3988-124">Jeśli jednak dane w rekordach są tego samego typu co unia dyskryminowana, należy zdefiniować wszystkie typy jako wzajemnie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="e3988-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="e3988-125">Korzystanie z rekordów anonimowych pozwala uniknąć tego ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="e3988-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="e3988-126">Poniżej przedstawiono przykładowy typ i funkcję, która pasuje do niego:</span><span class="sxs-lookup"><span data-stu-id="e3988-126">What follows is an example type and function that pattern matches over it:</span></span>

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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="e3988-127">Kopiowanie i aktualizowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e3988-127">Copy and update expressions</span></span>

<span data-ttu-id="e3988-128">Anonimowe rekordy obsługują budowę z [wyrażeniami kopiowania i aktualizacji](copy-and-update-record-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e3988-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="e3988-129">Na przykład oto jak można skonstruować nowe wystąpienie rekordu anonimowego, który kopiuje istniejące dane:</span><span class="sxs-lookup"><span data-stu-id="e3988-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="e3988-130">Jednak w przeciwieństwie do nazwanych rekordów rekordy anonimowe umożliwiają konstruowanie zupełnie innych formularzy z wyrażeniami kopiowania i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="e3988-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="e3988-131">W powyższym przykładzie jest ten sam anonimowy rekord z poprzedniego przykładu i rozszerza go do nowego rekordu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="e3988-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="e3988-132">Istnieje również możliwość konstruowania rekordów anonimowych z wystąpień nazwanych rekordów:</span><span class="sxs-lookup"><span data-stu-id="e3988-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="e3988-133">Można również kopiować dane do i z dokumentacji i struktury rekordów anonimowych:</span><span class="sxs-lookup"><span data-stu-id="e3988-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="e3988-134">Właściwości rekordów anonimowych</span><span class="sxs-lookup"><span data-stu-id="e3988-134">Properties of anonymous records</span></span>

<span data-ttu-id="e3988-135">Anonimowe rekordy mają wiele cech, które są niezbędne do pełnego zrozumienia, w jaki sposób mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="e3988-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="e3988-136">Anonimowe rekordy są nominalne</span><span class="sxs-lookup"><span data-stu-id="e3988-136">Anonymous records are nominal</span></span>

<span data-ttu-id="e3988-137">Rekordy anonimowe są [typami nominalnymi](https://en.wikipedia.org/wiki/Nominal_type_system).</span><span class="sxs-lookup"><span data-stu-id="e3988-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="e3988-138">Są one najlepiej traktowane jako nazwane typy [rekordów](records.md) (które są również nominalne), które nie wymagają deklaracji z góry.</span><span class="sxs-lookup"><span data-stu-id="e3988-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="e3988-139">Rozważmy następujący przykład z dwóch anonimowych deklaracji rekordu:</span><span class="sxs-lookup"><span data-stu-id="e3988-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="e3988-140">Wartości `x` `y` i mają różne typy i nie są ze sobą kompatybilne.</span><span class="sxs-lookup"><span data-stu-id="e3988-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="e3988-141">Nie są one zbywalne i nie są porównywalne.</span><span class="sxs-lookup"><span data-stu-id="e3988-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="e3988-142">Aby to zilustrować, należy wziąć pod uwagę odpowiednik rekordu o nazwie:</span><span class="sxs-lookup"><span data-stu-id="e3988-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="e3988-143">Nie ma nic z natury różni się o anonimowych rekordów w porównaniu z ich odpowiednikami rekord, gdy dotyczące równoważności typu lub porównania.</span><span class="sxs-lookup"><span data-stu-id="e3988-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="e3988-144">Anonimowe zapisy wykorzystują równość strukturalną i porównanie</span><span class="sxs-lookup"><span data-stu-id="e3988-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="e3988-145">Podobnie jak typy rekordów, anonimowe rekordy są strukturalnie zbywalne i porównywalne.</span><span class="sxs-lookup"><span data-stu-id="e3988-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="e3988-146">Jest to prawdą tylko wtedy, gdy wszystkie typy składników obsługują równość i porównanie, na przykład w przypadku typów rekordów.</span><span class="sxs-lookup"><span data-stu-id="e3988-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="e3988-147">Aby obsługiwać równość lub porównanie, dwa anonimowe rekordy muszą mieć ten sam "kształt".</span><span class="sxs-lookup"><span data-stu-id="e3988-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="e3988-148">Anonimowe rekordy są możliwe do serializacji</span><span class="sxs-lookup"><span data-stu-id="e3988-148">Anonymous records are serializable</span></span>

<span data-ttu-id="e3988-149">Można serializować rekordy anonimowe tak samo, jak w przypadku nazwanych rekordów.</span><span class="sxs-lookup"><span data-stu-id="e3988-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="e3988-150">Oto przykład za pomocą [Newtonsoft.Json:](https://www.nuget.org/packages/Newtonsoft.Json/)</span><span class="sxs-lookup"><span data-stu-id="e3988-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="e3988-151">Rekordy anonimowe są przydatne do wysyłania lekkich danych przez sieć bez konieczności definiowania domeny dla typów serializowanych/deserializowanych z góry.</span><span class="sxs-lookup"><span data-stu-id="e3988-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="e3988-152">Rekordy anonimowe współpracują z typami anonimowymi języka C#</span><span class="sxs-lookup"><span data-stu-id="e3988-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="e3988-153">Istnieje możliwość użycia interfejsu API .NET, który wymaga użycia [typów anonimowych języka C#.](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="e3988-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="e3988-154">Typy anonimowe języka C# są trywialne do współdziałania przy użyciu rekordów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="e3988-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="e3988-155">W poniższym przykładzie pokazano, jak używać rekordów anonimowych do wywoływania przeciążenia [LINQ,](../../csharp/programming-guide/concepts/linq/index.md) które wymaga typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="e3988-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="e3988-156">Istnieje wiele innych interfejsów API używanych w całej .NET, które wymagają użycia przekazywania w typie anonimowym.</span><span class="sxs-lookup"><span data-stu-id="e3988-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="e3988-157">Anonimowe rekordy są narzędziem do pracy z nimi.</span><span class="sxs-lookup"><span data-stu-id="e3988-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="e3988-158">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="e3988-158">Limitations</span></span>

<span data-ttu-id="e3988-159">Anonimowe rekordy mają pewne ograniczenia w ich użyciu.</span><span class="sxs-lookup"><span data-stu-id="e3988-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="e3988-160">Niektóre z nich są nieodłącznym elementem ich projektu, ale inne są podatne na zmiany.</span><span class="sxs-lookup"><span data-stu-id="e3988-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="e3988-161">Ograniczenia z dopasowaniem wzorców</span><span class="sxs-lookup"><span data-stu-id="e3988-161">Limitations with pattern matching</span></span>

<span data-ttu-id="e3988-162">Rekordy anonimowe nie obsługują dopasowywania wzorców, w przeciwieństwie do nazwanych rekordów.</span><span class="sxs-lookup"><span data-stu-id="e3988-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="e3988-163">Istnieją trzy powody:</span><span class="sxs-lookup"><span data-stu-id="e3988-163">There are three reasons:</span></span>

1. <span data-ttu-id="e3988-164">Wzorzec musiałby uwzględniać każde pole rekordu anonimowego, w przeciwieństwie do nazwanych typów rekordów.</span><span class="sxs-lookup"><span data-stu-id="e3988-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="e3988-165">Dzieje się tak, ponieważ rekordy anonimowe nie obsługują podtypowania strukturalnego — są to typy nominalne.</span><span class="sxs-lookup"><span data-stu-id="e3988-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="e3988-166">Ze względu na (1) nie ma możliwości, aby dodatkowe wzorce w wyrażeniu dopasowania wzorca, jak każdy odrębny wzorzec będzie oznaczać inny typ rekordu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="e3988-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="e3988-167">Ze względu na (3) każdy wzorzec rekordu anonimowego będzie bardziej szczegółowy niż użycie notacji "kropka".</span><span class="sxs-lookup"><span data-stu-id="e3988-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="e3988-168">Istnieje sugestia otwartego języka, aby [umożliwić dopasowywanie wzorców w ograniczonych kontekstach.](https://github.com/fsharp/fslang-suggestions/issues/713)</span><span class="sxs-lookup"><span data-stu-id="e3988-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="e3988-169">Ograniczenia z zmienność</span><span class="sxs-lookup"><span data-stu-id="e3988-169">Limitations with mutability</span></span>

<span data-ttu-id="e3988-170">Obecnie nie jest możliwe zdefiniowanie `mutable` rekordu anonimowego z danymi.</span><span class="sxs-lookup"><span data-stu-id="e3988-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="e3988-171">Istnieje [sugestia otwartego języka,](https://github.com/fsharp/fslang-suggestions/issues/732) aby umożliwić zmienne dane.</span><span class="sxs-lookup"><span data-stu-id="e3988-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="e3988-172">Ograniczenia z rekordami anonimowymi struct</span><span class="sxs-lookup"><span data-stu-id="e3988-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="e3988-173">Nie można zadeklarować rekordów anonimowych `IsByRefLike` `IsReadOnly`jako lub .</span><span class="sxs-lookup"><span data-stu-id="e3988-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="e3988-174">Istnieje [sugestia otwartego](https://github.com/fsharp/fslang-suggestions/issues/712) języka `IsByRefLike` `IsReadOnly` dla i anonimowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="e3988-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
