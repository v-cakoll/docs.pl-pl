---
title: Asynchroniczne szczegółowo
description: Dowiedz się, jak I/O-powiązane z Procesora CPU asynchronicznego pisanie kodu wykonywanego i jest proste przy użyciu modelu opartego na zadaniach .NET async.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 0c098d0697dff3e1e772c348597a84ac9d262104
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085319"
---
# <a name="async-in-depth"></a>Asynchroniczne szczegółowo

Zapisywanie operacji We/Wy i Procesora CPU kodu asynchronicznego jest proste przy użyciu modelu opartego na zadaniach .NET async. Model jest uwidaczniany przez `Task` i `Task<T>` typów i `async` i `await` słów kluczowych w języku C# i Visual Basic. (Specyficzne dla języka zasoby znajdują się w [Zobacz też](#see-also) sekcji.) W tym artykule wyjaśniono, jak używać asynchronicznych .NET i zapewnia wgląd w ramach asynchronicznych używane w sposób niewidoczny.

## <a name="task-and-tasklttgt"></a>Zadanie i zadania&lt;T&gt;

Zadania są konstrukcji używanych do wdrożenia, co jest nazywane [Promise modelu współbieżności](https://en.wikipedia.org/wiki/Futures_and_promises).  Krótko mówiąc oferują one, że możesz element "promise", które działają zakończy się w późniejszym czasie, dzięki czemu możesz skontaktować się z zobowiązania przy użyciu czystego interfejsu API.

*   `Task` reprezentuje pojedynczej operacji, która nie zwraca wartości.
*   `Task<T>` reprezentuje jednej operacji, która zwraca wartość typu `T`.

Ważne jest, aby Przyczyna o zadaniach jako abstrakcje wykonywane asynchronicznie, pracy i *nie* abstrakcji wątków. Domyślnie wykonywane podzadania wchodzące w bieżącym wątku i delegata pracy do systemu operacyjnego, zgodnie z potrzebami. Opcjonalnie, zadania można jawnie wymagane do uruchamiania w oddzielnym wątku za pomocą `Task.Run` interfejsu API.

Zadania ujawnić protokół interfejsu API oraz funkcje monitorowania i oczekiwania na dostęp do wartości wyniku (w przypadku właściwości `Task<T>`) zadania. Integracja języka, za pomocą `await` — słowo kluczowe, zapewnia wyższego poziomu abstrakcji dotyczące korzystania z zadań. 

Za pomocą `await` umożliwia aplikacji lub usługi wykonać przydatnych działań po uruchomieniu zadania przez reaguje formantu do obiektu wywołującego, dopóki zadanie jest wykonywane. Twój kod nie trzeba polegać na wywołania zwrotne lub zdarzeń w celu kontynuowania wykonywania po ukończeniu zadania. Języku i za pomocą integracji interfejsu API zadań robi to za Ciebie. Jeśli używasz `Task<T>`, `await` — słowo kluczowe zostanie dodatkowo "Odkodowywanie" wartość zwracana, gdy zadanie zostało ukończone.  Szczegóły dotyczące sposobu działania zostały wyjaśnione poniżej.

Dowiedz się więcej o zadaniach i różne sposoby interakcji z użytkownikiem w [opartego na zadaniach asynchronicznej wzorca (TAP)](~/docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) tematu.

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>Bardziej zgłębić temat na zadania dla operacji I/O-powiązane z

W poniższej sekcji opisano, co się dzieje z wywołania operacji We/Wy async typowy widok metr 10 000. Zacznijmy od kilka przykładów.

Pierwszy przykład wywołuje metodę async i zwraca aktywne zadanie, prawdopodobnie jeszcze zakończyć.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    return client.GetStringAsync("http://www.dotnetfoundation.org");
}
```

Drugi przykład dodaje użytkowania `async` i `await` słów kluczowych do działania na zadanie.

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

Wywołanie `GetStringAsync()` wywołań za pośrednictwem niższego poziomu bibliotek programu .NET (być może wywołaniem innych metod asynchronicznych) dopóki osiągnie P/Invoke międzyoperacyjny wywołania natywne biblioteki sieciowej. Bibliotekę natywną później może wywołać do wywołania interfejsu API systemu (takich jak `write()` do gniazda w systemie Linux). Obiekt zadania, które zostaną utworzone na granicy natywnego/zarządzanego, prawdopodobnie za pomocą [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)). Obiekt zadania będą przekazywane warstw, prawdopodobnie działa jako lub bezpośrednio zwracana, ostatecznie zwracana do początkowego obiektu wywołującego. 

W drugim przykładzie powyżej `Task<T>` obiektu zostanie zwrócony z `GetStringAsync`. Korzystanie z `await` — słowo kluczowe spowoduje, że metoda zwraca obiekt nowo utworzonym zadaniem. Formant powraca do obiektu wywołującego z tej lokalizacji w `GetFirstCharactersCountAsync` metody. Metody i właściwości [zadań&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) obiektów wywołujących Włącz, aby monitorować postęp zadania, które zostanie ukończone, gdy pozostały kod GetFirstCharactersCountAsync zostało wykonane.

Po wywołaniu interfejsu API w systemu żądanie teraz obszaru jądra osiągnął w drodze do podsystemu sieci systemu operacyjnego (takich jak `/net` w jądrze systemu Linux).  W tym miejscu systemu operacyjnego będzie obsługiwać żądania sieciowe *asynchronicznie*.  Szczegółów może różnić się w zależności od systemu operacyjnego używany (wywołanie sterownika urządzenia mogą być zaplanowane jako sygnał wysyłanych z powrotem do środowiska uruchomieniowego lub wywołania sterownika urządzenia, które mogą być nawiązywane i *następnie* sygnał odesłał), ale ostatecznie zostanie poinformowana środowiska uruchomieniowego czy żądanie sieci jest w toku.  W tej chwili pracy dla sterownika urządzenia będą albo być zaplanowane, w toku lub już zakończona (żądanie jest już się "przewodowo") -, ale ponieważ jest to wszystkie wykonywane asynchronicznie, sterownik urządzenia jest w stanie natychmiast obsługi coś innego!

Na przykład w system operacyjny Windows wątek nawiązuje połączenie ze sterownikiem urządzenia sieci i prosi można wykonać operacji sieci za pośrednictwem przerwań żądania pakietu (IRP), które reprezentuje operację.  Sterownik urządzenia otrzymuje MPP, sprawia, że połączenie z siecią, oznacza MPP jako "pending" i zwraca z powrotem do systemu operacyjnego.  Ponieważ teraz wątku systemu operacyjnego wie, że MPP jest "pending", nie ma żadnych więcej działań w celu dla tego zadania i "zwraca wartość" tak, aby może służyć do wykonywania innych zadań.

Gdy żądanie jest spełniony, a danych wróci za pośrednictwem sterownika urządzenia, powiadamia Procesora nowych danych odebranych za pośrednictwem przerwania.  Pobiera obsługi przerwań to różnią się w zależności od systemu operacyjnego, ale ostatecznie dane zostaną przekazane za pośrednictwem systemu operacyjnego aż do napotkania międzyoperacyjny wywołania systemowego (na przykład w systemie Linux obsługi przerwania będą planować dolnej połowie przerwania do danych za pośrednictwem systemu operacyjnego  asynchronicznie).  Uwaga że *również* się asynchronicznie stanie!  Wynik jest umieszczane w kolejce do czasu następnego dostępny wątek jest w stanie Wykonywanie metody asynchronicznej i "Odkodowywanie" wyniki ukończonego zadania.

W trakcie tego procesu całego kluczowym wnioskiem jest to, że **żaden wątek nie jest przeznaczony do obsługi zadania**.  Mimo że praca jest wykonywana w kontekście niektóre (oznacza to, system operacyjny musi przekazać dane do sterownika urządzenia i reagować na przerwania), żaden wątek nie jest dedykowany do *oczekiwania* dla danych z żądania, aby wrócić do tego.  Dzięki temu system do obsługi znacznie większa ilość pracy, zamiast czekać, aż niektóre wywołania operacji We/Wy zakończyć.

Mimo że powyżej może wydawać się wiele zadań do wykonania, gdy mierzy czas zegarowy, jest miniscule w porównaniu do czasu, jaki zajmuje wykonują rzeczywistą pracę we/wy. Mimo że w ogóle nie będzie dokładny potencjalnych oś czasu dla takich wywołania będzie wyglądać następująco:

0-1————————————————————————————————————————————————–2-3

*   Czas poświęcony na z punktów `0` do `1` to wszystko, aż do metody asynchronicznej przekazuje sterowanie do obiektu wywołującego.
*   Czas poświęcony na z punktów `1` do `2` jest czas spędzony na We/Wy przy użyciu procesora CPU, nie kosztów.
*   Ponadto czas działania z punktów `2` do `3` to przekazanie kontroli Wstecz (i potencjalnie wartości) do metody asynchronicznej, w tym momencie jest wykonywane ponownie.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Co to oznacza dla scenariusza serwera

Ten model dobrze działa z obciążenie serwera typowego scenariusza.  Ponieważ nie istnieją wątki dedykowanego blokuje niezakończonych zadań, threadpool serwer może obsłużyć znacznie większą ilość żądań sieci web.

Należy wziąć pod uwagę dwa serwery: taki, który jest uruchamiany kod asynchroniczny i jedną, która nie ma.  Na potrzeby tego przykładu każdy serwer ma tylko 5 wątków dostępnych do obsługi żądań.  Należy pamiętać, że te liczby są imaginarily małe i pełnią wyłącznie w kontekście demonstrative.

Załóżmy, że oba serwery odbierania 6 współbieżnych żądań. Każde żądanie wykonuje operację We/Wy.  Serwer *bez* kod asynchroniczny ma 6. żądania w kolejce do momentu mają jeden z wątków 5 zakończy pracę I/O-powiązane z i zapisywane odpowiedzi. W punkcie, które pochodzą żądania 20 serwer może uruchomić spowolnienia, ponieważ kolejka jest wprowadzenie zbyt długa.

Serwer *z* kolejek się 6. żądanie jest nadal uruchomiony kod async, ale ponieważ używa ona `async` i `await`, każdy z wątków są zwalniane po uruchomieniu pracy I/O-powiązane z, a nie po zakończeniu.  Do czasu żądania 20 jest dostarczany w kolejce dla żądań przychodzących będzie znacznie mniejsza (jeśli ma niczego w niej w ogóle), i nie spowalniają serwera.

Chociaż jest to przykład contrived, działa w sposób bardzo podobne w świecie rzeczywistym.  W rzeczywistości można oczekiwać, że serwer może obsługiwać więcej żądań przy użyciu o rząd wielkości `async` i `await` niż jeśli jego zostały dedykowanym wątku dla każdego żądania odbiera.

### <a name="what-does-this-mean-for-client-scenario"></a>Co to oznacza dla scenariusza klienta

Największe korzyści dotyczące korzystania z `async` i `await` dla klienta, aplikacja jest zwiększenie czasu odpowiedzi.  Chociaż można wykonać aplikacji interaktywnych duplikując wątków ręcznie, podczas duplikowania wątku jest kosztowną operacją względem tylko przy użyciu `async` i `await`.  Szczególnie w przypadku podobny grę na urządzenia przenośne wpływ na wątku interfejsu użytkownika jak najmniejszy których to dotyczy operacji We/Wy jest niezwykle istotne.

Co ważniejsze ponieważ praca I/O-powiązane z spędzony przez praktycznie w krótkim czasie na procesorze CPU, przypisywanie całego wątku procesora CPU w celu wykonania ledwie jakiejkolwiek przydatnej pracy będzie Niewydajne wykorzystanie zasobów.

Ponadto wywołujący pracę w wątku interfejsu użytkownika (takie jak aktualizowanie interfejsu użytkownika) jest bardzo proste dzięki `async` metod i nie wymaga dodatkowej pracy (na przykład podczas wywoływania delegata wątkowo).

## <a name="deeper-dive-into-task-and-tasklttgt-for-a-cpu-bound-operation"></a>Bardziej zgłębić temat do zadań i zadań&lt;T&gt; dla operacji zależne od Procesora CPU

Zależne od Procesora CPU `async` kod jest nieco inna niż I/O-granica `async` kodu.  Ponieważ praca odbywa się na procesorze CPU, nie ma możliwości można pobrać na dedykowanym wątku do obliczeń.  Korzystanie z `async` i `await` oferuje użytkownikowi eleganckie rozwiązanie do interakcji z tłem wątku i Zachowaj dynamiczne obiektu wywołującego metody async.  Należy pamiętać, że nie zapewnia żadnej ochrony dla udostępnionych danych.  Jeśli używasz udostępnionych danych nadal konieczne będzie zastosowanie strategii synchronizacji odpowiednich.

W tym miejscu znajduje się 10 000 stóp wywołanie asynchroniczne zależne od Procesora CPU:

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

`CalculateResult()` wykonuje w wątku, który został wywołany w.  Kiedy wywołuje `Task.Run`, jego kolejki kosztowna operacja Procesora CPU `DoExpensiveCalculation()`, w puli wątków i odbiera `Task<int>` obsługi.  `DoExpensiveCalculation()` Po pewnym czasie działa równolegle na następny dostępny wątek, prawdopodobnie na inny rdzeń procesora CPU.  Istnieje możliwość wykonania współbieżnych pracy podczas `DoExpensiveCalculation()` jest zajęty w innym wątku, ponieważ wątku, która nosi nazwę `CalculateResult()` jest nadal wykonywane.

Raz `await` napotkaniu wykonywania `CalculateResult()` jest uzyskane do obiektu wywołującego, dzięki czemu inne prace, co można zrobić za pomocą bieżącego wątku podczas `DoExpensiveCalculation()` jest wychodzi się wynik.  Po zakończeniu, wynik jest umieszczone w kolejce do uruchomienia w wątku głównym.  Po pewnym czasie, wątek główny powróci do wykonywania `CalculateResult()`, w tym momencie jej wynik `DoExpensiveCalculation()`.

### <a name="why-does-async-help-here"></a>Dlaczego czy asynchroniczne pomaga w tym miejscu?

`async` i `await` są najlepszym rozwiązaniem Zarządzanie zadań intensywnie angażujących Procesor, gdy będziesz potrzebować czasu odpowiedzi. Istnieje wiele wzorce przy użyciu async za pomocą zadań intensywnie angażujących Procesor. Należy pamiętać, że istnieje niewielkim kosztem za pomocą async i nie jest zalecane w ścisłej pętli for.  To pozwala określić, jak pisać kod wokół tej nowej możliwości.

## <a name="see-also"></a>Zobacz także

* [Programowanie asynchroniczne w języku C#](~/docs/csharp/async.md)   
* [Programowanie asynchroniczne z async i await (C#)](../csharp/programming-guide/concepts/async/index.md)  
* [Programowanie asynchroniczne w języku F #](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
* [Programowanie asynchroniczne z Async i Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
