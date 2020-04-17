---
title: Programowanie asynchroniowe
description: Dowiedz się, jak F# zapewnia czystą obsługę asynchrony na podstawie modelu programowania na poziomie języka pochodzących z podstawowych koncepcji programowania funkcjonalnego.
ms.date: 12/17/2018
ms.openlocfilehash: 9b2e3057c126d84474c21fde653da5bbee32938a
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608039"
---
# <a name="async-programming-in-f"></a>Programowanie asynchroniowe w F\#

Programowanie asynchroniczne jest mechanizmem, który jest niezbędny do nowoczesnych zastosowań z różnych powodów. Istnieją dwa podstawowe przypadki użycia, które napotka większość deweloperów:

- Przedstawianie procesu serwera, który może obsługiwać znaczną liczbę równoczesnych żądań przychodzących, przy jednoczesnym zminimalizowaniu zasobów systemowych zajętych podczas przetwarzania żądań oczekuje na dane wejściowe z systemów lub usług zewnętrznych dla tego procesu
- Obsługa elastycznego interfejsu użytkownika lub wątku głównego przy jednoczesnym postępie pracy w tle

Chociaż praca w tle często wiąże się z wykorzystaniem wielu wątków, ważne jest, aby rozważyć pojęcia asynchrony i wielowątkowe oddzielnie. W rzeczywistości są to odrębne obawy, a jedno nie oznacza drugiego. Co znajduje się w tym artykule opisano to bardziej szczegółowo.

## <a name="asynchrony-defined"></a>Asynchrony zdefiniowane

Poprzedni punkt - że asynchrony jest niezależna od wykorzystania wielu wątków - warto wyjaśnić nieco dalej. Istnieją trzy pojęcia, które są czasami powiązane, ale ściśle niezależne od siebie:

- Współbieżność; gdy wiele obliczeń wykonuje się w nakładających się okresach.
- Równoległość; gdy wiele obliczeń lub kilka części pojedynczych obliczeń działa dokładnie w tym samym czasie.
- Asynchrony; gdy jedno lub więcej obliczeń może być wykonywanych oddzielnie od głównego przepływu programu.

Wszystkie trzy są pojęciami ortogonalnymi, ale można je łatwo skondensować, zwłaszcza gdy są używane razem. Na przykład może być konieczne wykonanie wielu obliczeń asynchronicznych równolegle. Nie oznacza to, że równoległość czy asynchrony implikuje się nawzajem.

Jeśli wziąć pod uwagę etymologię słowa "asynchroniczne", istnieją dwa elementy zaangażowane:

- "a", czyli "nie".
- "synchroniczne", co oznacza "w tym samym czasie".

Po połączeniu tych dwóch terminów zobaczysz, że "asynchroniczne" oznacza "nie w tym samym czasie". Gotowe. Nie ma żadnych konsekwencji współbieżności lub równoległości w tej definicji. Dotyczy to również w praktyce.

W praktyce obliczenia asynchroniczne w języku F# są zaplanowane do wykonania niezależnie od głównego przepływu programu. Nie oznacza to współbieżności lub równoległości, ani nie oznacza, że obliczenia zawsze dzieje się w tle. W rzeczywistości obliczenia asynchroniczne można nawet wykonać synchronicznie, w zależności od charakteru obliczeń i środowiska, w jakim obliczenia są wykonywane.

Głównym wynos powinieneś mieć to, że obliczenia asynchroniczne są niezależne od głównego przepływu programu. Chociaż istnieje kilka gwarancji dotyczących tego, kiedy lub jak wykonuje obliczenia asynchroniczne, istnieją pewne podejścia do ich organizowania i planowania. W dalszej części tego artykułu eksploruje podstawowe pojęcia dla asynchrony F# i jak używać typów, funkcji i wyrażeń wbudowanych w F#.

## <a name="core-concepts"></a>Kluczowe pojęcia

W języku F# programowanie asynchroniczne jest wyśrodkowane wokół trzech podstawowych pojęć:

- Typ, `Async<'T>` który reprezentuje obliczeń asynchronicznych komponowania.
- Funkcje modułu, `Async` które umożliwiają planowanie pracy asynchronicznej, komponowanie obliczeń asynchronicznych i przekształcanie wyników asynchronicznych.
- Wyrażenie `async { }` [obliczeń](../../language-reference/computation-expressions.md), które zapewnia wygodną składnię do tworzenia i kontrolowania obliczeń asynchronicznych.

Te trzy pojęcia można zobaczyć w poniższym przykładzie:

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

W przykładzie `printTotalFileBytes` funkcja jest `string -> Async<unit>`typu . Wywołanie funkcji faktycznie nie wykonuje obliczeń asynchronicznych. Zamiast tego `Async<unit>` zwraca, który działa jako *specyfikacja* pracy, która ma wykonać asynchronicznie. Wywołuje `Async.AwaitTask` w swoim ciele, który konwertuje wynik <xref:System.IO.File.ReadAllBytesAsync%2A> do odpowiedniego typu.

Inną ważną linią jest `Async.RunSynchronously`wezwanie do . Jest to jedna z funkcji uruchamiania modułu Async, które należy wywołać, jeśli chcesz faktycznie wykonać obliczenia asynchroniczne F#.

Jest to zasadnicza różnica w stylu `async` programowania języka C#/Visual Basic. W języku F# obliczenia asynchroniczne można traktować jako **zimne zadania**. Muszą one być jawnie rozpoczęte do faktycznie wykonać. Ma to pewne zalety, ponieważ pozwala na łączenie i sekwencji pracy asynchronicznej znacznie łatwiej niż w języku C# lub Visual Basic.

## <a name="combine-asynchronous-computations"></a>Łączenie obliczeń asynchronicznych

Oto przykład, który opiera się na poprzednim, łącząc obliczenia:

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

Jak widać, `main` funkcja ma sporo więcej połączeń wykonanych. Koncepcyjnie wykonuje następujące czynności:

1. Przekształć `Async<unit>` argumenty wiersza polecenia w obliczenia za pomocą pliku `Array.map`.
2. `Async<'T[]>` Utwórz, który planuje `printTotalFileBytes` i uruchamia obliczenia równolegle podczas pracy.
3. `Async<unit>` Utwórz, który uruchomi obliczenia równoległe i zignoruje jego wynik.
4. Jawnie uruchomić ostatnie obliczenia `Async.RunSynchronously` z i bloku, dopóki nie zostanie zakończona.

Po uruchomieniu tego `printTotalFileBytes` programu działa równolegle dla każdego argumentu wiersza polecenia. Ponieważ obliczenia asynchroniczne są wykonywane niezależnie od przepływu programu, nie ma kolejności drukowania informacji i zakończenia wykonywania. Obliczenia będą zaplanowane równolegle, ale ich kolejność wykonywania nie jest gwarantowana.

## <a name="sequence-asynchronous-computations"></a>Sekwencja obliczeń asynchronicznych

Ponieważ `Async<'T>` jest to specyfikacja pracy, a nie już uruchomione zadanie, można łatwo wykonywać bardziej skomplikowane przekształcenia. Oto przykład, który sekwencjonuje zestaw obliczeń Asynchronii, aby wykonać jeden po drugim.

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
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

Spowoduje to `printTotalFileBytes` zaplanowanie wykonania w kolejności `argv` elementów, a nie ich równoległego planowania. Ponieważ następny element nie zostanie zaplanowany dopiero po zakończeniu wykonywania ostatniego obliczenia, obliczenia są sekwencjonowane w taki sposób, że nie ma nakładania się w ich wykonaniu.

## <a name="important-async-module-functions"></a>Ważne funkcje modułu Asynchronii

Podczas pisania kodu asynchroniiowego w języku F# zwykle będziesz wchodzić w interakcje z platformą, która obsługuje planowanie obliczeń dla Ciebie. Jednak nie zawsze tak jest, więc dobrze jest nauczyć się różnych funkcji początkowych, aby zaplanować pracę asynchronizacę.

Ponieważ obliczenia asynchroniczne F# są _specyfikacją_ pracy, a nie reprezentacją pracy, która jest już wykonywana, muszą być jawnie uruchomione z funkcją początkową. Istnieje wiele [funkcji uruchamiania Async,](https://msdn.microsoft.com/library/ee370232.aspx) które są pomocne w różnych kontekstach. W poniższej sekcji opisano niektóre z bardziej typowych funkcji początkowych.

### <a name="asyncstartchild"></a>Async.StartChild

Rozpoczyna obliczanie podrzędne w obliczeniach asynchronicznych. Dzięki temu wiele obliczeń asynchronicznych mają być wykonywane jednocześnie. Obliczenia podrzędne współumisuje token anulowania z obliczeń nadrzędnych. Jeśli obliczenia nadrzędne są anulowane, obliczenia podrzędne są również anulowane.

Podpis:

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

Kiedy stosować:

- Jeśli chcesz wykonać wiele obliczeń asynchronicznych jednocześnie, a nie jeden na raz, ale nie mają ich zaplanowane równolegle.
- Jeśli chcesz powiązać okres istnienia obliczeń podrzędnych z okresem istnienia obliczeń nadrzędnych.

Na co uważać:

- Uruchamianie wielu `Async.StartChild` obliczeń z nie jest taka sama jak planowanie ich równolegle. Jeśli chcesz zaplanować obliczenia równolegle, `Async.Parallel`użyj .
- Anulowanie obliczeń nadrzędnych spowoduje anulowanie wszystkich obliczeń podrzędnych, które uruchomił.

### <a name="asyncstartimmediate"></a>Async.StartImmediate

Uruchamia obliczenia asynchroniczne, uruchamia się natychmiast w bieżącym wątku systemu operacyjnego. Jest to przydatne, jeśli trzeba zaktualizować coś w wątku wywołującym podczas obliczeń. Na przykład jeśli obliczenia asynchroniczne muszą zaktualizować interfejs użytkownika (na przykład `Async.StartImmediate` aktualizowanie paska postępu), należy użyć.

Podpis:

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Kiedy stosować:

- Gdy trzeba zaktualizować coś na wątku wywołującego w środku obliczeń asynchronicznych.

Na co uważać:

- Kod w obliczeniach asynchronicznych będzie działać na dowolnym wątku jeden dzieje się zaplanowane na. Może to być problematyczne, jeśli ten wątek jest w jakiś sposób wrażliwe, takie jak wątek interfejsu użytkownika. W takich `Async.StartImmediate` przypadkach, jest prawdopodobne, niewłaściwe w użyciu.

### <a name="asyncstartastask"></a>Async.StartAsTask

Wykonuje obliczenia w puli wątków. <xref:System.Threading.Tasks.Task%601> Zwraca, który zostanie ukończony w odpowiednim stanie po zakończeniu obliczeń (daje wynik, zgłasza wyjątek lub zostanie anulowany). Jeśli nie podano tokenu anulowania, używany jest domyślny token anulowania.

Podpis:

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

Kiedy stosować:

- Gdy trzeba wywołać interfejs API platformy .NET, który <xref:System.Threading.Tasks.Task%601> oczekuje, że reprezentuje wynik obliczeń asynchronicznych.

Na co uważać:

- To wywołanie przydzieli dodatkowy `Task` obiekt, który może zwiększyć obciążenie, jeśli jest często używany.

### <a name="asyncparallel"></a>Async.Parallel (Async.Parallel)

Planuje sekwencję obliczeń asynchronicznych, które mają być wykonywane równolegle. Stopień równoległości można opcjonalnie dostroić/ograniczyć, `maxDegreesOfParallelism` określając parametr.

Podpis:

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Kiedy go używać:

- Jeśli musisz uruchomić zestaw obliczeń w tym samym czasie i nie mają polegania na ich kolejności wykonywania.
- Jeśli nie potrzebujesz wyników z obliczeń zaplanowanych równolegle, dopóki nie zostaną ukończone.

Na co uważać:

- Wynikową tablicę wartości można uzyskać tylko po zakończeniu wszystkich obliczeń.
- Obliczenia będą uruchamiane, jednak w końcu są one coraz zaplanowane. Oznacza to, że nie można polegać na ich kolejności ich wykonania.

### <a name="asyncsequential"></a>Async.Sequential

Planuje sekwencję obliczeń asynchronicznych do wykonania w kolejności, w jakiej są przekazywane. Pierwsze obliczenia zostaną wykonane, następnie następne i tak dalej. Żadne obliczenia nie będą wykonywane równolegle.

Podpis:

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

Kiedy go używać:

- Jeśli musisz wykonać wiele obliczeń w kolejności.

Na co uważać:

- Wynikową tablicę wartości można uzyskać tylko po zakończeniu wszystkich obliczeń.
- Obliczenia będą uruchamiane w kolejności, w jakiej są przekazywane do tej funkcji, co może oznaczać, że zanim wyniki zostaną zwrócone, upłynie więcej czasu.

### <a name="asyncawaittask"></a>Async.AwaitTask (Async.AwaitTask)

Zwraca obliczenia asynchroniczne, które czekają <xref:System.Threading.Tasks.Task%601> na zakończenie danego i zwraca jego wynik jako`Async<'T>`

Podpis:

```fsharp
task: Task<'T>  -> Async<'T>
```

Kiedy stosować:

- Podczas korzystania z interfejsu API platformy <xref:System.Threading.Tasks.Task%601> .NET, który zwraca w ramach F# obliczeń asynchronicznych.

Na co uważać:

- Wyjątki są <xref:System.AggregateException> zawijane w następujące konwencji biblioteki równoległej zadania i różni się to od sposobu F# async zazwyczaj powierzchnie wyjątków.

### <a name="asynccatch"></a>Async.Catch (Async.Catch)

Tworzy obliczenia asynchroniczne, które wykonuje `Async<'T>`dany `Async<Choice<'T, exn>>`, zwracając . Jeśli podane `Async<'T>` zakończy się pomyślnie, a następnie `Choice1Of2` zwracany z wartością wynikową. Jeśli wyjątek zostanie zgłoszony przed jego `Choice2of2` zakończeniem, a następnie zwracany z zgłoszonym wyjątkiem. Jeśli jest on używany w obliczeniach asynchronicznych, który sam składa się z wielu obliczeń, a jedno z tych obliczeń zgłasza wyjątek, obejmujące obliczeń zostanie całkowicie zatrzymany.

Podpis:

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Kiedy stosować:

- Podczas wykonywania pracy asynchroniiowej, które mogą zakończyć się niepowodzeniem z wyjątkiem i chcesz obsłużyć ten wyjątek w wywołującym.

Na co uważać:

- W przypadku korzystania z połączonych lub sekwencjonowane obliczeń asynchronicznych, obejmujące obliczeń zostanie całkowicie zatrzymane, jeśli jeden z jego "wewnętrznych" obliczeń zgłasza wyjątek.

### <a name="asyncignore"></a>Async.Ignore (Async.Ignore)

Tworzy obliczenia asynchroniczne, który uruchamia danego obliczeń i ignoruje jego wynik.

Podpis:

```fsharp
computation: Async<'T> -> Async<unit>
```

Kiedy stosować:

- Gdy masz obliczenia asynchroniczne, których wynik nie jest potrzebny. Jest to analogiczne `ignore` do kodu dla kodu nieynchroniowego.

Na co uważać:

- Jeśli musisz użyć tego, ponieważ `Async.Start` chcesz użyć `Async<unit>`lub innej funkcji, która wymaga, należy rozważyć, czy odrzucenie wyniku jest w porządku. Odrzucanie wyników tylko po to, aby dopasować podpis typu, nie powinno być zazwyczaj wykonywane.

### <a name="asyncrunsynchronously"></a>Async.RunSynchronously

Uruchamia obliczenia asynchroniczne i oczekuje na jego wynik w wątku wywołującym. To wywołanie jest blokowanie.

Podpis:

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

Kiedy go używać:

- Jeśli tego potrzebujesz, użyj go tylko raz w aplikacji — w punkcie wejścia dla pliku wykonywalnego.
- Gdy nie dbasz o wydajność i chcesz wykonać zestaw innych operacji asynchronicznych na raz.

Na co uważać:

- Wywołanie `Async.RunSynchronously` blokuje wątek wywołujący, dopóki wykonanie nie zostanie zakończone.

### <a name="asyncstart"></a>Async.Start

Uruchamia obliczenia asynchroniczne w puli wątków, która zwraca `unit`. Nie czeka na jego wynik. Obliczenia zagnieżdżone rozpoczęte `Async.Start` są uruchamiane całkowicie niezależnie od obliczeń nadrzędnych, które je nazwały. Ich żywotność nie jest związana z żadnymi obliczeniami nadrzędnych. Jeśli obliczenia nadrzędne zostaną anulowane, żadne obliczenia podrzędne nie zostaną anulowane.

Podpis:

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Stosować tylko wtedy, gdy:

- Masz obliczenia asynchroniczne, które nie dają wynik i/lub wymagają przetwarzania jednego.
- Nie musisz wiedzieć, kiedy obliczenia asynchroniczne zakończyć.
- Nie obchodzi cię, który wątek jest uruchamiany na obliczeniach asynchronicznych.
- Nie musisz być świadomy lub zgłaszać wyjątki wynikające z zadania.

Na co uważać:

- Wyjątki wywoływane przez `Async.Start` obliczenia rozpoczęte z nie są propagowane do wywołującego. Stos wywołań zostanie całkowicie rozwiany.
- Wszelkie prace efektowne `printfn`(takie `Async.Start` jak wywołanie) rozpoczęte z nie spowoduje efekt się na głównym wątku wykonywania programu.

## <a name="interoperate-with-net"></a>Współdziałanie z .NET

Być może pracujesz z biblioteką .NET lub bazą kodu Języka C#, która używa programowania asynchroniowego asynchroniiowego [asynchronii.](../../../standard/async.md) Ponieważ C# i większość bibliotek .NET <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> używać i typów jako `Async<'T>`ich abstrakcje podstawowe, a nie , należy przekroczyć granicę między tymi dwoma podejściami do asynchrony.

### <a name="how-to-work-with-net-async-and-taskt"></a>Jak pracować z .NET async i`Task<T>`

Praca z bibliotekami asynchronizacyjnymi <xref:System.Threading.Tasks.Task%601> platformy .NET i bazami kodu, które używają (czyli obliczeń asynchronii, które mają zwracane wartości) jest prosta i ma wbudowaną obsługę z F#.

Za pomocą `Async.AwaitTask` funkcji można oczekiwać na obliczenia asynchroniczne platformy .NET:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

Za pomocą `Async.StartAsTask` tej funkcji można przekazać obliczenia asynchroniczne do wywołującego .NET:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>Jak pracować z .NET async i`Task`

Aby pracować z interfejsami <xref:System.Threading.Tasks.Task> API, które używają (czyli .NET async obliczeń, które nie zwracają wartość), `Async<'T>` może <xref:System.Threading.Tasks.Task>być konieczne dodanie dodatkowej funkcji, która spowoduje konwersję na:

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

Istnieje `Async.AwaitTask` już, że akceptuje <xref:System.Threading.Tasks.Task> jako dane wejściowe. Za pomocą tej i `startTaskFromAsyncUnit` wcześniej zdefiniowanej funkcji <xref:System.Threading.Tasks.Task> można uruchamiać i czekać na typy z obliczeń asynchronowych języka F#.

## <a name="relationship-to-multi-threading"></a>Relacja z wieloma wątkami

Chociaż wątki jest wymieniony w tym artykule, istnieją dwie ważne rzeczy do zapamiętania:

1. Nie ma koligacji między obliczeniami asynchronizacyjnymi a wątkiem, chyba że jawnie rozpoczęto w bieżącym wątku.
1. Programowanie asynchroniczne w języku F# nie jest abstrakcją dla wielowątkowych.

Na przykład obliczenia mogą faktycznie działać na wątku wywołującego, w zależności od charakteru pracy. Obliczenia mogą również "przeskakiwać" między wątkami, pożyczając je przez niewielką ilość czasu, aby wykonać użyteczną pracę między okresami "oczekiwania" (na przykład podczas przesyłania połączenia sieciowego).

Chociaż F# zapewnia pewne możliwości, aby rozpocząć obliczenia asynchroniczne w bieżącym wątku (lub jawnie nie w bieżącym wątku), asynchrony ogólnie nie jest skojarzony z określonej strategii wątków.

## <a name="see-also"></a>Zobacz też

- [Model programowania asynchroniiowego F#](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet.com's F# Przewodnik Async](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F# dla zabawy i zysku Asynchroniczne Przewodnik programowania](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [Async w języku C# i F#: Asynchroniczne gotchas w C #](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
