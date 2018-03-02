---
title: "Asynchroniczne szczegółowo"
description: "Dowiedz się, jak kod I/E-granica i procesora asynchroniczne jest proste przy użyciu modelu opartego na zadaniach .NET async."
keywords: .NET, .NET Core, .NET Standard
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b01aa5d0fade29d04313a9db2e44517b6512166b
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="async-in-depth"></a>Asynchroniczne szczegółowo

Zapisu We/Wy i procesora asynchroniczne kodu jest proste przy użyciu modelu opartego na zadaniach .NET asynchronicznego. Model jest udostępniany przez `Task` i `Task<T>` typów i `async` i `await` słów kluczowych w języku C# i Visual Basic. (Zostaną znalezione zasoby specyficzne dla języka w [Zobacz też](#see-also) sekcji.) W tym artykule wyjaśniono, jak używać asynchronicznych .NET i zapewnia wgląd w framework async używany w tle.

## <a name="task-and-tasklttgt"></a>Zadań i zadań&lt;T&gt;

Zadania są konstrukcje używane do implementowania, co jest nazywane [Promise modelu współbieżności](https://en.wikipedia.org/wiki/Futures_and_promises).  Krótko mówiąc oferują się, że możesz "promise" działa zostanie ukończona w późniejszym czasie, co pozwala koordynować z promise z czystą interfejsu API.

*   `Task` reprezentuje pojedynczy operacji, która nie zwraca wartości.
*   `Task<T>` reprezentuje jednej operacji, która zwraca wartość typu `T`.

Ważne jest, aby Przyczyna o zadaniach jako obiekty abstrakcyjne pracy wykonywane asynchronicznie, i *nie* abstrakcji za pośrednictwem wątków. Domyślnie zadania wykonać na bieżącym wątku a obiektem delegowanym pracy do systemu operacyjnego, zgodnie z potrzebami. Opcjonalnie zadań można jawnie wymagane do uruchomienia w oddzielnym wątku za pośrednictwem `Task.Run` interfejsu API.

Zadania uwidacznia interfejs API protokołu monitorowania, oczekiwanie na i uzyskiwania dostępu do wartości wynik (w przypadku liczby `Task<T>`) zadania. Integracja języka z `await` — słowo kluczowe, udostępnia abstrakcję wyższego poziomu za pomocą zadań. 

Przy użyciu `await` umożliwia aplikacji lub usługi do wykonywania pracy przydatne podczas wykonywania zadania przez reaguje formantu do swojego obiektu wywołującego, dopóki zadanie jest wykonywane. Kod nie trzeba polegać na wywołania zwrotne lub zdarzeń, aby kontynuować działanie po zakończeniu zadania. Język i integracja z interfejsem API zadań nie. Jeśli używasz `Task<T>`, `await` — słowo kluczowe zostanie również "rozpakowywania" wartość zwracana, gdy zadanie zostanie zakończone.  Szczegółowe informacje dotyczące sposobu działania są opisano szczegółowo poniżej.

Dowiedz się więcej o zadaniach i różne sposoby interakcji z użytkownikiem w [opartego na zadaniach asynchronicznej wzorca (TAP)](~/docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) tematu.

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>Bardziej zgłębić temat na zadania dla operacji I/E-granica

W poniższej sekcji opisano, co się dzieje z wywołaniem operacji We/Wy async typowy widok stopy 10 000. Zacznijmy od kilka przykładów.

Pierwszym przykładzie wywołuje metody asynchronicznej i zwraca aktywne zadanie, prawdopodobnie jeszcze zakończyć.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    return client.GetStringAsync("http://www.dotnetfoundation.org");
}
```

Drugi przykład dodaje stosowania `async` i `await` słowa kluczowe do działania na zadania.

```csharp
public async Task<string> GetFirstCharactersCountAsync(string url, int count)
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    // Execution of GetFirstCharactersCountAsync() is yielded to the caller here
    // GetStringAsync returns a Task<string>, which is *awaited*
    var page = await client.GetStringAsync("http://www.dotnetfoundation.org");
    
    // Execution resumes when the client.GetStringAsync task completes,
    // becoming synchronous again.
    
    if (count > page.Length)
    {
        return page;
    }
    else
    {
        return page.Substring(0, count);
    }
}
```

Wywołanie `GetStringAsync()` wywołania do bibliotek .NET niższego poziomu (prawdopodobnie wywołaniem innych metod asynchronicznych) dopóki osiągnie wywołanie międzyoperacyjnego P/Invoke do natywnej biblioteki sieciowej. Natywnej biblioteki może następnie wywołują wywołania interfejsu API systemu (takich jak `write()` do gniazda, w systemie Linux). Obiekt zadania zostanie utworzone w granicę natywną/zarządzaną, prawdopodobnie przy użyciu [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)). Obiekt zadania będą przekazywane warstwy, prawdopodobnie jest obsługiwany przez lub bezpośrednio zwrócił, ostatecznie zwracana do początkowego wywołującego. 

W powyższym przykładzie drugi `Task<T>` obiektu zostanie zwrócony z `GetStringAsync`. Korzystanie z `await` — słowo kluczowe powoduje, że metoda zwraca obiekt nowo utworzone zadanie. Formant zwraca do elementu wywołującego z tej lokalizacji w `GetFirstCharactersCountAsync` metody. Metody i właściwości [zadań&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) obiekt wywołań Włącz, aby monitorować postęp zadania, które zostanie zakończony, jeśli pozostały kod GetFirstCharactersCountAsync zostało wykonane.

Po wywołaniu interfejsu API systemu żądania jest teraz obszaru jądra wprowadzenie drodze do podsystemu sieci systemu operacyjnego (takich jak `/net` jądra systemu Linux).  W tym miejscu system operacyjny będzie obsługiwać żądania sieciowe *asynchronicznie*.  Szczegóły może się różnić w zależności od systemu operacyjnego używany (wywołanie sterownika urządzenia może być zaplanowany jako sygnał wysyłane z powrotem do środowiska uruchomieniowego lub mogą być nawiązywane połączenie sterowników urządzeń i *następnie* sygnał odesłał), po pewnym czasie zostaną o tym poinformowany środowiska uruchomieniowego czy żądania sieci jest w toku.  W tej chwili pracy sterownika urządzenia zostanie albo zostać zaplanowane, w toku lub już zakończone (żądanie jest już limit "przez sieć") — ale ponieważ jest to wszystkie wykonywane asynchronicznie, może natychmiast obsługi czegoś innego sterownika urządzenia!

Na przykład w systemie operacyjnym Windows wątku nawiązuje połączenie ze sterownikiem urządzenia sieci i prosi o jej do wykonania tej operacji sieciowych za pośrednictwem przerwań żądania pakietu (IRP) reprezentuje operację.  Sterownik urządzenia otrzymuje MPP, sprawia, że połączenie z siecią oznacza MPP jako "oczekujące" i zwraca do systemu operacyjnego.  Ponieważ wątku systemu operacyjnego ustalił, że MPP jest "oczekujące", nie ma żadnych więcej pracy dla tego zadania i "zwraca wartość" tak, aby może służyć do wykonywania innych zadań.

Gdy żądanie jest spełniony, a danych wróci za pośrednictwem sterownika urządzenia, powiadamia Procesora nowych danych odebranych za pośrednictwem przerwania.  Pobiera obsługi przerwań to będą się różnić w zależności od systemu operacyjnego, ale ostatecznie dane zostaną przekazane za pośrednictwem systemu operacyjnego aż osiągnie międzyoperacyjnego wywołanie systemu (na przykład w systemie Linux obsługi przerwań zaplanowane dolnej połowie IRQ do danych za pośrednictwem systemu operacyjnego  asynchronicznie).  Uwaga tego *również* asynchroniczne!  Wynik jest w kolejce, dopóki następnego wątku dostępne jest w stanie wykonania metody asynchronicznej oraz "rozpakowywania" wyniki ukończonego zadania.

W trakcie tego całego procesu takeaway klucza oznacza, że **nie wątek jest dedykowany do wykonywania zadania**.  Mimo że pracy jest wykonywany w kontekście niektórych (oznacza to, system operacyjny ma reagowania na przerwania i przekazywanie danych do sterownika urządzenia), nie wątku jest dedykowana dla *oczekiwania* dane z żądania, aby wrócić do.  Dzięki temu system do obsługi znacznie większą ilość pracy, a nie oczekiwanie na połączenie niektórych operacji We/Wy zakończyć.

Powyższe może się wydawać wiele zadań do wykonania, gdy mierzy się jako czas zegarowy, ale jest miniscule w porównaniu do czasu, jaki zajmuje wykonują rzeczywistą pracę we/wy. Mimo że w ogóle dokładne potencjalnych osi czasu dla takich wywołania będzie wyglądać następująco:

0-1————————————————————————————————————————————————–2-3

*   Czas działania z punktów `0` do `1` wszystko, co jest możliwe aż metody asynchronicznej daje formantu do swojego obiektu wywołującego.
*   Czas działania z punktów `1` do `2` jest czas spędzony na We/Wy nie procesor CPU kosztów.
*   Na koniec czas działania z punktów `2` do `3` do metody asynchronicznej, po czym jej wykonywania ponownie jest przekazanie sterowania Wstecz (i potencjalnie wartości).

### <a name="what-does-this-mean-for-a-server-scenario"></a>Co to znaczy w scenariuszu serwera

Ten model dobrze działa z obciążenia scenariusz typowe serwera.  Ponieważ nie zawiera żadnych wątków dedykowane do blokowania na niezakończonych zadań, puli wątków serwera może obsłużyć znacznie większą ilość żądań sieci web.

Należy wziąć pod uwagę dwa serwery:, który uruchamia kod async i jedną, która nie.  Na potrzeby tego przykładu każdego serwera zawiera tylko 5 wątków dostępnych do obsługi żądań.  Należy pamiętać, że te liczby imaginarily małe i służą wyłącznie w kontekście demonstrative.

Załóżmy, że oba serwery odbierania 6 równoczesnych żądań. Każde żądanie wykonuje operację We/Wy.  Serwer *bez* kod async ma do kolejki żądania 6. dopóki jeden z wątków 5 ma zakończy pracę I/E-granica i zapisywane odpowiedzi. W punkcie 20 żądanie serwer może uruchomić spowalniać, ponieważ kolejka jest wprowadzenie zbyt długa.

Serwer *z* kolejek żądanie 6, jest nadal uruchomiony kod asynchroniczne, ale ponieważ używa `async` i `await`, każdy z wątków są zwalniane po rozpoczęciu pracy I/E-granica, zamiast po zakończeniu.  W czasie 20 żądania jest dostarczany w kolejce dla przychodzących żądań będzie znacznie mniejsza (jeśli posiada niczego w niej w ogóle), a serwer nie będzie działać wolniej.

Jest to przykład contrived, działa w sposób bardzo podobne w świecie rzeczywistym.  W rzeczywistości, można oczekiwać, że serwer, aby można było obsługiwać rzędu więcej żądań przy użyciu `async` i `await` niż w przypadku zostały dedykowanym wątku dla każdego żądania odbierze.

### <a name="what-does-this-mean-for-client-scenario"></a>Co to znaczy w scenariuszu klienta

Największych korzyści dotyczące korzystania z `async` i `await` dla klienta, aplikacja jest zwiększenie czasu odpowiedzi.  Mimo że mogą być aplikacji reakcji duplikując wątków ręcznie, duplikowania wątku jest kosztowna operacja względem tylko przy użyciu `async` i `await`.  Szczególnie w przypadku wyglądać mniej więcej tak przenośnych gry wpływające na wątku interfejsu użytkownika jak najmniejszy gdzie dotyczy operacji We/Wy jest niezwykle istotne.

Co ważniejsze ponieważ pracy I/E-powiązane z spędza praktycznie bez czasu procesora, przypisywanie całego wątku procesora CPU w celu wykonania prawie przydatnych działań będzie słabe wykorzystanie zasobów.

Ponadto podczas wysyłania zadań do wątku interfejsu użytkownika (np. Aktualizowanie interfejsu użytkownika) jest bardzo prosty z `async` metod i nie wymaga dodatkowej pracy (taką jak wywołanie delegata wątkowo).

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a>Bardziej zgłębić temat do zadań i zadań<T> operacji procesora

Procesor `async` kod jest nieco inne niż I/E-granica `async` kodu.  Ponieważ praca odbywa się na Procesorze, nie istnieje sposób poruszania przypisywanie wątku do obliczenia.  Korzystanie z `async` i `await` udostępnia z czystą sposób interakcji z tło wątku i zachowanie reakcji wywołujący metody asynchronicznej.  Należy pamiętać, że nie ma żadnych ochronę udostępnionych danych.  Jeśli używasz udostępnionych danych nadal musisz zastosować strategii odpowiedniej synchronizacji.

W tym miejscu jest 10 000 stopy widok wywołania asynchronicznego procesora:

```csharp
public async Task<int> CalculateResult(InputData data)
{
    // This queues up the work on the threadpool.
    var expensiveResultTask = Task.Run(() => DoExpensiveCalculation(data));
    
    // Note that at this point, you can do some other work concurrently,
    // as CalculateResult() is still executing!
    
    // Execution of CalculateResult is yielded here!
    var result = await expensiveResultTask;
    
    return result;
}
```

`CalculateResult()` wykonuje, na który została wywołana w wątku.  Gdy wywołuje `Task.Run`, jego kolejki kosztowna operacja procesora `DoExpensiveCalculation()`, w puli wątków i odbiera `Task<int>` obsługi.  `DoExpensiveCalculation()` Po pewnym czasie działa jednocześnie na dalej dostępne wątku, prawdopodobnie w innym rdzeń procesora CPU.  Istnieje możliwość pracy równoczesnych podczas `DoExpensiveCalculation()` jest zajęty w innym wątku, ponieważ wątek, który wywołuje `CalculateResult()` jest nadal wykonywane.

Raz `await` napotkano, wykonanie `CalculateResult()` jest zwróciło do swojego obiektu wywołującego, dzięki czemu inne pracy z bieżącego wątku, podczas `DoExpensiveCalculation()` jest mieszaniu limit wyników.  Po zakończeniu, wynik jest umieszczone w kolejce do uruchomienia w głównym wątku.  Po pewnym czasie głównego wątku nastąpi powrót do wykonywania `CalculateResult()`, po czym jej wynik `DoExpensiveCalculation()`.

### <a name="why-does-async-help-here"></a>Dlaczego usługa async pomaga w tym miejscu?

`async` i `await` są najlepszym rozwiązaniem zarządzania pracy procesora, gdy będziesz potrzebować czas odpowiedzi. Istnieje wiele wzorców korzystania z procesora pracy przy użyciu asynchronicznej. Należy zauważyć, że istnieje małych koszt za pomocą async i nie jest zalecane dla ścisłej pętli.  Jest ustalenie sposobu pisania kodu wokół tej nowej możliwości.

## <a name="see-also"></a>Zobacz także

[Programowanie asynchroniczne w języku C#](~/docs/csharp/async.md)   
[Programowanie asynchroniczne z async i await (C#)](../csharp/programming-guide/concepts/async/index.md)  
[Programowanie asynchroniczne w języku F #](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
[Programowanie asynchroniczne z Async i Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
