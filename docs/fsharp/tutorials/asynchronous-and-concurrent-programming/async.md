---
title: Programowanie asynchroniczne wF#
description: Dowiedz F# się, jak zapewniać czystą pomoc techniczną dla asynchroniczności w oparciu o model programowania na poziomie języka pochodzący z podstawowych koncepcji programowania funkcjonalnego.
ms.date: 12/17/2018
ms.openlocfilehash: 1ede4a5c1e26df271ac94f9b2c216ac84fb38f59
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395788"
---
# <a name="async-programming-in-f"></a>Programowanie asynchroniczne w F @ no__t-0

Programowanie asynchroniczne jest mechanizmem, który jest niezbędny dla nowoczesnych aplikacji z różnych powodów. Istnieją dwa podstawowe przypadki użycia, które napotykają większość deweloperów:

- Przedstawienie procesu serwera, który może obsłużyć znaczną liczbę współbieżnych żądań przychodzących, jednocześnie minimalizując zasoby systemowe zajęte podczas przetwarzania żądań czeka na dane wejściowe z systemów lub usług zewnętrznych dla tego procesu
- Utrzymywanie odpowiedzi na interfejsie użytkownika lub głównego wątku podczas współbieżnego postępu pracy w tle

Mimo że prace w tle często obejmują wykorzystanie wielu wątków, ważne jest, aby rozważyć koncepcje asynchroniczności i wielowątkowości osobno. W rzeczywistości są one oddzielnymi problemami, a jeden z nich nie ma innych. W tym artykule opisano to w bardziej szczegółowy sposób.

## <a name="asynchrony-defined"></a>Asynchroniczności zdefiniowany

Poprzedni punkt — ten asynchroniczności jest niezależny od użycia wielu wątków — jest również bardziej opisowy. Istnieją trzy koncepcje, które są czasami powiązane, ale ściśle niezależne od siebie:

- Współbieżności gdy wiele obliczeń jest wykonywanych w nadchodzących okresach czasowych.
- Równoległości gdy wiele obliczeń lub kilka części jednego obliczenia jest wykonywanych w dokładnie tym samym czasie.
- Asynchroniczności gdy jedno lub więcej obliczeń można wykonać niezależnie od przepływu głównego programu.

Wszystkie trzy są koncepcjami prostopadłymi, ale można je łatwo rozliczać, szczególnie gdy są używane razem. Na przykład może być konieczne wykonanie wielu obliczeń asynchronicznych równolegle. Nie oznacza to, że równoległość lub asynchroniczności oznacza siebie nawzajem.

Jeśli rozważasz etymology słowa "asynchroniczne", istnieją dwa elementy:

- "a", znaczenie "nie".
- "synchroniczne", znaczenie "w tym samym czasie".

Po umieszczeniu tych dwóch terminów, zobaczysz, że "asynchroniczne" oznacza "nie w tym samym czasie". To wszystko! W tej definicji nie ma implikacji współbieżności ani równoległości. Ta metoda jest również prawdziwa.

W praktyce, asynchroniczne obliczenia w programie F# są zaplanowane do wykonania niezależnie od przepływu głównego programu. Nie oznacza to współbieżności ani równoległości, ani nie oznacza, że Obliczanie zawsze odbywa się w tle. W rzeczywistości asynchroniczne obliczenia mogą nawet wykonywać synchronicznie, w zależności od rodzaju obliczenia i środowiska, w którym jest wykonywane obliczenie.

Głównym wnioskiemem jest to, że obliczenia asynchroniczne są niezależne od przepływu głównego programu. Chociaż istnieją pewne gwarancje dotyczące tego, kiedy lub jak są wykonywane asynchroniczne obliczenia, istnieją niektóre podejścia do organizowania i planowania. Pozostała część tego artykułu eksploruje podstawowe koncepcje dotyczące F# asynchroniczności oraz sposób używania typów, funkcji i wyrażeń wbudowanych w. F#

## <a name="core-concepts"></a>Podstawowe pojęcia

W F#programie programowanie asynchroniczne zawiera trzy podstawowe koncepcje:

- Typ `Async<'T>`, który reprezentuje szeregowe Obliczanie asynchroniczne.
- Funkcje modułu `Async`, które umożliwiają planowanie pracy asynchronicznej, tworzenie obliczeń asynchronicznych i przekształcanie asynchronicznych wyników.
- [Wyrażenie obliczeniowe](../../language-reference/computation-expressions.md)`async { }`, które zapewnia wygodną składnię do kompilowania i kontrolowania asynchronicznych obliczeń.

Te trzy koncepcje można zobaczyć w następującym przykładzie:

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

W przykładzie funkcja `printTotalFileBytes` jest typu `string -> Async<unit>`. Wywołanie funkcji nie powoduje rzeczywistego wykonania obliczeń asynchronicznych. Zamiast tego zwraca `Async<unit>`, który działa jako Specyfikacja * dla pracy, która jest wykonywana asynchronicznie. Wywoła `Async.AwaitTask` w swojej treści, co spowoduje przekonwertowanie wyniku <xref:System.IO.File.WriteAllBytesAsync%2A> na odpowiedni typ, gdy zostanie on wywołany.

Innym ważnym wierszem jest wywołanie `Async.RunSynchronously`. Jest to jeden z funkcji uruchamiania modułów asynchronicznych, które należy wywołać, jeśli chcesz rzeczywiście wykonać F# asynchroniczne obliczanie.

Jest to podstawowa różnica w stylu C#/VB programowanie `async`. W F#programie asynchroniczne obliczenia można traktować jako **zimne zadania**. Muszą być jawnie uruchomione w celu rzeczywistego wykonania. Ma to pewne zalety, ponieważ umożliwia łączenie i sekwencję asynchronicznych zadań znacznie łatwiej niż w C#/VB.

## <a name="combining-asynchronous-computations"></a>Łączenie asynchronicznych obliczeń

Oto przykład, który kompiluje się na poprzednim, przez połączenie obliczeń:

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

Jak widać, funkcja `main` ma wiele większej liczby wywołań. Koncepcyjnie wykonuje następujące czynności:

1. Przekształć argumenty wiersza polecenia na obliczenia `Async<unit>` z `Array.map`.
2. Utwórz `Async<'T[]>`, które harmonogramy i uruchamiają obliczenia `printTotalFileBytes` równolegle, gdy zostanie uruchomione.
3. Utwórz `Async<unit>`, które uruchomi obliczenia równoległe i zignoruj jego wynik.
4. Jawnie Uruchom ostatnie obliczenie z `Async.RunSynchronously` i blokuj do momentu zakończenia.

Po uruchomieniu tego programu `printTotalFileBytes` uruchamia się równolegle dla każdego argumentu wiersza polecenia. Ponieważ asynchroniczne obliczenia są wykonywane niezależnie od przepływu programu, nie ma kolejności, w której drukują informacje i kończą wykonywanie. Obliczenia będą wykonywane równolegle, ale ich kolejność wykonywania nie jest gwarantowana.

## <a name="sequencing-asynchronous-computations"></a>Asynchroniczne obliczenia sekwencjonowania

Ponieważ `Async<'T>` to specyfikacja pracy, a nie zadania już uruchomionego, można łatwo wykonywać bardziej intricatee przekształcenia. Oto przykład, który służy do sekwencjonowania zestawu asynchronicznych obliczeń, tak aby były wykonywane jeden po drugim.

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.RunSynchronously
    |> ignore
```

Spowoduje to zaplanowanie wykonywania `printTotalFileBytes` w kolejności elementów `argv`, a nie planowanie ich równolegle. Ponieważ następny element nie zostanie zaplanowany do momentu zakończenia ostatniego obliczenia, obliczenia zostaną uporządkowane w taki sposób, że ich wykonanie nie nakłada się na siebie.

## <a name="important-async-module-functions"></a>Ważne funkcje modułu asynchronicznego

Gdy piszesz kod asynchroniczny F# , zwykle współdziała z platformą, która obsługuje planowanie obliczeń. Nie jest to jednak zawsze przypadek, dlatego warto poznać różne funkcje uruchamiania w celu zaplanowania pracy asynchronicznej.

Ponieważ F# asynchroniczne obliczenia są _specyfikacją_ pracy, a nie reprezentacją już wykonywanej pracy, muszą być jawnie uruchomione przy użyciu funkcji początkowej. Istnieje wiele [funkcji uruchamiania asynchronicznego](https://msdn.microsoft.com/library/ee370232.aspx) , które są przydatne w różnych kontekstach. W poniższej sekcji opisano niektóre typowe funkcje uruchamiania.

### <a name="asyncstartchild"></a>Async. StartChild —

Uruchamia obliczenie elementu podrzędnego w ramach obliczeń asynchronicznych. Umożliwia to współbieżne wykonywanie wielu asynchronicznych obliczeń. Podrzędne obliczenie udostępnia token anulowania z obliczeniami nadrzędnymi. Jeśli Obliczanie nadrzędne zostanie anulowane, obliczenia podrzędne również zostaną anulowane.

Podpisane

```fsharp
computation: Async<'T> - timeout: ?int -> Async<Async<'T>>
```

Kiedy używać:

- Jeśli chcesz wykonać wiele asynchronicznych obliczeń jednocześnie, a nie jeden na raz, ale nie zaplanowano ich równolegle.
- Gdy chcesz powiązać okres istnienia obliczeń podrzędnych z tym, że jest to obliczenie nadrzędne.

Co należy obserwować:

- Uruchamianie wielu obliczeń przy użyciu `Async.StartChild` nie jest tak samo jak w przypadku planowania ich równolegle. Jeśli chcesz zaplanować obliczenia równolegle, użyj `Async.Parallel`.
- Anulowanie obliczenia nadrzędnego spowoduje anulowanie wszystkich rozpoczętych obliczeń podrzędnych.

### <a name="asyncstartimmediate"></a>Async. StartImmediate —

Uruchamia asynchroniczne obliczenie, rozpoczynając od razu od bieżącego wątku systemu operacyjnego. Jest to przydatne, jeśli trzeba zaktualizować coś w wątku wywołującym podczas obliczania. Na przykład jeśli asynchroniczne obliczenie musi zaktualizować interfejs użytkownika (na przykład zaktualizować pasek postępu), należy użyć `Async.StartImmediate`.

Podpisane

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Kiedy używać:

- Gdy trzeba zaktualizować coś w wątku wywołującym w środku obliczeń asynchronicznych.

Co należy obserwować:

- Kod w asynchronicznym obliczaniu zostanie uruchomiony niezależnie od wątku, w którym ma zostać zaplanowana. Może to być problematyczne, jeśli ten wątek jest w sposób niezależny, na przykład wątek interfejsu użytkownika. W takich przypadkach `Async.StartImmediate` jest prawdopodobnie nieodpowiednie do użycia.

### <a name="asyncstartastask"></a>Async. Startastask —

Wykonuje obliczenia w puli wątków. Zwraca <xref:System.Threading.Tasks.Task%601>, który zostanie wykonany w odpowiadającym stanie po zakończeniu obliczeń (tworzy wynik, zgłasza wyjątek lub jest anulowany). Jeśli nie podano tokenu anulowania, zostanie użyty domyślny token anulowania.

Podpisane

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

Kiedy używać:

- Gdy musisz wywołać interfejs API platformy .NET, który oczekuje <xref:System.Threading.Tasks.Task%601>, aby przedstawić wynik obliczeń asynchronicznych.

Co należy obserwować:

- To wywołanie spowoduje przydzielenie dodatkowego obiektu `Task`, co może zwiększyć obciążenie, jeśli jest używane często.

### <a name="asyncparallel"></a>Async. Parallel

Planuje sekwencję asynchronicznych obliczeń, które mają być wykonywane równolegle. Stopień równoległości można opcjonalnie dostrajać/ograniczyć przez określenie parametru `maxDegreesOfParallelism`.

Podpisane

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Kiedy używać go:

- Jeśli konieczne jest uruchomienie zestawu obliczeń w tym samym czasie i nie ma on zależności od ich kolejności wykonywania.
- Jeśli nie są wymagane wyniki z obliczeń zaplanowanych równolegle, dopóki nie zostaną ukończone.

Co należy obserwować:

- Można uzyskać dostęp tylko do wyników tablicy wartości po zakończeniu wszystkich obliczeń.
- Obliczenia będą wykonywane niezależnie od tego, że zaplanowano. Oznacza to, że nie można polegać na ich kolejności wykonywania.

### <a name="asyncsequential"></a>Async. sekwencyjny

Planuje sekwencję asynchronicznych obliczeń do wykonania w kolejności, w jakiej zostały przesłane. Pierwsze obliczenie zostanie wykonane, następnie następne i tak dalej. Żadne obliczenia nie będą wykonywane równolegle.

Podpisane

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

Kiedy używać go:

- Jeśli konieczne jest wykonanie wielu obliczeń w kolejności.

Co należy obserwować:

- Można uzyskać dostęp tylko do wyników tablicy wartości po zakończeniu wszystkich obliczeń.
- Obliczenia będą wykonywane w kolejności, w jakiej są przesyłane do tej funkcji, co może oznaczać, że upłynie więcej czasu przed zwróceniem wyników.

### <a name="asyncawaittask"></a>Async. Awaittask —

Zwraca asynchroniczne obliczenie, które oczekuje na wykonanie <xref:System.Threading.Tasks.Task%601> i zwróci jego wynik jako `Async<'T>`

Podpisane

```fsharp
task: Task<'T>  -> Async<'T>
```

Kiedy używać:

- Gdy korzystasz z interfejsu API platformy .NET, który zwraca <xref:System.Threading.Tasks.Task%601> w ramach F# obliczeń asynchronicznych.

Co należy obserwować:

- Wyjątki są opakowane w <xref:System.AggregateException> zgodnie z Konwencją biblioteki równoległej zadania i różnią się od sposobu F# , w jaki Async ogólnie występują wyjątki.

### <a name="asynccatch"></a>Async. catch

Tworzy asynchroniczne obliczenie, które wykonuje daną `Async<'T>`, zwracając `Async<Choice<'T, exn>>`. W przypadku pomyślnego zapełnienia `Async<'T>` zostanie zwrócona wartość `Choice1Of2` z wynikową wartością. Jeśli przed zakończeniem zostanie zgłoszony wyjątek, zostanie zwrócona wartość `Choice2of2` z podniesionym wyjątkem. Jeśli jest używany w przypadku obliczeń asynchronicznych, które są tworzone w wielu obliczeniach, a jedno z tych obliczeń zgłasza wyjątek, obliczenia obejmujące obejmie zostaną całkowicie zatrzymane.

Podpisane

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Kiedy używać:

- Gdy wykonujesz asynchroniczne zadanie, które może zakończyć się niepowodzeniem z wyjątkiem i chcesz obsłużyć ten wyjątek w obiekcie wywołującym.

Co należy obserwować:

- W przypadku korzystania z połączonych lub sekwencyjnych obliczeń asynchronicznych Obliczanie obejmujące obliczenia zostanie całkowicie zatrzymane, jeśli jedno z jego "wewnętrznego" obliczeń zgłosi wyjątek.

### <a name="asyncignore"></a>Async. Ignore

Tworzy asynchroniczne obliczenie, które uruchamia danego obliczenia i ignoruje jego wynik.

Podpisane

```fsharp
computation: Async<'T> -> Async<unit>
```

Kiedy używać:

- W przypadku obliczeń asynchronicznych, których wynik nie jest wymagany. Jest to analogiczne do kodu `ignore` dla kodu nieasynchronicznego.

Co należy obserwować:

- Jeśli musisz użyć tego przykładu, ponieważ chcesz użyć `Async.Start` lub innej funkcji wymagającej `Async<unit>`, należy rozważyć, czy odrzucanie wyniku nie jest możliwe. Odrzucanie wyników tylko w celu dopasowania do podpisu typu nie powinno być ogólnie wykonywane.

### <a name="asyncrunsynchronously"></a>Async. metody RunSynchronously

Uruchamia asynchroniczne obliczenie i czeka na wynik wątku wywołującego. To wywołanie blokuje.

Podpisane

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

Kiedy używać go:

- Jeśli potrzebujesz tego, użyj go tylko raz w aplikacji — w punkcie wejścia dla pliku wykonywalnego.
- Gdy nie masz opieki nad wydajnością i chcesz wykonać zestaw innych operacji asynchronicznych jednocześnie.

Co należy obserwować:

- Wywołanie `Async.RunSynchronously` blokuje wątek wywołujący do momentu zakończenia wykonywania.

### <a name="asyncstart"></a>Async. Start

Uruchamia asynchroniczne obliczenie w puli wątków, które zwraca `unit`. Nie czeka na jego wynik. Zagnieżdżone obliczenia rozpoczęte dla `Async.Start` są uruchamiane całkowicie niezależnie od obliczeń nadrzędnych, które je wywołały. Ich okres istnienia nie jest powiązany z żadnym z obliczeń nadrzędnych. Jeśli Obliczanie nadrzędne zostało anulowane, nie są anulowane żadne obliczenia podrzędne.

Podpisane

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Używaj tylko wtedy, gdy:

- Istnieje asynchroniczne obliczenie, które nie zwraca wyniku i/lub wymaga przetwarzania jednego.
- Nie musisz wiedzieć, kiedy kończy się Obliczanie asynchroniczne.
- Nie musisz określać wątku, w którym jest wykonywane asynchroniczne obliczenie.
- Nie trzeba znać ani zgłosić wyjątków wynikających z zadania.

Co należy obserwować:

- Wyjątki wywoływane przez obliczenia rozpoczęte z `Async.Start` nie są propagowane do obiektu wywołującego. Stos wywołań zostanie całkowicie odłożony.
- Wszelkie efekty pracy (takie jak wywołanie `printfn`) rozpoczęte z `Async.Start` nie spowoduje wystąpienia efektu w głównym wątku wykonywania programu.

## <a name="interoperating-with-net"></a>Współdziałanie z platformą .NET

Być może pracujesz z biblioteką lub C# bazą kodu .NET, która używa asynchronicznego [/oczekującego](../../../standard/async.md)programowania w stylu. Ze C# względu na to, że większość bibliotek .NET używa typów <xref:System.Threading.Tasks.Task%601> i <xref:System.Threading.Tasks.Task> jako ich rdzeńi podstawowe zamiast `Async<'T>`, należy przekroczyć granicę między tymi dwoma podejściami do asynchroniczności.

### <a name="how-to-work-with-net-async-and-taskt"></a>Jak korzystać z asynchronicznej platformy .NET i `Task<T>`

Praca z bibliotekami asynchronicznymi platformy .NET i bazami kodu, które używają <xref:System.Threading.Tasks.Task%601> (czyli obliczeń asynchronicznych, które mają zwracane wartości) jest prosta i wbudowana F#w program.

Można użyć funkcji `Async.AwaitTask` do oczekiwania na asynchroniczne Obliczanie platformy .NET:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

Za pomocą funkcji `Async.StartAsTask` można przekazać asynchroniczne obliczenie do obiektu wywołującego platformy .NET:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>Jak korzystać z asynchronicznej platformy .NET i `Task`

Aby korzystać z interfejsów API, które używają <xref:System.Threading.Tasks.Task> (czyli obliczeń asynchronicznych platformy .NET, które nie zwracają wartości), może być konieczne dodanie dodatkowej funkcji, która spowoduje przekonwertowanie `Async<'T>` na <xref:System.Threading.Tasks.Task>:

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

Istnieje już `Async.AwaitTask`, która akceptuje <xref:System.Threading.Tasks.Task> jako dane wejściowe. Za pomocą tej i wcześniej zdefiniowanej funkcji `startTaskFromAsyncUnit` można rozpocząć i oczekiwać <xref:System.Threading.Tasks.Task> typów z obliczeń F# asynchronicznych.

## <a name="relationship-to-multithreading"></a>Relacja do wielowątkowości

Chociaż wątki są wymienione w tym artykule, istnieją dwie ważne kwestie, które należy zapamiętać:

1. Nie ma koligacji między asynchronicznym obliczaniem a wątkiem, chyba że jest on jawnie uruchamiany w bieżącym wątku.
1. Programowanie asynchroniczne w F# programie nie jest abstrakcją dla wielowątkowości.

Na przykład obliczenia mogą być uruchamiane w wątku wywołującego, w zależności od rodzaju pracy. Obliczenia mogą również "przeskoczyć" między wątkami, co pociąga za sobą niewielką ilość czasu, aby wykonywać przydatne działania w okresie "oczekiwanie" (na przykład podczas przesyłania połączenia sieciowego).

Chociaż F# program zapewnia pewne możliwości uruchamiania obliczeń asynchronicznych w bieżącym wątku (lub jawnie nie w bieżącym wątku), asynchroniczności zazwyczaj nie jest skojarzony z określoną strategią wątkowości.

## <a name="see-also"></a>Zobacz także

- [F# Asynchroniczny model programowania](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Przewodnik F# asynchroniczny aparatu Jet. com](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F#dla zabawy i asynchronicznego Przewodnik programowania](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [Asynchroniczny C# w F#i: asynchroniczny pytania dotyczące usługi wC#](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
