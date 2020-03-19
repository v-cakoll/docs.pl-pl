---
title: C# — konwencje kodowania
description: Podczas pisania kodu F# poznaj ogólne wskazówki i idiomy.
ms.date: 01/15/2020
ms.openlocfilehash: 7266211e501bdb52564220781e2347d1aceaf296
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400310"
---
# <a name="f-coding-conventions"></a>C# — konwencje kodowania

Następujące konwencje są formułowane z doświadczenia pracy z dużych baz kodu F#. [Pięć zasad dobrego kodu F#](index.md#five-principles-of-good-f-code) są podstawą każdego zalecenia. Są one związane z [wytycznymi projektowania składników F#,](component-design-guidelines.md)ale mają zastosowanie do dowolnego kodu F#, a nie tylko składników, takich jak biblioteki.

## <a name="organizing-code"></a>Organizowanie kodu

F# oferuje dwa podstawowe sposoby organizowania kodu: moduły i przestrzenie nazw. Są one podobne, ale mają następujące różnice:

* Przestrzenie nazw są kompilowane jako obszary nazw .NET. Moduły są kompilowane jako klasy statyczne.
* Przestrzenie nazw są zawsze najwyższego poziomu. Moduły mogą być najwyższego poziomu i zagnieżdżone w innych modułach.
* Przestrzenie nazw mogą obejmujeć wiele plików. Moduły nie mogą.
* Moduły mogą być `[<RequireQualifiedAccess>]` ozdobione i `[<AutoOpen>]`.

Poniższe wskazówki pomogą Ci użyć tych do zorganizowania kodu.

### <a name="prefer-namespaces-at-the-top-level"></a>Preferuj przestrzenie nazw na najwyższym poziomie

Dla każdego publicznie zużywalny kod przestrzenie nazw są preferencyjne dla modułów na najwyższym poziomie. Ponieważ są one kompilowane jako przestrzenie nazw .NET, są one zużywalne z języka C# bez problemu.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Przy użyciu modułu najwyższego poziomu nie może wyglądać inaczej, gdy wywoływane tylko z F#, ale dla konsumentów języka C#, obiekty wywołujące mogą być zaskoczeni konieczności zakwalifikowania się `MyClass` z modułem. `MyCode`

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Ostrożnie nałożyć`[<AutoOpen>]`

Konstrukcja `[<AutoOpen>]` może zanieczyścić zakres tego, co jest dostępne dla dzwoniących, a odpowiedź na to, skąd coś pochodzi, to "magia". To nie jest dobra rzecz. Wyjątkiem od tej reguły jest sama biblioteka rdzenia F# (choć ten fakt jest również nieco kontrowersyjny).

Jednak jest to wygoda, jeśli masz funkcje pomocnika dla publicznego interfejsu API, który chcesz zorganizować oddzielnie od tego publicznego interfejsu API.

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...

    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

Dzięki temu można czysto oddzielić szczegóły implementacji od publicznego interfejsu API funkcji bez konieczności pełnego zakwalifikowania pomocnika za każdym razem, gdy go wywołać.

Ponadto uwidając metody rozszerzenia i konstruktorów wyrażeń na `[<AutoOpen>]`poziomie przestrzeni nazw można starannie wyrazić za pomocą .

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Używaj, `[<RequireQualifiedAccess>]` gdy nazwy mogą być sprzeczne lub uważasz, że pomaga w czytelności

Dodanie `[<RequireQualifiedAccess>]` atrybutu do modułu wskazuje, że moduł nie może być otwarty i że odwołania do elementów modułu wymagają jawnego kwalifikowanego dostępu. Na przykład `Microsoft.FSharp.Collections.List` moduł ma ten atrybut.

Jest to przydatne, gdy funkcje i wartości w module mają nazwy, które mogą kolidować z nazwami w innych modułach. Wymaganie wykwalifikowanego dostępu może znacznie zwiększyć długoterminową łatwość konserwacji i evolvability biblioteki.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Sortowanie `open` instrukcji topologicznych

W F#kolejność deklaracji ma znaczenie, `open` w tym z oświadczeniami. Jest to w przeciwieństwie do `using` Języka `using static` C#, gdzie efekt i jest niezależny od kolejności tych instrukcji w pliku.

W F#, elementy otwarte w zakresie może cienia innych już obecnych. Oznacza to, że `open` zmiana kolejności instrukcji może zmienić znaczenie kodu. W rezultacie wszelkie dowolne `open` sortowanie wszystkich instrukcji (na przykład alfanumerycznie) nie jest zalecane, aby nie generować różne zachowanie, które można oczekiwać.

Zamiast tego zalecamy sortowanie ich [topologicznie;](https://en.wikipedia.org/wiki/Topological_sorting) oznacza to, `open` że zamów instrukcje w kolejności, w jakiej _warstwy_ systemu są zdefiniowane. Można również wziąć pod uwagę sortowanie alfanumeryczne w różnych warstwach topologicznych.

Na przykład w tym miejscu przedstawiono sortowanie topologiczne dla publicznego pliku interfejsu API usługi kompilatora F#:

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

Należy zauważyć, że podział wiersza oddziela warstwy topologiczne, a każda warstwa jest następnie sortowana alfanumerycznie. To czysto organizuje kod bez przypadkowo przesłanianie wartości.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Użyj klas, aby zawierać wartości, które mają skutki uboczne

Inicjowanie wartości może mieć wiele razy, takie jak tworzenie wystąpienia kontekstu do bazy danych lub innego zasobu zdalnego. Kuszące jest inicjowanie takich rzeczy w module i używanie ich w kolejnych funkcjach:

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

Jest to często zły pomysł z kilku powodów:

Po pierwsze, konfiguracja aplikacji jest `dep1` `dep2`wypychana do bazy kodu z i . Jest to trudne do utrzymania w większych bazach kodu.

Po drugie, statycznie inicjowane dane nie powinny zawierać wartości, które nie są bezpieczne dla wątków, jeśli składnik będzie sam używać wielu wątków. Jest to wyraźnie `dep3`naruszone przez .

Na koniec inicjowanie modułu kompiluje się do konstruktora statycznego dla całej jednostki kompilacji. Jeśli wystąpi błąd w inicjowaniu wartości let-bound w tym `TypeInitializationException` module, manifestuje się jako buforowany przez cały okres istnienia aplikacji. Może to być trudne do zdiagnozowania. Zwykle istnieje wewnętrzny wyjątek, który można spróbować rozsądek o, ale jeśli nie jest, to nie ma co jest przyczyną.

Zamiast tego wystarczy użyć prostej klasy do przechowywania zależności:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Umożliwia to następujące czynności:

1. Wypychanie dowolnego stanu zależnego poza samym interfejsem API.
2. Konfiguracja może być teraz wykonywana poza interfejsem API.
3. Błędy w inicjowaniu dla wartości zależnych `TypeInitializationException`prawdopodobnie nie będą manifestować jako .
4. Interfejs API jest teraz łatwiejsze do przetestowania.

## <a name="error-management"></a>Zarządzanie błędami

Zarządzanie błędami w dużych systemach jest złożonym i zniuansowanym przedsięwzięciem, a nie ma srebrnych kul w zapewnieniu, że systemy są odporne na uszkodzenia i zachowują się dobrze. Poniższe wskazówki powinny oferować wskazówki dotyczące nawigacji po tej trudnej przestrzeni.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Reprezentowanie przypadków błędów i niedozwolonych typów wewnętrznych z domeną

W [przypadku związków dyskryminowanych](../language-reference/discriminated-unions.md)F# umożliwia reprezentowanie wadliwego stanu programu w systemie typów. Przykład:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

W tym przypadku istnieją trzy znane sposoby, aby wypłata pieniędzy z konta bankowego może się nie powieść. Każdy przypadek błędu jest reprezentowany w typie i dlatego można je bezpiecznie rozwiązać w całym programie.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Ogólnie rzecz biorąc, jeśli można modelować różne sposoby, że coś może **się nie powieść** w domenie, a następnie błąd obsługi kodu nie jest już traktowany jako coś, co musi radzić sobie oprócz regularnego przepływu programu. Jest to po prostu część normalnego przepływu programu, a nie uważane za **wyjątkowe**. Istnieją dwie podstawowe korzyści do tego:

1. Jest to łatwiejsze w utrzymaniu, ponieważ domena zmienia się wraz z uchwadnianiem.
2. Przypadki błędów są łatwiejsze do testowania jednostkowego.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Użyj wyjątków, gdy błędy nie mogą być reprezentowane z typami

Nie wszystkie błędy mogą być reprezentowane w domenie problemu. Tego rodzaju błędy mają *charakter wyjątkowy,* stąd możliwość podnoszenia i wyłapywanie wyjątków w F#.

Najpierw zaleca się przeczytanie [wytycznych dotyczących projektowania wyjątków](../../standard/design-guidelines/exceptions.md). Mają one również zastosowanie do Języka F#.

Główne konstrukcje dostępne w języku F# na potrzeby podnoszenia wyjątków powinny być brane pod uwagę w następującej kolejności preferencji:

| Funkcja | Składnia | Przeznaczenie |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Wywołuje `System.ArgumentNullException` nazwę z określonym argumentem. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Wywołuje `System.ArgumentException` nazwę określonego argumentu i wiadomość. |
| `invalidOp` | `invalidOp "message"` | Wywołuje `System.InvalidOperationException` a z określonym komunikatem. |
|`raise`| `raise (ExceptionType("message"))` | Mechanizm ogólnego przeznaczenia do zgłaszania wyjątków. |
| `failwith` | `failwith "message"` | Wywołuje `System.Exception` a z określonym komunikatem. |
| `failwithf` | `failwithf "format string" argForFormatString` | Wywołuje `System.Exception` z komunikatem określonym przez ciąg formatu i jego dane wejściowe. |

Użyj `nullArg` `invalidArg` , `invalidOp` i jako `ArgumentNullException`mechanizm `ArgumentException` `InvalidOperationException` do rzucania , i kiedy jest to właściwe.

I `failwith` `failwithf` funkcje zazwyczaj należy unikać, ponieważ podnieść `Exception` typ podstawowy, a nie określony wyjątek. Zgodnie z [wytycznymi dotyczącymi projektowania wyjątków,](../../standard/design-guidelines/exceptions.md)chcesz podnieść bardziej szczegółowe wyjątki, gdy tylko możesz.

### <a name="using-exception-handling-syntax"></a>Korzystanie ze składni obsługi wyjątków

F# obsługuje wzorce `try...with` wyjątków za pośrednictwem składni:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Pojednanie funkcji do wykonania w obliczu wyjątku z dopasowywania wzorca może być nieco trudne, jeśli chcesz zachować kod w czystości. Jednym z takich sposobów obsługi jest użycie [aktywnych wzorców](../language-reference/active-patterns.md) jako środka do grupowania funkcji otaczających przypadek błędu z samym wyjątkiem. Na przykład może być zużywa interfejsu API, który, gdy zgłasza wyjątek, zawiera cenne informacje w metadanych wyjątku. Rozpakowanie użytecznej wartości w treści przechwyconego wyjątku wewnątrz aktywnego wzorca i zwrócenie tej wartości może być pomocne w niektórych sytuacjach.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Nie używaj obsługi błędów monadyjskich, aby zastąpić wyjątki

Wyjątki są postrzegane jako nieco tabu w programowaniu funkcjonalnym. Rzeczywiście, wyjątki naruszają czystość, więc można bezpiecznie uznać je za niecałkiem funkcjonalne. Jednak to ignoruje rzeczywistość, gdzie kod musi działać i że mogą wystąpić błędy w czasie wykonywania. Ogólnie rzecz biorąc, napisz kod przy założeniu, że większość rzeczy nie jest ani czysta, ani całkowita, aby zminimalizować nieprzyjemne niespodzianki.

Ważne jest, aby wziąć pod uwagę następujące podstawowe mocne/aspekty wyjątków w odniesieniu do ich przydatności i stosowności w ekosystemie wykonywania .NET i międzyjęzykowych jako całości:

1. Zawierają one szczegółowe informacje diagnostyczne, co jest bardzo przydatne podczas debugowania problemu.
2. Są one dobrze rozumiane przez czas wykonywania i innych języków .NET.
3. Mogą one zmniejszyć znaczne standardowe w porównaniu z kodem, który wychodzi z drogi, aby *uniknąć* wyjątków, implementując niektóre podzbiór ich semantyki na zasadzie ad hoc.

Ten trzeci punkt ma kluczowe znaczenie. W przypadku nietrywialnych operacji złożonych nieużycie wyjątków może spowodować radzenie sobie ze strukturami takimi jak ten:

```fsharp
Result<Result<MyType, string>, string list>
```

Co może łatwo prowadzić do kruchego kodu, takiego jak dopasowywanie wzorców na błędach typu "typu ciągowego":

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Dodatkowo, może być kuszące, aby połknąć każdy wyjątek w pragnienie "prostej" funkcji, która zwraca typu "ładniejszy":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Niestety, `tryReadAllText` może zgłosić wiele wyjątków na podstawie niezliczonych rzeczy, które mogą się zdarzyć w systemie plików, a ten kod odrzuca wszelkie informacje o tym, co może być rzeczywiście dzieje się źle w danym środowisku. Jeśli zastąpisz ten kod typem wyniku, powrócisz do analizy komunikatu o błędzie "typu ciągowego":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

I umieszczenie samego obiektu `Error` wyjątku w konstruktorze po prostu wymusza poprawnie radzić sobie z typem wyjątku w witrynie wywołania, a nie w funkcji. W ten sposób skutecznie tworzy sprawdzone wyjątki, które są notorycznie niezabawne do czynienia jako obiekt wywołujący interfejsu API.

Dobrą alternatywą dla powyższych przykładów jest wychwytywanie *określonych* wyjątków i zwracanie znaczącej wartości w kontekście tego wyjątku. Jeśli zmodyfikujesz funkcję `tryReadAllText` `None` w następujący sposób, ma większe znaczenie:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Zamiast działać jako catch-all, ta funkcja będzie teraz poprawnie obsługiwać sprawę, gdy plik nie został znaleziony i przypisać to znaczenie do zwrotu. Ta wartość zwracana można mapować do tego przypadku błędu, nie odrzucając żadnych informacji kontekstowych lub zmuszając obiekty wywołujące do czynienia ze sprawą, która może nie być istotne w tym momencie w kodzie.

Typy, `Result<'Success, 'Error>` takie jak są odpowiednie dla podstawowych operacji, w których nie są zagnieżdżone i F# opcjonalne typy są idealne do reprezentowania, gdy coś może zwrócić *coś* lub *nic*. Nie są one jednak zamiennikiem wyjątków i nie powinny być używane w celu zastąpienia wyjątków. Należy je raczej stosować rozważnie w celu uwzględnienia konkretnych aspektów polityki zarządzania wyjątkami i błędami w sposób ukierunkowany.

## <a name="partial-application-and-point-free-programming"></a>Częściowe stosowanie i programowanie bezpunktowe

F# obsługuje częściowej aplikacji, a tym samym różne sposoby programowania w stylu bez punktu. Może to być korzystne dla ponownego użycia kodu w module lub implementacji coś, ale nie jest coś do ujawnienia publicznie. Ogólnie rzecz biorąc, programowanie bez punktów nie jest cnotą samą w sobie i może dodać znaczącą barierę poznawczą dla ludzi, którzy nie są zanurzeni w tym stylu.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Nie należy używać częściowej aplikacji i currying w publicznych interfejsów API

Z wyjątkiem małych wyjątków, korzystanie z częściowej aplikacji w publicznych interfejsów API może być mylące dla konsumentów. Zazwyczaj `let`wartości powiązane w kodzie F# są **wartościami**, a nie **wartościami funkcji**. Mieszanie wartości i wartości funkcji może spowodować zapisanie niewielkiej liczby wierszy kodu w zamian za sporo `>>` obciążenie poznawcze, zwłaszcza w połączeniu z operatorami, takich jak komponowanie funkcji.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Należy wziąć pod uwagę implikacje narzędzi dla programowania bezpunktowego

Funkcje curried nie oznaczają swoich argumentów. Ma to implikacje narzędziowe. Należy wziąć pod uwagę następujące dwie funkcje:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Oba są prawidłowe `funcWithApplication` funkcje, ale jest funkcją curried. Po umieszczeniu wskaźnika myszy na ich typach w edytorze jest widoczne:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

W witrynie wywołania etykietki narzędzi w narzędziach, takich jak Visual `string` Studio `int` nie daje znaczące informacje, co i typy danych wejściowych faktycznie reprezentują.

W przypadku napotkania kodu `funcWithApplication` bezpunktu, takiego jak ten, który jest publicznie zużywalny, zaleca się wykonanie pełnego rozszerzenia η, aby narzędzia mogły odbierać znaczące nazwy argumentów.

Ponadto debugowanie kodu bez punktów może być trudne, jeśli nie niemożliwe. Narzędzia debugowania polegać na wartości powiązane `let` z nazwami (na przykład powiązania), dzięki czemu można sprawdzić wartości pośrednie w połowie wykonywania. Gdy kod nie ma żadnych wartości do sprawdzenia, nie ma nic do debugowania. W przyszłości narzędzia debugowania mogą ewoluować, aby syntetyzować te wartości na podstawie wcześniej wykonanych ścieżek, ale nie jest dobrym pomysłem zabezpieczenie zakładów na *potencjalne* funkcje debugowania.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Należy rozważyć częściowe zastosowanie jako technikę w celu zmniejszenia wewnętrznych standardowych

W przeciwieństwie do poprzedniego punktu, częściowe zastosowanie jest wspaniałym narzędziem do redukcji standardowego wnętrza aplikacji lub głębszych wewnętrznych interfejsu API. Może to być pomocne w testowaniu jednostkowym implementacji bardziej skomplikowanych interfejsów API, gdzie standardowe jest często ból do czynienia z. Na przykład poniższy kod pokazuje, jak można wykonać to, co najbardziej szyderczy chamstwo daje bez podejmowania zależności zewnętrznej od takiej struktury i konieczności uczenia się powiązanych interfejsu API na zamówienie.

Rozważmy na przykład następującą topografię rozwiązania:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj`może uwidaczniać kod, takich jak:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Testowanie `Transactions.doTransaction` jednostkowe jest `ImplementationLogic.Tests.fsproj` łatwe:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Częściowo `doTransaction` stosowane z makiety obiektu kontekstu umożliwia wywołanie funkcji we wszystkich testów jednostkowych bez konieczności konstruowania makiety kontekstu za każdym razem:

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

Ta technika nie powinna być powszechnie stosowana do całej bazy kodu, ale jest to dobry sposób na zmniejszenie standardowego dla skomplikowanych wewnętrznych i testowania jednostek tych wewnętrznych.

## <a name="access-control"></a>Kontrola dostępu

F# ma wiele opcji [kontroli dostępu,](../language-reference/access-control.md)dziedziczone z tego, co jest dostępne w programie .NET runtime. Nie są one po prostu użyteczne dla typów - można ich używać również do funkcji.

* Preferuj`public` nie-typy i członków, dopóki nie potrzebujesz ich do publicznego zużywania. To również minimalizuje to, co konsumenci para do.
* Staraj się zachować wszystkie `private`funkcje pomocnika .
* Należy wziąć `[<AutoOpen>]` pod uwagę korzystanie z prywatnego modułu funkcji pomocnika, jeśli stają się one liczne.

## <a name="type-inference-and-generics"></a>Wnioskowanie o typie i generyk

Wnioskowanie typu może zaoszczędzić od wpisywania dużo standardowego. Automatyczne uogólnienie w kompilatorze F# może pomóc w zapisie bardziej ogólnego kodu bez prawie żadnego dodatkowego wysiłku ze strony użytkownika. Jednak te cechy nie są powszechnie dobre.

* Należy wziąć pod uwagę etykietowania nazw argumentów z jawnych typów w publicznych interfejsów API i nie polegać na wnioskowanie o typie dla tego.

    Powodem tego jest to, że **powinieneś** mieć kontrolę nad kształtem interfejsu API, a nie kompilatorem. Mimo że kompilator może wykonać drobne zadanie przy wnioskowaniu typów dla Ciebie, możliwe jest, aby mieć kształt zmiany interfejsu API, jeśli wewnętrzne, na których opiera się, zmieniły typy. To może być to, co chcesz, ale prawie na pewno spowoduje przełomową zmianę interfejsu API, że downstream konsumentów będzie musiał radzić sobie z. Zamiast tego, jeśli jawnie kontrolować kształt publicznego interfejsu API, a następnie można kontrolować te zmiany. W kategoriach DDD można to traktować jako warstwę antykorupcyjną.

* Rozważ nadanie znaczącej nazwy argumentom rodzajowym.

    Jeśli nie piszesz prawdziwie ogólnego kodu, który nie jest specyficzny dla określonej domeny, znacząca nazwa może pomóc innym programistom zrozumieć domenę, w której pracują. Na przykład parametr typu `'Document` o nazwie w kontekście interakcji z bazą danych dokumentów sprawia, że jaśniejsze, że ogólne typy dokumentów mogą być akceptowane przez funkcję lub element członkowski, z którym pracujesz.

* Należy wziąć pod uwagę nazewnictwa parametrów typu ogólnego z PascalCase.

    Jest to ogólny sposób wykonywania czynności w .NET, dlatego zaleca się użycie PascalCase zamiast snake_case lub camelCase.

Na koniec automatyczne uogólnienie nie zawsze jest dobrodziejstwem dla osób, które są nowe f# lub dużej bazy kodu. Istnieje obciążenie poznawcze w użyciu składników, które są ogólne. Ponadto, jeśli automatycznie uogólnione funkcje nie są używane z różnymi typami danych wejściowych (nie mówiąc już o tym, jeśli są przeznaczone do użycia jako takie), to nie ma żadnych rzeczywistych korzyści dla nich jest ogólny w tym momencie. Zawsze należy wziąć pod uwagę, jeśli kod, który piszesz rzeczywiście skorzystają z jest ogólny.

## <a name="performance"></a>Wydajność

### <a name="prefer-structs-for-small-data-types"></a>Preferuj struktury dla małych typów danych

Przy użyciu struktur (nazywane również typy wartości) często może spowodować wyższą wydajność dla niektórych kodu, ponieważ zazwyczaj pozwala uniknąć przydzielania obiektów. Jednak struktury nie zawsze są przyciskiem "go faster": jeśli rozmiar danych w strukturze przekracza 16 bajtów, kopiowanie danych często może spowodować więcej czasu procesora niż przy użyciu typu odwołania.

Aby ustalić, czy należy użyć struktury, należy wziąć pod uwagę następujące warunki:

- Jeśli rozmiar danych jest 16 bajtów lub mniejsze.
- Jeśli istnieje prawdopodobieństwo, że wiele z tych typów danych jest dostępnych w pamięci w uruchomionym programie.

Jeśli pierwszy warunek ma zastosowanie, należy ogólnie użyć struktury. Jeśli oba stosuje, prawie zawsze należy użyć struktury. Mogą wystąpić przypadki, w których obowiązują poprzednie warunki, ale przy użyciu struktury nie jest lepsze lub gorsze niż przy użyciu typu odniesienia, ale mogą one być rzadkie. Ważne jest, aby zawsze mierzyć przy wprowadzaniu takich zmian, a nie działać na założeniu lub intuicji.

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a>Preferuj krotek struct podczas grupowania małych typów wartości

Należy wziąć pod uwagę następujące dwie funkcje:

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

Podczas porównywania tych funkcji za pomocą statystycznego narzędzia do analizy porównawczej, takiego jak [BenchmarkDotNet,](https://benchmarkdotnet.org/)przekonasz się, że `runWithStructTuple` funkcja, która używa krotek struct działa 40% szybciej i nie przydziela pamięci.

Jednak te wyniki nie zawsze będą w przypadku własnego kodu. Jeśli oznaczysz `inline`funkcję jako , kod, który używa krotek referencyjnych może uzyskać dodatkowe optymalizacje lub kod, który przydzieli, może być po prostu zoptymalizowany. Należy zawsze mierzyć wyniki, gdy chodzi o wydajność, i nigdy nie działać w oparciu o założenia lub intuicji.

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a>Preferuj rekordy struktury, gdy typ danych jest mały

Reguła opisana wcześniej również przechowuje dla [typów rekordów F#.](../language-reference/records.md) Należy wziąć pod uwagę następujące typy danych i funkcje, które je przetwarzają:

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

Jest to podobne do poprzedniego kodu krotki, ale tym razem w przykładzie używa rekordów i wbudowanej funkcji wewnętrznej.

Podczas porównywania tych funkcji za pomocą statystycznego narzędzia do analizy `processStructPoint` porównawczej, takiego jak [BenchmarkDotNet,](https://benchmarkdotnet.org/)przekonasz się, że działa prawie 60% szybciej i nie przydziela niczego na zarządzanym stercie.

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a>Preferuj struktury dyskryminowane związki, gdy typ danych jest mały

Poprzednie obserwacje dotyczące wydajności z struct krotek i rekordów posiada również dla [F# Dyskryminowane związki](../language-reference/discriminated-unions.md). Spójrzmy na poniższy kod:

```fsharp
    type Name = Name of string

    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

Często definiuje się pojedyncze związki dyskryminowane, takie jak ta dla modelowania domen. Podczas porównywania tych funkcji za pomocą statystycznego narzędzia do analizy `structReverseName` porównawczej, takiego jak `reverseName` [BenchmarkDotNet,](https://benchmarkdotnet.org/)przekonasz się, że działa o 25% szybciej niż w przypadku małych ciągów. W przypadku dużych ciągów oba działają mniej więcej tak samo. Tak więc, w tym przypadku, zawsze lepiej jest użyć struktury. Jak wcześniej wspomniano, zawsze mierzyć i nie działać na założeniach lub intuicji.

Chociaż poprzedni przykład wykazał, że struktura Unia dyskryminowana przyniosła lepszą wydajność, często podczas modelowania domeny występuje większa liczba dyskryminowanych związków. Większe typy danych, takie jak to może nie działać, jak również, jeśli są one struktury w zależności od operacji na nich, ponieważ więcej kopiowania może być zaangażowany.

### <a name="functional-programming-and-mutation"></a>Programowanie funkcjonalne i mutacja

F# wartości są domyślnie niezmienne, co pozwala uniknąć niektórych klas błędów (zwłaszcza tych obejmujących współbieżność i równoległości). Jednak w niektórych przypadkach, w celu osiągnięcia optymalnej (lub nawet uzasadnione) efektywności wykonywania czasu lub alokacji pamięci, zakres pracy może być najlepiej realizowane przy użyciu mutacji w miejscu stanu. Jest to możliwe w zasadzie opt-in `mutable` z F# ze słowem kluczowym.

Korzystanie `mutable` z w F# może czuć się w sprzeczności z czystości funkcjonalnej. Jest to zrozumiałe, ale funkcjonalna czystość wszędzie może być sprzeczna z celami wydajności. Kompromisem jest hermetyzacja mutacji w taki sposób, że dzwoniący nie muszą dbać o to, co się dzieje, gdy nazywają funkcję. Dzięki temu można napisać interfejs funkcjonalny za pomocą implementacji opartej na mutacji dla kodu o krytycznym znaczeniu dla wydajności.

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Zawijanie kodu zmiennego w interfejsach niezmiennych

Z przezroczystości referencyjnej jako cel, ważne jest, aby napisać kod, który nie ujawnia zmienny podbrzusze funkcji krytycznych dla wydajności. Na przykład następujący kod implementuje `Array.contains` funkcję w bibliotece podstawowej F#:

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

Wywołanie tej funkcji wiele razy nie zmienia podstawowej tablicy, ani nie wymaga utrzymania stanu zmiennego w jej użyciu. Jest referencyjnie przezroczysty, mimo że prawie każdy wiersz kodu w nim używa mutacji.

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>Rozważ hermetyzacje zmiennych danych w klasach

W poprzednim przykładzie użyto pojedynczej funkcji do hermetyzacji operacji przy użyciu danych zapisywanych. Nie zawsze jest to wystarczające dla bardziej złożonych zestawów danych. Należy wziąć pod uwagę następujące zestawy funkcji:

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

Ten kod jest działanie, ale udostępnia strukturę danych opartych na mutacji, które obiekty wywołujące są odpowiedzialne za utrzymanie. To może być zawijana wewnątrz klasy bez podstawowych elementów członkowskich, które można zmienić:

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table`hermetyzuje podstawową strukturę danych opartą na mutacji, nie zmuszając w ten sposób osób dzwoniących do utrzymania podstawowej struktury danych. Klasy są skutecznym sposobem hermetyzacji danych i procedur, które są oparte na mutacji bez ujawniania szczegółów dla wywoływania.

#### <a name="prefer-let-mutable-to-reference-cells"></a>Wolę `let mutable` odwoływać się do komórek

Komórki referencyjne są sposobem reprezentowania odwołania do wartości, a nie samej wartości. Mimo że mogą być używane dla kodu o krytycznym znaczeniu dla wydajności, nie są zalecane. Rozważmy następujący przykład:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Użycie komórki odniesienia teraz "zanieczyszcza" wszystkie kolejne kodu z konieczności wyłuskania i ponownego odwoływania się do danych źródłowych. Zamiast tego `let mutable`należy wziąć pod uwagę:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Oprócz pojedynczego punktu mutacji w środku wyrażenia lambda, wszystkie `acc` inne typy, które dotknie można to zrobić `let`w sposób, który nie różni się od użycia normalnej wartości niezmiennej. Ułatwi to zmianę w czasie.

## <a name="object-programming"></a>Programowanie obiektów

F# ma pełną obsługę obiektów i koncepcji zorientowanych obiektowo (OO). Chociaż wiele koncepcji oo są potężne i przydatne, nie wszystkie z nich są idealne do użycia. Poniższe listy zawierają wskazówki dotyczące kategorii funkcji oo na wysokim poziomie.

**Należy rozważyć użycie tych funkcji w wielu sytuacjach:**

* Notacja kropka`x.Length`( )
* Członkowie instancji
* Konstruktory niejawne
* Statyczne składowe
* Notacja indeksatora (`arr.[x]`)
* Argumenty nazwane i opcjonalne
* Interfejsy i implementacje interfejsów

**Nie sięgnij po te funkcje, ale rozsądnie zastosuj je, gdy są wygodne do rozwiązania problemu:**

* Przeciążenie metody
* Zhermetyzowane dane zmienne
* Operatorzy na typach
* Właściwości automatyczne
* Wdrażanie `IDisposable` i wdrażanie`IEnumerable`
* Rozszerzenia typu
* Zdarzenia
* Struktury
* Delegaty
* Wyliczenia

**Generalnie unikaj tych funkcji, chyba że musisz z nich korzystać:**

* Hierarchie typów oparte na dziedziczeniu i dziedziczenie implementacji
* Wartości null i`Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Preferuj kompozycję niż dziedziczenie

[Skład nad dziedziczeniem](https://en.wikipedia.org/wiki/Composition_over_inheritance) jest od dawna idiom, że dobry kod F# można stosować się do. Podstawową zasadą jest, że nie należy uwidaczniać klasy podstawowej i wymusić obiekty wywołujące dziedziczyć z tej klasy podstawowej, aby uzyskać funkcjonalność.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Użyj wyrażeń obiektów do zaimplementowania interfejsów, jeśli nie potrzebujesz klasy

[Wyrażenia obiektów](../language-reference/object-expressions.md) umożliwiają implementowanie interfejsów w locie, powiązanie zaimplementowanego interfejsu z wartością bez konieczności wykonywania tego wewnątrz klasy. Jest to wygodne, zwłaszcza jeśli trzeba _tylko_ zaimplementować interfejs i nie ma potrzeby pełnej klasy.

Na przykład oto kod, który jest uruchamiany w [Jonide,](http://ionide.io/) aby zapewnić akcję poprawki kodu, `open` jeśli dodano symbol, który nie ma instrukcji dla:

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

Ponieważ nie ma potrzeby klasy podczas interakcji z interfejsem API kodu programu Visual Studio, wyrażenia obiektów są idealnym narzędziem do tego. Są one również cenne dla testowania jednostkowego, gdy chcesz wycinek interfejs z procedur testowych w sposób doraźny.

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>Należy wziąć pod uwagę skróty tekstu, aby skrócić podpisy

[Skróty tekstu](../language-reference/type-abbreviations.md) są wygodnym sposobem przypisywania etykiety do innego typu, takiego jak podpis funkcji lub typ bardziej złożony. Na przykład następujący alias przypisuje etykietę do tego, co jest potrzebne do zdefiniowania obliczeń z [CNTK](https://docs.microsoft.com/cognitive-toolkit/), biblioteki uczenia głębokiego:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

Nazwa `Computation` jest wygodnym sposobem oznaczania dowolnej funkcji, która pasuje do podpisu, który jest aliasing. Korzystanie z skrótów typu jak to jest wygodne i pozwala na bardziej zwięzły kod.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Unikaj używania skrótów tekstu do reprezentowania domeny

Chociaż skróty typu są wygodne do nadania nazwy sygnaturom funkcji, mogą być mylące podczas skracania innych typów. Należy wziąć pod uwagę ten skrót:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Może to być mylące na wiele sposobów:

* `BufferSize`nie jest abstrakcją; to tylko inna nazwa liczby całkowitej.
* Jeśli `BufferSize` jest narażony w publicznym interfejsie API, można go łatwo `int`błędnie zinterpretować jako coś więcej niż tylko . Ogólnie rzecz biorąc typy domen mają wiele atrybutów do `int`nich i nie są typy pierwotne, takie jak . Ten skrót narusza to założenie.
* Obudowa `BufferSize` (PascalCase) oznacza, że ten typ przechowuje więcej danych.
* Ten alias nie oferuje większej jasności w porównaniu z dostarczaniem nazwany argument do funkcji.
* Skrót nie będzie przejawiać się w skompilowanym IL; jest to tylko liczba całkowita i ten alias jest kompilacji czasu.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

Podsumowując, pułapka z skrótami typu jest to, że **nie** są abstrakcje nad typami są skróty. W poprzednim przykładzie `BufferSize` jest `int` tylko pod przykrywką, bez dodatkowych danych, ani `int` żadnych korzyści z systemu typu oprócz tego, co już ma.

Alternatywnym podejściem do używania skrótów typów do reprezentowania domeny jest użycie jednoprzypadkówowych związków dyskryminowanych. Poprzedni przykład można modelować w następujący sposób:

```fsharp
type BufferSize = BufferSize of int
```

Jeśli piszesz kod, który `BufferSize` działa pod względem i jego wartości bazowej, należy skonstruować jeden, a nie przekazać w dowolnej dowolnych liczb całkowitych:

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

Zmniejsza to prawdopodobieństwo omyłkowego przekazywania dowolnych liczb całkowitych `send` do `BufferSize` funkcji, ponieważ obiekt wywołujący musi skonstruować typ, aby zawinąć wartość przed wywołaniem funkcji.
