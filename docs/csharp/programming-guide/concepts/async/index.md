---
title: Programowanie asynchroniczne z async i await (C#)
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 482b77c7dd151dc454082b0def7843fdb0798260
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297442"
---
# <a name="asynchronous-programming-with-async-and-await-c"></a>Programowanie asynchroniczne z async i await (C#)
Możesz uniknąć problemów z wydajnością i poprawić ogólny czas odpowiedzi aplikacji, stosując programowanie asynchroniczne. Jednak tradycyjne techniki pisania aplikacji asynchronicznych mogą być skomplikowane, przez co trudne do pisania, debugowania i konserwacji.  
  
[C# 5](../../../whats-new/index.md#previous-versions) wprowadzone uproszczone podejście, programowanie async, wykorzystującego obsługi komunikacji asynchronicznej w .NET Framework 4.5 lub nowszym, .NET Core i środowiska wykonawczego Windows. Kompilator wykonuje trudną pracę, którą kiedyś wykonywał programista, a aplikacja zachowuje strukturę logiczną przypominającą kod synchroniczny. W efekcie masz wszystkie korzyści wynikające z programowania asynchronicznego przy ułamkowym nakładzie pracy.  
  
Ten temat zawiera omówienie, kiedy i jak stosować programowanie async oraz zawiera łącza do tematów zawierających szczegółowe informacje oraz przykłady.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> Programowanie Async poprawia czas odpowiedzi  
 Asynchroniczność jest istotna dla działań, które mogą powodować blokowanie, takich jak dostęp w sieci web. Dostęp do zasobów sieci Web bywa powolny lub opóźniony. Jeśli takie działanie jest zablokowane w procesie synchronicznym, cała aplikacji musi czekać. W procesie asynchronicznym aplikacja może kontynuować wykonywanie innych zadań, które nie są zależne od zasobów sieci Web, do momentu zakończeniem zadania mogącego powodować blokowanie.  
  
 W poniższej tabeli przedstawiono typowe obszary, w których programowanie asynchroniczne poprawia czas odpowiedzi. Wymienione interfejsy API .NET, środowisko wykonawcze Windows zawierają metody, które obsługują programowanie asynchroniczne.  
  
| Obszar aplikacji    | Typy .NET przy użyciu metod asynchronicznych     | Typy środowiska wykonawczego Windows za pomocą metod asynchronicznych  |
|---------------------|-----------------------------------|-------------------------------------------|
|Web access|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Praca z plikami|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|  
|Praca z obrazami||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|  
|Programowanie WCF|[Operacje synchroniczne i asynchroniczne](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||  
  
Asynchroniczność okazuje się szczególnie cenna w przypadku aplikacji, które mają dostęp do wątku interfejsu użytkownika, ponieważ wszystkie działania związane z interfejsem użytkownika korzystają zazwyczaj z jednego wątku. Jeśli w aplikacji synchronicznej jest zablokowany jakikolwiek proces, zablokowane są wszystkie procesy. Aplikacja przestanie odpowiadać i możesz dojść do wniosku, że uległa awarii, a tymczasem może po prostu być w stanie oczekiwania.  
  
 Kiedy używasz metod asynchronicznych, aplikacja dalej odpowiada interfejsowi użytkownika. Możesz przykładowo zmienić rozmiar lub zminimalizować aplikację lub możesz ją zamknąć, jeżeli nie chcesz czekać aż zakończy zadanie.  
  
 Podejście async oferuje również odpowiednik automatycznego przejścia do listy opcji do wybrania przy projektowaniu operacji asynchronicznych. Oznacza to, że można korzystać z wszystkich zalet tradycyjnego programowania asynchronicznego, ale przy znacznie mniejszym nakładzie pracy programisty.  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Metody asynchroniczne są łatwiejsze do zapisu  
 [Async](../../../../csharp/language-reference/keywords/async.md) i [await](../../../../csharp/language-reference/keywords/await.md) słowa kluczowe w języku C# to jądro programowania asynchronicznego. Za pomocą tych dwóch słów kluczowych, można użyć zasobów .NET Framework, .NET Core lub środowiska wykonawczego Windows, do tworzenia metody asynchronicznej niemal jako prosty jak przy tworzeniu metody synchronicznej. Metody asynchroniczne definiowane za pomocą `async` — słowo kluczowe są określane jako *metod asynchronicznych*.  
  
 W poniższym przykładzie przedstawiono metodę async. Prawie wszystko w kodzie powinno wyglądać znajomo. Komentarze wywołują funkcje dodawane przez użytkownika w celu uzyskania asynchroniczności.  
  
 Można znaleźć pełny Windows Presentation Foundation (WPF) przykładowy plik na końcu tego tematu i możesz pobrać próbkę z [przykład Async: przykład z "Programowania asynchronicznego z Async i Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
// Three things to note in the signature:  
//  - The method has an async modifier.   
//  - The return type is Task or Task<T>. (See "Return Types" section.)  
//    Here, it is Task<int> because the return statement returns an integer.  
//  - The method name ends in "Async."  
async Task<int> AccessTheWebAsync()  
{   
    // You need to add a reference to System.Net.Http to declare client.  
    HttpClient client = new HttpClient();  
  
    // GetStringAsync returns a Task<string>. That means that when you await the  
    // task you'll get a string (urlContents).  
    Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");  
  
    // You can do work here that doesn't rely on the string from GetStringAsync.  
    DoIndependentWork();  
  
    // The await operator suspends AccessTheWebAsync.  
    //  - AccessTheWebAsync can't continue until getStringTask is complete.  
    //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
    //  - Control resumes here when getStringTask is complete.   
    //  - The await operator then retrieves the string result from getStringTask.  
    string urlContents = await getStringTask;  
  
    // The return statement specifies an integer result.  
    // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
    return urlContents.Length;  
}  
```  
  
 Jeśli `AccessTheWebAsync` nie ma żadnych działań do wykonania pomiędzy wywołaniem `GetStringAsync` i oczekuje na jego zakończenie, można uprościć kod, realizując wywołanie i Oczekiwanie w następującej pojedynczej instrukcji.  
  
```csharp  
string urlContents = await client.GetStringAsync();  
```  
 
Poniższy opis podsumowuje, co sprawia, że poprzedni przykład jest metodą asynchroniczną.  
  
-   Podpis metody zawiera `async` modyfikator.  
  
-   Nazwa metody async kończy się zwyczajowo sufiksem „Async”.  
  
-   Zwracany typ może być jednym z następujących:  
  
    -   <xref:System.Threading.Tasks.Task%601> Jeśli metoda zawiera instrukcję return, w której operator ma typ `TResult`.  
  
    -   <xref:System.Threading.Tasks.Task> Jeśli metoda nie zawiera instrukcji return lub zawiera instrukcję return bez argumentu operacji.  
  
    -   `void` Jeśli piszesz obsługę zdarzeń async.  

    -   Typ, który ma `GetAwaiter` — metoda (rozpoczynający się znakami języka C# 7.0).
  
     Aby uzyskać więcej informacji, zobacz [Return Types i parametry](#BKMK_ReturnTypesandParameters) sekcji.  
  
-   Metoda zazwyczaj zawiera co najmniej jedno wyrażenie „await”, które oznacza punkt, w którym metoda nie może kontynuować pracy do czasu ukończenia operacji asynchronicznej. W tym czasie metoda jest zawieszona, a sterowanie powraca do obiektu wywołującego metodę. Następna sekcji tego tematu przedstawia, co się dzieje w punkcie zawieszenia.  
  
 W metodzie asynchronicznej używasz podanych słów kluczowych i typów w celu wskazania, co chcesz zrobić, a kompilator zajmie się resztą, w tym śledzeniem tego, co musi się zdarzyć, gdy sterowanie powraca do punktu oczekiwania w metodzie zawieszonej. Niektóre procesy, takie jak pętle i obsługa wyjątków, mogą być trudne do obsłużenia w tradycyjnym kodzie asynchronicznym. W metodzie asynchronicznej wpisujesz te elementy podobnie jak w rozwiązaniu synchronicznym i problem rozwiązany.  
  
 Aby uzyskać więcej informacji dotyczących asynchroniczności w poprzednich wersjach programu .NET Framework, zobacz [TPL i tradycyjnym .NET Framework Asynchronous Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Co się dzieje w metodzie async  
 Ważne jest, aby rozumieć programowanie asynchroniczne jako przepływ sterowania od metody do metody. Poniższy diagram ilustruje ten proces.  
  
 ![Śledzenie programu async](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Liczby w diagramie odpowiadają poniższym krokom.  
  
1.  Program obsługi zdarzeń wywołuje i czeka `AccessTheWebAsync` metody asynchronicznej.  
  
2.  `AccessTheWebAsync` Tworzy <xref:System.Net.Http.HttpClient> wystąpienie i wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronicznej metody do pobierania zawartości witryny sieci Web jako ciąg.  
  
3.  Coś się dzieje w `GetStringAsync` , co wstrzymuje jej postęp. Być może metoda musi czekać na pobranie strony internetowej lub inne działanie blokujące. Aby uniknąć blokowania zasobów,, `GetStringAsync` oddaje kontrole wywołującemu, `AccessTheWebAsync`.  
  
     `GetStringAsync` Zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest ciągiem, a `AccessTheWebAsync` przypisuje zadania `getStringTask` zmiennej. Zadanie przedstawia ciągły proces wywołania metody `GetStringAsync`, z zobowiązaniem utworzenia faktycznej wartości ciągu po ukończeniu pracy.  
  
4.  Ponieważ `getStringTask` nie miało jeszcze, `AccessTheWebAsync` można kontynuować inne prace, które nie są zależne od wyniku końcowego `GetStringAsync`. Że praca jest reprezentowana przez wywołanie metody synchronicznej `DoIndependentWork`.  
  
5.  `DoIndependentWork` jest metodą synchroniczną, która działa i wraca do.  
  
6.  `AccessTheWebAsync` ma za mało pracy, która może wykonywać bez wyniku z `getStringTask`. `AccessTheWebAsync` dalej chce obliczyć i zwracać długość pobranego ciągu, ale metoda nie może obliczyć tej wartości dopóki metoda ma ciąg.  
  
     W związku z tym `AccessTheWebAsync` stosuje await operator, aby zawiesić postęp i oddać kontrolę do metody, która wywołała `AccessTheWebAsync`. `AccessTheWebAsync` Zwraca `Task<int>` do obiektu wywołującego. Zadanie przedstawia obietnicę utworzenia w wyniku liczby całkowitej, która jest długością pobranego ciągu.  
  
    > [!NOTE]
    >  Jeśli `GetStringAsync` (i w związku z tym `getStringTask`) zostanie zakończona, zanim `AccessTheWebAsync` czeka na jego, sterowanie pozostanie w `AccessTheWebAsync`. Wydatków, a następnie powrotu do `AccessTheWebAsync` zostałby zmarnowany, gdyby wywołany proces asynchroniczny (`getStringTask`) został już ukończony i `AccessTheWebSync` nie musiałby czekać na wynik końcowy.  
  
     Przetwarzanie wzorca jest kontynuowane wewnątrz elementu wywołującego (programu obsługi zdarzeń w tym przykładzie). Obiekt wywołujący może wykonywać inne czynności, które nie są zależne od wyników `AccessTheWebAsync` przed oczekiwaniem na wynik lub obiekt wywołujący może czekać natychmiast.   Program obsługi zdarzeń oczekuje na `AccessTheWebAsync`, i `AccessTheWebAsync` oczekuje na `GetStringAsync`.  
  
7.  `GetStringAsync` kończy i produkuje wynik w postaci ciągu. Wynikowy ciąg nie jest zwracany przez wywołanie `GetStringAsync` w taki sposób, jakiego można by oczekiwać. (Należy pamiętać, że metoda zwróciła już zadanie w kroku 3). Zamiast tego wynikowy ciąg jest zapisywany w zadaniu, które reprezentuje ukończenie metody, `getStringTask`. Operator "await" pobiera wyniki z `getStringTask`. Instrukcja przypisania przypisuje wynik pobrany `urlContents`.  
  
8.  Gdy `AccessTheWebAsync` ma wynik ciągu, metoda może obliczyć długość ciągu. Następnie praca `AccessTheWebAsync` jest również zakończona i czekający program obsługi zdarzenia może wznowić działanie. W pełnym przykładzie na końcu tematu można zobaczyć, że program obsługi zdarzeń pobiera i drukuje wynikową wartość długości.    
Jeśli dopiero zaczynasz przygodę z programowaniem asynchronicznym, zastanów się przez chwilę, jaka jest różnica między zachowaniem synchronicznym i asynchronicznym. Metoda synchroniczna kończy działanie, gdy praca jest zakończona (krok 5), natomiast metoda asynchroniczna zwraca wartość zadania, gdy jej praca jest zawieszona (kroki 3 i 6). Gdy metoda async ukończy pracę, zadanie jest oznaczane jako ukończone, a wynik, o ile istnieje, jest zapisywany w zadaniu.  
  
Aby uzyskać więcej informacji na temat formantów flow, zobacz [przepływ sterowania w programach Async (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> Metody async interfejsu API  
 Użytkownik może się zastanawiać, gdzie można znaleźć metody takie jak `GetStringAsync` które obsługują programowanie async. .NET Framework 4.5 lub nowszy i .NET Core zawierają wiele elementów członkowskich, które działają z `async` i `await`. Możesz je rozpoznać przyrostku "Async", która jest dołączana do nazwy elementu członkowskiego i ich typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Na przykład `System.IO.Stream` klasa zawiera metody <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, i <xref:System.IO.Stream.WriteAsync%2A> synchroniczne metody <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, i <xref:System.IO.Stream.Write%2A>.  
  
 Środowisko wykonawcze Windows zawiera również wiele metod, których można używać z `async` i `await` w aplikacji Windows. Aby uzyskać więcej informacji, zobacz [wątki i programowanie async](/windows/uwp/threading-async/) do tworzenia aplikacji platformy uniwersalnej systemu Windows, a [(aplikacje Windows Store) programowanie asynchroniczne](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) i [Szybki Start: wywołanie asynchroniczne API w języku C# lub Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) Jeśli używasz starszej wersji środowiska uruchomieniowego Windows.  
  
##  <a name="BKMK_Threads"></a> Wątki  
Metody async mają być operacjami niepowodującymi blokowania. `await` Wyrażenia w metodzie async nie blokuje bieżącego wątku, gdy oczekiwane zadanie jest uruchomione. Zamiast tego, wyrażenie rejestruje pozostałą część metody jako kontynuację i przekazuje sterowanie do obiektu wywołującego metody async.  
  
`async` i `await` słów kluczowych nie powodują dodatkowe wątki nie ma zostać utworzony. Metody komunikacji async nie wymagają wielowątkowości, ponieważ nie działają we własnym wątku. Metoda działa w bieżącym kontekście synchronizacji i używa czasu wątku, tylko wtedy, gdy jest aktywna. Możesz użyć <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> przenieść zadań intensywnie angażujących Procesor do wątku w tle, ale tło wątku nie pomóc procesu, który tylko oczekuje na wyniki staną się dostępne.  
  
Podejście async do programowania asynchronicznego jest preferowane prawie w każdym przypadku. W szczególności, to podejście jest lepsze niż <xref:System.ComponentModel.BackgroundWorker> klasy I/O-powiązane z operacji, ponieważ kod jest prostszy i nie masz zabezpieczyć się przed wyścigu. W połączeniu z <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody, programowanie async jest lepsze niż <xref:System.ComponentModel.BackgroundWorker> dla Procesora CPU, operacji ponieważ asynchroniczne programowanie oddziela szczegóły dotyczące koordynacji uruchomienia kodu z pracy `Task.Run` przesyła do puli wątków.  
  
##  <a name="BKMK_AsyncandAwait"></a> Async i await  
 Jeśli określisz, że metoda jest metodą asynchroniczną za pomocą [async](../../../../csharp/language-reference/keywords/async.md) modyfikator, włączysz następujące dwie możliwości.  
  
-   Można użyć oznaczonej metody asynchronicznej [await](../../../../csharp/language-reference/keywords/await.md) do wskazania punktów zawieszenia. `await` Operator informuje kompilator, że metoda async nie może kontynuować działania prowadzące do czasu zakończenia procesu asynchronicznego oczekiwane. W międzyczasie sterowanie powraca do obiektu wywołującego metodę async.  
  
     Zawieszenie metody async na `await` wyrażenie nie stanowi wyjścia z metody i `finally` bloki nie są wykonywane.  
  
-   Metoda oznaczona jako async sama może być oczekiwana przez metody, które ją wywołują.  
  
Metoda async zazwyczaj zawiera jeden lub więcej wystąpień `await` operatora, ale brak `await` wyrażeń nie powoduje błędu kompilatora. Jeśli metoda async nie używa `await` operator, aby oznaczyć punkt zawieszenia, metoda jest wykonywana jak metoda synchroniczna, pomimo `async` modyfikator. Kompilator generuje ostrzeżenia dla takich metod.  
  
 `async` i `await` są kontekstowymi słowami kluczowymi. Aby uzyskać więcej informacji i przykładów, zobacz następujący temat:  
  
-   [async](../../../../csharp/language-reference/keywords/async.md)  
  
-   [await](../../../../csharp/language-reference/keywords/await.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Typy zwracane i parametry  
Metoda asynchroniczna zwykle zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Wewnątrz metody asynchronicznej `await` operator jest stosowany do zadania, który jest zwracany z wywołania do innej metody async.  
  
Należy określić <xref:System.Threading.Tasks.Task%601> jako typ zwracany, jeśli metoda zawiera [zwracają](../../../../csharp/language-reference/keywords/return.md) instrukcję, która określa operandę typu `TResult`. 
  
Możesz użyć <xref:System.Threading.Tasks.Task> jako typ zwracany, jeśli metoda nie zawiera instrukcji return lub zawiera instrukcję return, która nie zwraca operandu.  

Począwszy od języka C# 7.0, można również określić inny typ zwracany, pod warunkiem, że zawiera typ `GetAwaiter` metody. <xref:System.Threading.Tasks.ValueTask%601> jest przykładem takiego typu. Jest on dostępny w [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) pakietu NuGet.
  
 W poniższym przykładzie pokazano, jak deklarować i wywoływać metodę zwracającą <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>.  
  
```csharp  
// Signature specifies Task<TResult>  
async Task<int> TaskOfTResult_MethodAsync()  
{  
    int hours;  
    // . . .  
    // Return statement specifies an integer result.  
    return hours;  
}  
  
// Calls to TaskOfTResult_MethodAsync  
Task<int> returnedTaskTResult = TaskOfTResult_MethodAsync();  
int intResult = await returnedTaskTResult;  
// or, in a single statement  
int intResult = await TaskOfTResult_MethodAsync();  
  
// Signature specifies Task  
async Task Task_MethodAsync()  
{  
    // . . .  
    // The method has no return statement.    
}  
  
// Calls to Task_MethodAsync  
Task returnedTask = Task_MethodAsync();  
await returnedTask;  
// or, in a single statement  
await Task_MethodAsync();  
```  
  
Każde zwracane zadanie reprezentuje zadanie pracy w toku. Zadanie zawiera informacje o stanie procesu asynchronicznego i, ostatecznie, albo ostatecznego wyniku procesu lub wyjątku, który zgłasza proces, jeśli się nie powiedzie.  
  
Metoda asynchroniczna może także zawierać `void` typ zwracany. Ten typ zwracany jest używany głównie do definiowania programów obsługi zdarzeń, gdzie `void` jest wymagany typ zwracany. Programy async obsługi zdarzeń często służą jako punkt wejścia dla programów async.  
  
Metoda asynchroniczna, która ma `void` zwrotu typu nie może być oczekiwany, a obiekt wywołujący metodę zwracającą typ void nie może przechwytywać wyjątków, które metoda wygeneruje.  
  
Nie można zadeklarować metody asynchronicznej [w](../../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../../csharp/language-reference/keywords/ref.md) lub [się](../../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów, ale metodę można wywołać metody, które mają takie parametry. Podobnie metody asynchronicznej nie może zwracać wartość przez odwołanie, mimo że można wywołać metody za pomocą ref wartości zwracane. 
  
Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md). Aby uzyskać więcej informacji dotyczących wyjątków CATCH w metodach asynchronicznych, zobacz [try-catch —](../../../../csharp/language-reference/keywords/try-catch.md). 
  
Asynchroniczne API w programowaniu Windows Runtime mieć jedną z następujących typów zwrotu, które są podobne do zadań:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, która odnosi się do <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, która odnosi się do <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
   
  
##  <a name="BKMK_NamingConvention"></a> Konwencje nazewnictwa  
 Umownie, dołączasz "Asynchroniczny" do nazw metod mających `async` modyfikator.  
  
 Można zignorować konwencję, gdy zdarzenie, klasa bazowa lub kontrakt interfejsu sugeruje inną nazwę. Na przykład nie należy zmieniać nazw wspólnej procedury obsługi zdarzeń, takich jak `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> Tematy pokrewne i przykłady (Visual Studio)  
  
|Tytuł|Opis|Przykład|  
|-----------|-----------------|------------|  
|[Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Przedstawia, w jaki sposób konwertować synchroniczne rozwiązanie WPF do asynchronicznego rozwiązania WPF. Ta aplikacja pobiera szereg witryn sieci Web.|[Próbka asynchroniczna: Dostęp do instruktażu sieci Web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Dodaje <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do poprzedniego przewodnika. Korzystanie z `WhenAll` rozpoczyna wszystkie akcje pobierania w tym samym czasie.||  
|[Porady: wiele żądań sieci Web równolegle za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ilustruje, jak uruchomić kilka zadań w tym samym czasie.|[Próbka asynchroniczna: Złożyć wiele żądań sieci Web równolegle](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Asynchroniczne typy zwracane (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)|Ilustruje typy zwracane przez metody async i wyjaśnia, kiedy poszczególne typy są odpowiednie.||  
|[Przepływ sterowania w programach Async (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)|Śledzi szczegółowo przepływ sterowania w serii wyrażeń await w programie asynchronicznym.|[Próbka asynchroniczna: Przepływ sterowania w aplikacjach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[Dostrajanie aplikacji Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Przedstawia, w jaki sposób dodać następujące funkcje do rozwiązania async:<br /><br /> -   [Anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich, po ich zakończeniu (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Próbka asynchroniczna: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Przedstawia, w jaki sposób obsługiwać przypadki, w których podczas działania uruchamiana jest ponownie aktywna operacja asynchroniczna.||  
|[WhenAny: Łączenie platformy .NET Framework i środowiska uruchomieniowego Windows](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)|Pokazuje, jak typy zadań w .NET Framework i IAsyncOperations w [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby można było używać <xref:System.Threading.Tasks.Task.WhenAny%2A> z [!INCLUDE[wrt](~/includes/wrt-md.md)] metody.|[Próbka Asynchroniczae: Pomostu między .NET i programem obsługi Windows (AsTask i WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|  
|Anulowanie asynchroniczne: łączenie platformy .NET Framework ze środowiskiem wykonawczym systemu Windows|Pokazuje, jak typy zadań w .NET Framework i IAsyncOperations w [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby można było używać <xref:System.Threading.CancellationTokenSource> z [!INCLUDE[wrt](~/includes/wrt-md.md)] metody.|[Próbka Asynchroniczae: Pomostu między .NET i programem obsługi Windows (AsTask i anulowania)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[Użycie Async do uzyskiwania dostępu do plików (C#)](../../../../csharp/programming-guide/concepts/async/using-async-for-file-access.md)|Wyświetla listę korzyści wynikających ze stosowania słów kluczowych async i await przy uzyskiwaniu dostępu do plików.||  
|[Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Opisano nowy wzorzec asynchronii w .NET Framework. Wzorzec jest oparty na <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> typów.||  
|[Asynchroniczne wideo w witrynie Channel 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Oferuje łącza do różnych plików wideo dotyczących programowania asynchronicznego.||  
  
##  <a name="BKMK_CompleteExample"></a> Kompletny przykład  
 Poniższy kod jest plik MainWindow.xaml.cs z aplikacji Windows Presentation Foundation (WPF), która w tym temacie omówiono. Możesz pobrać próbkę z [przykład Async: przykład z "Programowania asynchronicznego z Async i Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http;  
using System.Net.Http;  
  
namespace AsyncFirstExample  
{  
    public partial class MainWindow : Window  
    {  
        // Mark the event handler with async so you can use await in it.  
        private async void StartButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Call and await separately.  
            //Task<int> getLengthTask = AccessTheWebAsync();  
            //// You can do independent work here.  
            //int contentLength = await getLengthTask;  
  
            int contentLength = await AccessTheWebAsync();  
  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
        }  
  
        // Three things to note in the signature:  
        //  - The method has an async modifier.   
        //  - The return type is Task or Task<T>. (See "Return Types" section.)  
        //    Here, it is Task<int> because the return statement returns an integer.  
        //  - The method name ends in "Async."  
        async Task<int> AccessTheWebAsync()  
        {   
            // You need to add a reference to System.Net.Http to declare client.  
            HttpClient client = new HttpClient();  
  
            // GetStringAsync returns a Task<string>. That means that when you await the  
            // task you'll get a string (urlContents).  
            Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");  
  
            // You can do work here that doesn't rely on the string from GetStringAsync.  
            DoIndependentWork();  
  
            // The await operator suspends AccessTheWebAsync.  
            //  - AccessTheWebAsync can't continue until getStringTask is complete.  
            //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
            //  - Control resumes here when getStringTask is complete.   
            //  - The await operator then retrieves the string result from getStringTask.  
            string urlContents = await getStringTask;  
  
            // The return statement specifies an integer result.  
            // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
            return urlContents.Length;  
        }  
  
        void DoIndependentWork()  
        {  
            resultsTextBox.Text += "Working . . . . . . .\r\n";  
        }  
    }  
}  
  
// Sample Output:  
  
// Working . . . . . . .  
  
// Length of the downloaded string: 41564.  
```  
  
## <a name="see-also"></a>Zobacz też

- [async](../../../../csharp/language-reference/keywords/async.md)  
- [await](../../../../csharp/language-reference/keywords/await.md)  
- [Programowanie asynchroniczne](../../../../csharp/async.md)  
- [Async — omówienie](../../../../standard/async.md)  
