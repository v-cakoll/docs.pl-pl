---
title: Async w głębi
description: Dowiedz się, jak pisanie kodu asynchronicznego związanego z we/wy i cpu jest proste przy użyciu modelu asynchronicznego opartego na zadaniu .NET.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 91fd37ce329c03b43b5472e4579be7f5ef961738
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70169110"
---
# <a name="async-in-depth"></a>Async w głębi

Pisanie kodu asynchronicznego związanego z i procesorem CPU jest proste przy użyciu modelu asynchronicznego opartego na zadaniu .NET. Model jest narażony `Task` przez `Task<T>` i `async` typów `await` i słów kluczowych i w języku C# i Visual Basic. (Zasoby specyficzne dla języka znajdują się w sekcji [Zobacz również).](#see-also) W tym artykule wyjaśniono, jak korzystać z usługi .NET async i zapewnia wgląd w strukturę asynchronicznej używane w ramach obejmuje.

## <a name="task-and-taskt"></a>> zadania\<i zadania T

Zadania są konstrukcje używane do implementowania, co jest znane jako [Promise Model współbieżności](https://en.wikipedia.org/wiki/Futures_and_promises).  Krótko mówiąc, oferują one "obietnicę", że praca zostanie zakończona w późniejszym czasie, co pozwala koordynować z obietnicą z czystym interfejsem API.

- `Task`reprezentuje pojedynczą operację, która nie zwraca wartości.
- `Task<T>`reprezentuje pojedynczą operację, która `T`zwraca wartość typu .

Ważne jest, aby rozumować o zadaniach jako abstrakcje pracy dzieje asynchronicznie, a *nie* abstrakcji nad wątkowości. Domyślnie zadania są wykonywane w bieżącym wątku i delegują pracę do systemu operacyjnego, odpowiednio. Opcjonalnie można jawnie zażądać zadań do uruchamiania `Task.Run` w oddzielnym wątku za pośrednictwem interfejsu API.

Zadania uwidaczniają protokół interfejsu API do monitorowania, `Task<T>`oczekiwania i uzyskiwania dostępu do wartości wyniku (w przypadku) zadania. Integracja języka, `await` ze słowem kluczowym, zapewnia abstrakcję wyższego poziomu za pomocą zadań.

Za `await` pomocą aplikacji lub usługi do wykonywania przydatnej pracy, gdy zadanie jest uruchomione przez plonowanie kontroli do jego obiektu wywołującego, dopóki zadanie nie zostanie wykonane. Kod nie musi polegać na wywołaniach wywołania wsteczne lub zdarzenia, aby kontynuować wykonywanie po zakończeniu zadania. Integracja interfejsu API języka i zadania robi to za Ciebie. Jeśli używasz `Task<T>`, `await` słowo kluczowe dodatkowo "rozpakowuje" wartość zwróconą po zakończeniu zadania.  Szczegóły dotyczące tego, jak to działa, wyjaśniono poniżej.

Więcej informacji na temat zadań i różnych sposobów interakcji z nimi można znaleźć w temacie [Wzorca asynchronicznego (TAP) opartego na zadaniach.](./asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>Głębsze zagłębianie się w zadania operacji związanej z we/wy

W poniższej sekcji opisano widok 10 000 stóp tego, co dzieje się z typowym wywołaniem we/wy asynchronicznej. Zacznijmy od kilku przykładów.

Pierwszy przykład wywołuje metodę asynchroniczną i zwraca aktywne zadanie, prawdopodobnie jeszcze do wykonania.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();

    return client.GetStringAsync("https://www.dotnetfoundation.org");
}
```

Drugi przykład dodaje użycie `async` i `await` słowa kluczowe do działania na zadanie.

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

Wywołanie `GetStringAsync()` wywołania za pośrednictwem bibliotek .NET niższego poziomu (być może wywołanie innych metod asynchronicznej), dopóki nie osiągnie wywołania interop P/Invoke do natywnej biblioteki sieciowej. Biblioteka natywna może następnie wywołać wywołanie `write()` interfejsu API systemu (na przykład do gniazda w systemie Linux). Obiekt zadania zostanie utworzony na granicy macierzystej/zarządzanej, prawdopodobnie przy użyciu [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)). Obiekt zadania będą przekazywane przez warstwy, prawdopodobnie obsługiwane na lub bezpośrednio zwrócone, ostatecznie zwrócony do początkowego obiektu wywołującego.

W drugim przykładzie powyżej `Task<T>` obiekt zostanie zwrócony z `GetStringAsync`. Użycie słowa `await` kluczowego powoduje, że metoda zwraca nowo utworzony obiekt zadania. Formant powraca do obiektu wywołującego `GetFirstCharactersCountAsync` z tej lokalizacji w metodzie. Metody i właściwości [task&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) obiektu umożliwiają wywołującym monitorowanie postępu zadania, który zostanie ukończony po wykonaniu pozostałego kodu w GetFirstCharactersCountAsync.

Po wywołaniu interfejsu API systemu żądanie znajduje się teraz w przestrzeni jądra, co `/net` trafia do podsystemu sieciowego systemu operacyjnego (na przykład w jądrze Linuksa).  W tym miejscu os będzie obsługiwać żądanie sieci *asynchronicznie*.  Szczegóły mogą się różnić w zależności od używanego systema operacyjnego (wywołanie sterownika urządzenia może być zaplanowane jako sygnał wysłany z powrotem do czasu wykonywania lub można wywołać sterownik urządzenia, a *następnie* sygnał wysłany z powrotem), ale ostatecznie czas wykonywania zostanie poinformowany, że żądanie sieci jest w toku.  W tej chwili praca dla sterownika urządzenia zostanie zaplanowana, w toku lub już zakończona (żądanie jest już "przez sieć") - ale ponieważ wszystko to dzieje się asynchronicznie, sterownik urządzenia jest w stanie natychmiast obsłużyć coś innego!

Na przykład w systemie Windows wątek systemu operacyjnego wykonuje wywołanie sterownika urządzenia sieciowego i prosi go o wykonanie operacji sieciowej za pomocą pakietu żądania przerwania (IRP), który reprezentuje operację.  Sterownik urządzenia odbiera MPP, wykonuje wywołanie do sieci, oznacza MPP jako "oczekujące" i wraca do os.  Ponieważ wątek os teraz wie, że MPP jest "oczekujące", nie ma więcej pracy do zrobienia dla tego zadania i "zwraca" z powrotem, dzięki czemu może służyć do wykonywania innych prac.

Gdy żądanie zostanie spełnione, a dane powrócą przez sterownik urządzenia, powiadomi procesor o nowych danych otrzymanych za pomocą przerwania.  Sposób obsługi tego przerwania będzie się różnić w zależności od systemu operacyjnego, ale ostatecznie dane będą przekazywane przez system operacyjny, dopóki nie dotrze do połączenia międzyoperacyjnego systemu (na przykład w systemie Linux program obsługi przerwań zaplanuje dolną połowę Przerwania, aby przekazać dane za pośrednictwem systemu operacyjnego asynchronicznie).  Należy pamiętać, że dzieje się to *również* asynchronicznie!  Wynik jest umieszczany w kolejce, dopóki następny dostępny wątek nie będzie mógł wykonać metody asynchronicznej i "rozpakować" wynik ukończonego zadania.

W całym tym procesie, klucz na wynos jest to, że **żaden wątek nie jest dedykowany do uruchamiania zadania**.  Mimo że praca jest wykonywana w pewnym kontekście (oznacza to, że system operacyjny musi przekazać dane do sterownika urządzenia i odpowiedzieć na przerwanie), nie ma wątku dedykowanego do *oczekiwania* na dane z żądania, aby wrócić.  Dzięki temu system może obsługiwać znacznie większą ilość pracy, zamiast czekać na zakończenie niektórych wywołań we/wy.

Chociaż powyższe może wydawać się dużo pracy do zrobienia, gdy mierzona pod względem czasu zegara ściennego, to malutkie w porównaniu do czasu potrzebnego do rzeczywistej pracy We/Wy. Chociaż wcale nie jest to precyzyjne, potencjalny harmonogram takiego połączenia wyglądałby tak:

0-1————————————————————————————————————————————————–2-3

- Czas spędzony `0` od `1` punktów do jest wszystko do metody asynchronicznej daje kontrolę do jego obiektu wywołującego.
- Czas spędzony `1` z `2` punktów do to czas spędzony na we/wy, bez kosztów procesora.
- Na koniec czas `2` spędzony `3` z punktów do jest przekazywanie kontroli z powrotem (i potencjalnie wartość) do metody asynchronicznej, w którym to momencie jest wykonywana ponownie.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Co to oznacza dla scenariusza serwera?

Ten model działa dobrze z typowym obciążeniem scenariusza serwera.  Ponieważ nie ma żadnych wątków przeznaczonych do blokowania niedokończonych zadań, pula wątków serwera może obsługiwać znacznie większą liczbę żądań sieci Web.

Należy wziąć pod uwagę dwa serwery: jeden, który uruchamia kod asynchronicznego, a jeden, który nie.  Na potrzeby tego przykładu każdy serwer ma tylko 5 wątków dostępnych dla żądań obsługi.  Należy zauważyć, że liczby te są wyimaginowane małe i służyć tylko w kontekście demonstracyjne.

Załóżmy, że oba serwery odbierają 6 równoczesnych żądań. Każde żądanie wykonuje operację we/wy.  Serwer *bez* kodu asynchronicznego musi ustawiać się w kolejce do 6 żądania, dopóki jeden z 5 wątków nie zakończy pracy związanej z we/wy i nie napisze odpowiedzi. W momencie, gdy pojawia się 20 żądanie, serwer może zacząć zwalniać, ponieważ kolejka jest zbyt długa.

Serwer *z* uruchomionym kodem asynchronicznym nadal umieszcza w `async` kolejce 6 żądanie, ale ponieważ używa i `await`, każdy z jego wątków są zwalniane po rozpoczęciu pracy związanej we/wy, a nie po zakończeniu.  Do czasu wejścia 20 żądania kolejka dla żądań przychodzących będzie znacznie mniejsza (jeśli w ogóle ma w sobie coś), a serwer nie zwolni.

Chociaż jest to wymyślony przykład, działa w bardzo podobny sposób w prawdziwym świecie.  W rzeczywistości można oczekiwać, że serwer będzie w stanie `async` obsłużyć o rząd wielkości więcej żądań przy użyciu i `await` niż gdyby był dedykowany wątku dla każdego żądania, które otrzymuje.

### <a name="what-does-this-mean-for-client-scenario"></a>Co to oznacza dla scenariusza klienta?

Największym zyskiem `async` za `await` korzystanie z aplikacji klienckiej i dla niego jest wzrost responsywności.  Chociaż można sprawić, że aplikacja będzie reagować przez ręczne tarło wątków, akt tarła wątku jest kosztowną operacją w stosunku do tylko przy użyciu `async` i `await`.  Szczególnie dla czegoś takiego jak gra mobilna, wpływ na wątek interfejsu użytkownika w jak najmniejszym stopniu, jeśli chodzi o We/Wy, ma kluczowe znaczenie.

Co ważniejsze, ponieważ praca związana z we/wy nie spędza praktycznie czasu na procesorze, poświęcając cały wątek procesora do wykonywania prawie żadnej użytecznej pracy byłoby słabe wykorzystanie zasobów.

Ponadto wysyłanie pracy do wątku interfejsu użytkownika (na przykład aktualizowanie interfejsu `async` użytkownika) jest bardzo proste z metodami i nie wymaga dodatkowej pracy (na przykład wywoływanie delegata bezpiecznego dla wątków).

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a>Głębiej zanurz się\<w> zadania i zadania T dla operacji związanej z procesorem

Kod związany `async` z procesorem CPU jest nieco `async` inny niż kod związany z we/wy.  Ponieważ praca jest wykonywana na procesorze CPU, nie ma sposobu, aby obejść poświęcając wątek do obliczeń.  Korzystanie z `async` `await` i zapewnia czysty sposób interakcji z wątku w tle i zachować obiekt wywołujący metody asynchronicznej elastyczne.  Należy pamiętać, że nie zapewnia to żadnej ochrony udostępnionych danych.  Jeśli używasz udostępnionych danych, nadal trzeba będzie zastosować odpowiednią strategię synchronizacji.

Oto 10 000 stóp widok wywołania asynchronicznego związanego z procesorem:

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

`CalculateResult()`wykonuje w wątku, który został wezwany.  Gdy wywołuje `Task.Run`, kolejki kosztowne operacji cpu `DoExpensiveCalculation()`związane, , w puli `Task<int>` wątków i odbiera dojście.  `DoExpensiveCalculation()`jest ostatecznie uruchamiany jednocześnie na następnym dostępnym wątku, prawdopodobnie na innym rdzeniu procesora.  Jest możliwe do równoczesnych prac, gdy `DoExpensiveCalculation()` jest zajęty w innym `CalculateResult()` wątku, ponieważ wątek, który wywoływany jest nadal wykonywane.

Po `await` napotkaniu, wykonanie `CalculateResult()` jest udomowiony do jego obiektu wywołującego, `DoExpensiveCalculation()` dzięki czemu inne prace do wykonania z bieżącego wątku podczas ubijania obecnie wynik.  Po zakończeniu wynik jest umieszczany w kolejce do uruchomienia w wątku głównym.  Ostatecznie główny wątek powróci do `CalculateResult()`wykonywania , w którym to `DoExpensiveCalculation()`momencie będzie miał wynik .

### <a name="why-does-async-help-here"></a>Dlaczego async pomaga tutaj?

`async`i `await` są najlepszym rozwiązaniem w zarządzaniu pracą związaną z procesorem, gdy potrzebujesz reakcji. Istnieje wiele wzorców do używania asynchronii z pracą związaną z procesorem CPU. Ważne jest, aby pamiętać, że korzystanie z asynchronii jest niewielkie i nie jest zalecane w przypadku ciasnych pętli.  To do Ciebie, aby określić, jak napisać kod wokół tej nowej funkcji.

## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne w języku C #](../csharp/async.md)
- [Asynchroniczne programowanie z async i await (C#)](../csharp/programming-guide/concepts/async/index.md)
- [Programowanie asynchroniczne w f #](../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Programowanie asynchroniczne z asynchroniczną i oczekiwaną (Visual Basic)](../visual-basic/programming-guide/concepts/async/index.md)
