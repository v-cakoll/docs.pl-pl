---
title: Byrefs
description: Dowiedz się więcej o byref i byref-jak typy w F#, które są używane do programowania niskiego poziomu.
ms.date: 11/04/2019
ms.openlocfilehash: 527f465ee87fe153a2deae1306b6730531dc4123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187051"
---
# <a name="byrefs"></a>Byrefs

F# ma dwa główne obszary funkcji, które zajmują się w przestrzeni programowania niskiego poziomu:

* `byref` / `inref` Typy, / `outref` które są wskaźnikami zarządzanymi. Mają ograniczenia dotyczące użycia, dzięki czemu nie można skompilować program, który jest nieprawidłowy w czasie wykonywania.
* -jak `byref`struct, który jest [strukturą,](structures.md) która ma podobną semantykę `byref<'T>`i te same ograniczenia czasu kompilacji co . Jednym z <xref:System.Span%601>przykładów jest .

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

## <a name="byref-inref-and-outref"></a>Byref, inref i outref

Istnieją trzy formy: `byref`

* `inref<'T>`, wskaźnik zarządzany do odczytu wartości źródłowej.
* `outref<'T>`, wskaźnik zarządzany do zapisu do wartości źródłowej.
* `byref<'T>`, wskaźnik zarządzany do odczytu i zapisu wartości źródłowej.

A `byref<'T>` mogą być `inref<'T>` przekazywane, gdzie oczekuje się. Podobnie `byref<'T>` można przekazać, gdzie `outref<'T>` oczekuje się.

## <a name="using-byrefs"></a>Korzystanie z byrefs

Aby użyć `inref<'T>`, musisz uzyskać wartość `&`wskaźnika z:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Aby zapisać wskaźnik za `outref<'T>` pomocą `byref<'T>`lub , należy również zrobić wartość `mutable`chwycić wskaźnik do .

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

Jeśli piszesz tylko wskaźnik zamiast go `outref<'T>` czytać, `byref<'T>`rozważ użycie zamiast .

### <a name="inref-semantics"></a>Semantyka inref

Spójrzmy na poniższy kod:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Semantycznie oznacza to, co następuje:

* Posiadacz wskaźnika `x` może go używać tylko do odczytu wartości.
* Każdy wskaźnik uzyskany do `struct` `SomeStruct` pól zagnieżdżonych w danym typu `inref<_>`.

Prawdą jest również:

* Nie ma żadnych implikacji, że inne wątki lub aliasy nie mają dostępu do zapisu . `x`
* Nie ma implikacji, `SomeStruct` która jest niezmienna `x` ze `inref`względu na to, że jest .

Jednak dla typów wartości **are** F#, które `this` są niezmienne, wskaźnik `inref`jest wywnioskować, aby być .

Wszystkie te reguły razem oznacza, `inref` że posiadacz wskaźnika nie może modyfikować natychmiastowej zawartości pamięci jest wskazywany.

### <a name="outref-semantics"></a>Semantyka Outref

Celem `outref<'T>` jest wskazanie, że wskaźnik powinien być tylko zapisywany. Nieoczekiwanie `outref<'T>` pozwala na odczyt wartości źródłowej pomimo jego nazwy. Ma to na celu zgodność. Semantycznie, `outref<'T>` nie `byref<'T>`różni się od .

### <a name="interop-with-c"></a>Interop z C\#

C# obsługuje `in ref` `out ref` i słowa kluczowe, `ref` oprócz zwraca. W poniższej tabeli pokazano, jak F# interpretuje, co elewuje c#:

|Konstrukcja języka C#|Wnioskowanie F#|
|------------|---------|
|`ref`zwracawartość|`outref<'T>`|
|`ref readonly`zwracawartość|`inref<'T>`|
|`in ref`Parametr|`inref<'T>`|
|`out ref`Parametr|`outref<'T>`|

W poniższej tabeli przedstawiono, co f# emituje:

|Konstrukcja Języka F#|Emitowana konstrukcja|
|------------|-----------------|
|Argument `inref<'T>`|`[In]`atrybut na argument|
|`inref<'T>`Zwraca|`modreq`atrybut na wartości|
|`inref<'T>`w abstrakcyjnym gnieździe lub implementacji|`modreq`na argument lub powrót|
|Argument `outref<'T>`|`[Out]`atrybut na argument|

### <a name="type-inference-and-overloading-rules"></a>Reguły wnioskowania i przeciążenia typu

Typ `inref<'T>` jest wywnioskowany przez kompilator F# w następujących przypadkach:

1. Parametr .NET lub typ zwracany, który ma atrybut. `IsReadOnly`
2. Wskaźnik `this` na typ struktury, który nie ma pól zmiennoskowych.
3. Adres lokalizacji pamięci pochodzące z `inref<_>` innego wskaźnika.

Gdy niejawny `inref` adres niejawnego jest podejmowana, `SomeType` przeciążenie z argumentem typu `inref<SomeType>`jest preferowane przeciążenia z argumentem typu . Przykład:

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

W obu przypadkach przeciążenia biorąc `System.DateTime` są rozwiązywane, `inref<System.DateTime>`a nie przeciążenia biorąc .

## <a name="byref-like-structs"></a>Struktury podobne do Byref

`byref` / `outref` Oprócz / trio, można zdefiniować własne struktury, które mogą `byref`przylegać do -jak semantyka. `inref` Odbywa się to <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> za pomocą atrybutu:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`nie oznacza `Struct`. Oba muszą być obecne na typie.

Struktura`byref`"-like" w języku F# jest typem wartości powiązanym ze stosem. Nigdy nie jest przydzielany na zarządzanym stercie. Struktura `byref`-like jest przydatna w programowaniu o wysokiej wydajności, ponieważ jest wymuszana z zestawem silnych kontroli dotyczących okresu istnienia i braku przechwytywania. Zasady są następujące:

* Mogą być używane jako parametry funkcji, parametry metody, zmienne lokalne, zwraca metoda.
* Nie mogą być statyczne lub wystąpienia elementów członkowskich klasy lub normalnej struktury.
* Nie mogą być przechwytywane`async` przez dowolną konstrukcję zamknięcia (metody lub wyrażenia lambda).
* Nie można ich używać jako parametru ogólnego.

Ten ostatni punkt ma kluczowe znaczenie dla programowania `|>` w stylu potoku F#, podobnie jak funkcja ogólna, która parametryzuje jego typy danych wejściowych. Ograniczenie to może `|>` być złagodzone w przyszłości, ponieważ jest wbudowane i nie wykonuje żadnych wywołań do funkcji ogólnych niewbudowanych w jego treści.

Chociaż reguły te zdecydowanie ograniczają użycie, robią to, aby spełnić obietnicę obliczeń o wysokiej wydajności w bezpieczny sposób.

## <a name="byref-returns"></a>Zwroty Byref

Byref zwraca z funkcji F# lub elementów członkowskich mogą być produkowane i używane. Podczas korzystania `byref`z -returning metody, wartość jest niejawnie wyłusk. Przykład:

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

Aby zwrócić wartość byref, zmienna, która zawiera wartość musi żyć dłużej niż bieżący zakres.
Ponadto, aby zwrócić byref, użyj `&value` (gdzie wartość jest zmienna, która żyje dłużej niż bieżący zakres).

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

Aby uniknąć niejawne wywanie, takie jak `&x` przekazywanie `x` odwołania za pośrednictwem wielu wywołań łańcuchowych, użyj (gdzie jest wartość).

Można również bezpośrednio przypisać do `byref`zwrotu . Należy wziąć pod uwagę następujący (bardzo imperatyw) program:

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
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

## <a name="scoping-for-byrefs"></a>Zakres dla byrefs

Wartość `let`-bound nie może mieć odwołania przekracza zakres, w którym została zdefiniowana. Na przykład nie zezwala się na następujące czynności:

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

Zapobiega to uzyskiwanie różnych wyników w zależności od tego, czy skompilować z optymalizacji, czy nie.
