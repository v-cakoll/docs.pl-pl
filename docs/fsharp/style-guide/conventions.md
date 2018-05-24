---
title: 'Konwencje kodowania F #'
description: 'Informacje ogólne wytyczne i idioms podczas zapisywania w kodzie języka F #.'
ms.date: 05/14/2018
ms.openlocfilehash: f3d16f735ddc1901aeaa5ebb39e2fa2b70a3d836
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="f-coding-conventions"></a>Konwencje kodowania F #

Następujące konwencje są formułowane z doświadczenia w pracy z dużą F # codebases. [Pięć zasadami dobrej kodzie języka F #](index.md#five-principles-of-good-f-code) są podstawę poszczególne zalecenia. Są one związane z [F # składnika zaleceń dotyczących projektowania](component-design-guidelines.md), ale są stosowane do dowolnego kodzie języka F #, nie tylko składniki, takie jak biblioteki.

## <a name="organizing-code"></a>Organizowanie kodu

Dwa podstawowe sposoby organizowanie kodu funkcje F #: moduły i przestrzenie nazw. Te są podobne, ale różnią się w następujący sposób:

* Przestrzenie nazw są kompilowane jako przestrzenie nazw .NET. Moduły są kompilowane jako klasy statyczne.
* Przestrzenie nazw są zawsze najwyższego poziomu. Moduły mogą być najwyższego poziomu i zagnieżdżone w innych modułach.
* Przestrzenie nazw może obejmować wiele plików. Nie można modułów.
* Moduły mogą być oznaczone `[<RequireQualifiedAccess>]` i `[<AutoOpen>]`.

Poniższe wskazówki ułatwiają ich używać do organizowania kodu.

### <a name="prefer-namespaces-at-the-top-level"></a>Preferowane jest przestrzeni nazw na najwyższym poziomie

Dla żadnego kodu publicznie eksploatacyjny przestrzenie nazw są preferencyjne modułów na najwyższym poziomie. Ponieważ są one kompilowane jako przestrzenie nazw .NET, są one dostępne w języku C# nie problem.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Za pomocą modułu najwyższego poziomu mogą nie być wyświetlane inaczej wywoływane tylko z F #, ale C# konsumentów, może oczekiwano wywołań, pozwalając na kwalifikować się `MyClass` z `MyCode` modułu.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Starannie Zastosuj `[<AutoOpen>]`

`[<AutoOpen>]` Konstrukcja można charakteryzują się zakres co jest dostępne dla kodu wywołującego, a odpowiedź na coś, z której pochodzi to "magicznych". Zwykle nie jest to dobrze, że. Wyjątek od tej reguły jest biblioteki podstawowej F #, sama (chociaż ten fakt również jest nieco kontrowersyjna).

Jednak jest on udogodnienie, jeśli masz funkcji pomocnika dla publiczny interfejs API, który ma zostać organizowanie oddzielnie z tym publiczny interfejs API.

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

Dzięki temu można szczegóły implementacji oddzielne bezpośrednio z publiczny interfejs API funkcji bez konieczności pełnej kwalifikacji pomocnika za każdym razem, należy wywołać.

Ponadto udostępnia metody rozszerzenia i konstruktorów wyrażeń na poziomie przestrzeni nazw może być starannie wyrażona z `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Użyj `[<RequireQualifiedAccess>]` podczas każdego może powodować konflikt nazw lub uważasz, że ułatwia czytelności

Dodawanie `[<RequireQualifiedAccess>]` modułu dla atrybutu wskazuje, że moduł nie może być otwarty i że odwołania do elementów modułu, wymaga jawnego kwalifikowana dostępu. Na przykład `Microsoft.FSharp.Collections.List` moduł ma tego atrybutu.

Jest to przydatne, gdy wartości w module i funkcje mają nazwy, które mogą powodować konflikt z nazwami w innych modułach. Wymagających dostępu kwalifikowaną może znacznie zwiększyć długoterminowej utrzymanie i evolvability biblioteki.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Sortuj `open` instrukcje topologically

W języku F #, ma znaczenie kolejności zgłoszeń, łącznie z `open` instrukcje. Jest to w przeciwieństwie do języka C#, gdzie efekt `using` i `using static` jest niezależna od kolejności tych instrukcji w pliku.

W języku F # elementy otwarte w zakresie można w tle innych jeszcze nie istnieje. Oznacza to, że zmiana kolejności `open` instrukcje może zmienić znaczenie kodu. W rezultacie, wszystkie dowolnego sortowanie wszystkich `open` instrukcje (na przykład alfanumerycznie) zwykle nie jest zalecane, co najmniej Generowanie inaczej, które mogą wymagać.

Zamiast tego zaleca się je posortować [topologically](https://en.wikipedia.org/wiki/Topological_sorting); oznacza to, że kolejność Twojej `open` instrukcje w kolejności, w jakiej _warstwy_ systemu są zdefiniowane. Podczas sortowania w różnych warstwach topologiczne alfanumeryczne mogą być również uwzględnione.

Na przykład poniżej przedstawiono topologiczne sortowania dla języka F # kompilatora publicznego interfejsu API pliku usługi:

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

Należy pamiętać, że podział wiersza oddziela topologiczne warstwy z każdej warstwy sortowane alfanumerycznie później. Kod zostanie prawidłowo organizuje bez przypadkowo przesłanianie wartości.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Klasy służą do zawierają wartości, które ma efekty uboczne

Istnieje wiele razy podczas inicjowania wartość może mieć efekty uboczne, takich jak tworzenie wystąpień kontekstu do bazy danych lub innego zasobu zdalnego. Jest kuszące zainicjować takich elementów w module i użyć go w kolejnych funkcje:

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

To jest często dobrym pomysłem kilku powodów:

Po pierwsze, konfiguracji aplikacji zostanie przypisany do codebase z `dep1` i `dep2`. To jest trudne w utrzymaniu w się, że codebases większy.

Drugi, statycznie zainicjowane danych nie może zawierać wartości, które nie są bezpieczne dla wątków, jeśli sam składnika będzie używać wiele wątków. Jest to wyraźnie naruszone przez `dep3`.

Na koniec inicjowania modułu kompiluje w konstruktorze statycznym kompilacji całej jednostki. W przypadku błędu podczas inicjowania let granica wartości w module, manifesty go jako `TypeInitializationException` który następnie jest buforowana przez cały czas ich istnienia aplikacji. Może to być trudne do diagnozowania. Zazwyczaj jest wyjątek wewnętrzny, który można spróbować przyczyny o, ale jeśli nie ma, to nie ma żadnych informuje jest główną przyczynę.

Po prostu użyj prostą klasę do przechowywania zależności:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Umożliwia to następujące czynności:

1. Wypychanie każdy stan zależnych poza samego interfejsu API.
2. Teraz można konfiguracji poza interfejsu API.
3. Błędy podczas inicjowania dla wartości zależnych nie są może być przedstawiany jako `TypeInitializationException`.
4. Interfejs API jest teraz łatwiejsze testowanie.

## <a name="error-management"></a>Błąd zarządzania

Błąd zarządzania w dużych systemach jest pozwala złożone i nuanced i nie ma żadnych silver punktory w celu zapewnienia systemy są odpornej na uszkodzenia i zachowywać się również. Poniższe wskazówki powinno oferować wskazówki przechodzenia to miejsce trudne.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>W przypadku wystąpienia błędów i stan niedozwolony w typach wewnętrznej do domeny

Z [Suma rozłączna unie](../language-reference/discriminated-unions.md), F # daje możliwość reprezentuje stan uszkodzony programu w systemie typów. Na przykład:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

W takim przypadku istnieją trzy sposoby znane, których wycofanie pieniędzy z konta bankowego może zakończyć się niepowodzeniem. Każdy przypadek błędu jest reprezentowana w typie, a w związku z tym można przetwarzać bezpiecznie w programie.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Ogólnie rzecz biorąc, jeśli modelu różne sposoby szukają można **niepowodzenie** w domenie, następnie kod obsługi błędów jest już traktowany jako element musi dotyczyć oprócz zwykłego przepływu. Jest po prostu część przepływu normalnego programu, a nie omówiono **wyjątkowych**. Istnieją dwie główne korzyści wynikające z to:

1. Jest łatwiejsze w obsłudze, ponieważ domeny zmienia się wraz z upływem czasu.
2. W przypadku wystąpienia błędów są łatwiejsze do testu jednostkowego.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Użyj wyjątków, jeśli błędy nie może być reprezentowana typów

Nie wszystkie błędy mogą być reprezentowane w domeny problemu. Tego rodzaju błędów są *wyjątkowych* charakter, dlatego możliwość pozyskiwania i przechwytywanie wyjątków w języku F #.

Po pierwsze zaleca się przeczytanie [zaleceń dotyczących projektowania wyjątek](../../standard/design-guidelines/exceptions.md). Są to również zastosowanie do F #.

Główne konstrukcje, dostępne w języku F # na potrzeby występowanie wyjątków należy rozważyć w podanej poniżej kolejności preferencji:

| Funkcja | Składnia | Cel |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Zgłasza `System.ArgumentNullException` o nazwie określonego argumentu. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Wywołuje `System.ArgumentException` z nazwą określony argument i komunikatu. |
| `invalidOp` | `invalidOp "message"` | Wywołuje `System.InvalidOperationException` z określonym komunikatem. |
|`raise`| `raise (ExceptionType("message"))` | Mechanizm ogólnego przeznaczenia zgłaszanie wyjątków. |
| `failwith` | `failwith "message"` | Wywołuje `System.Exception` z określonym komunikatem. |
| `failwithf` | `failwithf "format string" argForFormatString` | Zgłasza `System.Exception` komunikatem określona przez ciąg formatu i jego danych wejściowych. |

Użyj `nullArg`, `invalidArg` i `invalidOp` jako mechanizm throw `ArgumentNullException`, `ArgumentException` i `InvalidOperationException` w odpowiednim przypadku.

`failwith` i `failwithf` funkcje ogólnie należy unikać, ponieważ ich podnieść podstawowym `Exception` wpisz określony wyjątek. Zgodnie [zaleceń dotyczących projektowania wyjątek](../../standard/design-guidelines/exceptions.md), aby zgłaszał bardziej szczegółowe wyjątki, które można wykonywać następujące czynności.

### <a name="using-exception-handling-syntax"></a>Przy użyciu składni Obsługa wyjątków

F # obsługuje wzorce wyjątek za pośrednictwem `try...with` składni:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Uzgadnianie funkcja do wykonania w wypadku wyjątków o dopasowanie wzorca mogą być nieco trudnych, jeśli chcesz zachować czysty kod. Jeden sposób obsługi to jest użycie [aktywne wzorce](../language-reference/active-patterns.md) jako środek do funkcji grupy otaczającego przypadek błędu, z wyjątkiem samej siebie. Na przykład użytkownik może korzystać z interfejs API, który po zgłasza wyjątek, umieszcza cenne informacje w metadanych wyjątku. Odkodowywania wartość przydatne w treści przechwycony wyjątek wewnątrz aktywnego wzorca i zwracanie, czy wartość może być pomocny w niektórych sytuacjach.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Nie używaj monadic obsługę błędów do zastąpienia wyjątków

Wyjątki są widoczne jako nieco taboo w programowanie funkcjonalne. W rzeczywistości wyjątki narusza czystości, więc bezpiecznie wziąć pod uwagę ich nie całkiem funkcjonalności. Jednak to ignoruje rzeczywistości gdzie uruchomić kod i że środowiska uruchomieniowego, które mogą wystąpić błędy. Ogólnie rzecz biorąc przy założeniu, że większości zadań nie są pure ani całkowity, aby zminimalizować nieprzyjemny niespodzianki należy napisać kod.

Należy wziąć pod uwagę następujące podstawowe sile/aspekty wyjątków względem ich znaczenie i właściwości środowisko uruchomieniowe platformy .NET i wielu języków ekosystemu jako całość:

1. Zawierają szczegółowe informacje diagnostyczne, które jest bardzo przydatne, gdy debugowanie problemu.
2. Są one przejrzyste przez środowisko uruchomieniowe i innych języków platformy .NET.
3. Mogą zmniejszać znaczących umożliwiającego w porównaniu z kodem wykraczające poza jego sposobem *uniknąć* wyjątki zaimplementowanie niektórych podzbiór ich semantyki na podstawie ad hoc.

Bardzo ważne jest ten punkt trzecich. Proste operacji złożonych można użyć wyjątki może spowodować zajmowanie struktur w następujący sposób:

```fsharp
Result<Result<MyType, string>, string list>
```

Łatwo a to może prowadzić do słabe kodu jak dopasowania wzorca w "stringly wpisane" błędy:

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Ponadto może być kuszące jest swallow żadnych wyjątków w desire dla funkcji "prosty", który zwraca typ "wrażeń":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Niestety `tryReadAllText` może zgłosić wiele wyjątków opartych na różnych rzeczy, które mogą wystąpić w systemie plików i ten kod nieobecności odrzuca żadnych informacji o co może być przechodzenia do niewłaściwej w danym środowisku. Jeśli typ wyniku możesz zastąpić ten kod, następnie wszystko do analizowania komunikat "stringly wpisane" Błąd:

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

I wprowadzania sam obiekt wyjątku w `Error` Konstruktor tylko wymusza prawidłowo radzenia sobie z typ wyjątku, w miejsce wywołania, a nie w funkcji. Spowoduje to skutecznie tworzy zaznaczone wyjątki, które są bardzo unfun radzenia sobie z jako obiekt wywołujący interfejs API.

Dobrą alternatywą do powyższe przykłady ma catch *określonych* wyjątków i przywracać odpowiednią wartość w kontekście tego wyjątku. Jeśli zmodyfikujesz `tryReadAllText` działa w następujący sposób `None` ma więcej znaczenie:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Zamiast działać jako catch-all, ta funkcja zostanie teraz poprawnie obsługiwać przypadku plik nie został znaleziony i przypisanie tego znaczenie do powrotu. Zwrócona wartość można mapować do tego przypadku błędu podczas nie odrzuca wszystkie informacje kontekstowe lub wymuszania wywołań radzenia sobie z przypadkiem, które nie mogą być użyteczne w tym momencie w kodzie.

Typy, takich jak `Result<'Success, 'Error>` są odpowiednie dla podstawowe operacje, których nie są one zagnieżdżone i F # opcjonalne typy są idealne w przypadku reprezentujący, gdy coś można albo zwrot *coś* lub *nic*. One zastępuje wyjątki, nie są jednak i nie może być używany w próba do zastąpienia wyjątków. Zamiast ich powinny być stosowane rozważnie aspektów określonego adresu wyjątków i błędów zasad zarządzania w sposób docelowych.

## <a name="partial-application-and-point-free-programming"></a>Aplikacja częściowa i bez punktu programowania

F # obsługuje aplikacja częściowa i w związku z tym różne sposoby program w stylu bez punktu. Może to być przydatne do ponownego użycia kodu w module lub wykonania elementu, ale zazwyczaj nie jest element zostać udostępniona publicznie. Ogólnie rzecz biorąc bez punktu programowania nie jest mocy w i samego siebie i można dodać kognitywnych dużą przeszkodę dla osób, które nie są zanurzony w stylu.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Nie należy używać aplikacja częściowa i currying w publicznych interfejsach API

Z wyjątkiem małego korzystanie z częściowa aplikacji w publicznych interfejsach API może być mylące dla użytkowników. Zazwyczaj `let`-są powiązane wartości w kodzie języka F # **wartości**, a nie **funkcji wartości**. Zmieszanie wartości i wartości funkcji może spowodować zapisywanie niewielką liczbę wierszy kodu w zamian dość nieco kognitywnych obciążenie, zwłaszcza, jeśli takie jak połączeniu z operatorami `>>` utworzenie funkcji.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Należy wziąć pod uwagę wpływ narzędzi do programowania za wolny od punktu

Funkcje rozwinięte nie etykiety ich argumentów. Ma to wpływ narzędzi. Należy wziąć pod uwagę następujące dwie funkcje:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Oba są prawidłowe funkcje, ale `funcWithApplication` jest funkcją rozwinięte. Po umieszczeniu na ich typów w edytorze, zobacz to:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

W witrynie wywołania etykietki narzędzi w narzędzia, takiego jak Visual Studio nie zapewni przydatne informacje dotyczące co `string` i `int` faktycznie stanowi typów wejściowych.

Jeśli wystąpią bez punktu kodu, takie jak `funcWithApplication` jest publicznie eksploatacyjny, zaleca się wykonywać pełnym rozszerzeniu η narzędzi można wybrać w górę na łatwy do rozpoznania nazwy argumentów.

Ponadto debugowanie kodu bez punktu może być wyzwaniem, jeśli jest to niemożliwe. Narzędzia debugowania zależą od wartości powiązany z nazwy (na przykład `let` powiązań), aby sprawdzić wartości pośrednich połowie poprzez wykonanie. Gdy kodu nie zawiera żadnych wartości do zbadania, nie ma nic do debugowania. W przyszłości, narzędzia debugowania mogą rozwijać syntetyzować te wartości oparte na ścieżkach poprzednio wykonane, ale nie jest dobrym pomysłem jest zabezpieczenie sieci trafień na *potencjalne* debugowanie funkcji.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Należy wziąć pod uwagę aplikacja częściowa jako technika zmniejszyć umożliwiającego wewnętrzny

W przeciwieństwie do poprzedniego punktu aplikacja częściowa jest narzędziem cudowne zmniejszenia umożliwiającego wewnątrz aplikacji lub lepszy mechanizmów wewnętrznego interfejsu API. Może być przydatna do implementacji interfejsów API bardziej skomplikowany, gdzie standardowy jest często słabe radzenia sobie z testów jednostkowych. Na przykład w poniższym kodzie jak można wykonać jakie najbardziej mocking platform zapewniają bez konieczności przełączania zależności zewnętrznej na takie framework i konieczności uczenia się z odpowiednimi tworzony na zamówienie interfejsu API.

Na przykład wziąć pod uwagę następujące topografii rozwiązania:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` może udostępniać kod takich jak:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Testy jednostkowe `Transactions.doTransaction` w `ImplementationLogic.Tests.fspoj` jest prosty:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Częściowo stosowania `doTransaction` z kontekstem mocking obiekt umożliwia wywołanie funkcji we wszystkich testów jednostkowych bez konieczności tworzenia kontekstu mocked zawsze:

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

Ta technika nie powinny być powszechnie stosowane do całego baza kodu, ale jest to dobry sposób na zmniejszyć umożliwiającego wewnętrzne skomplikowane i te ustawienia wewnętrzne testy jednostkowe.

## <a name="access-control"></a>Kontrola dostępu

F # udostępnia wiele opcji [kontrola dostępu](../language-reference/access-control.md), dziedziczone z co to jest dostępne w środowisku wykonawczym .NET. Nie są użyteczne tylko dla typów — można je Użyj zbyt dla funkcji.

* Preferowane jest inne niż`public` typów i członków, dopóki nie należy ich być publicznie dostępne. Zmniejsza to także kilka jakie konsumentów do
* Dokładamy wszelkich starań zachować wszystkie funkcje pomocnicze `private`.
* Rozważ użycie `[<AutoOpen>]` na modułu prywatnego funkcji pomocnika, jeśli staną się wiele.

## <a name="type-inference-and-generics"></a>Wnioskowanie o typie i typy ogólne

Wnioskowanie o typie można zapisać możesz wpisać dużo standardowego. I automatyczna Generalizacja w kompilatorze języka F # ułatwia pisanie bardziej ogólnym kodu z prawie nie dodatkowego nakładu pracy ze strony użytkownika. Jednak te funkcje nie są powszechnie dobra.

* Warto nadać nazwy argumentów jawnego typów w publicznych interfejsach API i nie należy polegać na wnioskowanie o typie dla tego.

    Jest to spowodowane tym, że **można** powinna być w formancie kształtu interfejsu API, nie kompilatora. Kompilator może wykonać przeprowadzać zadania na wnioskowanie typów dla Ciebie, jest możliwe kształtu zmiany interfejsu API wewnętrzne, które opiera się na zmiany typów. Może to być, co ma, ale prawie na pewno spowoduje na istotne zmiany interfejsu API niższego rzędu konsumentów będzie miał radzenia sobie z. Zamiast tego należy jawnie kontrolować kształt publiczny interfejs API, następnie można sterować te zmiany podziału. W kategoriach DDD to można można traktować jako warstwa przed uszkodzeniem.

* Należy wziąć pod uwagę, zapewniając łatwy do rozpoznania nazwy argumentów ogólnych.

    Jeśli piszesz naprawdę ogólnego kod, który nie jest specyficzne dla konkretnej domeny zrozumiałą nazwę może pomóc w innych programistów opis domeny, które działają w. Na przykład, parametru typu o nazwie `'Document` w kontekście interakcji z dokumentem bazy danych, ułatwia jaśniejszy, że typy dokumentu typu ogólnego może zostać zaakceptowane przez funkcji lub elementu członkowskiego, w przypadku korzystania z.

* Należy rozważyć nazw parametrów typu ogólnego z PascalCase.

    Jest to ogólne sposób, aby wykonać czynności w .NET, dlatego zalecane jest, że używasz PascalCase zamiast snake_case lub (camelcase).

Na koniec automatyczna Generalizacja nie zawsze jest zwiększa dla osób, które są nowe w F # lub duże codebase. Brak kognitywnych obciążenie przy użyciu składników, które są ogólne. Ponadto jeśli automatycznie uogólniony funkcje nie są używane z różnych typów wejściowych (umożliwiają tylko, jeśli są one przeznaczone do użycia jako takie), a następnie rozwiązanie nie przynosi żadnych rzeczywistych do nich ogólnego w danym momencie. Zawsze należy rozważyć, jeśli kod, który pisania faktycznie będą korzystać z ogólnym.

## <a name="performance"></a>Wydajność

F # wartości są niezmienne domyślnie, dzięki czemu można uniknąć niektórych klas usterek (szczególnie tych dotyczących współbieżności i równoległości). Jednak w niektórych przypadkach, aby osiągnąć optymalną (lub nawet uzasadnione) skuteczność czas wykonania lub przydziału pamięci zakresu pracy mogą najlepiej można implementować przy użyciu mutacji w miejscu stanu. Jest to możliwe w zasadzie opcjonalnych w języku F # z `mutable` — słowo kluczowe.

Jednak użycie `mutable` w języku F # mogą uznać kłóci czystości funkcjonalności. Jest to poprawnie, jeśli oczekiwań z czystości [referencyjnej przezroczystość](https://en.wikipedia.org/wiki/Referential_transparency). Przezroczystość referencyjnej — nie czystości — jest jej celem podczas zapisywania funkcje F #. Umożliwia to pisanie funkcjonalności interfejsu na podstawie mutacji implementację kodu krytycznego wydajności.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Zawijanie modyfikowalną kodu w niezmienne interfejsów

Z referencyjnej przezroczystości jako cel, bardzo ważne jest napisanie kodu, który nie ujawnia modyfikowalną underbelly krytyczne wydajności funkcji. Na przykład poniższy kod implementuje `Array.contains` funkcji biblioteki podstawowej F #:

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

Wiele razy podczas wywoływania tej funkcji nie zmienia tabeli podstawowej, ani nie wymaga do utrzymania każdy stan modyfikowalną podczas używania go. Jest referentially niewidoczne, mimo że prawie każdego wiersza kodu w niej używa mutacji.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Należy wziąć pod uwagę hermetyzując modyfikowalną danych w klasach

Poprzedni przykład metodę jednej funkcji hermetyzacji operacje przy użyciu tych danych. To nie zawsze jest wystarczająca dla bardziej złożonych zestawów danych. Należy wziąć pod uwagę następujące zestawy funkcji:

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

Ten kod jest wydajność, ale udostępnia ona struktury danych opartych na mutacji odpowiedzialny za konserwację czy obiekty wywołujące. Może to być zawijany wewnątrz klasy bez członków podstawowych, które można zmienić:

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table` hermetyzuje struktury danych opartych na mutacji, a tym samym nie wymuszania obiekty wywołujące do obsługi podstawowej struktury danych. Klasy są zaawansowane metody hermetyzacji danych i procedur, które są oparte na mutacji bez narażania szczegóły dotyczące obiektów wywołujących.

### <a name="prefer-let-mutable-to-reference-cells"></a>Preferowane jest `let mutable` do komórki odwołań

Komórki odwołań służą do reprezentowania odwołania do wartości, a nie z samą wartość. Mimo że można nimi dla kodu wrażliwego na wydajność, one zazwyczaj nie jest zalecane. Rozważmy następujący przykład:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Użyj komórka odwołania teraz "pollutes" wszystkie kolejne kodu z konieczności cofnięcia odwołania i ponownie odwołują się dane. Zamiast tego należy wziąć pod uwagę `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Jako uzupełnienie pojedynczy punkt mutacji w trakcie wykonywania wyrażenia lambda, wszystkie inne kodu, który dotyka `acc` to zrobić w taki sposób, który nie różni się do użycia jako normalny `let`-powiązana wartość niezmienialny. Ułatwi zmiany w czasie.

## <a name="object-programming"></a>Obiekt programowania

F # ma pełną obsługę obiektów i koncepcje zorientowane obiektowo (OO). Mimo że wiele pojęć OO są wydajne i przydatne, nie wszystkie z nich są idealne do użycia. Poniższe listy oferują wskazówki dotyczące kategorii funkcji OO na wysokim poziomie.

**Rozważ użycie tych funkcji w wielu sytuacjach:**

* Kropkowego (`x.Length`)
* Elementy członkowskie wystąpień
* Niejawne konstruktory
* Statyczne elementy członkowskie
* Notacja indeksatora (`arr.[x]`)
* Argumenty nazwane i opcjonalne
* Interfejsy i implementacje interfejsu

**Nie najpierw uzyskać dostęp do tych funkcji, ale należy rozważnie zastosować je, jeśli są one wygodny do rozwiązania problemu:**

* Przeciążenie metody
* Hermetyzowany modyfikowalną danych
* Operatory dla typów
* Właściwości auto
* Implementowanie `IDisposable` i `IEnumerable`
* Rozszerzenia typu
* Zdarzenia
* Struktury
* Delegaty
* Wyliczenia

**Ogólnie należy unikać tych funkcji, chyba że należy użyć:**

* Hierarchii dziedziczenia na podstawie typu i dziedziczenie implementacji
* Wartości null i `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Preferuj kompozycji przed dziedziczenia

[Kompozycja za pośrednictwem dziedziczenia](https://en.wikipedia.org/wiki/Composition_over_inheritance) jest idiom długotrwałe, który dobrej kodzie języka F # można stosować się do. Podstawowe zasadą jest, że należy nie uwidacznia klasy podstawowej i wymusić wywołującym dziedziczą z tej klasy podstawowej, aby funkcje.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Implementować interfejsów, jeśli klasa nie ma potrzeby za pomocą wyrażeń obiektu

[Obiekt wyrażenia](../language-reference/object-expressions.md) umożliwiają implementować interfejsów na bieżąco, powiązanie z zaimplementowanym interfejsem wartość bez konieczności zrobić wewnątrz klasy. Opcja ta jest przydatna, zwłaszcza, jeśli użytkownik _tylko_ musi implementować interfejs i nie potrzebują pełnego klasy.

Na przykład, w tym miejscu jest kod, który jest uruchamiany w [Ionide](http://ionide.io/) zapewnienie Akcja poprawki kodu, jeśli dodano symbol, który nie ma `open` instrukcji dla:

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

Ponieważ nie jest konieczne dla klasy, gdy korzysta z API do kodu programu Visual Studio, wyrażenia obiektów są idealne narzędzie to. Są one również przydatna do testowania, jeśli chcesz zastąpić klasą zastępczą interfejsu testujące w sposób ad hoc jednostek.

## <a name="type-abbreviations"></a>Skróty typów

[Skróty typów](../language-reference/type-abbreviations.md) to wygodny sposób można przypisywać etykietę do innego typu, na przykład sygnatura funkcji lub bardziej złożonej typu. Na przykład następujący alias przypisuje etykietę co jest potrzebne do definiowania obliczeń z [CNTK](https://www.microsoft.com/cognitive-toolkit/), bezpośrednich uczenia biblioteki:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation` Nazwa to wygodny sposób do oznaczania każda funkcja, która odpowiada podpis jest aliasów. Za pomocą skrótów typu takie jest wygodne i umożliwia bardziej zwięzły kodu.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Unikaj skrótów typu do reprezentowania domeny

Chociaż skróty typów jest wygodną metodą nadanie nazwy do sygnatury funkcji, mogą być mylące podczas używanie innych typów. Należy wziąć pod uwagę ten skrót:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Może to być mylące na wiele sposobów:

* `BufferSize` nie jest klasą abstrakcyjną; jest po prostu inną nazwę dla liczby całkowitej.
* Jeśli `BufferSize` jest widoczna w publiczny interfejs API go łatwo zostać błędnie zinterpretowane oznacza więcej niż tylko `int`. Ogólnie rzecz biorąc, typy domeny ma wiele atrybutów do nich i nie są typy pierwotne, takie jak `int`. Ten skrót narusza tego założeń.
* Wielkość liter w wyrazie `BufferSize` (PascalCase) oznacza, że ten typ zawiera więcej danych.
* Ten alias nie oferuje zwiększenia przejrzystości w porównaniu z dostarczanie nazwany argument do funkcji.
* Skrót nie zostanie powiadomiony IL skompilowanych; jest tylko całkowitą i ten alias jest konstrukcję kompilacji.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

Podsumowując, niedogodności z skróty typów te są **nie** abstrakcje przez typy są ich używanie. W poprzednim przykładzie `BufferSize` jest po prostu `int` w obszarze obejmuje, z żadnych dodatkowych danych ani żadnych korzyści z systemu typu poza co `int` ma już.
