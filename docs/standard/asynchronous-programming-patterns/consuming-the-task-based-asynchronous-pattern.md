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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b538cb53e1cbc1fdbd8e34506710a1967e50f9d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615550"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Wykorzystywanie wzorca asynchronicznego opartego na zadaniach
Gdy używasz opartego na zadaniach asynchronicznej wzorca (TAP) do pracy z operacji asynchronicznych, możesz korzystać z wywołań zwrotnych do osiągnięcia oczekiwania bez blokowania.  W przypadku zadań jest to realizowane przez metody takie jak <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Obsługa komunikacji asynchronicznej opartych na języku ukrywa wywołań zwrotnych, umożliwiając operacji asynchronicznych Oczekiwanie w ramach normalnych sterowanie przepływem i kod generowany przez kompilator obsługuje ten sam poziom interfejsu API.  
  
## <a name="suspending-execution-with-await"></a>Zawieszenie wykonywania za pomocą Await  
 Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], możesz użyć [await](~/docs/csharp/language-reference/keywords/await.md) — słowo kluczowe w języku C# i [operatora Await](~/docs/visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic asynchronicznie oczekują na <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiektów. Jeśli masz oczekujące na <xref:System.Threading.Tasks.Task>, `await` wyrażenie jest typu `void`. Jeśli masz oczekujące na <xref:System.Threading.Tasks.Task%601>, `await` wyrażenie jest typu `TResult`. `await` Wyrażenie musi wystąpić w treści metody asynchronicznej. Aby uzyskać więcej informacji na temat języka C# i Visual Basic obsługują w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobacz temat specyfikacji języka C# i Visual Basic.  
  
 Dzieje się w tle funkcje await instaluje wywołanie zwrotne do zadania za pomocą kontynuacji.  To wywołanie zwrotne wznawia metody asynchronicznej w punkcie zawieszenia. Po wznowieniu metody asynchronicznej Jeśli oczekiwane działanie, zakończyło się pomyślnie i został <xref:System.Threading.Tasks.Task%601>, jego `TResult` jest zwracana.  Jeśli <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> , oczekiwany zostało zakończone w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu, <xref:System.OperationCanceledException> wyjątku.  Jeśli <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> , oczekiwany zostało zakończone w <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu, jest zgłaszany wyjątek, który spowodował jego błędów. A `Task` błędów wyniku wiele wyjątków może, ale tylko jeden z tych wyjątków jest propagowany. Jednak <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.AggregateException> wyjątek, który zawiera wszystkie błędy.  
  
 Jeśli kontekst synchronizacji (<xref:System.Threading.SynchronizationContext> obiektu) jest skojarzony z wątkiem, wykonywanej metody asynchronicznej w chwili zawieszenia (na przykład, jeśli <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> właściwość nie jest `null`), metoda asynchroniczna wznawia na tym Ten sam kontekst synchronizacji przy użyciu kontekstu <xref:System.Threading.SynchronizationContext.Post%2A> metody. W przeciwnym razie opiera się na harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler> obiektu) było aktualne w chwili zawieszenia. Zazwyczaj jest to domyślny harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), który jest przeznaczony dla puli wątków. Ten harmonogram zadań określa, czy operacji asynchronicznej powinna zostać wznowiona, gdzie ukończone lub tego, czy powinna zostać zaplanowana wznowienia. Domyślnego harmonogramu zezwala zazwyczaj na kontynuację uruchamiać w wątku, który, oczekiwane operacja zakończona.  
  
 Gdy wywoływana jest metoda asynchroniczna, synchronicznie wykonuje treści funkcji do czasu pierwszy operator await, wyrażenie na oczekujący wystąpienie, które nie zostało jeszcze zakończone, w tym momencie wywołania powraca do obiektu wywołującego. Jeśli metoda asynchroniczna zwraca `void`, <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiekt jest zwracany do reprezentowania trwającą obliczeń. W metodzie asynchronicznej, innym niż void, jeśli zostanie osiągnięty instrukcji return lub osiągnięty zostanie koniec treści metody, zadanie zostało ukończone w <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stan końcowy. Jeśli nieobsługiwany wyjątek powoduje, że formant opuścić tekstu metody asynchronicznej, zadanie kończy się <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu. Jeśli wyjątkiem jest sytuacja, <xref:System.OperationCanceledException>, zadanie kończy się zamiast tego na <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu. W ten sposób wynik lub wyjątek po pewnym czasie została opublikowana.  
  
 Istnieje kilka ważnych zmian, to zachowanie.  Ze względu na wydajność Jeśli zadanie zostało już ukończone do czasu trwa oczekiwanie na zadanie, kontrolki nie jest uzyskane i kontynuuje wykonywanie funkcji.  Ponadto powrotu do oryginalnego kontekstu nie zawsze są żądane zachowanie i można ją zmienić; to jest opisany bardziej szczegółowo w następnej sekcji.  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Konfigurowanie zawieszenia i wznowienia przy użyciu produktywności i ConfigureAwait  
 Kilka metod zapewniają większą kontrolę nad wykonywaniem metody asynchronicznej. Na przykład, można użyć <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metodę, aby wprowadzić punkt yield do metod asynchronicznych:  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 Jest to równoważne do asynchronicznego przesyłania lub harmonogramów bieżącego kontekstu.  
  
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
  
 Można również użyć <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metody dla lepszej kontroli nad zawieszenia i wznowienia w metodzie asynchronicznej.  Jak już wspomniano, domyślnie bieżącego kontekstu są przechwytywane w czasie, które metody asynchronicznej jest wstrzymana, a ten kontekście przechwyconym służy do wywoływania metody asynchronicznej kontynuacji po wznowieniu.  W wielu przypadkach jest dokładne zachowanie, które chcesz.  W innych przypadkach może nie interesujące Cię kontekst kontynuacji i lepszą wydajność można uzyskać, unikając takie wpisy powrót do oryginalnego kontekstu.  Aby włączyć tę opcję, należy użyć <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodę, aby poinformować operacji await nie w celu przechwycenia i wznowić w kontekście, ale kontynuuje wykonywanie, wszędzie tam, gdzie ukończyć operację asynchroniczną, która jest oczekiwany:  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a>Anulowanie operacji asynchronicznej  
 Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], metody wzorca TAP obsługuje anulowanie Podaj co najmniej jeden przeciążenia, które akceptuje token odwołania (<xref:System.Threading.CancellationToken> obiektu).  
  
 Token anulowania jest tworzony przez źródło tokenu anulowania (<xref:System.Threading.CancellationTokenSource> obiektu).  Źródło <xref:System.Threading.CancellationTokenSource.Token%2A> właściwość zwraca token anulowania, który zostanie zasygnalizowane podczas źródła <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda jest wywoływana.  Na przykład, jeśli chcesz pobrać pojedynczej strony sieci Web i chcesz mieć możliwość anulować operację, należy utworzyć <xref:System.Threading.CancellationTokenSource> obiektu, przekazać token jej do metody wzorca TAP, a następnie wywołaj źródła <xref:System.Threading.CancellationTokenSource.Cancel%2A> metody, gdy wszystko będzie gotowe anulować operację:  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 Aby anulować wielu wywołań asynchronicznych, można przekazać tego samego tokenu do wywołania wszystkich:  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 Alternatywnie można przekazać tego samego tokenu do podzbioru selektywne operacje:  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 Może zostać zainicjowane żądań anulowania z żadnym z wątków.  
  
 Możesz przekazać <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> wartość do dowolnej metody, które akceptuje token anulowania, aby wskazać, że anulowanie nigdy nie będzie wymagane.  Powoduje to, że <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> właściwości do zwrócenia `false`, i odpowiednio zoptymalizować wywoływanej metody.  Do celów testowych można również przekazać token anulowania wstępnie anulowane, który zostanie uruchomiony przy użyciu konstruktora, który przyjmuje wartość logiczną, aby wskazać, czy token powinna uruchomić się w stanie już anulowana lub nie można anulować.  
  
 Takie podejście do anulowania ma kilka zalet:  
  
-   Można przekazać ten sam token odwołania do dowolnej liczby operacji synchronicznego i asynchronicznego.  
  
-   Tego samego żądania anulowania może proliferated do dowolnej liczby odbiorników.  
  
-   Deweloper asynchronicznego interfejsu API jest pełną kontrolę nad tego, czy można żądać anulowania i kiedy może obowiązywać.  
  
-   Kod, który wykorzystuje interfejs API może określić selektywnie wywołania asynchroniczne, które będzie propagowane żądań anulowania.  
  
## <a name="monitoring-progress"></a>Postęp monitorowania  
 Niektóre metody asynchronicznej uwidocznić postęp za pomocą interfejsu postępu, przekazywane do metody asynchronicznej.  Na przykład należy wziąć pod uwagę, że funkcja, która asynchronicznie pobiera ciągu tekstu, a po drodze zgłasza aktualizacji w toku, obejmujących procent do pobrania, które zostało ukończone w związku z tym daleko.  Taka metoda może być używane w aplikacji Windows Presentation Foundation (WPF) w następujący sposób:  
  
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
## <a name="using-the-built-in-task-based-combinators"></a>Za pomocą wbudowanych kombinacji opartych na zadaniach  
 <xref:System.Threading.Tasks> Przestrzeń nazw zawiera kilka metod tworzenia i pracy z zadaniami.  
  
### <a name="taskrun"></a>Task.Run  
 <xref:System.Threading.Tasks.Task> Klasy zawiera kilka <xref:System.Threading.Tasks.Task.Run%2A> metod, które pozwalają na łatwe odciążania pracę jako <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> do puli wątków, na przykład:  
  
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
  
 Niektóre z nich <xref:System.Threading.Tasks.Task.Run%2A> metod, takich jak <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> przeciążenia, istnieje jako skrót dla <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody.  Inne przeciążenia, takich jak <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, Włącz przy użyciu await Odciążone utworu, na przykład:  
  
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
  
 Takimi przeciążeniami są logicznie równoważne użyciu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody w połączeniu z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia w bibliotece zadań równoległych.  
  
### <a name="taskfromresult"></a>Task.FromResult  
 Użyj <xref:System.Threading.Tasks.Task.FromResult%2A> metoda w scenariuszach, w którym dane mogą być już dostępne i po prostu musi być zwracane przez metodę zwracającą zadanie podniesiony do <xref:System.Threading.Tasks.Task%601>:  
  
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
 Użyj <xref:System.Threading.Tasks.Task.WhenAll%2A> metoda asynchronicznie oczekiwania na wiele operacji asynchronicznych, które są reprezentowane jako zadania.  Metoda ma wiele przeciążeń, które obsługują zestaw zadań innych niż ogólne lub zestaw obsługuje technologię niejednolitego ogólnych zadań (na przykład asynchronicznie oczekuje na wiele operacji zwracającą typ void lub asynchronicznie oczekuje dla wielu metod, zwracając wartość gdzie Każda wartość może mieć inny typ) i jednolity zbiór zadań rodzajowych obsługujących (takie jak asynchronicznie oczekuje wielu `TResult`— metody zwracające typ).  
  
 Załóżmy, że użytkownik chce wysyłać wiadomości e-mail do wielu klientów. Użytkownik może nakładać się na wysyłanie wiadomości, więc nie oczekiwania na ukończenie przed wysłaniem następnego jednej wiadomości. Można również znaleźć się po zakończeniu operacji wysyłania i tego, czy wystąpiły błędy:  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 Ten kod nie obsługuje jawnie wyjątków, które mogą wystąpić, ale umożliwia wyjątki dostawały się z `await` w zadanie wynikowe z <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Aby obsłużyć wyjątki, można użyć kodu, takie jak następujące:  
  
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
  
 W tym przypadku jeśli żadnych operacji asynchronicznej zakończy się niepowodzeniem, wszystkie wyjątki zostaną skonsolidowane w w <xref:System.AggregateException> wyjątek, który jest przechowywany w <xref:System.Threading.Tasks.Task> zwrócone z <xref:System.Threading.Tasks.Task.WhenAll%2A> metody.  Jednak tylko jeden z tych wyjątków są rozprowadzane przez `await` — słowo kluczowe.  Jeśli chcesz sprawdzić wszystkie wyjątki, można napisać ponownie poprzedniego kodu w następujący sposób:  
  
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
  
 Rozważmy przykład pobierane jest kilka plików z sieci web asynchronicznie.  W takim przypadku wszystkie operacje asynchroniczne mają typy wyników jednorodnych i łatwo uzyskiwać dostęp do wyników:  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 Można użyć tych samych technik obsługi wyjątków, które omówiono w poprzednim scenariuszu zwracającą typ void:  
  
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
 Możesz użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda asynchronicznie czekać na co najmniej jeden wiele operacji asynchronicznych w postaci zadania do wykonania.  Ta metoda służy cztery główne przypadki użycia:  
  
-   Nadmiarowość: Operację wielokrotnie i wybierania odpowiedniego kończące się pierwszym (na przykład, kontaktując się z wielu usług sieci web giełdowych generujących jeden wynik i wybierania odpowiedniego kończące najszybsza).  
  
-   Z przeplotem: Uruchamianie wielu operacji oczekiwania na wszystkich z nich, aby zakończyć, a ich przetwarzania, po ich zakończeniu.  
  
-   Ograniczanie: Umożliwiając dodatkowych operacji w celu rozpoczęcia po zakończeniu przez inne osoby.  Jest to rozszerzenie interleaving scenariusza.  
  
-   Wczesne podejmowano: na przykład operacji reprezentowany przez t1 zadania mogą być grupowane w <xref:System.Threading.Tasks.Task.WhenAny%2A> zadania za pomocą innej t2 zadań, a także możesz poczekać <xref:System.Threading.Tasks.Task.WhenAny%2A> zadania. Zadanie t2 może reprezentować limit czasu anulowania i/lub inne sygnał, który powoduje, że <xref:System.Threading.Tasks.Task.WhenAny%2A> zadań do wykonania przed zakończeniem t1.  
  
#### <a name="redundancy"></a>Nadmiarowość  
 Należy rozważyć przypadek, w której chcesz podjąć decyzję o tym, czy na kupowaniu akcji.  Istnieje kilka usług sieci web podstawowe zalecenia, którym ufasz, ale w zależności od obciążenia dziennego każda usługa może wystąpić powolnych w różnym czasie.  Możesz użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metody, aby otrzymać powiadomienie po zakończeniu każdej operacji:  
  
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
  
 W odróżnieniu od <xref:System.Threading.Tasks.Task.WhenAll%2A>, która zwraca nieopakowane wyniki wszystkich zadań, które zostało ukończone pomyślnie, <xref:System.Threading.Tasks.Task.WhenAny%2A> zwraca zadanie, które zakończona. Jeśli zadanie zakończy się niepowodzeniem, należy wiedzieć, że nie powiodło się, a jeśli zadanie zakończy się powodzeniem, ważne jest, aby wiedzieć, które zadanie wartość zwracana jest skojarzona z.  Dlatego należy dostęp do wyniku zwróconego zadania lub dodatkowo await, jak pokazano w tym przykładzie.  
  
 Podobnie jak w przypadku <xref:System.Threading.Tasks.Task.WhenAll%2A>, muszą być w stanie obsłużyć wyjątki.  Ponieważ pojawi się ponownie ukończonego zadania, może poczekać zwracane zadanie propagacji, błędy i `try/catch` ich odpowiednio; na przykład:  
  
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
  
 Ponadto nawet jeśli pierwsze zadanie zakończy się pomyślnie, kolejne zadania może zakończyć się niepowodzeniem.  W tym momencie masz kilka opcji związanych z wyjątkami: Możesz poczekać, aż uruchomionego zadania zostały wykonane, w którym to przypadku należy użyć <xref:System.Threading.Tasks.Task.WhenAll%2A> metody lub możesz zdecydować, czy wszystkie wyjątki są ważne i musi być zalogowany.  W tym celu można użyć kontynuacji, aby otrzymać powiadomienie, gdy zadania zostaną zakończone asynchronicznie:  
  
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
  
 a nawet:  
  
```  
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
  
 Na koniec można anulować pozostałe operacje:  
  
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
  
#### <a name="interleaving"></a>Z przeplotem  
 Należy rozważyć przypadek, gdzie jesteś pobierania obrazów z sieci web i przetwarzanie każdego obrazu (na przykład dodawanie obrazu do kontrolki interfejsu użytkownika).  Należy wykonać przetwarzanie sekwencyjnie w wątku interfejsu użytkownika, ale chcesz pobrać obrazów jako równocześnie, jak to możliwe. Ponadto, użytkownik nie chce wstrzymać Dodawanie obrazów do Interfejsu użytkownika, dopóki wszystkie pobraniu — mają zostać dodane po ich zakończeniu:  
  
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
  
 Można również stosować z przeplotem do scenariusza, który obejmuje przetwarzanie wymaga dużej mocy obliczeniowej na <xref:System.Threading.ThreadPool> obrazów pobrane; na przykład:  
  
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
  
#### <a name="throttling"></a>Dławienie  
 Należy wziąć pod uwagę przykład interleaving, chyba że użytkownik jest pobierany tak wiele obrazów, plików do pobrania trzeba ograniczenia; na przykład chcesz określoną liczbę plików do pobrania ma być wykonywana równolegle. Aby to osiągnąć, można uruchomić podzestaw operacji asynchronicznych.  Po zakończeniu operacji, można zacząć dodatkowych operacji w celu ich miejsce:  
  
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
  
#### <a name="early-bailout"></a>Wczesne podejmowano  
 Należy wziąć pod uwagę, że czekasz asynchronicznie operacji do wykonania podczas jednoczesnego odpowiedzi na żądanie anulowania przez użytkownika (na przykład użytkownik kliknął przycisk Anuluj). Poniższy kod ilustruje ten scenariusz:  
  
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
  
 Ta implementacja włączające interfejsu użytkownika, jak najszybciej podjąć decyzję o poręczenie, ale nie anuluje podstawowych operacji asynchronicznych.  Inną alternatywą jest anulowania oczekujących operacji w przypadku podjęcia decyzji o poręczenie, ale nie przywraca interfejsu użytkownika do momentu faktycznie zakończeniu potencjalnie ze względu na kończenie wcześnie ze względu na żądanie anulowania operacji:  
  
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
  
 Innym przykładem wczesne podejmowano polega na użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A> metody w połączeniu z <xref:System.Threading.Tasks.Task.Delay%2A> metodę, zgodnie z opisem w następnej sekcji.  
  
### <a name="taskdelay"></a>Task.Delay  
 Możesz użyć <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metodę, aby wprowadzić wstrzymuje działanie do wykonania metody asynchronicznej.  Jest to przydatne dla wielu rodzajów funkcje, w tym tworzenie pętli sondowania i opóźnienia obsługę uprzednio ustalonym czasie dane wejściowe użytkownika.  <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda może być również przydatne w połączeniu z <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> dla implementacji przekroczeń limitu czasu na czeka.  
  
 Jeśli zadanie, które jest częścią większej operację asynchroniczną (na przykład usługi sieci web platformy ASP.NET) trwa zbyt długo, operację ogólną może to spowodować obniżenie, zwłaszcza, jeśli nie jest on nigdy nie zakończyć.  Z tego powodu jest ważne móc limit czasu podczas oczekiwania na operację asynchroniczną.  Synchronicznej <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody akceptować wartości limitu czasu, ale odpowiedni <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> i wymienionych wcześniej <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>nie metody.  Zamiast tego można użyć <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> w połączeniu, aby zaimplementować upływu limitu czasu.  
  
 Na przykład w aplikacji interfejsu użytkownika, załóżmy, że chcesz pobrać obraz i Wyłącz interfejs użytkownika podczas pobierania obrazu. Jednak jeśli pobieranie trwa zbyt długo, chcesz ponownie włączyć interfejs użytkownika i odrzucić pliki do pobrania:  
  
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
  
 To samo dotyczy wiele plików do pobrania, ponieważ <xref:System.Threading.Tasks.Task.WhenAll%2A> zwraca klasę task:  
  
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
  
## <a name="building-task-based-combinators"></a>Tworzenie metody opartego na zadaniach  
 Ponieważ zadanie jest w stanie całkowicie reprezentuje operację asynchroniczną i synchroniczne i asynchroniczne możliwości dołączania za pomocą operacji, podczas pobierania wyników i tak dalej, możesz tworzyć przydatne bibliotek kombinacji są metody, które tworzą zadania tworzenie większych wzorców.  Zgodnie z opisem w poprzedniej sekcji, program .NET Framework zawiera kilka wbudowanych kombinacji, ale możesz również tworzyć własne. Poniższe sekcje zawierają kilka przykładów potencjalnych przedsięwzięciu combinator metody i typy.  
  
### <a name="retryonfault"></a>RetryOnFault  
 W wielu sytuacjach można ponowić próbę wykonania operacji, jeśli poprzednia próba nie powiedzie się.  Dla kodu synchronicznego, możesz utworzyć metodę pomocnika takich jak `RetryOnFault` w poniższym przykładzie w tym celu:  
  
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
  
 Możesz tworzyć metody pomocnika prawie identyczne dla asynchronicznych operacji, które są implementowane przez NACIŚNIĘCIE i dlatego zwracają zadania:  
  
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
  
 Można następnie użyć tym przedsięwzięciu combinator do zakodowania ponownych prób w aplikacji logiki... na przykład:  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 Można rozszerzyć `RetryOnFault` działać dalej. Na przykład funkcja może akceptować innego `Func<Task>` , zostanie wywołany, między kolejnymi próbami do określenia, kiedy i spróbuj wykonać operację ponownie, na przykład:  
  
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
  
 Można następnie użyć funkcji w następujący sposób czekać na chwilę przed ponowieniem próby wykonania operacji:  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a>NeedOnlyOne  
 Czasami możesz korzystać z zalet nadmiarowość, aby zwiększyć opóźnienie i szanse na powodzenie operacji.  Należy wziąć pod uwagę wiele usług sieci web, które zapewniają notowań giełdowych, ale o różnych porach dnia, każda usługa może dostarczyć różne poziomy jakości i czasów odpowiedzi.  Radzenia sobie z tymi zmianami, może wysyłać żądania do wszystkich usług sieci web i tak szybko, jak uzyskać odpowiedzi z jednej, anulowanie pozostałych żądań.  Możesz zaimplementować funkcji pomocnika, aby ułatwić zaimplementować ten wspólny wzorzec uruchamianie wielu operacji, oczekiwania, a następnie anulować pozostałe. `NeedOnlyOne` Funkcji w poniższym przykładzie przedstawiono w tym scenariuszu:  
  
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
 Brak potencjalny problem z wydajnością przy użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A> metody w celu obsługi interleaving scenariusz, podczas pracy z bardzo dużych zestawów zadań.  Każde wywołanie <xref:System.Threading.Tasks.Task.WhenAny%2A> wyniki w zarejestrowanej za pomocą każde zadanie kontynuacji. N liczbę zadań powoduje to kontynuacji O(N2) utworzone w okresie istnienia interleaving operacji.  Jeśli pracujesz z dużym zestawem zadań, możesz użyć kombinatorem (`Interleaved` w poniższym przykładzie) Aby rozwiązać problem z wydajnością:  
  
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
  
 Przedsięwzięciu combinator można następnie użyć do przetwarzania wyników zadania po ich zakończeniu; na przykład:  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a>WhenAllOrFirstException  
 W niektórych scenariuszach dotyczących punktowy/zbieranie możesz chcieć poczekaj, aż wszystkie zadania w zestawie, chyba że jeden z nich błędów, w którym to przypadku chcesz zatrzymać czekających zaraz po wystąpieniu wyjątku.  Można osiągnąć, za pomocą metody przedsięwzięciu combinator takich jak `WhenAllOrFirstException` w następującym przykładzie:  
  
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
  
## <a name="building-task-based-data-structures"></a>Struktury danych oparta na zadaniach tworzenia  
 Oprócz możliwości tworzenia niestandardowej metody opartego na zadaniach, mających struktury danych w <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> reprezentujący wyniki operacji asynchronicznej i niezbędne synchronizacji połączyć się z nim sprawia, że bardzo zaawansowany Wpisz, na której można utworzyć struktury danych niestandardowych, które ma być używany w scenariuszach asynchronicznego.  
  
### <a name="asynccache"></a>AsyncCache  
 Jednym ważnym aspektem zadaniem jest, czy jego może można przekazać do wielu odbiorców, z których mogą oczekiwać, zarejestruj kontynuacje za ich pomocą uzyskać jego wynik lub wyjątki (w przypadku właściwości <xref:System.Threading.Tasks.Task%601>), i tak dalej.  To sprawia, że <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> doskonale nadaje się do użycia w asynchronicznej infrastruktury buforowania.  Oto przykład małego, ale zaawansowanych asynchronicznego pamięci podręcznej skompilowane na <xref:System.Threading.Tasks.Task%601>:  
  
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
  
 [AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) jako obiekt delegowany do jej konstruktora klasy akceptuje funkcji, która przyjmuje `TKey` i zwraca <xref:System.Threading.Tasks.Task%601>.  Wszelkie wartości wcześniej używanych z pamięci podręcznej są przechowywane w wewnętrznego słownika i `AsyncCache` gwarantuje, że tylko jedno zadanie jest generowany na klucz, nawet wtedy, gdy pamięć podręczna jest uzyskiwany współbieżnie.  
  
 Na przykład można utworzyć pamięć podręczną pobranych stron sieci web:  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 Następnie można użyć tej pamięci podręcznej w metodach asynchronicznych, zawsze, gdy potrzebujesz zawartość strony sieci web. `AsyncCache` Klasy gwarantuje, czy są pobierane jako kilka stron, jak to możliwe i pamięci podręczne wyniki.  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection  
 Zadania umożliwia również tworzenie struktur danych koordynacji działań asynchronicznych.  Jednym z wzorców klasycznego równoległe projektu należy wziąć pod uwagę: producenta i odbiorcy.  W tym wzorcu producentów Generowanie danych, które jest używane przez konsumentów i producentów i konsumentów mogą być wykonywane równolegle. Na przykład Odbiorca przetwarza pozycji 1, który wcześniej został wygenerowany przez producenta, który jest teraz tworzenie pozycji 2.  Wzorzec producenta i odbiorcy niezmiennie wymaga niektórych elementów struktury danych do przechowywania pracy utworzony przez producentów tak, aby konsumenci mogą otrzymać powiadomienie o nowe dane i znaleźć go, jeśli jest dostępna.  
  
 Oto prosta struktura danych utworzonych na szczycie zadań umożliwiającą metod asynchronicznych, które ma być używany jako producentów i konsumentów:  
  
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
  
 Za pomocą tej struktury danych w miejscu można napisać kod, takie jak następujące:  
  
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
  
 <xref:System.Threading.Tasks.Dataflow> Przestrzeń nazw zawiera <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typ, który można użyć w podobny sposób, ale bez konieczności tworzenia niestandardowej kolekcji typów:  
  
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
>  <xref:System.Threading.Tasks.Dataflow> Przestrzeni nazw jest dostępna w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] za pośrednictwem **NuGet**. Aby zainstalować zestaw, który zawiera <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw, otwórz projekt w programie [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wybierz **Zarządzaj pakietami NuGet** z menu projektu i wyszukaj w trybie online pakiet Microsoft.Tpl.Dataflow.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
- [Implementowanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
- [Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
