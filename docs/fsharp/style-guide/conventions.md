---
title: 'Konwencje kodowania F #'
description: 'Informacje ogólne wytyczne i idiomy podczas pisania kodu, F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 21119b6d69e00f359104bfb6eab7681bdbfb8d78
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "49087391"
---
# <a name="f-coding-conventions"></a>Konwencje kodowania F #

Poniższe konwencje są formułowane z doświadczenia w pracy z dużą F # bazach kodu. [Pięć zasadami dobrej kodzie języka F #](index.md#five-principles-of-good-f-code) stanowiących poszczególne zalecenia. Są one związane z [F # składnika wytyczne dotyczące projektowania](component-design-guidelines.md), ale są odpowiednie dla dowolnego kodzie języka F #, nie tylko składniki, takie jak biblioteki.

## <a name="organizing-code"></a>Organizowanie kodu

F # zawiera dwa podstawowe sposoby organizowania kodu: modułów i przestrzeni nazw. Te są podobne, ale różnią się w następujący sposób:

* Przestrzenie nazw są kompilowane jako obszary nazw .NET. Moduły są kompilowane jako klas statycznych.
* Przestrzenie nazw są zawsze najwyższego poziomu. Moduły mogą być najwyższego poziomu i zagnieżdżone w innych modułach.
* Przestrzenie nazw może obejmować wiele plików. Nie można modułów.
* Moduły mogą być dekorowane za pomocą `[<RequireQualifiedAccess>]` i `[<AutoOpen>]`.

Poniższe wskazówki mogą pomóc w ich użyć do organizowania kodu.

### <a name="prefer-namespaces-at-the-top-level"></a>Preferuj przestrzeni nazw na najwyższym poziomie

Dla dowolnego publicznie konsumpcyjnych kodu przestrzenie nazw są preferencyjne modułów na najwyższym poziomie. Ponieważ są one kompilowane jako obszary nazw .NET, są one może być używany przez C# nie problemu.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Za pomocą najwyższego poziomu modułu mogą pojawiać się różne, gdy zostanie wywołana tylko z języka F #, ale dla języka C# konsumentów, może oczekiwano obiektów wywołujących, dzięki kwalifikowania `MyClass` z `MyCode` modułu.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Stosowanie starannie `[<AutoOpen>]`

`[<AutoOpen>]` Konstrukcji można charakteryzują się zakres co jest dostępne dla kodu wywołującego, a odpowiedź na coś, z której pochodzi to "Magia". To zwykle nie jest dobrym znakiem. Wyjątkiem od tej reguły jest biblioteka Core F #, sama (chociaż ten fakt jest również nieco kontrowersyjny).

Jednak to udogodnienie Jeśli masz funkcjonalność pomocnika dla publicznego interfejsu API, którą chcesz zorganizować niezależnie od tego publicznego interfejsu API.

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

Dzięki temu można szczegółów klarownie implementacji oddzielne z publicznego interfejsu API funkcji bez konieczności pełnej kwalifikacji pomocnika za każdym razem, należy wywołać.

Ponadto udostępnianie rozszerzenie metod i konstruktorów wyrażeń na poziomie przestrzeni nazw mogą być starannie wyrównywać wyrażone za pomocą `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Użyj `[<RequireQualifiedAccess>]` zawsze, gdy nazwy mogą powodować konflikt lub uważasz, że ułatwia z czytelność

Dodawanie `[<RequireQualifiedAccess>]` atrybut do modułu wskazuje, że moduł nie może być otwarty i że odwołania do elementów moduł wymaga jawnego kwalifikowana dostępu. Na przykład `Microsoft.FSharp.Collections.List` moduł ma tego atrybutu.

Jest to przydatne, gdy funkcje i wartości w module mają nazwy, które mogą powodować konflikt z nazwami w innych modułach. Wymagające dostępu kwalifikowana może znacznie zwiększyć długoterminowe łatwość konserwacji i evolvability biblioteki.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Sortuj `open` instrukcji topologically

W języku F #, kolejności deklaracji dla Ciebie ważne, łącznie z `open` instrukcji. Jest to w przeciwieństwie do języka C#, gdy efekt `using` i `using static` jest niezależna od kolejności te instrukcje w pliku.

W języku F # można w tle elementy otwarte w zakresie inne osoby już istnieje. Oznacza to, że zmiana kolejności `open` instrukcji może zmienić znaczenie kodu. W wyniku tego wszystkie dowolnego sortowania wszystkich `open` instrukcji (na przykład alfanumerycznie) ogólnie nie zaleca się, co najmniej wygenerować różne zachowanie, które można by oczekiwać.

Zamiast tego zaleca się je posortować [topologically](https://en.wikipedia.org/wiki/Topological_sorting); oznacza to, że kolejność swoje `open` instrukcji w kolejności, w którym _warstwy_ systemu są zdefiniowane. Wykonując alfanumeryczne, sortowanie w różnych warstwach topologii mogą być również uwzględnione.

Na przykład poniżej przedstawiono topologii sortowania dla języka F # kompilatora publicznego interfejsu API pliku usługi:

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

Należy pamiętać, że podział wiersza oddziela warstwy topologii z poszczególnymi warstwami posortowana alfanumerycznie później. Kod zostanie prawidłowo organizuje bez przypadkowo przesłanianie wartości.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Używanie klas do zawierają wartości, które mają skutki uboczne

Istnieje wiele razy podczas inicjowania wartość może mieć efekty uboczne, takie jak utworzenie wystąpienia kontekstu do bazy danych lub innego zasobu zdalnego. Jest kuszące, aby zainicjować takich elementów w module i używać go w kolejnych funkcji:

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

Jest to często to zły pomysł kilka możliwych przyczyn:

Po pierwsze Konfiguracja aplikacji są przesyłane do bazy kodu z `dep1` i `dep2`. Jest to trudne utrzymanie w większych bazach kodu.

Drugi, statycznie zainicjowane danych nie może zawierać wartości, które nie są bezpieczne dla wątków, jeśli sam składnik użyje wielu wątków. Jest to wyraźnie naruszona przez `dep3`.

Na koniec inicjowania modułu kompiluje w konstruktorze statycznym jednostki całej kompilacji. W przypadku dowolnego błędu podczas inicjowania umożliwiają granica wartości w tym module, manifesty go jako `TypeInitializationException` który następnie jest buforowana przez cały okres istnienia aplikacji. Może to być trudny do zdiagnozowania. Zazwyczaj jest wyjątek wewnętrzny, który może próbować poprawić, ale jeśli nie istnieje, to nie ma żadnych informacją jest główną przyczynę.

Po prostu użyj prostą klasę do przechowywania zależności:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Dzięki temu następujące czynności:

1. Wypychanie dowolny stan zależne spoza sam interfejs API.
2. Teraz można przeprowadzić konfigurację poza interfejsu API.
3. Błędy podczas inicjowania wartości zależne nie są może być przedstawiany jako `TypeInitializationException`.
4. Interfejs API jest teraz łatwiejsze do testowania.

## <a name="error-management"></a>Błąd zarządzania

Zarządzanie błędami w dużych systemach jest pozwala złożone i rozmowach i nie ma żadnych silver punktorów w celu zapewnienia systemy są odporne na uszkodzenia i zachowywać się również. Poniższe wskazówki powinno oferować się ze wskazówkami zawartymi w przechodząc miejsce to trudne.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Reprezentuje przypadków błędów i stan niedozwolony w typach wewnętrznej do Twojej domeny

Za pomocą [sumy rozłączne](../language-reference/discriminated-unions.md), F # zapewnia możliwość reprezentuje stan programu wadliwe w Twoim systemie typu. Na przykład:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

W tym przypadku istnieją trzy sposoby znane, których wycofanie pieniądze z konta bankowego może zakończyć się niepowodzeniem. Każdy przypadek błędu jest reprezentowana w typie, a ten sposób można przetwarzać bezpiecznie w całym programie.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Ogólnie rzecz biorąc, jeśli można modelować różne sposoby szukają mogą **się nie powieść** w domenie, następnie dodanymi komentarzami kodu jest już traktowany jako coś muszą radzić sobie z oprócz zwykłego przepływu. Jest po prostu część przepływu normalnego programu, a nie traktowane jako **wyjątkowych**. Istnieją dwie podstawowe korzyści, w tym:

1. Jest łatwiejsze w konserwacji zgodnie z domeny zmienia się wraz z upływem czasu.
2. W przypadku wystąpienia błędów są łatwiejsze do testów jednostkowych.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Użyj wyjątków, kiedy nie może być reprezentowana błędy typów

Nie wszystkie błędy mogą być reprezentowane w domenie problem. Te rodzaje błędów są *wyjątkowych* pochylone, w związku z tym możliwości pozyskiwania i przechwytywać wyjątki w języku F #.

Po pierwsze, zaleca się przeczytanie [wytyczne dotyczące projektowania wyjątek](../../standard/design-guidelines/exceptions.md). Te mają również zastosowanie do F #.

Główne konstrukcji, dostępna w języku F # na potrzeby zgłaszania wyjątków, należy rozważyć w następującej kolejności priorytetu:

| Funkcja | Składnia | Cel |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Wywołuje `System.ArgumentNullException` o nazwie określony argument. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Wywołuje `System.ArgumentException` z nazwą określonego argumentu i wiadomość. |
| `invalidOp` | `invalidOp "message"` | Wywołuje `System.InvalidOperationException` z określonym komunikatem. |
|`raise`| `raise (ExceptionType("message"))` | Mechanizm ogólnego przeznaczenia zgłaszanie wyjątków. |
| `failwith` | `failwith "message"` | Wywołuje `System.Exception` z określonym komunikatem. |
| `failwithf` | `failwithf "format string" argForFormatString` | Wywołuje `System.Exception` komunikatem określona przez ciąg formatu i jego danych wejściowych. |

Użyj `nullArg`, `invalidArg` i `invalidOp` jako mechanizm do zgłoszenia `ArgumentNullException`, `ArgumentException` i `InvalidOperationException` po zidentyfikowaniu odpowiednich.

`failwith` i `failwithf` funkcje ogólnie należy unikać, ponieważ pobierają one base `Exception` typu określonego wyjątku. Zgodnie [wytyczne dotyczące projektowania wyjątek](../../standard/design-guidelines/exceptions.md), należy podnieść bardziej szczegółowe wyjątki, kiedy tylko można.

### <a name="using-exception-handling-syntax"></a>Przy użyciu składni obsługi wyjątków

Język F # obsługuje wyjątek wzorców za pośrednictwem `try...with` składni:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Uzgadnianie funkcji do wykonania w przypadku wyjątku z dopasowaniem wzorca mogą być nieco trudne, jeśli chcesz zachować zgodność czystego kodu. Jeden sposób obsługi to jest użycie [wzorców](../language-reference/active-patterns.md) jako środek do funkcji grupy otaczającego przypadki błędów, z wyjątkiem samej. Na przykład użytkownik może zużywałoby interfejsu API, który po jego zgłasza wyjątek, otacza cenne informacje metadanych wyjątku. Rozpakowanie przydatne wartości w treści przechwycony wyjątek wewnątrz — aktywny wzorzec i zwraca, czy wartość może być pomocny w niektórych sytuacjach.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Nie należy używać obsługi wyjątków zastąpić monadic błędów

Wyjątki są postrzegane jako nieco taboo w programowania funkcjonalnego. W rzeczywistości wyjątki narusza czystość, dzięki czemu można bezpiecznie należy wziąć pod uwagę ich nie całkiem funkcjonalności. Jednak to ignoruje rzeczywistość, której kod należy uruchomić i że środowisko uruchomieniowe, które mogą wystąpić błędy. Ogólnie rzecz biorąc można napisać kod, przy założeniu, że większość elementów są pure ani total, aby zminimalizować nieprzyjemnych niespodzianek.

Warto wziąć pod uwagę następujące podstawowe zalety/aspekty wyjątki względem ich istotności i stosowności środowisko uruchomieniowe platformy .NET i wielu języków ekosystemu jako całości:

1. Zawierają one szczegółowych informacji diagnostycznych, który jest bardzo pomocne przy debugowaniu problemu.
2. Są one dobrze rozumiane przez środowisko uruchomieniowe i innymi językami .NET.
3. One może zmniejszyć znaczące standardowy w porównaniu z kodem, który wykracza poza drodze do *uniknąć* wyjątki przez zaimplementowanie pewien podzbiór semantyki ich na podstawie zapytań ad-hoc.

Ten punkt trzeci ma krytyczne znaczenie. Proste i złożone operacji kończy się niepowodzeniem, należy używać wyjątków może spowodować radzenia sobie ze strukturami następująco:

```fsharp
Result<Result<MyType, string>, string list>
```

Łatwo co może prowadzić do delikatna kodu, takich jak dopasowania do wzorca w "stringly wpisane" błędy:

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Ponadto może być kuszące wchłonąć każdy wyjątek, wymaganą dla funkcji "prosta", która zwraca typ "wrażeń":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Niestety `tryReadAllText` może zgłosić liczne wyjątki, w oparciu o wiele rzeczy, które mogą wystąpić w systemie plików, a ten kod natychmiast odrzuca wszelkie informacje na temat co może rzeczywiście być pójdzie w danym środowisku. Jeśli ten kod można zastąpić typu wyniku, jesteś do analizowania komunikatów "stringly wpisane" Błąd:

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

I wprowadzania do samego obiektu wyjątku w `Error` Konstruktor tylko wymusza prawidłowo radzenia sobie z typu wyjątku w witrynie wywołania, a nie w funkcji. Spowoduje to skutecznie tworzy zaznaczone wyjątków, które są bardzo unfun radzenia sobie z jako obiekt wywołujący interfejs API.

Jest dobrą alternatywą do powyższych przykładach catch *określonych* wyjątków i zwrócenia zrozumiałą wartość w kontekście tego wyjątku. Jeśli zmodyfikujesz `tryReadAllText` funkcji w następujący sposób, `None` ma więcej znaczenie:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Zamiast działa jako przechwytującą cały, ta funkcja będzie teraz poprawnie obsługiwać przypadku jeśli plik nie został znaleziony i przypisać tym znaczenie zwrotu. Ta wartość zwracana można mapować do tego przypadku błąd podczas nie odrzucanie żadnych informacji kontekstowych lub wymuszanie wywołań, aby poradzić sobie z przypadkiem, które mogą nie być odpowiednie w tym momencie w kodzie.

Typy takie jak `Result<'Success, 'Error>` są odpowiednie dla podstawowe operacje, których nie są one zagnieżdżone i F # opcjonalne typy są idealne do reprezentowania, gdy coś, co może albo zwracany *coś* lub *nic*. One zamiennika dla wyjątków, nie są jednak i nie może być używany w celu podjęcia do zastąpienia wyjątków. Zamiast ich powinny dotyczyć rozsądnie adres konkretnych aspektów wyjątków i zasady dotyczące zarządzania błędów względami docelowych.

## <a name="partial-application-and-point-free-programming"></a>Aplikacja częściowa i programowanie bez punktu

Język F # obsługuje aplikacja częściowa i różne sposoby, aby program w stylu bezpłatne punktu. Może to być przydatne w przypadku ponownego użycia kodu w ramach modułu lub wykonania elementu, ale zwykle nie jest coś do udostępnić publicznie. Ogólnie rzecz biorąc programowanie bez punktu jest kapitałowymi w i samego siebie i można dodać cognitive dużą przeszkodę dla osób, które nie są pracować w stylu.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Nie należy używać aplikacja częściowa i currying w publicznych interfejsów API

Z wyjątkiem mały Użyj częściowe aplikacji w publicznych interfejsów API może być mylące dla klientów. Zazwyczaj `let`— są powiązane wartości w kodzie języka F # **wartości**, a nie **funkcji wartości**. Łączenie ze sobą, wartości i wartości funkcji może spowodować zapisywanie niewielką liczbę wierszy kodu w zamian za znacznej liczby cognitive obciążenie, zwłaszcza, jeśli połączone przy użyciu operatorów, takich jak `>>` do redagowania funkcji.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Należy wziąć pod uwagę wpływ narzędzi do programowania bez punktu

Funkcje rozwinięte etykiety nie ich argumentów. Ma to wpływ narzędzi. Należy wziąć pod uwagę następujące dwie funkcje:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Oba są prawidłowe funkcje, ale `funcWithApplication` jest funkcją rozwinięte. Po umieszczeniu ich typów w edytorze widzisz taki komunikat:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

W witrynie wywołania etykietek narzędzi w narzędzia, takiego jak Visual Studio nie zapewni istotnych informacji o tym, co `string` i `int` faktycznie reprezentują typów wejściowych.

Jeśli napotkasz bezpłatne punkt kodu, takich jak `funcWithApplication` jest w użyciu publicznie, zaleca się zrobić pełnym rozszerzeniu η, aby narzędzi można wybrać w górę w nazw opisowych dla argumentów.

Ponadto debugowanie kodu bez punktu może stanowić wyzwanie, jeśli jest to niemożliwe. Narzędzia do debugowania opierają się na wartościach powiązany z nazw (na przykład `let` powiązania) tak, aby sprawdzić wartości pośrednich midway przez wykonanie. Jeśli Twój kod nie ma żadnych wartości, aby sprawdzić, nie ma nic do debugowania. W przyszłości, narzędzia debugowania, może się rozwijać syntetyzować te wartości opartym o ścieżki wykonanych wcześniej, ale nie jest dobry pomysł, aby zabezpieczyć postawienie na *potencjalnych* debugowania funkcjonalności.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Należy wziąć pod uwagę częściowego stosowania jako technika zmniejszyć wewnętrzny standardowy

W przeciwieństwie do wcześniejszego punktu aplikacja częściowa to narzędzie nagraliście w celi zmniejszenia standardowy wewnątrz aplikacji lub bardziej podstawy interfejsu API. Może być przydatne w przypadku implementacji interfejsów API bardziej skomplikowane, gdzie standardowy jest często bolesne radzenia sobie z testów jednostkowych. Na przykład ilustruje poniższy kod, jak można osiągnąć jakie najbardziej pozorowania struktury nadaj możesz bez przełączania zewnętrzna zależność od takiego framework i konieczności uczenia się z odpowiednimi tworzony na zamówienie interfejsu API.

Na przykład należy wziąć pod uwagę następujące topografii rozwiązania:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` może udostępniać takie jak kod:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Testy jednostkowe `Transactions.doTransaction` w `ImplementationLogic.Tests.fspoj` jest proste:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Częściowe stosowanie `doTransaction` z kontekstem pozorowania obiekt umożliwia wywołanie funkcji we wszystkich testów jednostkowych, bez konieczności utworzenia kontekstu pozorowane każdorazowo:

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

Ta technika nie powinny być powszechnie stosowane do całej bazie kodu, ale jest dobrym sposobem zmniejszenia standardowy skomplikowane elementy wewnętrzne i te elementy wewnętrzne testy jednostkowe.

## <a name="access-control"></a>Kontrola dostępu

F # zawiera wiele opcji [kontroli dostępu](../language-reference/access-control.md), dziedziczone od co to jest dostępne w środowisku uruchomieniowym .NET. Nie są one po prostu użyteczne dla typów — można ich użyć zbyt dla funkcji.

* Preferuj non -`public` typów i elementów członkowskich, dopóki nie będą one potrzebne do być publicznie w użyciu. Zmniejsza to także jakie kilku klientów do.
* Dokładamy wszelkich starań zachować wszystkie funkcje Pomocnika `private`.
* Rozważ użycie `[<AutoOpen>]` na prywatny moduł funkcji pomocnika, gdy staną się wiele.

## <a name="type-inference-and-generics"></a>Wnioskowanie o typie i typami ogólnymi

Wnioskowanie o typie mogą pomóc w pisaniu mnóstwo standardowy. I automatyczna Generalizacja w kompilatorze F # mogą pomóc, dzięki czemu można tworzyć bardziej ogólnymi kodu przy użyciu prawie żadnego dodatkowego wysiłku z Twojej strony. Jednak te funkcje nie są powszechnie dobre.

* Warto nadać nazwy argumentów za pomocą jawnych typów w publicznych interfejsów API i nie należy polegać na wnioskowanie o typie dla tego.

    Jest to spowodowane tym, że **możesz** powinna mieć kontrolę nad kształt interfejsu API, nie kompilatora. Mimo że kompilator może wykonać zadanie poprawnie na wnioskowanie typów dla Ciebie, istnieje możliwość mają kształtu zmiany interfejsu API, jeśli elementy wewnętrzne, które opiera się na zostały zmienione typy. Może to być, co chcesz zrobić, ale prawie na pewno będzie skutkować istotne zmiany interfejsu API niższego rzędu konsumentów będzie miał do czynienia z. Zamiast tego należy jawnie kontrolować kształt publicznego interfejsu API, następnie można sterować tymi przełomowe zmiany. W warunkach DDD to może być uważane za warstwę przeciwdegradacyjną.

* Należy rozważyć nadanie znaczącą nazwę, aby argumenty ogólne.

    Chyba, że piszesz naprawdę rodzajowy kod, który nie jest specyficzna dla danej domeny, nazwę opisową może pomóc inni programiści zrozumienie domeny, które działają w. Na przykład, parametru typu o nazwie `'Document` w kontekście interakcji z dokumentem bazy danych zrozumiałe, typów dokumentu ogólnego można zaakceptować według funkcji lub elementu członkowskiego, w którym pracujesz.

* Należy wziąć pod uwagę nazywanie parametrów typu ogólnego, za pomocą PascalCase.

    Jest ogólny sposób, aby wykonywały na platformie .NET, dlatego zalecane jest, że używasz PascalCase zamiast snake_case lub camelCase.

Na koniec automatyczna Generalizacja nie zawsze jest boon dla osób, które są nowe w F # lub dużej bazy kodu. Jest cognitive obciążenie za pomocą składników, które są rodzajowe. Ponadto jeśli automatycznie uogólnionego funkcje nie są używane z różnymi typami danych wejściowych (umożliwiają tylko, jeśli są one przeznaczone do użycia jako takie), a następnie daje żadnych korzyści rzeczywistych do nich jest ogólny w danym momencie. Zawsze należy rozważyć, jeśli kod, który zapisuje się faktycznie będą korzystać z ogólnych.

## <a name="performance"></a>Wydajność

F # wartości są niezmienne domyślnie, co pozwala uniknąć niektórych rodzajów błędów (szczególnie tych dotyczących współbieżności i równoległości). Jednak w niektórych przypadkach, w celu osiągnięcia optymalnej (lub nawet uzasadnione) skuteczność czas wykonywania lub alokacji pamięci zakresu pracy może najlepiej zaimplementować przy użyciu mutacji w miejscu stanu. Jest to możliwe w zasadzie zgłoszenie zgody na uczestnictwo w języku F # za pomocą `mutable` — słowo kluczowe.

Jednak użycie `mutable` w języku F # mogą uznać kłóci czystości funkcjonalności. To jest w dobrym stanie, jeśli dostosowano oczekiwań z czystości [referencyjną przezroczystości](https://en.wikipedia.org/wiki/Referential_transparency). Przezroczystość referencyjnej — nie czystości — jest jej celem podczas pisania funkcji F #. Umożliwia to zapisywanie funkcjonalności interfejsu za pośrednictwem implementacji opartej na mutacji wydajności kodu krytycznego.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Zawijania mutable kodu za pomocą niezmienialnych interfejsów

Z przezroczystością referencyjną jako cel ważne jest aby napisać kod, który nie ujawnia mutable underbelly newralgicznym dla wydajności funkcji. Na przykład, poniższy kod implementuje `Array.contains` funkcji w podstawowej biblioteki języka F #:

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

Wywołanie tej funkcji wiele razy nie zmienia się tablica bazowa, ani nie wymaga zachować wszystkie modyfikowalny stan, w jego wykorzystanie. Jest referentially przezroczyste, mimo że prawie każdy wiersz kodu w nim używa mutacji.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Należy wziąć pod uwagę enkapsulacji mutable danych w klasach

W powyższym przykładzie użyto jednej funkcji do hermetyzacji operacje przy użyciu tych danych. Nie zawsze jest to wystarczające dla bardziej złożonych zestawów danych. Należy wziąć pod uwagę następujące zestawy funkcji:

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

Ten kod jest wydajna, ale udostępnia struktury danych mutacji, że obiekty wywołujące odpowiedzialność. Może to zostać zawinięty wewnątrz klasy bez członków podstawowych, które można zmienić:

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

`Closure1Table` hermetyzuje wewnętrzna struktura danych mutacji, a tym samym nie wymuszanie obiekty wywołujące do obsługi podstawowej struktury danych. Klasy są wydajnym sposobem hermetyzacji danych i procedur, które są oparte na mutacji bez narażania szczegółowe informacje dotyczące obiektów wywołujących.

### <a name="prefer-let-mutable-to-reference-cells"></a>Preferuj `let mutable` do komórki odwołań

Komórki odwołań są sposobem reprezentowania odwołania do wartości, a nie z samą wartość. Mimo że mogą one służyć do kodu wrażliwego na wydajność, zwykle nie są zalecane. Rozważmy następujący przykład:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Używanie komórek odwołań teraz "pollutes" wszystkie kolejne kodu z konieczności cofnięcia odwołania i ponownie odwoływać się do danych bazowych. Zamiast tego należy wziąć pod uwagę `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Oprócz pojedynczy punkt mutacji w trakcie wykonywania wyrażenia lambda wszystkie inny kod, który dotyka `acc` to zrobić w taki sposób, który nie różni się do użycia jako normalny `let`-granica wartości niezmienne. Ułatwi zmiany wraz z upływem czasu.

## <a name="object-programming"></a>Programowanie obiektów

F # zawiera pełną pomoc techniczną dla obiektów i pojęcia zorientowane obiektowo (wprowadzaniem). Chociaż wiele pojęć wprowadzaniem są wydajne i użyteczne, nie wszystkie z nich są idealne do użycia. Następujące listy oferuje wskazówki dotyczące kategorii funkcji wprowadzaniem na wysokim poziomie.

**Rozważ użycie tych funkcji w wielu sytuacjach:**

* Notacji z kropką (`x.Length`)
* Elementy członkowskie wystąpień
* Niejawne konstruktorów
* Statyczne elementy członkowskie
* Notacja indeksatora (`arr.[x]`)
* Argumenty nazwane i opcjonalne
* Interfejsy i implementacje interfejsu

**Nie najpierw dotrzeć do tych funkcji, ale rozsądnie zastosować je, gdy są one wygodny w celu rozwiązania problemu:**

* Przeciążenie metody
* Encapsulated mutable danych
* Operatory typów
* Właściwości automatyczne
* Implementowanie `IDisposable` i `IEnumerable`
* Rozszerzenia typu
* Zdarzenia
* Struktury
* Delegaty
* Wyliczenia

**Ogólnie należy unikać tych funkcji, chyba że należy użyć:**

* Hierarchie dziedziczenia na podstawie typu i dziedziczenie implementacji
* Wartości null i `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Preferuj kompozycji przed dziedziczenia

[Kompozycja przez dziedziczenie](https://en.wikipedia.org/wiki/Composition_over_inheritance) jest długotrwałych idiom, które można stosować dobre kodzie języka F #. Podstawową zasadą jest, konieczne jest dalsze nie uwidocznić klasę bazową i wymusić wywołujących dziedziczyć z tej klasy bazowej, aby uzyskać funkcjonalność.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Użyj wyrażenia obiektów do implementacji interfejsów, jeśli nie potrzebujesz, klasa

[Wyrażenia obiektów](../language-reference/object-expressions.md) umożliwiają implementować interfejsy na bieżąco, powiązanie zaimplementowanego interfejsu z wartością bez konieczności zrobić wewnątrz klasy. Jest to wygodne, zwłaszcza wtedy, gdy użytkownik _tylko_ muszą implementować interfejs i nie potrzebują pełnego klasy.

Na przykład poniżej przedstawiono kod, który jest uruchamiany w [Ionide](http://ionide.io/) zapewnienie Akcja poprawki kodu, jeśli po dodaniu symboli, które nie mają `open` poufności informacji dotyczące:

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

Ponieważ nie ma potrzeby klasy podczas interakcji z API kodu w usłudze Visual Studio, wyrażenia obiektów są idealnym narzędziem do tego. Są one również przydatny w przypadku testowania jednostkowego, gdy chcesz zastąpić klasą zastępczą interfejsu testujące w sposób ad-hoc.

## <a name="type-abbreviations"></a>Skróty typów

[Skróty typów](../language-reference/type-abbreviations.md) to wygodny sposób, aby przypisać etykietę do innego typu, takiego jak sygnatura funkcji lub bardziej złożonych typów. Na przykład, następujący alias przypisuje etykietę co jest potrzebne do definiowania obliczeń z [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), biblioteka do uczenia głębokiego:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation` Nazwa jest wygodnym sposobem określenia żadnej funkcji, która pasuje do podpisu jest tworzenie aliasów. Za pomocą skróty typów, takich jak to jest wygodne i pozwala na bardziej zwięzłą kodu.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Należy unikać skróty typów do reprezentowania Twojej domeny

Chociaż skróty typów jest wygodne w przypadku nadania nazwy do sygnatury funkcji, mogą to być mylące po używanie innych typów. Należy wziąć pod uwagę ten skrót:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Może to być mylące na wiele sposobów:

* `BufferSize` nie jest klasą abstrakcyjną; jest po prostu inną nazwę dla liczby całkowitej.
* Jeśli `BufferSize` jest uwidaczniany w publiczny interfejs API go mogą łatwo zostać błędnie zinterpretowane jako oznaczenie więcej niż tylko `int`. Ogólnie rzecz biorąc, typy domen mają wiele atrybutów do nich i nie typy pierwotne, takie jak `int`. Ten skrót narusza tego założeń.
* Wielkość liter w wyrazie `BufferSize` (PascalCase) oznacza, że ten typ posiada większej ilości danych.
* Ten alias nie oferuje większą przejrzystość w porównaniu ze świadczeniem nazwany argument do funkcji.
* Skrót nie zostanie powiadomiony w skompilowanych IL; jest po prostu liczbą całkowitą, a ten alias jest konstrukcją kompilacji.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

Podsumowanie niedogodności z skróty typów te są **nie** abstrakcji za pośrednictwem typów są ich używanie. W poprzednim przykładzie `BufferSize` jest po prostu `int` dzieje się w tle, z Brak dodatkowych danych ani żadnych korzyści z system typów, oprócz co `int` ma już.
