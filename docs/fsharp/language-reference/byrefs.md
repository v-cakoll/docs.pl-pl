---
title: 'Zkratka (F #)'
description: 'Więcej informacji na temat byref i byref typy w języku F #, które są używane na potrzeby programowania niskiego poziomu.'
ms.date: 09/02/2018
ms.openlocfilehash: 6131104e4325f77da84368c337f998c6b2b5309b
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46485486"
---
# <a name="byrefs"></a>Zkratka

F # zawiera dwa obszary najważniejszych funkcji, które zajmują w obszarze programowania niskiego poziomu:

* `byref` / `inref` / `outref` Typów, które są wskaźnikami zarządzanymi. Mają one ograniczenia dotyczące użycia, więc, że nie można skompilować program, który jest nieprawidłowy w czasie wykonywania.
* A `byref`— takie jak struktury, która jest [struktury](structures.md) ma podobną semantyką i takim samym ograniczeniom kompilacji, jak `byref<'T>`. Przykładem jest <xref:System.Span%601>.

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

Istnieją trzy rodzaje `byref`:

* `inref<'T>`, wskaźnika zarządzanych do odczytywania wartości podstawowej.
* `outref<'T>`, wskaźnika zarządzanych do zapisywania wartości podstawowej.
* `byref<'T>`, wskaźnika zarządzanych do odczytywania i zapisywania podstawową wartość.

A `byref<'T>` mogą być przekazywane w przypadku gdy `inref<'T>` oczekuje. Podobnie `byref<'T>` mogą być przekazywane w przypadku gdy `outref<'T>` oczekuje.

## <a name="using-byrefs"></a>Za pomocą zkratka

Aby użyć `inref<'T>`, należy uzyskać wartość wskaźnika z `&`:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let dt = DateTime.Now
f &dt // Pass a pointer to 'dt'
```

Można zapisać do wskaźnika za pomocą `outref<'T>` lub `byref<'T>`, należy również upewnić wartość, Pobierz wskaźnik do `mutable`.

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

Jeśli piszesz wskaźnika zamiast wczytaniem go, należy wziąć pod uwagę przy użyciu `outref<'T>` zamiast `byref<'T>`.

### <a name="inref-semantics"></a>Semantyka Inref

Rozważmy poniższy kod:

```fsharp
let f (x: inref<SomeStruct>) = s.SomeField
```

Semantycznie oznacza to, że:

* Posiadacz `x` wskaźnika można używać go tylko odczytać wartości.
* Dowolny wskaźnik uzyskanych do `struct` pola zagnieżdżone w obrębie `SomeStruct` podano typ `inref<_>`.

Oto również wartość true:

* Istnieje nie domniemanie na to, że inne wątki, lub aliasy nie ma dostęp do zapisu `x`.
* Nie ma żadnych domniemanie, `SomeStruct` można modyfikować na mocy niniejszej `x` trwa `inref`.

Jednak dla języka F # wartości typów, które **są** niemodyfikowalny `this` wskaźnik wywnioskowana jest `inref`.

Wszystkie te reguły, które są razem oznaczają, że właściciel `inref` wskaźnik nie może modyfikować natychmiastowego zawartość pamięci wskazywany.

### <a name="outref-semantics"></a>Semantyka Outref

Celem `outref<'T>` jest, aby wskazać, że wskaźnik powinni czytać tylko z. Nieoczekiwanie `outref<'T>` zezwolenia na odczytywanie podstawowych wartości niezależnie od jego nazwę. Jest to na potrzeby zgodności. Semantycznie `outref<'T>` nie różni się od `byref<'T>`.

### <a name="interop-with-c"></a>Współdziałanie z języka C# #

C# obsługuje `in ref` i `out ref` słów kluczowych, oprócz `ref` zwraca. W poniższej tabeli przedstawiono, jak F # interpretuje co C# emituje:

|Konstrukcja w języku C#|Wnioskuje F #|
|------------|---------|
|`ref` Wartość zwracana|`outref<'T>`|
|`ref readonly` Wartość zwracana|`inref<'T>`|
|`in ref` Parametr|`inref<'T>`|
|`out ref` Parametr|`outref<'T>`|

W poniższej tabeli przedstawiono, jakie F # emituje:

|Konstrukcji F #|Konstrukcja emitowany|
|------------|-----------------|
|`inref<'T>` Argument|`[In]` argument atrybutu|
|`inref<'T>` Wróć|`modreq` atrybut na wartość|
|`inref<'T>` w abstrakcyjny gniazdo lub wdrożenia|`modreq` argument lub zwracany|
|`outref<'T>` Argument|`[Out]` argument atrybutu|

### <a name="type-inference-and-overloading-rules"></a>Wnioskowanie o typie i przeciążenie reguły

`inref<'T>` Typ jest wnioskowany przez kompilator F # w następujących przypadkach:

1. .NET parametr lub zwracany typ, który ma `IsReadOnly` atrybutu.
2. `this` Wskaźnika na typie struct, który nie ma tych pól.
3. Adres lokalizacji pamięci pochodzi z innego `inref<_>` wskaźnika.

Gdy niejawne adres `inref` jest przełączana, przeciążenia z nieprawidłowym argumentem typu `SomeType` jest preferowany do przeciążenia z nieprawidłowym argumentem typu `inref<SomeType>`. Na przykład:

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

W obu przypadkach przeciążenia, biorąc `System.DateTime` są rozwiązywane zamiast przeciążenia, biorąc `inref<System.DateTime>`.

## <a name="byref-like-structs"></a>ByRef — podobne do struktury

Oprócz `byref` / `inref` / `outref` Trójka, można zdefiniować własne struktur, które można stosować się do `byref`— takich jak semantyki. Jest to zrobić za pomocą <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atrybutu:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` nie oznacza `Struct`. Zarówno musi być obecny w typie.

Element "`byref`— takich jak" struct w języku F # to typ wartości powiązanym ze stosu. Nigdy nie zostanie przydzielona na stosie zarządzanym. A `byref`— takie jak struktura jest przydatne w przypadku programowania o wysokiej wydajności, jak są wymuszane za pomocą zestawu silne testów o okresie istnienia i -capture. Dostępne są następujące reguły:

* One może służyć jako parametry funkcji, parametrów metody, zmienne lokalne, metoda zwraca wartość.
* Nie mogą one być statyczne lub wystąpieniami elementów członkowskich klasy lub struktury normalne.
* Nie można przechwycić według konstrukcji zamknięcia (`async` metod lub wyrażenia lambda).
* Nie mogą one służyć jako parametr ogólny.

Ten ostatni punkt ma kluczowe znaczenie dla F # potoku programowaniu w stylu jako `|>` jest funkcja ogólna, które parametryzuje dane jego typów wejściowych. To ograniczenie może zostać złagodzone dla `|>` w przyszłości, ponieważ jest wbudowana i nie wprowadzać wszelkie wywołania-śródwierszowych ogólne funkcje w jej treści.

Mimo że te reguły ograniczają bardzo silnie użycia, to zrobią do spełnienia obietnicy o wysokiej wydajności obliczeniowej w bezpieczny sposób.

## <a name="byref-returns"></a>Wartości zwracane ByRef

Wartości zwracane ByRef z F # funkcji lub elementów członkowskich może być tworzone i używane. Podczas używania `byref`— metodę zwracającą, wartość jest wyłuskiwany niejawnie. Na przykład:

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

Aby uniknąć niejawne wyłuskania, takich jak przekazywaniem odwołań do wielu wywołań łańcuchowych, należy użyć `&x` (gdzie `x` jest wartością).

Możesz także bezpośrednio przypisać do zwrotu `byref`. Należy wziąć pod uwagę następujący program (wysoce imperatywne):

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

## <a name="scoping-for-byrefs"></a>Wyznaczanie zakresu dla zkratka

A `let`— powiązana wartość nie może zawierać odwołanie, przekracza zakres, w którym został zdefiniowany. Na przykład że jest niedozwolone:

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

Uniemożliwia to wprowadzenie różne wyniki w zależności od tego, jeśli kompilujesz z optymalizacjami lub wyłączyć.
