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
ms.openlocfilehash: f7fd03a43d8722e32f64dd9cbe2936301d6bd2f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579499"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Wykorzystywanie wzorca asynchronicznego opartego na zadaniach
Gdy używasz opartego na zadaniach asynchronicznej wzorca (TAP) do pracy z operacji asynchronicznych służy wywołań zwrotnych do osiągnięcia oczekiwania bez blokowania.  W przypadku zadań to odbywa się za pośrednictwem metody takie jak <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Obsługa komunikacji asynchronicznej opartych na języku ukrywa wywołania zwrotne zezwalając operacji asynchronicznych do dokumentów, w ramach przepływu sterowania normalne i kod wygenerowany przez kompilator obsługuje ten sam poziom interfejsu API.  
  
## <a name="suspending-execution-with-await"></a>Wstrzymywanie wykonywania z Await  
 Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], można użyć [await](~/docs/csharp/language-reference/keywords/await.md) — słowo kluczowe języka C# i [operatora Await](~/docs/visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic asynchronicznie oczekują na <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiektów. Gdy jest oczekiwanie na <xref:System.Threading.Tasks.Task>, `await` wyrażenie jest typu `void`. Gdy jest oczekiwanie na <xref:System.Threading.Tasks.Task%601>, `await` wyrażenie jest typu `TResult`. `await` Wyrażenie musi wystąpić w treści metody asynchronicznej. Aby uzyskać więcej informacji na temat języka C# i Visual Basic obsługuje w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobacz specyfikacje języka C# i Visual Basic.  
  
 W obszarze obejmuje funkcje await instaluje wywołanie zwrotne zadania za pomocą utrzymania.  To wywołanie zwrotne wznawia metod asynchronicznych w punkcie zawieszenia. Po wznowieniu metod asynchronicznych Jeśli oczekiwano operacja zakończyła się pomyślnie i został <xref:System.Threading.Tasks.Task%601>, jego `TResult` jest zwracany.  Jeśli <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> który oczekiwany zakończone w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu, <xref:System.OperationCanceledException> wyjątku.  Jeśli <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> który oczekiwany zakończone w <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu jest zwracany wyjątek, który spowodował błąd. A `Task` można błędów wyniku wiele wyjątków, ale tylko jeden z tych wyjątków są propagowane. Jednak <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> zwraca <xref:System.AggregateException> wyjątek, który zawiera wszystkie błędy.  
  
 Jeśli kontekst synchronizacji (<xref:System.Threading.SynchronizationContext> obiektu) jest skojarzony z wątkiem wykonywanej metody asynchronicznej w chwili zawieszenia (na przykład, jeśli <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> właściwość nie jest `null`), metoda asynchroniczna wznawia na tym tego samego kontekstu synchronizacji przy użyciu kontekstu <xref:System.Threading.SynchronizationContext.Post%2A> metody. W przeciwnym razie polega na harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler> obiektu) który były aktualne w chwili zawieszenia. Zazwyczaj jest to domyślny harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), który jest przeznaczony dla puli wątków. Ten harmonogram zadania określa, czy Oczekiwano operacji asynchronicznej powinien wznowić, gdy zakończy pracę, lub czy powinny zostać zaplanowane wznowienie. Domyślny harmonogram umożliwia zwykle kontynuacji do uruchamiania w wątku, który zakończył Oczekiwano operacji.  
  
 Po wywołaniu metody asynchronicznej synchronicznie wykonywania treści funkcji dopóki pierwsza await wyrażenia na oczekujący wystąpienie, które nie zostało jeszcze zakończone, w którym wywołanie zwraca do obiektu wywołującego. Jeśli metoda asynchroniczna nie zwraca `void`, <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiekt jest zwracany do reprezentowania trwającą obliczeń. W metodzie asynchronicznej niż void, jeśli instrukcja return lub jest osiągnięty koniec treści metody, zadanie zostanie ukończone w <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stan końcowy. Jeśli wystąpił nieobsługiwany wyjątek powoduje, że formant opuścić tekstu metody asynchronicznej, zadanie kończy się <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu. Jeśli ten wyjątek jest <xref:System.OperationCanceledException>, zamiast tego zadania kończy się na <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu. W ten sposób wynik lub wyjątek ostatecznie jest opublikowana.  
  
 Istnieje kilka ważnych zmian tego zachowania.  Ze względu na wydajność Jeśli zadanie zostało już ukończone w czasie zadania jest oczekiwane, formantu nie jest uzyskane i kontynuuje wykonywanie funkcji.  Ponadto wracając do oryginalnego kontekstu nie zawsze jest zamierzone zachowanie i może zostać zmieniona; jest to opisane bardziej szczegółowo w następnej sekcji.  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Konfigurowanie zawieszenia i wznowienia z wydajności i ConfigureAwait  
 Kilka metod zapewniają większą kontrolę nad wykonanie metody asynchronicznej. Na przykład można użyć <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metody wprowadzenie punktu yield do metod asynchronicznych:  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 Jest to równoważne asynchronicznie księgowej lub planowania bieżącego kontekstu.  
  
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
  
 Można również użyć <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metody dla lepszej kontroli nad zawieszenia i wznowienia w metody asynchronicznej.  Jak wspomniano wcześniej, domyślnie bieżącego kontekstu jest przechwytywany w momencie metody asynchronicznej jest wstrzymana, a tego kontekstu przechwyconych służy do wywoływania metody asynchronicznej kontynuacji po wznowieniu.  W wielu przypadkach to zachowanie dokładne, który ma.  W innych przypadkach może nie zależy Ci kontekstu kontynuacji, a można osiągnąć lepszą wydajność dzięki unikaniu takie stanowiska wstecz do oryginalnego kontekstu.  Aby włączyć tę opcję, należy użyć <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodę, aby poinformować operacji await nie do przechwytywania i wznowić w kontekście, ale do kontynuowania wykonywania wszędzie tam, gdzie ukończyć operację asynchroniczną, która jest oczekiwany:  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a>Anulowanie operacji asynchronicznej  
 Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], NACIŚNIJ metody, które obsługuje anulowania Podaj co najmniej jedno przeciążenie akceptuje token anulowania (<xref:System.Threading.CancellationToken> obiektu).  
  
 Token anulowania jest tworzony przez źródło token anulowania (<xref:System.Threading.CancellationTokenSource> obiektu).  Źródło <xref:System.Threading.CancellationTokenSource.Token%2A> właściwość zwraca token anulowania, który zostanie zasygnalizowane podczas źródła <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda jest wywoływana.  Na przykład, jeśli chcesz pobrać pojedyncza strona sieci Web i chcesz mieć możliwość anulowania operacji, należy utworzyć <xref:System.Threading.CancellationTokenSource> obiektów, Przekaż token jej do metody NACIŚNIJ, a następnie wywołać źródła <xref:System.Threading.CancellationTokenSource.Cancel%2A> metody, gdy wszystko jest gotowe do anulowania operacji:  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 Aby anulować wiele wywołań asynchronicznych, można przekazać tego samego tokenu do wszystkich wywołań:  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 Lub można przekazać tego samego tokenu do selektywnego podzbiór operacje:  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 Żądania anulowania można zainicjować z dowolnego wątku.  
  
 Można przekazać <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> wartość do dowolnej metody, która akceptuje token anulowania, aby wskazać, że anulowania nigdy nie będzie wymagane.  Powoduje to <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> właściwości do zwrócenia `false`, i odpowiednio zoptymalizować wywołaną metodę.  Do celów testowych można również przekazać token anulowania wstępnie anulowane, który zostanie uruchomiony przy użyciu konstruktora, który akceptuje wartość logiczna wskazująca, czy token powinna uruchomić się w stanie już anulowana lub nie można anulować.  
  
 Takie podejście do anulowania ma kilka zalet:  
  
-   Ten sam token anulowania można przekazać do dowolnej liczby operacji synchronicznego i asynchronicznego.  
  
-   Tym samym żądanie anulowania może proliferated na dowolną liczbę odbiorników.  
  
-   Deweloper asynchronicznego interfejsu API ma pełną kontrolę nad czy anulowania można zażądać i kiedy mogą zostać zastosowane.  
  
-   Kod, który wykorzystuje interfejs API selektywnie mogą określić wywołania asynchroniczne, które żądań anulowania będzie propagowane do.  
  
## <a name="monitoring-progress"></a>Postęp monitorowania  
 W przypadku niektórych metod asynchronicznych ujawnia postęp za pośrednictwem interfejsu postępu przekazany do metody asynchronicznej.  Na przykład należy rozważyć funkcja, która asynchronicznie pobiera ciąg tekstu i wzdłuż sposób zgłasza aktualizacje postępu, zawierające procent pobieranie, które zostało zakończone w związku z tym do tej pory.  Taka metoda może być używana w aplikacji Windows Presentation Foundation (WPF) w następujący sposób:  
  
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
## <a name="using-the-built-in-task-based-combinators"></a>Za pomocą wbudowanych Combinators opartego na zadaniach  
 <xref:System.Threading.Tasks> Przestrzeń nazw zawiera kilka metod tworzenia i pracy z zadaniami.  
  
### <a name="taskrun"></a>Task.Run  
 <xref:System.Threading.Tasks.Task> Klasy zawiera kilka <xref:System.Threading.Tasks.Task.Run%2A> metod, które pozwalają łatwo odciążania pracy jako <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> do puli wątków, na przykład:  
  
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
  
 Niektóre z nich <xref:System.Threading.Tasks.Task.Run%2A> metod, takich jak <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> przeciążenia, istnieje jako skrócona forma <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody.  Overloads innych, takie jak <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, Włącz można używać operatora await w ramach Odciążone pracy, na przykład:  
  
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
  
 Takie przeciążenia są logicznie równoważne użyciu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> w połączeniu z metody <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> — metoda rozszerzenia w bibliotece równoległych zadań.  
  
### <a name="taskfromresult"></a>Task.FromResult  
 Użyj <xref:System.Threading.Tasks.Task.FromResult%2A> metody w scenariuszach, w których dane mogą być już dostępne, a tylko musi zwracaną z metody umożliwiające zwracanie zadań unosiło do <xref:System.Threading.Tasks.Task%601>:  
  
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
 Użyj <xref:System.Threading.Tasks.Task.WhenAll%2A> metody asynchronicznie oczekiwania na wiele operacji asynchronicznych, które są reprezentowane jako zadania.  Metoda ma kilka przeciążeń, które obsługuje zestaw zadań nierodzajową lub zestawu niejednolitego ogólnych zadań (na przykład asynchronicznie oczekiwanie na wiele operacji zwracające typ void lub asynchronicznie oczekiwanie na wiele metod zwracających wartość gdzie Każda wartość może być innego typu) która obsługuje jednolitego zestaw ogólnych zadań (takich jak asynchronicznie oczekiwanie na wielu `TResult`-zwracanie metody).  
  
 Załóżmy, że chcesz wysyłać wiadomości e-mail do wielu klientów. Możesz mogą nakładać się na wysyłanie wiadomości, więc nie oczekiwania dla jednego komunikatu do wykonania przed wysłaniem następnego. Można również sprawdzić po ukończeniu operacji wysyłania i określa, czy wystąpiły błędy:  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 Ten kod nie jawnie obsługi wyjątków, które mogą wystąpić, ale umożliwia propagowanie poza wyjątkami `await` w zadaniu wynikowym z <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Do obsługi wyjątków, można użyć kodu, takie jak następujące:  
  
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
  
 W tym przypadku jeśli żadnej operacji asynchronicznych nie powiedzie się, wszystkie wyjątki zostaną skonsolidowane w w <xref:System.AggregateException> wyjątek, który jest przechowywany w <xref:System.Threading.Tasks.Task> zwracanego z <xref:System.Threading.Tasks.Task.WhenAll%2A> metody.  Jednak tylko jeden z tych wyjątków są propagowane przy `await` — słowo kluczowe.  Jeśli chcesz sprawdzić wszystkie wyjątki, poprzedni kod można przepisać w następujący sposób:  
  
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
  
 Zastanówmy się z przykładem asynchronicznie pobrania wiele plików w sieci web.  W takim przypadku wszystkich operacji asynchronicznych mają typy wyników jednorodne i łatwo uzyskać dostępu do wyników:  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 Można używać tych samych metod obsługi wyjątków, które omówiono w poprzednim scenariuszu zwracające typ void:  
  
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
 Można użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metody asynchronicznie oczekuje tylko jednego z wielu operacji asynchronicznych reprezentowane jako zadania do wykonania.  Ta metoda służy cztery przypadki użycia głównej:  
  
-   Nadmiarowość: Wykonywanie operacji wielokrotnie i wybierania odpowiedniego zakończeniu pierwszego (na przykład kontaktowania się z wielu usług sieci web giełdowych powodującymi jeden wynik i wybierania odpowiedniego kończące najszybsze).  
  
-   Z przeplotem: Uruchamianie wielu operacji i Oczekiwanie na ich zakończenie wszystkich, ale przetwarzanie ich w chwili zakończenia.  
  
-   Ograniczanie: Stosowanie dodatkowe operacje rozpocząć w innym zakończenia.  To rozszerzenie interleaving scenariusza.  
  
-   Wczesne podejmowano: na przykład operacji reprezentowany przez t1 zadania można grupować w <xref:System.Threading.Tasks.Task.WhenAny%2A> zadań z innym t2 zadań, a może czekać <xref:System.Threading.Tasks.Task.WhenAny%2A> zadań. Zadanie t2 może reprezentować limit czasu lub anulowania lub innych sygnał, który powoduje, że <xref:System.Threading.Tasks.Task.WhenAny%2A> zadań do wykonania przed zakończeniem t1.  
  
#### <a name="redundancy"></a>Nadmiarowość  
 Rozważmy, której chcesz podjęcie decyzji o tym, czy kupić zasobu.  Istnieje kilka usług sieci web standardowych zalecenie zaufanych, ale w zależności od obciążenia codzienne każdej usługi można przechodzili powolnych w różnym czasie.  Można użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metody, aby otrzymać powiadomienie po zakończeniu każdej operacji:  
  
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
  
 W odróżnieniu od <xref:System.Threading.Tasks.Task.WhenAll%2A>, które zwraca wyniki bez otoki wszystkich zadań, które ukończone pomyślnie, <xref:System.Threading.Tasks.Task.WhenAny%2A> zwraca zadania, które wykonane. Jeśli zadanie nie powiedzie się, należy wiedzieć, że nie powiodło się, a jeśli zadanie zakończy się powodzeniem, ważne jest, aby wiedzieć, które zadanie wartość zwracana jest skojarzony z.  Należy więc dostęp do wyniku zadania zwróconego lub dalsze await, jak pokazano na poniższym przykładzie.  
  
 Jak <xref:System.Threading.Tasks.Task.WhenAll%2A>, muszą być w stanie wyjątkami.  Ponieważ zostanie wyświetlony ponownie ukończonego zadania, można zdefiniować oczekiwania zadanie zwrócone błędy propagacji i `try/catch` ich odpowiednio; na przykład:  
  
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
  
 Ponadto nawet jeśli pierwsze zadanie zostało ukończone pomyślnie, kolejne zadania może się nie powieść.  W tym momencie możesz używać na kilka sposobów postępowania z wyjątkami: należy poczekać do czasu uruchomionego zadania zostały ukończone w takim przypadku można użyć <xref:System.Threading.Tasks.Task.WhenAll%2A> metody, lub można zdecydować, czy wszystkie wyjątki są ważne i muszą być rejestrowane.  W tym celu można użyć kontynuacje aby otrzymać powiadomienie po zakończeniu zadania asynchronicznie:  
  
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
  
#### <a name="interleaving"></a>Z przeplotem  
 Rozważmy przykład, gdzie jest pobieranie obrazów z sieci web i przetwarzania każdego obrazu (np. Dodawanie obrazu do formantu interfejsu użytkownika).  Musisz wykonać przetwarzania sekwencyjnie w wątku interfejsu użytkownika, ale chcesz pobrać obrazy jednocześnie jak to możliwe. Ponadto użytkownik nie chce utrzymanie Dodawanie obrazów do interfejsu użytkownika, dopóki wszystkie pobraniu — Aby dodać ich w chwili zakończenia:  
  
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
  
 Można także zastosować naprzemiennego wykonywania na potrzeby scenariusza, która obejmuje w praktyce znacznym przetwarzania <xref:System.Threading.ThreadPool> pobrany obrazów, np.:  
  
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
 Rozważmy przykład interleaving, z wyjątkiem tego, że użytkownik pobiera tak wiele obrazów, że ograniczenie; pliki do pobrania Możesz na przykład określoną liczbę pobrań wykonywane jednocześnie. Aby to osiągnąć, możesz uruchomić podzbiór operacji asynchronicznych.  Jak wykonać operacji, można uruchomić dodatkowe operacje ich odbywa się:  
  
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
 Należy wziąć pod uwagę, że czekasz asynchronicznie operacji do wykonania podczas jednocześnie odpowiedzi na żądanie anulowania przez użytkownika (na przykład użytkownik kliknął przycisk Anuluj). Poniższy kod ilustruje tego scenariusza:  
  
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
  
 Ta implementacja włączające interfejs użytkownika natychmiast podjąć decyzję o poręczenie, ale nie Anuluj podstawowych operacji asynchronicznych.  Alternatywą jest anulowania oczekujących operacji, jeśli zdecydujesz się poręczenie, ale nie przywrócić interfejs użytkownika do faktycznie pełną potencjalnie z powodu zakończenia wczesne ze względu na żądanie anulowania operacji:  
  
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
  
 Innym przykładem wczesne podejmowano polega na użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A> w połączeniu z metody <xref:System.Threading.Tasks.Task.Delay%2A> metody, zgodnie z opisem w następnej sekcji.  
  
### <a name="taskdelay"></a>Task.Delay  
 Można użyć <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metody wprowadzenie wstrzymuje działanie do wykonania metody asynchronicznej.  Jest to przydatne w przypadku wielu rodzajów funkcje, w tym tworzenie pętli sondowania i obsługi danych wejściowych użytkownika przez ustalonej czas opóźnienia.  <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda może być również przydatne w połączeniu z <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> dla wykonania przekroczeń limitu czasu na oczekiwanie.  
  
 Jeśli zadanie, które jest częścią większej operację asynchroniczną (na przykład usługi sieci web programu ASP.NET) trwa zbyt długo, ogólną operacji może pogorszyć, zwłaszcza, jeśli nie powiedzie się nigdy zakończyć.  Dlatego jest ważne można było upłynął limit czasu podczas oczekiwania na operację asynchroniczną.  Synchroniczne <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody zaakceptować wartości limitu czasu, ale odpowiadający mu <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> i to wymienione wcześniej <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>nie metody.  Zamiast tego można użyć <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> w połączeniu do zaimplementowania limit czasu.  
  
 Na przykład w aplikacji interfejsu użytkownika, załóżmy, że chcesz pobranie obrazu i wyłączyć interfejsu użytkownika podczas pobierania obrazu. Jednak jeśli pobieranie trwa zbyt długo, chcesz ponownie włączyć interfejsu użytkownika i odrzucić pobierania:  
  
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
  
 To samo dotyczy pobranie wielu materiałów, ponieważ <xref:System.Threading.Tasks.Task.WhenAll%2A> zwraca zadania:  
  
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
  
## <a name="building-task-based-combinators"></a>Tworzenie Combinators opartego na zadaniach  
 Ponieważ zadanie jest w stanie całkowicie reprezentują operację asynchroniczną i podaj synchroniczne i asynchroniczne możliwości łączenia z operacją, podczas pobierania wyników i tak dalej, można tworzyć przydatne bibliotek combinators tworzące zadań Tworzenie większej wzorce.  Zgodnie z opisem w poprzedniej sekcji, .NET Framework zawiera kilka wbudowanych combinators, ale można również tworzyć własne. Kilka przykładów potencjalnych metod kombinatorem i typów można znaleźć w poniższych sekcjach.  
  
### <a name="retryonfault"></a>RetryOnFault  
 W wielu sytuacjach możesz ponowić próbę wykonania operacji, jeśli poprzednia próba nie powiedzie się.  Synchroniczne kodu może zbudować metody pomocnika takich jak `RetryOnFault` w poniższym przykładzie w tym celu:  
  
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
  
 Można utworzyć metody pomocnika niemal identyczny dla asynchronicznych operacji, które są wykonywane przy wybierz, w związku z tym zwracać zadań:  
  
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
  
 Następnie można ten kombinatorem kodowanie ponownych prób do aplikacji logiki; na przykład:  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 Można rozszerzyć `RetryOnFault` więcej funkcji. Na przykład funkcja może akceptować innego `Func<Task>` który zostanie wywołany, między kolejnymi próbami do określenia, kiedy i spróbuj wykonać operację ponownie, np.:  
  
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
  
 Można następnie użyć funkcji w następujący sposób oczekiwania na chwilę przed ponowieniem operacji:  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a>NeedOnlyOne  
 Czasami użytkownik może korzystać z nadmiarowość, aby poprawić opóźnienia i prawdopodobieństwo powodzenia operacji.  Należy wziąć pod uwagę wiele usług sieci web, które zapewniają giełdowych, ale w różnych porach dnia, każda usługa może zapewnia różne poziomy jakości i czasy odpowiedzi.  Radzenia sobie z tymi zmianami, mogą wysyłać żądania do wszystkich usług sieci web i jak uzyskać odpowiedzi od jednego, Anuluj pozostałych żądań.  Można zaimplementować funkcji pomocnika, aby ułatwić implementacji tego wspólnego wzorca uruchamianie wielu operacji, oczekiwania i następnie anulowanie pozostałych. `NeedOnlyOne` Funkcji w poniższym przykładzie przedstawiono w tym scenariuszu:  
  
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
  
### <a name="interleaved-operations"></a>Operacje przeplotem  
 Brak potencjalny problem z wydajnością przy użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A> metody na potrzeby scenariusza interleaving podczas pracy z bardzo dużych zestawów zadań.  Co wywołanie <xref:System.Threading.Tasks.Task.WhenAny%2A> powoduje kontynuację jest zarejestrowany do każdego zadania. N liczbę zadań powoduje to kontynuacje O(N2) utworzona w okresie istnienia interleaving operacji.  Jeśli pracujesz z dużych zestawów zadań, można użyć kombinatorze (`Interleaved` w poniższym przykładzie) Aby rozwiązać problem z wydajnością:  
  
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
  
 Następnie można kombinatorem przetworzyć wyniki zadań w chwili zakończenia; na przykład:  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a>WhenAllOrFirstException  
 W pewnych sytuacjach punktowy/zbieranie możesz chcieć poczekaj, aż wszystkie zadania w zestawie, chyba że jeden z nich błędów, w którym to przypadku należy zatrzymać oczekuje się, gdy występuje wyjątek.  Można uzyskać, który za pomocą metody kombinatorem takich jak `WhenAllOrFirstException` w poniższym przykładzie:  
  
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
  
## <a name="building-task-based-data-structures"></a>Struktury danych oparty na zadaniach kompilowanie  
 Oprócz umożliwia tworzenie niestandardowych combinators opartego na zadaniach, mających struktury danych w <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> reprezentujący wyniki operacji asynchronicznej i synchronizacji niezbędne do przyłączenia z nim sprawia, że bardzo zaawansowane Wpisz, na której można utworzyć struktur danych niestandardowych można używać w scenariuszach asynchronicznego.  
  
### <a name="asynccache"></a>AsyncCache  
 Pobierz jedną istotnym elementem zadania jest, że jej może można przekazać do wielu klientów, z których mogą poczekać na jego kontynuacje rejestru, jego wynik lub wyjątki (w przypadku liczby <xref:System.Threading.Tasks.Task%601>) i tak dalej.  Dzięki temu <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> idealnie nadaje się do użycia w asynchronicznej infrastruktury buforowania.  Oto przykład małą, ale utworzona zaawansowanych asynchroniczne pamięć podręczna nad <xref:System.Threading.Tasks.Task%601>:  
  
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
  
 [AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) klasy akceptuje jak obiekt delegowany dla jego konstruktora funkcję, która przyjmuje `TKey` i zwraca <xref:System.Threading.Tasks.Task%601>.  Wszelkie wartości wcześniej używanych z pamięci podręcznej są przechowywane w słowniku wewnętrzny i `AsyncCache` gwarantuje, że tylko jedno zadanie jest generowany na klucz, nawet wtedy, gdy pamięć podręczna jest jednocześnie dostępny.  
  
 Można na przykład tworzenie pamięci podręcznej dla pobranego stron sieci web:  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 Następnie można użyć tej pamięci podręcznej w metod asynchronicznych przy każdym zawartości strony sieci web. `AsyncCache` Klasy gwarantuje, że jako możliwe i pamięci podręczne wyniki są pobierane jako kilka stron.  
  
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
 Zadania umożliwia również tworzenie struktur danych koordynacji działań asynchronicznego.  Weź pod uwagę jedną te wzorce projektowe równoległych klasycznego: producent/konsumenta.  W tym wzorcu producentów generować dane jest używane przez konsumentów, a producenci i konsumenci może działać równolegle. Na przykład konsumenta przetwarza element 1, który wcześniej został wygenerowany przez producenta, który jest teraz tworzenie pozycji 2.  Dla wzorca producent i konsument niezmiennie muszą niektóre struktury danych do przechowywania robocze tworzone przez producentów, dzięki czemu konsumentów może otrzymywać powiadomienia o nowych danych i znajdź go, jeśli jest dostępna.  
  
 W tym miejscu jest strukturą proste danych wbudowane zadania, która umożliwia metod asynchronicznych, które mają być używane jako producenci i konsumenci:  
  
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
  
 Z tej struktury danych w miejscu można napisać kod, takie jak następujące:  
  
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
  
 <xref:System.Threading.Tasks.Dataflow> Przestrzeń nazw zawiera <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typ, którego można użyć w podobny sposób, ale bez konieczności typ kolekcji niestandardowej kompilacji:  
  
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
>  <xref:System.Threading.Tasks.Dataflow> Przestrzeń nazw jest dostępna w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] za pośrednictwem **NuGet**. Aby zainstalować zestaw zawierający <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw, otwórz projekt w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wybierz **Zarządzaj pakietami NuGet** z menu projektu i wyszukaj w trybie online pakiet Microsoft.Tpl.Dataflow.  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Implementowanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
