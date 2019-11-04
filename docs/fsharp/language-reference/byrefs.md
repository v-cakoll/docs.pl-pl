---
title: Byrefs
description: Dowiedz się więcej o typach ByRef i ByRef F#, które są używane w programowaniu niskiego poziomu.
ms.date: 09/02/2018
ms.openlocfilehash: 453de2a5f30dc532dcd7f873b7f5defefdc814cd
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424774"
---
# <a name="byrefs"></a>Byrefs

F#Program ma dwa główne obszary funkcji, które zajmują miejsce w programowaniu na niskim poziomie:

* `byref`/`inref`/typy `outref`, które są zarządzanymi wskaźnikami. Mają ograniczenia dotyczące użycia, dzięki czemu nie można skompilować programu, który jest nieprawidłowy w czasie wykonywania.
* Struktury podobnej do `byref`, która jest [strukturą](structures.md) , która ma podobną semantykę i te same ograniczenia czasu kompilacji co `byref<'T>`. Jeden przykład jest <xref:System.Span%601>.

## <a name="syntax"></a>Składnia

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a>ByRef, inref i outref

Istnieją trzy formy `byref`:

* `inref<'T>`, zarządzany wskaźnik odczytu wartości źródłowej.
* `outref<'T>`, zarządzany wskaźnik zapisu do podstawowej wartości.
* `byref<'T>`, zarządzany wskaźnik służący do odczytywania i zapisywania podstawowej wartości.

`byref<'T>` można przekazywać, gdy oczekiwany jest `inref<'T>`. Podobnie `byref<'T>` można przekazywać, gdy oczekiwany jest `outref<'T>`.

## <a name="using-byrefs"></a>Korzystanie z ByRef

Aby użyć `inref<'T>`, należy uzyskać wartość wskaźnika z `&`:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Aby zapisać na wskaźniku przy użyciu `outref<'T>` lub `byref<'T>`, należy również wprowadzić wartość wskaźnika do `mutable`.

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

Jeśli chcesz tylko napisać wskaźnik zamiast odczytywania go, rozważ użycie `outref<'T>` zamiast `byref<'T>`.

### <a name="inref-semantics"></a>Semantyka Inref

Rozważmy następujący kod:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Semantycznie:

* Posiadacz wskaźnika `x` może go użyć tylko do odczytu wartości.
* Każdy wskaźnik uzyskany do pól `struct` zagnieżdżonych w `SomeStruct` jest podanym typem `inref<_>`.

Spełnione są również następujące kwestie:

* Nie ma żadnego znaczenia, że inne wątki lub aliasy nie mają dostępu do zapisu do `x`.
* Nie ma żadnych implikacji, że `SomeStruct` jest niemodyfikowalny na podstawie `x` `inref`.

Jednakże w przypadku F# typów wartości, które **są** niezmienne, wskaźnik `this` jest wywnioskowany jako `inref`.

Wszystkie te reguły razem oznaczają, że posiadacz wskaźnika `inref` może nie modyfikować natychmiastowej zawartości wskazanej pamięci.

### <a name="outref-semantics"></a>Semantyka Outref

Celem `outref<'T>` jest wskazanie, że wskaźnik powinien być tylko do odczytu. Nieoczekiwanie, `outref<'T>` umożliwia odczytywanie wartości podstawowej pomimo jej nazwy. Jest to przeznaczone do celów zgodności. Semantyka `outref<'T>` nie różni się od `byref<'T>`.

### <a name="interop-with-c"></a>Współdziałanie z\# C

C#Program obsługuje słowa kluczowe `in ref` i `out ref`, a także zwraca `ref`. W poniższej tabeli przedstawiono, F# w jaki sposób C# interpretuje emitowane przez niego emisje:

|C#Konstruuj|F#wnioskuje|
|------------|---------|
|`ref` wartość zwracana|`outref<'T>`|
|`ref readonly` wartość zwracana|`inref<'T>`|
|`in ref` parametr|`inref<'T>`|
|`out ref` parametr|`outref<'T>`|

W poniższej tabeli przedstawiono, F# co emituje:

|F#Konstruuj|Wyemitowana konstrukcja|
|------------|-----------------|
|`inref<'T>` argument|`[In]` atrybutu w argumencie|
|`inref<'T>` Zwróć|`modreq` atrybutu wartości|
|`inref<'T>` w nieabstrakcyjnym gnieździe lub implementacji|`modreq` argumentu lub Return|
|`outref<'T>` argument|`[Out]` atrybutu w argumencie|

### <a name="type-inference-and-overloading-rules"></a>Wnioskowanie o typie i reguły przeciążania

Typ `inref<'T>` jest wywnioskowany przez F# kompilator w następujących przypadkach:

1. Parametr .NET lub zwracany typ, który ma atrybut `IsReadOnly`.
2. `this` wskaźnik na typie struktury, który nie ma modyfikowalnych pól.
3. Adres lokalizacji pamięci pochodnej od innego wskaźnika `inref<_>`.

Gdy niejawny adres `inref` jest pobierany, do przeciążenia z argumentem typu `inref<SomeType>`jest preferowane Przeciążenie z argumentem typu `SomeType`. Na przykład:

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

W obu przypadkach przeciążenia pobierające `System.DateTime` są rozwiązywane, a nie przeciążenia `inref<System.DateTime>`.

## <a name="byref-like-structs"></a>Struktury podobne do ByRef

Oprócz `byref`/`inref`/`outref` trójka można definiować własne struktury, które mogą być zgodne z semantyką przypominającą `byref`. Jest to realizowane z atrybutem <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` nie implikuje `Struct`. Oba muszą być obecne w typie.

Struktura "`byref`like" w F# jest typem wartości związanym ze stosem. Nigdy nie jest przydzielany na zarządzanym stosie. Struktura przypominająca `byref`jest przydatna w programowaniu o wysokiej wydajności, ponieważ jest wymuszana z zestawem silnych testów dotyczących czasu istnienia i braku przechwytywania. Reguły są następujące:

* Mogą one być używane jako parametry funkcji, parametry metody, zmienne lokalne, Metoda Return.
* Nie mogą być statyczne ani składowe wystąpień klasy ani normalnej struktury.
* Nie mogą być przechwytywane przez żadną konstrukcję zamknięcia (`async` metody lub wyrażenia lambda).
* Nie mogą być używane jako parametr generyczny.

Ten ostatni punkt jest decydujący F# dla programowania w stylu potoku, ponieważ `|>` jest funkcją ogólną, która parameterizes jej typy wejściowe. To ograniczenie może być swobodne w przypadku `|>` w przyszłości, ponieważ jest ono wbudowane i nie wykonuje żadnych wywołań funkcji ogólnych nienależących do wiersza w treści.

Chociaż te reguły bardzo zdecydowanie ograniczają użycie, robią to w celu zapewnienia bezpieczeństwa obliczeń o wysokiej wydajności w bezpieczny sposób.

## <a name="byref-returns"></a>Zwracane przez ByRef

Element ByRef Return F# from Functions lub memberss może być produkowany i zużywany. W przypadku używania metody zwracającej `byref`, wartość jest niejawnie wykorzystana. Na przykład:

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

Aby uniknąć niejawnego odwołania, na przykład przekazywania odwołania przez wiele wywołań łańcucha, użyj `&x` (gdzie `x` jest wartością).

Można również bezpośrednio przypisać do `byref`zwracanego. Weź pod uwagę następujący (wysoce bezwzględny) program:

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override __.ToString() = String.Join(' ', nums)

    member __.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

Jest to produkt wyjściowy:

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>Określanie zakresu dla ByRef

Wartość powiązana z `let`nie może mieć odwołania przekroczenia zakresu, w którym został zdefiniowany. Na przykład następujące elementy są niedozwolone:

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

Dzięki temu można uzyskać różne wyniki w zależności od tego, czy kompilacja została skompilowana z optymalizacją.
