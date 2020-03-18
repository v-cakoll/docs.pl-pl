---
title: Wykorzystywanie wzorca asynchronicznego opartego na zadaniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
ms.openlocfilehash: f80e6ae520ab03c0f5f4edc30c0b7102193ee6c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139818"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Wykorzystywanie wzorca asynchronicznego opartego na zadaniach

Korzystając z wzorca asynchronicznego (TAP) opartego na zadaniach do pracy z operacjami asynchronicznymi, można użyć wywołań wywołania wstecznego w celu osiągnięcia oczekiwania bez blokowania.  W przypadku zadań jest to osiągane za pomocą takich metod, jak <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Obsługa asynchroniczna oparta na języku ukrywa wywołania wywołania wywołań, umożliwiając operacje asynchroniczne, które mają być oczekiwane w ramach normalnego przepływu sterowania, a kod wygenerowany przez kompilator zapewnia tę samą obsługę na poziomie interfejsu API.

## <a name="suspending-execution-with-await"></a>Zawieszanie realizacji z await
 Począwszy od .NET Framework 4.5, można użyć [await](../../csharp/language-reference/operators/await.md) słowa kluczowego w języku C# <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> i [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic asynchronicznie await i obiektów. Gdy oczekujesz na <xref:System.Threading.Tasks.Task>wyrażenie, `await` jest `void`typu . Gdy oczekujesz na <xref:System.Threading.Tasks.Task%601>wyrażenie, `await` jest `TResult`typu . Wyrażenie `await` musi występować wewnątrz treści metody asynchronicznej. For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.

 Pod okładkami funkcja await instaluje wywołanie odwetowe zadania przy użyciu kontynuacji.  To wywołanie wsteczne wznawia metodę asynchroniczną w punkcie zawieszenia. Po wznowieniu metody asynchronicznej, jeśli oczekiwana operacja została ukończona pomyślnie i została zwrócona, <xref:System.Threading.Tasks.Task%601>jej `TResult` jest zwracana.  Jeśli <xref:System.Threading.Tasks.Task> lub, <xref:System.Threading.Tasks.Task%601> że oczekiwano <xref:System.Threading.Tasks.TaskStatus.Canceled> zakończył się <xref:System.OperationCanceledException> w stanie, wyjątek.  Jeśli <xref:System.Threading.Tasks.Task> lub, <xref:System.Threading.Tasks.Task%601> że oczekiwano <xref:System.Threading.Tasks.TaskStatus.Faulted> zakończył się w stanie, wyjątek, który spowodował jego błąd jest generowany. A `Task` może błąd w wyniku wielu wyjątków, ale tylko jeden z tych wyjątków jest propagowane. Jednak <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.AggregateException> wyjątek, który zawiera wszystkie błędy.

 Jeśli kontekst synchronizacji<xref:System.Threading.SynchronizationContext> (obiekt) jest skojarzony z wątku, który był wykonywania metody asynchronicznej w czasie zawieszenia (na przykład, jeśli <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> właściwość nie `null`jest <xref:System.Threading.SynchronizationContext.Post%2A> ), metoda asynchroniczna wznawia w tym samym kontekście synchronizacji przy użyciu metody kontekstu. W przeciwnym razie opiera się<xref:System.Threading.Tasks.TaskScheduler> na harmonogram zadań (obiekt), który był bieżący w momencie zawieszenia. Zazwyczaj jest to domyślny harmonogram zadań<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>( ), który jest przeznaczony dla puli wątków. Ten harmonogram zadań określa, czy oczekiwana operacja asynchroniczna powinna zostać wznowiona tam, gdzie została ukończona, czy też należy zaplanować wznowienie. Domyślny harmonogram zazwyczaj umożliwia kontynuacji do uruchomienia w wątku, który oczekiwaną operację zakończone.

 Gdy wywoływana jest metoda asynchroniczna, synchronicznie wykonuje treść funkcji aż do pierwszego wyrażenia await w oczekiwanym wystąpieniu, które nie zostało jeszcze zakończone, w którym to momencie wywołanie zwraca do obiektu wywołującego. Jeśli metoda asynchroniczna `void`nie <xref:System.Threading.Tasks.Task> zwraca <xref:System.Threading.Tasks.Task%601> , a lub obiekt jest zwracany do reprezentowania bieżących obliczeń. W metodzie asynchronicznej nievoid, jeśli zostanie napotkana instrukcja zwrotu lub zostanie osiągnięty koniec <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> treści metody, zadanie zostanie ukończone w stanie końcowym. Jeśli nieobsługiwany wyjątek powoduje, że formant opuści treść metody asynchronicznej, <xref:System.Threading.Tasks.TaskStatus.Faulted> zadanie kończy się w stanie. Jeśli ten wyjątek <xref:System.OperationCanceledException>jest , zadanie <xref:System.Threading.Tasks.TaskStatus.Canceled> zamiast kończy się w stanie. W ten sposób wynik lub wyjątek jest ostatecznie publikowany.

 Istnieje kilka ważnych odmian tego zachowania.  Ze względu na wydajność, jeśli zadanie zostało już ukończone do czasu oczekiwania na zadanie, kontrola nie jest ustępowana, a funkcja jest nadal wykonywana.  Ponadto powrót do oryginalnego kontekstu nie zawsze jest żądanym zachowaniem i można je zmienić; jest to opisane bardziej szczegółowo w następnej sekcji.

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Konfigurowanie zawieszenia i wznowienia z wydajnością i configureawait
 Kilka metod zapewnia większą kontrolę nad wykonaniem metody asynchronicznej. Na przykład można użyć <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metody, aby wprowadzić punkt wydajności do metody asynchronicznej:

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 Jest to równoważne asynchronicznie księgowania lub planowania z powrotem do bieżącego kontekstu.

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 Można również użyć <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metody lepszej kontroli nad zawieszeniem i wznowienie w metodzie asynchronicznej.  Jak wspomniano wcześniej, domyślnie bieżący kontekst jest przechwytywany w momencie, gdy metoda asynchroniczna jest zawieszona i że przechwycony kontekst jest używany do wywoływania kontynuacji metody asynchronicznej po wznowieniu.  W wielu przypadkach jest to dokładne zachowanie, które chcesz.  W innych przypadkach może nie dbać o kontekście kontynuacji i można osiągnąć lepszą wydajność, unikając takich wpisów z powrotem do oryginalnego kontekstu.  Aby to włączyć, <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> należy użyć metody, aby poinformować oczekiwaną operację nie do przechwytywania i wznowienia w kontekście, ale kontynuować wykonywanie wszędzie tam, gdzie operacja asynchroniczna, która była oczekiwana ukończona:

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a>Anulowanie operacji asynchronicznej
 Począwszy od .NET Framework 4, metody TAP, które obsługują anulowanie zapewniają<xref:System.Threading.CancellationToken> co najmniej jedno przeciążenie, które akceptuje token anulowania (obiekt).

 Token anulowania jest tworzony za pośrednictwem<xref:System.Threading.CancellationTokenSource> źródła tokenu anulowania (obiektu).  <xref:System.Threading.CancellationTokenSource.Token%2A> Właściwość źródła zwraca token anulowania, który zostanie zasygnalizowany, <xref:System.Threading.CancellationTokenSource.Cancel%2A> gdy wywoływana jest metoda źródła.  Na przykład, jeśli chcesz pobrać pojedynczą stronę sieci Web i chcesz mieć <xref:System.Threading.CancellationTokenSource> możliwość anulowania operacji, utwórz obiekt, przekaż jego <xref:System.Threading.CancellationTokenSource.Cancel%2A> token do metody TAP, a następnie wywołaj metodę źródła, gdy będziesz gotowy do anulowania operacji:

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 Aby anulować wiele wywołań asynchronicznych, można przekazać ten sam token do wszystkich wywołań:

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 Można również przekazać ten sam token selektywnemu podzbiorowi operacji:

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 Żądania anulowania mogą być inicjowane z dowolnego wątku.

 Można przekazać <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> wartość do dowolnej metody, która akceptuje token anulowania, aby wskazać, że anulowanie nigdy nie będzie wymagane.  Powoduje to, <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> że `false`właściwość do zwrócenia , a wywoływana metoda może odpowiednio zoptymalizować.  Do celów testowych można również przekazać w pre-anulowane token anulowania, który jest tworzony przy użyciu konstruktora, który akceptuje wartość logiczną, aby wskazać, czy token powinien być uruchamiany w stanie już anulowane lub nie można anulować.

 Takie podejście do anulowania ma kilka zalet:

- Ten sam token anulowania można przekazać do dowolnej liczby operacji asynchronicznych i synchronicznych.

- To samo żądanie anulowania może być mnożyć się do dowolnej liczby słuchaczy.

- Deweloper asynchronicznego interfejsu API ma pełną kontrolę nad tym, czy można zażądać anulowania i kiedy może ono wejść w życie.

- Kod, który zużywa interfejs API może selektywnie określić wywołania asynchroniczne, do których będą propagowane żądania anulowania.

## <a name="monitoring-progress"></a>Postęp monitorowania
 Niektóre metody asynchroniczne uwidaczniają postęp za pośrednictwem interfejsu postępu przekazywanego do metody asynchronicznej.  Na przykład należy wziąć pod uwagę funkcję, która asynchronicznie pobiera ciąg tekstu, a po drodze wywołuje aktualizacje postępu, które zawierają procent pobierania, który został ukończony do tej pory.  Taka metoda może być używany w aplikacji Windows Presentation Foundation (WPF) w następujący sposób:

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a>Korzystanie z wbudowanych kombinatorów zadaniowych
 Obszar <xref:System.Threading.Tasks> nazw zawiera kilka metod tworzenia i pracy z zadaniami.

### <a name="taskrun"></a>Task.run
 Klasa <xref:System.Threading.Tasks.Task> zawiera <xref:System.Threading.Tasks.Task.Run%2A> kilka metod, które umożliwiają łatwe <xref:System.Threading.Tasks.Task> odciążanie pracy jako lub <xref:System.Threading.Tasks.Task%601> do puli wątków, na przykład:

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 Niektóre z <xref:System.Threading.Tasks.Task.Run%2A> tych metod, <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> takich jak przeciążenie, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> istnieją jako skrót dla metody.  Inne przeciążenia, <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>takie jak , umożliwiają korzystanie z await w odciążonej pracy, na przykład:

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 Takie przeciążenia są logicznie <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> równoważne przy <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> użyciu metody w połączeniu z metodą rozszerzenia w bibliotece równoległej zadania.

### <a name="taskfromresult"></a>Zadanie.FromResult
 Użyj <xref:System.Threading.Tasks.Task.FromResult%2A> metody w scenariuszach, w których dane mogą być już dostępne i po prostu <xref:System.Threading.Tasks.Task%601>musi zostać zwrócony z metody zwracania zadań zniesione do:

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a>Task.WhenAll
 <xref:System.Threading.Tasks.Task.WhenAll%2A> Użyj metody, aby asynchronicznie czekać na wiele operacji asynchronicznych, które są reprezentowane jako zadania.  Metoda ma wiele przeciążeń, które obsługują zestaw zadań nieogólnych lub niejednolity zestaw zadań ogólnych (na przykład asynchronicznie oczekiwanie na wiele operacji zwracania void lub asynchronicznie oczekiwanie na wiele metod zwracania wartości, gdzie każda wartość `TResult`może mieć inny typ) i do obsługi jednolitego zestawu zadań ogólnych (takich jak asynchronicznie oczekujących na wiele metod zwracania wartości).

 Załóżmy, że chcesz wysyłać wiadomości e-mail do kilku klientów. Możesz nakładać się na wysyłanie wiadomości, aby nie czekać na zakończenie jednej wiadomości przed wysłaniem następnej. Można również dowiedzieć się, kiedy operacje wysyłania zostały zakończone i czy wystąpiły błędy:

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 Ten kod nie jawnie obsługiwać wyjątki, które mogą wystąpić, ale `await` pozwala wyjątki <xref:System.Threading.Tasks.Task.WhenAll%2A>propagowane z na wynikowe zadanie z .  Aby obsłużyć wyjątki, można użyć kodu, takiego jak:

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 W takim przypadku jeśli jakakolwiek operacja asynchroniczna nie powiedzie się, wszystkie wyjątki zostaną skonsolidowane w wyjątku, <xref:System.AggregateException> który jest przechowywany <xref:System.Threading.Tasks.Task> w, który jest zwracany z <xref:System.Threading.Tasks.Task.WhenAll%2A> metody.  Jednak tylko jeden z tych wyjątków `await` jest propagowany przez słowo kluczowe.  Jeśli chcesz sprawdzić wszystkie wyjątki, możesz przepisać poprzedni kod w następujący sposób:

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 Rozważmy przykład pobierania wielu plików z sieci web asynchronicznie.  W takim przypadku wszystkie operacje asynchroniczne mają jednorodne typy wyników i łatwo jest uzyskać dostęp do wyników:

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 Można użyć tych samych technik obsługi wyjątków omówiono w poprzednim scenariuszu zwracania unieważnienia:

```csharp
Task [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a>Task.WhenAny
 <xref:System.Threading.Tasks.Task.WhenAny%2A> Metoda służy do asynchronicznego oczekiwania tylko na jedną z wielu operacji asynchronicznych reprezentowanych jako zadania do wykonania.  Ta metoda służy cztery podstawowe przypadki użycia:

- Nadmiarowość: wykonywanie operacji wiele razy i wybieranie tej, która kończy się jako pierwsza (na przykład skontaktowanie się z wieloma usługami sieci Web ofert giełdowych, które przyniosą pojedynczy wynik, i wybranie tego, który zakończy najszybszą).

- Przeplatanie: Rozpoczęcie wielu operacji i oczekiwanie na ich zakończenie, ale przetwarzanie ich po ich zakończeniu.

- Ograniczanie przepustowości: umożliwienie rozpoczęcia dodatkowych operacji w miarę ukończenia innych.  Jest to rozszerzenie scenariusza przeplotu.

- Wczesne ratowanie: Na przykład operacja reprezentowana przez zadanie t1 <xref:System.Threading.Tasks.Task.WhenAny%2A> może być pogrupowana w zadaniu <xref:System.Threading.Tasks.Task.WhenAny%2A> z innym zadaniem t2 i można poczekać na zadanie. Zadanie t2 może reprezentować uchyłek czasu lub <xref:System.Threading.Tasks.Task.WhenAny%2A> anulowanie lub inny sygnał, który powoduje zakończenie zadania przed zakończeniem t1.

#### <a name="redundancy"></a>Nadmiarowość
 Rozważmy przypadek, w którym chcesz podjąć decyzję o tym, czy kupić akcje.  Istnieje kilka usług sieci Web rekomendacji giełdowych, które ufasz, ale w zależności od codziennego obciążenia, każda usługa może skończyć się powolne w różnym czasie.  Można użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metody, aby otrzymywać powiadomienia po zakończeniu dowolnej operacji:

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 W <xref:System.Threading.Tasks.Task.WhenAll%2A>przeciwieństwie do , który zwraca nieopakowane wyniki <xref:System.Threading.Tasks.Task.WhenAny%2A> wszystkich zadań, które zakończyły się pomyślnie, zwraca zadanie, które zostało ukończone. Jeśli zadanie nie powiedzie się, ważne jest, aby wiedzieć, że nie powiodło się, a jeśli zadanie zakończy się pomyślnie, ważne jest, aby wiedzieć, z którym zadaniem jest skojarzona wartość zwracana.  W związku z tym należy uzyskać dostęp do wyniku zwróconego zadania lub dalej czekać na niego, jak pokazano w tym przykładzie.

 Podobnie <xref:System.Threading.Tasks.Task.WhenAll%2A>jak w przypadku , musisz być w stanie pomieścić wyjątki.  Ponieważ otrzymasz ukończone zadanie z powrotem, można oczekiwać na zwrócone `try/catch` zadanie, aby błędy propagowane i odpowiednio je; na przykład:

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 Ponadto nawet jeśli pierwsze zadanie zakończy się pomyślnie, kolejne zadania mogą zakończyć się niepowodzeniem.  W tym momencie masz kilka opcji radzenia sobie z wyjątkami: Możesz poczekać, aż wszystkie uruchomione zadania <xref:System.Threading.Tasks.Task.WhenAll%2A> zostały zakończone, w którym to przypadku można użyć metody, lub można zdecydować, że wszystkie wyjątki są ważne i muszą być rejestrowane.  W tym celu można użyć kontynuacji, aby otrzymywać powiadomienia, gdy zadania zostały zakończone asynchronicznie:

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 lub:

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 lub nawet:

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 Na koniec można anulować wszystkie pozostałe operacje:

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a>Przeplataniem
 Rozważmy przypadek, w którym pobierasz obrazy z sieci Web i przetwarzasz każdy obraz (na przykład dodając obraz do kontrolki interfejsu użytkownika).  Musisz wykonać przetwarzanie sekwencyjnie w wątku interfejsu użytkownika, ale chcesz pobrać obrazy tak równocześnie, jak to możliwe. Ponadto nie chcesz wstrzymywać dodawania obrazów do interfejsu, dopóki nie zostaną pobrane — chcesz dodać je po ich zakończeniu:

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 Można również zastosować przeplot do scenariusza, który obejmuje <xref:System.Threading.ThreadPool> obliczeniowo intensywne przetwarzanie na pobranych obrazów; na przykład:

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a>Ograniczanie przepływności
 Należy wziąć pod uwagę przykład przeplotu, z tą różnicą, że użytkownik pobiera tak wiele obrazów, że pliki do pobrania muszą być ograniczane; na przykład chcesz, aby tylko określona liczba pobrań odbywała się jednocześnie. Aby to osiągnąć, można uruchomić podzbiór operacji asynchronicznych.  Po zakończeniu operacji można rozpocząć dodatkowe operacje, aby zająć ich miejsce:

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a>Wczesne ratowanie
 Należy wziąć pod uwagę, że oczekujesz asynchronicznie na operację, aby zakończyć jednocześnie odpowiadając na żądanie anulowania użytkownika (na przykład użytkownik kliknął przycisk anuluj). Poniższy kod ilustruje ten scenariusz:

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 Ta implementacja ponownie włącza interfejs użytkownika, gdy tylko zdecydujesz się na ratowanie, ale nie anuluje podstawowych operacji asynchronicznych.  Inną alternatywą byłoby anulowanie oczekujących operacji, gdy zdecydujesz się na ratowanie, ale nie ponowne ustanowienie interfejsu użytkownika, dopóki operacje faktycznie nie zostaną zakończone, potencjalnie z powodu wcześniejszego zakończenia z powodu żądania anulowania:

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 Innym przykładem wczesnego ratowania <xref:System.Threading.Tasks.Task.WhenAny%2A> polega na <xref:System.Threading.Tasks.Task.Delay%2A> użyciu metody w połączeniu z metodą, jak omówiono w następnej sekcji.

### <a name="taskdelay"></a>Task.Delay
 Metoda służy <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> do wprowadzania pauz y do wykonania metody asynchronicznej.  Jest to przydatne w przypadku wielu rodzajów funkcji, w tym tworzenia pętli sondowania i opóźniania obsługi danych wejściowych użytkownika przez określony czas.  Metoda <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> może być również przydatne <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> w połączeniu z implementacji uchyliń czasu na czeka.

 Jeśli zadanie, które jest częścią większej operacji asynchronicznej (na przykład ASP.NET usługi sieci web) trwa zbyt długo, aby zakończyć, ogólna operacja może ucierpieć, zwłaszcza jeśli nigdy nie ukończ.  Z tego powodu ważne jest, aby mieć możliwość uchylania się czasu podczas oczekiwania na operację asynchroniczną.  Synchroniczne <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>i <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody akceptują wartości czasu uporu, ale odpowiednie <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> i wcześniej wymienione <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody nie.  Zamiast tego można <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> użyć i w połączeniu zaimplementować uchył.

 Na przykład w aplikacji interfejsu użytkownika załóżmy, że chcesz pobrać obraz i wyłączyć interfejs użytkownika podczas pobierania obrazu. Jeśli jednak pobieranie trwa zbyt długo, chcesz ponownie włączyć ui i odrzucić pobieranie:

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 To samo dotyczy wielu pobrań, ponieważ <xref:System.Threading.Tasks.Task.WhenAll%2A> zwraca zadanie:

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a>Tworzenie kombinatorów opartych na zadaniach
 Ponieważ zadanie jest w stanie całkowicie reprezentować operację asynchroniczną i zapewnić synchroniczne i asynchroniczne możliwości łączenia się z operacją, pobieranie jej wyników itd., można tworzyć przydatne biblioteki kombinatorów, które rekomponują zadania do tworzyć większe wzory.  Jak omówiono w poprzedniej sekcji .NET Framework zawiera kilka wbudowanych kombinatorów, ale można również tworzyć własne. W poniższych sekcjach podano kilka przykładów potencjalnych metod i typów kombinatora.

### <a name="retryonfault"></a>Ponowiony błąd
 W wielu sytuacjach można ponowić próbę wykonania operacji, jeśli poprzednia próba nie powiedzie się.  W przypadku kodu synchronicznego można utworzyć metodę `RetryOnFault` pomocnika, na przykład w poniższym przykładzie, aby to osiągnąć:

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 Można utworzyć prawie identyczną metodę pomocnika dla operacji asynchronicznych, które są implementowane za pomocą tap, a tym samym zwracać zadania:

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 Następnie można użyć tego kombinatora do kodowania ponownych prób do logiki aplikacji; na przykład:

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 Można rozszerzyć `RetryOnFault` funkcję dalej. Na przykład funkcja może `Func<Task>` zaakceptować inny, który zostanie wywołany między ponownych prób, aby określić, kiedy ponownie spróbować wykonać operację; na przykład:

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 Następnie można użyć funkcji w następujący sposób czekać na sekundę przed ponowieniem próby operacji:

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a>NeedOnlyOne (NeedOnlyOne)
 Czasami można skorzystać z nadmiarowości, aby zwiększyć opóźnienie operacji i szanse na powodzenie.  Należy wziąć pod uwagę wiele usług internetowych, które zapewniają notowania giełdowe, ale o różnych porach dnia, każda usługa może zapewnić różne poziomy jakości i czasu reakcji.  Aby poradzić sobie z tymi wahaniami, możesz wysyłać żądania do wszystkich usług sieci web, a gdy tylko otrzymasz odpowiedź od jednego, anuluj pozostałe żądania.  Można zaimplementować funkcję pomocnika, aby ułatwić implementowanie tego wspólnego wzorca uruchamiania wielu operacji, oczekiwanie na dowolne, a następnie anulowanie reszty. Funkcja `NeedOnlyOne` w poniższym przykładzie ilustruje ten scenariusz:

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 Następnie można użyć tej funkcji w następujący sposób:

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a>Operacje z przeplotem
 Istnieje potencjalny problem z wydajnością przy użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A> metody do obsługi scenariusza przeplotu podczas pracy z bardzo dużymi zestawami zadań. Każde wywołanie powoduje <xref:System.Threading.Tasks.Task.WhenAny%2A> kontynuacji są rejestrowane z każdego zadania. W przypadku N liczby zadań powoduje to kontynuacje O(N<sup>2)</sup>utworzone przez cały okres istnienia operacji przeplotu. Jeśli pracujesz z dużym zestawem zadań, możesz użyć`Interleaved` kombinatora (w poniższym przykładzie) w celu rozwiązania problemu z wydajnością:

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 Następnie można użyć kombinatora do przetwarzania wyników zadań podczas ich wykonywania; na przykład:

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a>WhenAllOrFirstException (Pierwszy wyjątek od WhenAllOrFirstException)
 W niektórych scenariuszach scatter/gather można poczekać na wszystkie zadania w zestawie, chyba że jeden z nich błędy, w którym to przypadku chcesz przestać czekać, jak tylko wystąpi wyjątek.  Można to osiągnąć za pomocą metody `WhenAllOrFirstException` kombinatora, takich jak w poniższym przykładzie:

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a>Tworzenie struktur danych opartych na zadaniach
 Oprócz możliwości tworzenia niestandardowych kombinatorów opartych na zadaniach, o strukturę danych i <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> który reprezentuje zarówno wyniki operacji asynchronicznej i niezbędne synchronizacji do przyłączenia się z nim sprawia, że bardzo zaawansowany typ, na którym do tworzenia struktur danych niestandardowych, które mają być używane w scenariuszach asynchronicznych.

### <a name="asynccache"></a>AsyncCache
 Ważnym aspektem zadania jest to, że może być rozdawane wielu konsumentom, z których wszyscy mogą na niego czekać, <xref:System.Threading.Tasks.Task%601>rejestrować z nim kontynuacje, uzyskać jego wynik lub wyjątki (w przypadku ) i tak dalej.  To <xref:System.Threading.Tasks.Task> sprawia, że i <xref:System.Threading.Tasks.Task%601> doskonale nadaje się do użycia w infrastrukturze buforowania asynchronicznego.  Oto przykład małej, ale potężnej asynchronicznej <xref:System.Threading.Tasks.Task%601>pamięci podręcznej zbudowanej na wierzchu:

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 [AsyncCache\<TKey, TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) klasa akceptuje jako delegat do swojego konstruktora <xref:System.Threading.Tasks.Task%601>funkcji, która przyjmuje `TKey` i zwraca .  Wszystkie wcześniej dostępne wartości z pamięci podręcznej są przechowywane `AsyncCache` w słowniku wewnętrznym, a zapewnia, że tylko jedno zadanie jest generowane na klucz, nawet jeśli pamięć podręczna jest jednocześnie dostępna.

 Na przykład można utworzyć pamięć podręczną dla pobranych stron internetowych:

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 Następnie można użyć tej pamięci podręcznej w metodach asynchronicznych, gdy potrzebujesz zawartości strony sieci web. Klasa `AsyncCache` zapewnia, że pobierasz jak najmniej stron i buforuje wyniki.

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection
 Za pomocą zadań można również tworzyć struktury danych do koordynowania działań asynchronicznych.  Rozważmy jeden z klasycznych wzorców projektowania równoległego: producent/ konsument.  W tym wzorzec producenci generują dane, które są zużywane przez konsumentów, a producenci i konsumenci mogą działać równolegle. Na przykład konsument przetwarza element 1, który został wcześniej wygenerowany przez producenta, który obecnie produkuje towar 2.  W przypadku struktury producenta/konsumenta niezmiennie potrzebna jest struktura danych do przechowywania prac stworzonych przez producentów, tak aby konsumenci mogli być powiadamiani o nowych danych i znajdować je, gdy są one dostępne.

 Oto prosta struktura danych zbudowana na zadaniach, która umożliwia metody asynchroniczne, które mają być używane jako producenci i konsumenci:

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 Dzięki tej strukturze danych w miejscu, można napisać kod, takich jak:

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

Obszar <xref:System.Threading.Tasks.Dataflow> nazw zawiera <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typ, którego można używać w podobny sposób, ale bez konieczności tworzenia niestandardowego typu kolekcji:

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> Obszar <xref:System.Threading.Tasks.Dataflow> nazw jest dostępny w .NET Framework 4.5 przez **NuGet**. Aby zainstalować zestaw <xref:System.Threading.Tasks.Dataflow> zawierający obszar nazw, otwórz projekt w programie Visual Studio, wybierz polecenie **Zarządzaj pakietami NuGet** z menu Projekt i wyszukaj w trybie online pakiet Microsoft.Tpl.Dataflow.

## <a name="see-also"></a>Zobacz też

- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Implementacja wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
