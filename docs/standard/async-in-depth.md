---
title: Na poziomie Async
description: Dowiedz się, jak pisanie kodu powiązanego we/wy oraz kod asynchroniczny związany z PROCESORem jest prosty przy użyciu modelu asynchronicznego opartego na zadaniach platformy .NET.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 776949e86f6eb3fa6a193b303f4c731e20bac1a5
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107311"
---
# <a name="async-in-depth"></a>Na poziomie Async

Pisanie we/wy i kod asynchroniczny związany z PROCESORem jest prosty przy użyciu modelu asynchronicznego opartego na zadaniach platformy .NET. `Task` Model jest udostępniany przez typy `async` i `Task<T>` i słowa kluczowe `await` C# oraz i Visual Basic. (Zasoby specyficzne dla języka znajdują się w sekcji [Zobacz też](#see-also) .) W tym artykule wyjaśniono, jak używać programu .NET Async i zapewnia wgląd w strukturę asynchroniczną używaną w ramach okładek.

## <a name="task-and-taskt"></a>Zadanie i zadanie\<T >

Zadania są konstrukcjami używanymi do implementowania elementu, który jest znany jako [model obietnicy współbieżności](https://en.wikipedia.org/wiki/Futures_and_promises).  W krótkim czasie oferują one "obietnice", które będą wykonywane w późniejszym momencie, co pozwala na koordynowanie z obietnicą za pomocą czystego interfejsu API.

- `Task`reprezentuje pojedynczą operację, która nie zwraca wartości.
- `Task<T>`reprezentuje pojedynczą operację, która zwraca wartość typu `T`.

Ważne jest, aby zwrócić uwagę na zadania jako abstrakcje pracy wykonywanej asynchronicznie, a *nie* abstrakcję w wątkach. Domyślnie zadania są wykonywane w bieżącym wątku i delegowanie pracy do systemu operacyjnego, zgodnie z potrzebami. Opcjonalnie zadania mogą być jawnie wymagane do uruchomienia w osobnym wątku za pośrednictwem `Task.Run` interfejsu API.

Zadania uwidaczniają protokół interfejsu API w celu monitorowania, oczekiwania na i uzyskiwania dostępu do wartości wyniku (w `Task<T>`przypadku) zadania. Integracja z językiem przy `await` użyciu słowa kluczowego zapewnia abstrakcję wyższego poziomu na potrzeby wykonywania zadań.

Użycie `await` umożliwia aplikacji lub usłudze wykonywanie użytecznych zadań, gdy zadanie jest uruchomione przez przekazanie kontroli do obiektu wywołującego do momentu wykonania zadania. Kod nie musi polegać na wywołaniach zwrotnych ani zdarzeniach, aby kontynuować wykonywanie po zakończeniu zadania. Integracja z interfejsem API języka i zadania jest dla Ciebie taka sama. `Task<T>`Jeśli używasz`await` , słowo kluczowe będzie dodatkowo "odwinięcie" wartości zwróconej po zakończeniu zadania.  Szczegóły dotyczące tego działania opisano poniżej.

Więcej informacji o zadaniach i różnych sposobach współpracy z nimi można znaleźć w temacie [asynchroniczny wzorzec oparty na zadaniach (TAP)](./asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) .

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>Dokładniejsze szczegółowe do zadań związanych z operacją we/wy

W poniższej sekcji opisano, co to jest 10 000, co się dzieje z typowym asynchronicznym wywołaniem we/wy. Zacznijmy od kilku przykładów.

Pierwszy przykład wywołuje metodę asynchroniczną i zwraca aktywne zadanie, które może jeszcze nie zostać ukończone.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();

    return client.GetStringAsync("https://www.dotnetfoundation.org");
}
```

Drugi przykład dodaje użycie `async` słów kluczowych i `await` do działania na zadaniu.

```csharp
public async Task<string> GetFirstCharactersCountAsync(string url, int count)
{
    // Execution is synchronous here
    var client = new HttpClient();

    // Execution of GetFirstCharactersCountAsync() is yielded to the caller here
    // GetStringAsync returns a Task<string>, which is *awaited*
    var page = await client.GetStringAsync("https://www.dotnetfoundation.org");

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

Wywołanie `GetStringAsync()` wywołań za pomocą bibliotek platformy .NET niższego poziomu (np. wywołania innych metod asynchronicznych) do momentu osiągnięcia wywołania międzyoperacyjności P/Invoke do natywnej biblioteki sieciowej. Biblioteka natywna może następnie wywołać wywołanie interfejsu API systemu ( `write()` na przykład w gnieździe w systemie Linux). Obiekt zadania zostanie utworzony na granicy natywnej/zarządzanej, prawdopodobnie przy użyciu [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)). Obiekt zadania zostanie przekierowany przez warstwy, które mogą być używane w lub bezpośrednio zwrócone, ostatecznie zwrócone do początkowego obiektu wywołującego.

W drugim przykładzie powyżej `Task<T>` obiekt zostanie zwrócony z. `GetStringAsync` Użycie `await` słowa kluczowego powoduje, że metoda zwraca nowo utworzony obiekt zadania. Kontrolka powraca do obiektu wywołującego z tej `GetFirstCharactersCountAsync` lokalizacji w metodzie. Metody i właściwości obiektu [Task&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) umożliwiają wywoływanie, aby monitorować postęp zadania, które zakończy się po wykonaniu pozostałej części kodu w GetFirstCharactersCountAsync.

Po wywołaniu interfejsu API systemu żądanie jest teraz w przestrzeni jądra, co umożliwia jego sposób do podsystemu sieciowego systemu operacyjnego ( `/net` na przykład w jądrze Linux).  W tym miejscu system operacyjny będzie obsługiwał żądaniesieciowe asynchronicznie.  Szczegóły mogą się różnić w zależności od używanego systemu operacyjnego (wywołanie sterownika urządzenia może być zaplanowane jako sygnał wysłany z powrotem do środowiska uruchomieniowego lub może zostać wykonane wywołanie sterownika urządzenia, a *następnie* sygnał wysłany z powrotem), ale wreszcie środowisko uruchomieniowe zostanie poinformowane o tym, że sieć żądanie jest w toku.  W tej chwili pracę dla sterownika urządzenia zostanie zaplanowana, w toku lub już zakończono (żądanie jest już w trakcie przesyłania), ale ponieważ wszystko to odbywa się asynchronicznie, sterownik urządzenia może natychmiast obsłużyć coś innego!

Na przykład w systemie Windows wątek systemu operacyjnego wykonuje wywołanie do sterownika urządzenia sieciowego i prosi o wykonanie operacji sieci za pośrednictwem pakietu żądania przerwania (IRP), który reprezentuje operację.  Sterownik urządzenia odbiera pakiet IRP, wywołuje połączenie z siecią, oznacza IRP jako "Pending" i zwraca z powrotem do systemu operacyjnego.  Ponieważ wątek systemu operacyjnego wie, że IRP jest "oczekiwanie", nie ma więcej pracy do wykonania dla tego zadania i "zwraca" z powrotem, aby można było go użyć do wykonywania innych zadań.

Gdy żądanie jest spełnione, a dane są przywracane za pośrednictwem sterownika urządzenia, powiadamia on o PROCESORAch nowych danych odbieranych za pośrednictwem przerwania.  Sposób obsługi tego przerwania będzie różny w zależności od systemu operacyjnego, ale ostatecznie dane będą przekazywane przez system operacyjny do momentu osiągnięcia wywołania międzyoperacyjności systemu (na przykład w systemie Linux procedura obsługi przerwania spowoduje zaplanowanie dolnej połowy PRZERWAnia w celu przekazania danych za pomocą systemu operacyjnego  asynchronicznie).  Należy zauważyć, że dzieje się to *również* asynchronicznie!  Wynik zostanie umieszczony w kolejce do momentu następnego dostępnego wątku będzie w stanie wykonać metodę asynchroniczną i "odwinięcie" wyniku zadania zakończonego.

W całym całym procesie wnioskiem Key polega na tym, że **żaden wątek nie jest przeznaczony do uruchamiania zadania**.  Chociaż prace są wykonywane w pewnym kontekście (to oznacza, że system operacyjny musi przekazywać dane do sterownika urządzenia i odpowiadać na przerwanie), nie istnieje wątek przeznaczony do *oczekiwania* na powrót danych z żądania.  Dzięki temu system może obsłużyć znacznie większą ilość pracy, a nie czekając na zakończenie pewnego wywołania we/wy.

Chociaż powyższe może wydawać się bardzo dużo pracy, gdy jest mierzony w warunkach zegara ściany, jest miniscule w porównaniu do czasu potrzebnego do wykonania rzeczywistej pracy we/wy. Chociaż nie jest to dokładne, potencjalna oś czasu dla takiego wywołania będzie wyglądać następująco:

0-1————————————————————————————————————————————————–2-3

- Czas spędzony w `0` punktach `1` to wszystko do momentu, aż Metoda asynchroniczna przeniesie kontrolę do obiektu wywołującego.
- Czas spędzony od `1` punktów `2` na to czas spędzony na operacji we/wy bez kosztu procesora.
- Na koniec czas spędzony przez `2` punkty `3` na przekazanie kontroli (i potencjalnie wartości) do metody asynchronicznej, w której punkt jest wykonywany ponownie.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Co to znaczy dla scenariusza serwera?

Ten model działa dobrze z typowym obciążeniem scenariusza serwera.  Ponieważ nie istnieją wątki przeznaczone do blokowania dla nieukończonych zadań, może ona obsłużyć znacznie wyższą liczbę żądań sieci Web.

Należy wziąć pod uwagę dwa serwery: jeden z nich uruchamia kod asynchroniczny, a nie.  Na potrzeby tego przykładu każdy serwer ma tylko 5 wątków dostępnych do obsługi żądań.  Należy zauważyć, że te liczby są imaginarily małe i służą tylko w kontekście wykazujących.

Przyjęto założenie, że oba serwery odbierają 6 współbieżnych żądań. Każde żądanie wykonuje operację we/wy.  Serwer *bez* kodu asynchronicznego musi kolejkować szóste żądanie, dopóki jeden z pięciu wątków zakończył pracę we/wy i zapisał odpowiedź. W punkcie, w którym znajduje się 20 żądań, serwer może zaczynać spowalniać pracę, ponieważ kolejka jest zbyt długa.

Serwer *z* działającym na nim kodem asynchronicznym nadal umieszcza w kolejce szóste żądanie, ale ponieważ `async` korzysta `await`z nich i, każdy z jego wątków jest zwalniany po rozpoczęciu pracy powiązanej we/wy, a nie po zakończeniu.  W czasie, gdy przychodzi 20 żądań, kolejka żądań przychodzących będzie znacznie mniejsza (Jeśli w ogóle zawiera wszystkie), a serwer nie zmniejszy się.

Chociaż jest to contrived przykład, działa on w podobny sposób w świecie rzeczywistym.  W rzeczywistości serwer może być w stanie obsłużyć żądanie o wielkości więcej żądań przy użyciu `async` i `await` niż w przypadku przydzielenia wątku dla każdego odebranego żądania.

### <a name="what-does-this-mean-for-client-scenario"></a>Co to znaczy dla scenariusza klienta?

Największe korzyści związane z `async` korzystaniem `await` z programu i dla aplikacji klienckiej to wzrost czasu odpowiedzi.  Mimo że można sprawić, że aplikacja będzie odpowiadać przez ręczne duplikowanie wątków, czynność duplikowania wątku jest kosztowną operacją względną do użycia `async` i `await`.  Szczególnie w przypadku urządzeń przenośnych, które mają wpływ na działanie wątku interfejsu użytkownika jak najmniejszej ilości miejsca I/O.

Co ważniejsze, ponieważ zadania związane z we/wy poświęcają praktycznie bez czasu na procesorze CPU, dedykowanie całego wątku procesora CPU stanowią jedynie ułamek wszelkie użyteczne działania byłyby niewłaściwym użyciem zasobów.

Ponadto wysyłanie zadań do wątku interfejsu użytkownika (na przykład aktualizowania interfejsu użytkownika) jest bardzo proste z `async` metodami i nie wymaga dodatkowej pracy (na przykład wywołania delegata bezpiecznego wątkowo).

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a>Dokładniejsze szczegółowe do zadań i\<zadań T > dla operacji związanej z procesorem

Kod powiązany `async` z procesorem jest nieco inny niż kod powiązany `async` we/wy.  Ponieważ prace odbywają się na procesorze CPU, nie ma możliwości uzyskania większej ilości przydzielenia wątku do obliczenia.  Korzystanie z programu `async` i `await` zapewnia czysty sposób współdziałania z wątkiem w tle i zachowanie obiektu wywołującego metody asynchronicznej.  Należy pamiętać, że nie zapewnia to ochrony danych udostępnionych.  W przypadku korzystania z danych udostępnionych nadal trzeba zastosować odpowiednią strategię synchronizacji.

Oto 10 000-krotne wywołanie asynchroniczne powiązane z PROCESORem:

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

`CalculateResult()`wykonuje w wątku, w którym został wywołany.  Gdy jest wywoływana `Task.Run`, jest kolejkuje kosztowną operację powiązaną z procesorem, `DoExpensiveCalculation()`, w puli `Task<int>` wątków i odbiera uchwyt.  `DoExpensiveCalculation()`jest ostatecznie uruchamiane współbieżnie na następnym dostępnym wątku, prawdopodobnie na innym rdzeń procesora CPU.  Możliwe jest wykonywanie współbieżnych zadań, gdy `DoExpensiveCalculation()` są one zajęte w innym wątku, ponieważ jest nadal `CalculateResult()` wykonywany wątek, który został wywołany.

Po `await` napotkaniu `CalculateResult()` zostanie osiągnięty jego obiekt wywołujący, co pozwala na wykonywanie innych zadań z bieżącym wątkiem podczas `DoExpensiveCalculation()` wycofywania wyniku.  Po zakończeniu wynik zostanie umieszczony w kolejce do uruchomienia w wątku głównym.  Ostatecznie wątek główny powróci do wykonania `CalculateResult()`, a następnie będzie miał `DoExpensiveCalculation()`wynik.

### <a name="why-does-async-help-here"></a>Dlaczego w tym miejscu jest dostępna pomoc Async?

`async`najlepszym `await` rozwiązaniem jest zarządzanie powiązanymi z procesorami zadań, gdy potrzebna jest czas odpowiedzi. Istnieje wiele wzorców do użycia async z zadaniami związanymi z PROCESORem. Należy pamiętać, że istnieje niewielki koszt korzystania z usługi asynchronicznej i nie jest to zalecane w przypadku ścisłych pętli.  Pozwala to określić sposób pisania kodu w ramach tej nowej funkcji.

## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne wC#](../csharp/async.md)
- [Programowanie asynchroniczne z Async i Await (C#)](../csharp/programming-guide/concepts/async/index.md)
- [Programowanie asynchroniczne wF#](../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../visual-basic/programming-guide/concepts/async/index.md)
