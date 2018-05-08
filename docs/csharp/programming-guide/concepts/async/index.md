---
title: Programowanie asynchroniczne z async i await (C#)
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: b1797a6d37728021820f5dfa5c01a7ee0c972f1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronous-programming-with-async-and-await-c"></a>Programowanie asynchroniczne z async i await (C#)
Możesz uniknąć problemów z wydajnością i poprawić ogólny czas odpowiedzi aplikacji, stosując programowanie asynchroniczne. Jednak tradycyjne techniki pisania aplikacji asynchronicznych mogą być skomplikowane, przez co trudne do pisania, debugowania i konserwacji.  
  
[C# 5](../../../whats-new/index.md#previous-versions) wprowadzona metoda uproszczona, programowania asynchronicznego, wykorzystującego Obsługa komunikacji asynchronicznej w programie .NET Framework 4.5 i wyższych .NET Core i środowiska wykonawczego systemu Windows. Kompilator wykonuje trudną pracę, którą kiedyś wykonywał programista, a aplikacja zachowuje strukturę logiczną przypominającą kod synchroniczny. W efekcie masz wszystkie korzyści wynikające z programowania asynchronicznego przy ułamkowym nakładzie pracy.  
  
Ten temat zawiera omówienie, kiedy i jak stosować programowanie async oraz zawiera łącza do tematów zawierających szczegółowe informacje oraz przykłady.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> Asynchroniczne skraca czas odpowiedzi  
 Asynchrony jest istotne dla działań, które są potencjalnie blokowanie, takich jak dostęp w sieci web. Dostęp do zasobów sieci Web bywa powolny lub opóźniony. Jeśli takie działanie jest blokowany w procesie synchroniczne, cała aplikacja musi czekać. W procesie asynchronicznym aplikacja może kontynuować wykonywanie innych zadań, które nie są zależne od zasobów sieci Web, do momentu zakończeniem zadania mogącego powodować blokowanie.  
  
 W poniższej tabeli przedstawiono typowe obszary, w których programowanie asynchroniczne poprawia czas odpowiedzi. Interfejsy API na liście z usług .NET i środowiska wykonawczego systemu Windows zawiera metody, które obsługują programowanie asynchroniczne.  
  
| Obszar aplikacji    | Typy .NET i metod asynchronicznych     | Typy środowiska wykonawczego systemu Windows za pomocą metod asynchronicznych  |
|---------------------|-----------------------------------|-------------------------------------------|
|Web access|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Praca z plikami|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|  
|Praca z obrazami||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|  
|Programowanie WCF|[Operacje synchroniczne i asynchroniczne](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||  
  
Asynchroniczność okazuje się szczególnie cenna w przypadku aplikacji, które mają dostęp do wątku interfejsu użytkownika, ponieważ wszystkie działania związane z interfejsem użytkownika korzystają zazwyczaj z jednego wątku. Jeśli w aplikacji synchronicznej jest zablokowany jakikolwiek proces, zablokowane są wszystkie procesy. Aplikacja przestanie odpowiadać i możesz dojść do wniosku, że uległa awarii, a tymczasem może po prostu być w stanie oczekiwania.  
  
 Kiedy używasz metod asynchronicznych, aplikacja dalej odpowiada interfejsowi użytkownika. Możesz przykładowo zmienić rozmiar lub zminimalizować aplikację lub możesz ją zamknąć, jeżeli nie chcesz czekać aż zakończy zadanie.  
  
 Podejście async oferuje również odpowiednik automatycznego przejścia do listy opcji do wybrania przy projektowaniu operacji asynchronicznych. Oznacza to, że można korzystać z wszystkich zalet tradycyjnego programowania asynchronicznego, ale przy znacznie mniejszym nakładzie pracy programisty.  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Metody asynchroniczne są łatwiejsze do zapisu  
 [Async](../../../../csharp/language-reference/keywords/async.md) i [await](../../../../csharp/language-reference/keywords/await.md) słów kluczowych w języku C# są Puls programowania asynchronicznego. Za pomocą tych dwóch słów kluczowych, zasobów w programie .NET Framework, .NET Core lub środowiska uruchomieniowego systemu Windows służy również do niemal, jak łatwo utworzyć metoda synchroniczna tworzenia metody asynchronicznej. Metod asynchronicznych, które definiują przy użyciu `async` — słowo kluczowe są określane jako *metod asynchronicznych*.  
  
 W poniższym przykładzie przedstawiono metodę async. Prawie wszystko w kodzie powinno wyglądać znajomo. Komentarze wywołują funkcje dodawane przez użytkownika w celu uzyskania asynchroniczności.  
  
 Pełny plik przykładowy Windows Presentation Foundation (WPF) na końcu tego tematu można znaleźć i pobrać przykładowy z [próbki Async: przykład z "Asynchronicznego programowania z Async i Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
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
    Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
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
  
 Jeśli `AccessTheWebAsync` nie ma żadnej pracy, które można wykonać między wywoływaniem `GetStringAsync` i oczekujące na jego ukończenie, można uprościć kodu przez wywołanie i oczekuje w następujących jednej instrukcji.  
  
```csharp  
string urlContents = await client.GetStringAsync();  
```  
 
Poniższy opis podsumowuje, co sprawia, że poprzedni przykład jest metodą asynchroniczną.  
  
-   Podpis metody zawiera `async` modyfikator.  
  
-   Nazwa metody async kończy się zwyczajowo sufiksem „Async”.  
  
-   Zwracany typ może być jednym z następujących:  
  
    -   <xref:System.Threading.Tasks.Task%601> Jeśli metodę zawiera instrukcję return, w którym argument operacji ma typ `TResult`.  
  
    -   <xref:System.Threading.Tasks.Task> Jeśli stosowana metoda ma nie instrukcji return lub instrukcji return zawierającej nie operandu.  
  
    -   `void` Jeśli piszesz asynchronicznej obsługi zdarzeń.  

    -   Innego typu, który ma `GetAwaiter` — metoda (począwszy od wersji 7.0 C#).
  
     Aby uzyskać więcej informacji, zobacz [parametry i typy zwracać](#BKMK_ReturnTypesandParameters) sekcji.  
  
-   Metoda zazwyczaj zawiera co najmniej jedno wyrażenie „await”, które oznacza punkt, w którym metoda nie może kontynuować pracy do czasu ukończenia operacji asynchronicznej. W tym czasie metoda jest zawieszona, a sterowanie powraca do obiektu wywołującego metodę. Następna sekcji tego tematu przedstawia, co się dzieje w punkcie zawieszenia.  
  
 W metodzie asynchronicznej używasz podanych słów kluczowych i typów w celu wskazania, co chcesz zrobić, a kompilator zajmie się resztą, w tym śledzeniem tego, co musi się zdarzyć, gdy sterowanie powraca do punktu oczekiwania w metodzie zawieszonej. Niektóre procesy, takie jak pętle i obsługa wyjątków, mogą być trudne do obsłużenia w tradycyjnym kodzie asynchronicznym. W metodzie asynchronicznej wpisujesz te elementy podobnie jak w rozwiązaniu synchronicznym i problem rozwiązany.  
  
 Aby uzyskać więcej informacji na temat asynchrony w poprzednich wersjach programu .NET Framework, zobacz [TPL i tradycyjnych .NET Framework asynchronicznego programowania](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Co się stanie w metodzie async  
 Ważne jest, aby rozumieć programowanie asynchroniczne jako przepływ sterowania od metody do metody. Poniższy diagram ilustruje ten proces.  
  
 ![Śledzenie programu async](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Liczby w diagramie odpowiadają poniższym krokom.  
  
1.  Wywołuje program obsługi zdarzeń i oczekujące na `AccessTheWebAsync` metody asynchronicznej.  
  
2.  `AccessTheWebAsync` Tworzy <xref:System.Net.Http.HttpClient> wystąpienia i wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2A> metod asynchronicznych w celu pobrania zawartości witryny sieci Web jako ciąg.  
  
3.  Wydarzy się coś w `GetStringAsync` który wstrzymuje postępu. Być może metoda musi czekać na pobranie strony internetowej lub inne działanie blokujące. Aby uniknąć zablokowania zasobów, `GetStringAsync` daje formantu do swojego obiektu wywołującego `AccessTheWebAsync`.  
  
     `GetStringAsync` Zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest ciągiem, a `AccessTheWebAsync` przypisuje zadania do `getStringTask` zmiennej. Zadanie reprezentuje ciągły proces dla wywołania `GetStringAsync`, z zobowiązań wygenerowało rzeczywistą wartością ciągu, po zakończeniu pracy.  
  
4.  Ponieważ `getStringTask` nie zostały jeszcze, oczekiwane `AccessTheWebAsync` można kontynuować inne zadania, które nie są zależne od wyniku końcowego z `GetStringAsync`. Czy praca jest reprezentowana przez wywołanie do metody synchroniczne `DoIndependentWork`.  
  
5.  `DoIndependentWork` Metoda synchroniczna nie jego pracy i zwraca go do swojego obiektu wywołującego jest.  
  
6.  `AccessTheWebAsync` Zabrakło pracy, który można zrobić bez wyników z `getStringTask`. `AccessTheWebAsync` dalej chce obliczania i zwraca długość ciągu pobrany, ale metoda nie może obliczyć tę wartość, dopóki metoda ma ciąg.  
  
     W związku z tym `AccessTheWebAsync` używa operatora await, aby zawiesić jego postęp i uzyskanie formantu do metody, która wywołuje `AccessTheWebAsync`. `AccessTheWebAsync` Zwraca `Task<int>` do obiektu wywołującego. Zadanie przedstawia obietnicę utworzenia w wyniku liczby całkowitej, która jest długością pobranego ciągu.  
  
    > [!NOTE]
    >  Jeśli `GetStringAsync` (i w związku z tym `getStringTask`) została ukończona przed `AccessTheWebAsync` oczekujące na jego sterowania pozostanie w `AccessTheWebAsync`. Wydatków wstrzymywania i następnie zwracany do `AccessTheWebAsync` może występować, jeśli proces asynchroniczny wywoływanego (`getStringTask`) zostało już ukończone i `AccessTheWebSync` nie musi czekać na wynik końcowy.  
  
     Przetwarzanie wzorca jest kontynuowane wewnątrz elementu wywołującego (programu obsługi zdarzeń w tym przykładzie). Obiekt wywołujący może wykonywanie innych zadań, które nie są zależne od wyników z `AccessTheWebAsync` przed oczekiwanie na wynik lub obiekt wywołujący może poczekać na natychmiast.   Program obsługi zdarzeń oczekuje na `AccessTheWebAsync`, i `AccessTheWebAsync` oczekuje na `GetStringAsync`.  
  
7.  `GetStringAsync` kończy i zwraca wynik ciągu. Wynik ciąg nie jest zwrócony przez wywołanie `GetStringAsync` w taki sposób, który może spodziewać się. (Należy pamiętać, że metoda zwróciła już zadania w kroku 3). Zamiast tego wyniku ciągu są przechowywane w zadanie reprezentujące zakończenie metody, `getStringTask`. Operatora await pobiera wynik `getStringTask`. W instrukcji przypisania przypisuje pobrane wynik `urlContents`.  
  
8.  Gdy `AccessTheWebAsync` ma wynik ciąg metody można obliczyć długość ciągu. Następnie pracy `AccessTheWebAsync` również zostanie zakończone, i wznowić oczekiwania programu obsługi zdarzeń. W pełnym przykładzie na końcu tematu można zobaczyć, że program obsługi zdarzeń pobiera i drukuje wynikową wartość długości.    
Jeśli dopiero zaczynasz przygodę z programowaniem asynchronicznym, zastanów się przez chwilę, jaka jest różnica między zachowaniem synchronicznym i asynchronicznym. Metoda synchroniczna kończy działanie, gdy praca jest zakończona (krok 5), natomiast metoda asynchroniczna zwraca wartość zadania, gdy jej praca jest zawieszona (kroki 3 i 6). Gdy metoda async ukończy pracę, zadanie jest oznaczane jako ukończone, a wynik, o ile istnieje, jest zapisywany w zadaniu.  
  
Aby uzyskać więcej informacji na temat przepływu sterowania, zobacz [przepływ sterowania w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> Metody asynchroniczne interfejsu API  
 Użytkownik może się zastanawiać, gdzie można znaleźć metody, takie jak `GetStringAsync` programowania asynchronicznego tej pomocy technicznej. .NET Framework 4.5 lub nowszy i .NET Core zawierają wiele elementów członkowskich, które współpracują z `async` i `await`. Możesz je rozpoznać sufiks "Async", która jest dołączana nazwa elementu członkowskiego i ich typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Na przykład `System.IO.Stream` klasa zawiera metody <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, i <xref:System.IO.Stream.WriteAsync%2A> obok metod synchronicznych <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, i <xref:System.IO.Stream.Write%2A>.  
  
 Środowisko wykonawcze systemu Windows zawiera także wiele metod, które można używać z `async` i `await` w aplikacjach systemu Windows. Aby uzyskać więcej informacji, zobacz [wątki i programowania asynchronicznego](/windows/uwp/threading-async/) do tworzenia aplikacji platformy uniwersalnej systemu Windows, i [(aplikacje ze Sklepu Windows) programowanie asynchroniczne](/previous-versions/windows/apps/hh464924(v=win.10)) i [Szybki Start: wywoływanie interfejsów API asynchronicznych w języku C# lub Visual Basic](/previous-versions/windows/apps/hh452713(v=win.10)) Jeśli używasz starszej wersji środowiska wykonawczego systemu Windows.  
  
##  <a name="BKMK_Threads"></a> Wątki  
Metody async mają być operacjami niepowodującymi blokowania. `await` Wyrażenie w metodzie asynchronicznej nie blokuje bieżącego wątku, podczas gdy oczekiwano zadanie jest uruchomione. Zamiast tego, wyrażenie rejestruje pozostałą część metody jako kontynuację i przekazuje sterowanie do obiektu wywołującego metody async.  
  
`async` i `await` słów kluczowych nie powodują dodatkowe wątki ma zostać utworzony. Metody komunikacji async nie wymagają wielowątkowości, ponieważ nie działają we własnym wątku. Metoda działa w bieżącym kontekście synchronizacji i używa czasu wątku, tylko wtedy, gdy jest aktywna. Można użyć <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> można przenieść procesor do wątku w tle, ale tło wątku nie pomoże z procesem, które właśnie oczekuje na wyniki stają się dostępne.  
  
Podejście async do programowania asynchronicznego jest preferowane prawie w każdym przypadku. W szczególności, ta metoda jest lepszym rozwiązaniem niż <xref:System.ComponentModel.BackgroundWorker> klasy I/E-powiązane z operacji, ponieważ kod jest prostsze i nie trzeba zabezpieczyć się przed wyścigu. W połączeniu z <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody programowania asynchronicznego jest lepszym rozwiązaniem niż <xref:System.ComponentModel.BackgroundWorker> dla procesora operacji ponieważ programowania asynchronicznego oddziela szczegóły koordynacji uruchomionych kodu z pracy `Task.Run` przesyła do puli wątków.  
  
##  <a name="BKMK_AsyncandAwait"></a> Async i await  
 Jeśli określisz, że metoda jest to metoda asynchroniczna przy użyciu [async](../../../../csharp/language-reference/keywords/async.md) modyfikator, zostanie włączone następujące dwie możliwości.  
  
-   Można użyć metody asynchronicznej oznaczone [await](../../../../csharp/language-reference/keywords/await.md) do wyznaczenia punktów zawieszenia. `await` Operator informuje kompilator, że metody asynchronicznej nie może kontynuować mimo tego punktu do czasu ukończenia oczekiwano proces asynchroniczny. W międzyczasie sterowanie powraca do obiektu wywołującego metodę async.  
  
     Zawieszenie metody asynchronicznej w `await` wyrażenia nie stanowią wyjście z metody i `finally` bloków nie działają.  
  
-   Metoda oznaczona jako async sama może być oczekiwana przez metody, które ją wywołują.  
  
Metoda asynchroniczna zwykle zawiera jeden lub więcej wystąpień `await` operatora, ale brak `await` wyrażeń nie powoduje błąd kompilatora. Jeśli metoda asynchroniczna nie używa `await` operatora, aby oznaczyć punktu zawieszenie, metoda wykonuje jak metoda synchroniczna pomimo `async` modyfikator. Kompilator generuje ostrzeżenia dla takich metod.  
  
 `async` i `await` są kontekstowe słowa kluczowe. Aby uzyskać więcej informacji i przykładów, zobacz następujący temat:  
  
-   [async](../../../../csharp/language-reference/keywords/async.md)  
  
-   [await](../../../../csharp/language-reference/keywords/await.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Parametry i zwracane typy  
Metoda asynchroniczna zwykle zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Wewnątrz metody asynchronicznej `await` operator jest stosowany do zadania, która jest zwracana z wywołania do innej metody asynchronicznej.  
  
Należy określić <xref:System.Threading.Tasks.Task%601> jako typ zwracany, jeśli metoda zawiera [zwracać](../../../../csharp/language-reference/keywords/return.md) instrukcji, która określa argumentu operacji typu `TResult`. 
  
Możesz użyć <xref:System.Threading.Tasks.Task> jako typ zwracany, jeśli metoda ma nie instrukcji return lub zawiera instrukcję return, która nie zwraca argumentu operacji.  

Począwszy od wersji 7.0 C#, można również określić innego typu zwracanego, pod warunkiem, że ten typ zawiera `GetAwaiter` metody. <xref:System.Threading.Tasks.ValueTask%601> jest to przykład takiego typu. Jest on dostępny w [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) pakietu NuGet.
  
 W poniższym przykładzie pokazano, jak deklarowanie i wywoływanie metody, która zwraca <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>.  
  
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
  
Metoda asynchroniczna może być również `void` typ zwracany. To zwracany typ jest używany głównie w celu definiowania metod obsługi zdarzeń, gdy `void` zwracany typ jest wymagany. Programy async obsługi zdarzeń często służą jako punkt wejścia dla programów async.  
  
To metoda asynchroniczna, która ma `void` zwracany typ nie jest oczekiwane, a obiekt wywołujący metody zwracające typ void nie może przechwycić wszelkie wyjątki, które metoda zgłasza.  
  
Nie można zadeklarować metody asynchronicznej [w](../../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów, ale metodę można wywołać metody, które mają takie parametry. Podobnie metoda asynchroniczna nie może zwracać wartość przez odwołanie, mimo że można wywołać metody z ref wartości zwracanych. 
  
Aby uzyskać dodatkowe informacje i przykłady, zobacz [typy zwracać Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md). Aby uzyskać więcej informacji o sposobie przechwytywanie wyjątków w metodach asynchronicznych, zobacz [try-catch](../../../../csharp/language-reference/keywords/try-catch.md). 
  
Asynchroniczne interfejsów API w programowaniu środowiska wykonawczego systemu Windows mają jeden z następujących zwracane typy, które są podobne do zadań:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, które odpowiada <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, które odpowiada <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
   
  
##  <a name="BKMK_NamingConvention"></a> Konwencja nazewnictwa  
 Według konwencji "Async" można dołączyć do nazwy metody, które mają `async` modyfikator.  
  
 Można zignorować konwencję, gdy zdarzenie, klasa bazowa lub kontrakt interfejsu sugeruje inną nazwę. Na przykład nie zmienisz typowych programów obsługi zdarzeń, takich jak `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> Tematy pokrewne i przykłady (Visual Studio)  
  
|Tytuł|Opis|Przykład|  
|-----------|-----------------|------------|  
|[Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Przedstawia, w jaki sposób konwertować synchroniczne rozwiązanie WPF do asynchronicznego rozwiązania WPF. Ta aplikacja pobiera szereg witryn sieci Web.|[Przykład Async: Uzyskiwanie dostępu do wskazówki sieci Web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Dodaje <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do poprzedniego wskazówki. Korzystanie z `WhenAll` uruchamia wszystkie pobrane pliki w tym samym czasie.||  
|[Porady: wiele żądań sieci Web równolegle za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ilustruje, jak uruchomić kilka zadań w tym samym czasie.|[Przykład Async: Należy żądania sieci Web równolegle](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Asynchroniczne typy zwracane (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)|Ilustruje typy zwracane przez metody async i wyjaśnia, kiedy poszczególne typy są odpowiednie.||  
|[Przepływ sterowania w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)|Śledzi szczegółowo przepływ sterowania w serii wyrażeń await w programie asynchronicznym.|[Przykład Async: Przepływ sterowania w aplikacjach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[Dostrajanie aplikacji Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Przedstawia, w jaki sposób dodać następujące funkcje do rozwiązania async:<br /><br /> -   [Anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Anulowanie pozostałych zadań asynchronicznych po jednym jest pełna (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Próbka asynchronicznych: Dostrajanie aplikacji dokładnej](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Przedstawia, w jaki sposób obsługiwać przypadki, w których podczas działania uruchamiana jest ponownie aktywna operacja asynchroniczna.||  
|[WhenAny: Łączenie platformy .NET Framework i środowiska wykonawczego systemu Windows](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)|Pokazuje, jak połączenie między typami zadań w programie .NET Framework i IAsyncOperations w [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby można było używać <xref:System.Threading.Tasks.Task.WhenAny%2A> z [!INCLUDE[wrt](~/includes/wrt-md.md)] metody.|[Przykład asynchroniczne: Łączenie platformy .NET i środowiska wykonawczego systemu Windows (metody AsTask i WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|  
|Anulowanie asynchroniczne: łączenie platformy .NET Framework ze środowiskiem wykonawczym systemu Windows|Pokazuje, jak połączenie między typami zadań w programie .NET Framework i IAsyncOperations w [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby można było używać <xref:System.Threading.CancellationTokenSource> z [!INCLUDE[wrt](~/includes/wrt-md.md)] metody.|[Przykład asynchroniczne: Łączenie platformy .NET i środowiska wykonawczego systemu Windows (metody AsTask & anulowania)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[Użycie Async do uzyskiwania dostępu do plików (C#)](../../../../csharp/programming-guide/concepts/async/using-async-for-file-access.md)|Wyświetla listę korzyści wynikających ze stosowania słów kluczowych async i await przy uzyskiwaniu dostępu do plików.||  
|[Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Opisano nowy wzorzec asynchronii w .NET Framework. Wzorzec jest oparta na <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> typów.||  
|[Asynchroniczne filmów wideo w witrynie Channel 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Oferuje łącza do różnych plików wideo dotyczących programowania asynchronicznego.||  
  
##  <a name="BKMK_CompleteExample"></a> Pełny przykład  
 Następujący kod to plik MainWindow.xaml.cs z aplikacji Windows Presentation Foundation (WPF), który w tym temacie omówiono. Możesz pobrać próbki z [próbki Async: przykład z "Asynchronicznego programowania z Async i Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
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
            Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [async](../../../../csharp/language-reference/keywords/async.md)  
 [await](../../../../csharp/language-reference/keywords/await.md)  
 [Programowanie asynchroniczne](../../../../csharp/async.md)  
 [Async — omówienie](../../../../standard/async.md)  
