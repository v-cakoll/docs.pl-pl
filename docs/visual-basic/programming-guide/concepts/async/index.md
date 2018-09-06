---
title: Programowanie asynchroniczne z Async i Await (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: 9798136bfa88e19764a064732637783620f77a73
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884679"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Programowanie asynchroniczne z Async i Await (Visual Basic)
Możesz uniknąć problemów z wydajnością i poprawić ogólny czas odpowiedzi aplikacji, stosując programowanie asynchroniczne. Jednak tradycyjne techniki pisania aplikacji asynchronicznych mogą być skomplikowane, przez co trudne do pisania, debugowania i konserwacji.  
  
 Program Visual Studio 2012 wprowadza uproszczone podejście, programowanie async, wykorzystującego obsługi komunikacji asynchronicznej w .NET Framework 4.5 lub nowszy oraz jak środowiska wykonawczego Windows. Kompilator wykonuje trudną pracę, którą kiedyś wykonywał programista, a aplikacja zachowuje strukturę logiczną przypominającą kod synchroniczny. W efekcie masz wszystkie korzyści wynikające z programowania asynchronicznego przy ułamkowym nakładzie pracy.  
  
 Ten temat zawiera omówienie, kiedy i jak stosować programowanie async oraz zawiera łącza do tematów zawierających szczegółowe informacje oraz przykłady.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> Programowanie Async poprawia czas odpowiedzi  
 Asynchroniczność jest istotna dla działań, które mogą powodować blokowanie, na przykład, gdy aplikacja uzyskuje dostęp do sieci Web. Dostęp do zasobów sieci Web bywa powolny lub opóźniony. Jeśli takie działanie jest zablokowane w procesie synchronicznym, cała aplikacji musi czekać. W procesie asynchronicznym aplikacja może kontynuować wykonywanie innych zadań, które nie są zależne od zasobów sieci Web, do momentu zakończeniem zadania mogącego powodować blokowanie.  
  
 W poniższej tabeli przedstawiono typowe obszary, w których programowanie asynchroniczne poprawia czas odpowiedzi. Wymienione interfejsy API z .NET Framework 4.5 i środowisko wykonawcze Windows zawierają metody, które obsługują programowanie asynchroniczne.  
  
|Obszar aplikacji|Obsługa interfejsów API, która obejmuje metody asynchroniczne|  
|----------------------|------------------------------------------------|  
|Web access|<xref:System.Net.Http.HttpClient>, <xref:Windows.Web.Syndication.SyndicationClient>|  
|Praca z plikami|<xref:Windows.Storage.StorageFile>, <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|  
|Praca z obrazami|<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|  
|Programowanie WCF|[Operacje synchroniczne i asynchroniczne](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)|  
|||  
  
 Asynchroniczność okazuje się szczególnie cenna w przypadku aplikacji, które mają dostęp do wątku interfejsu użytkownika, ponieważ wszystkie działania związane z interfejsem użytkownika korzystają zazwyczaj z jednego wątku. Jeśli w aplikacji synchronicznej jest zablokowany jakikolwiek proces, zablokowane są wszystkie procesy. Aplikacja przestanie odpowiadać i możesz dojść do wniosku, że uległa awarii, a tymczasem może po prostu być w stanie oczekiwania.  
  
 Kiedy używasz metod asynchronicznych, aplikacja dalej odpowiada interfejsowi użytkownika. Możesz przykładowo zmienić rozmiar lub zminimalizować aplikację lub możesz ją zamknąć, jeżeli nie chcesz czekać aż zakończy zadanie.  
  
 Podejście async oferuje również odpowiednik automatycznego przejścia do listy opcji do wybrania przy projektowaniu operacji asynchronicznych. Oznacza to, że można korzystać z wszystkich zalet tradycyjnego programowania asynchronicznego, ale przy znacznie mniejszym nakładzie pracy programisty.  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Metody asynchroniczne są łatwiejsze do zapisu  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md) i [Await](../../../../visual-basic/language-reference/modifiers/async.md) słowa kluczowe w języku Visual Basic to samo jądro programowania asynchronicznego. Za pomocą tych dwóch słów kluczowych, można użyć zasobów .NET Framework lub środowiska wykonawczego Windows, do tworzenia metody asynchronicznej niemal jako prosty jak przy tworzeniu metody synchronicznej. Metody asynchroniczne definiowane za pomocą `Async` i `Await` są określane jako metody async.  
  
 W poniższym przykładzie przedstawiono metodę async. Prawie wszystko w kodzie powinno wyglądać znajomo. Komentarze wywołują funkcje dodawane przez użytkownika w celu uzyskania asynchroniczności.  
  
 Można znaleźć pełny Windows Presentation Foundation (WPF) przykładowy plik na końcu tego tematu i możesz pobrać próbkę z [przykład Async: przykład z "Programowania asynchronicznego z Async i Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```vb  
' Three things to note in the signature:  
'  - The method has an Async modifier.   
'  - The return type is Task or Task(Of T). (See "Return Types" section.)  
'    Here, it is Task(Of Integer) because the return statement returns an integer.  
'  - The method name ends in "Async."  
Async Function AccessTheWebAsync() As Task(Of Integer)  
  
    ' You need to add a reference to System.Net.Http to declare client.  
    Dim client As HttpClient = New HttpClient()  
  
    ' GetStringAsync returns a Task(Of String). That means that when you await the  
    ' task you'll get a string (urlContents).  
    Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
    ' You can do work here that doesn't rely on the string from GetStringAsync.  
    DoIndependentWork()  
  
    ' The Await operator suspends AccessTheWebAsync.  
    '  - AccessTheWebAsync can't continue until getStringTask is complete.  
    '  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
    '  - Control resumes here when getStringTask is complete.   
    '  - The Await operator then retrieves the string result from getStringTask.  
    Dim urlContents As String = Await getStringTask  
  
    ' The return statement specifies an integer result.  
    ' Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
    Return urlContents.Length  
End Function  
```  
  
 Jeśli `AccessTheWebAsync` nie ma żadnych działań do wykonania pomiędzy wywołaniem `GetStringAsync` i oczekuje na jego zakończenie, można uprościć kod, realizując wywołanie i Oczekiwanie w następującej pojedynczej instrukcji.  
  
```vb  
Dim urlContents As String = Await client.GetStringAsync()  
```  
  
 Poniższy opis podsumowuje, co sprawia, że poprzedni przykład jest metodą asynchroniczną.  
  
-   Podpis metody zawiera `Async` modyfikator.  
  
-   Nazwa metody async kończy się zwyczajowo sufiksem „Async”.  
  
-   Zwracany typ może być jednym z następujących:  
  
    -   <xref:System.Threading.Tasks.Task%601> Jeśli metoda zawiera instrukcję return, w której operator ma typ TResult.  
  
    -   <xref:System.Threading.Tasks.Task> Jeśli metoda nie zawiera instrukcji return lub zawiera instrukcję return bez argumentu operacji.  
  
    -   [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) przypadku pisania programu async obsługi zdarzeń.  
  
     Aby uzyskać więcej informacji, zobacz „Typy zwracane i parametry” w dalszej części tego tematu.  
  
-   Metoda zazwyczaj zawiera co najmniej jedno wyrażenie „await”, które oznacza punkt, w którym metoda nie może kontynuować pracy do czasu ukończenia operacji asynchronicznej. W tym czasie metoda jest zawieszona, a sterowanie powraca do obiektu wywołującego metodę. Następna sekcji tego tematu przedstawia, co się dzieje w punkcie zawieszenia.  
  
 W metodzie asynchronicznej używasz podanych słów kluczowych i typów w celu wskazania, co chcesz zrobić, a kompilator zajmie się resztą, w tym śledzeniem tego, co musi się zdarzyć, gdy sterowanie powraca do punktu oczekiwania w metodzie zawieszonej. Niektóre procesy, takie jak pętle i obsługa wyjątków, mogą być trudne do obsłużenia w tradycyjnym kodzie asynchronicznym. W metodzie asynchronicznej wpisujesz te elementy podobnie jak w rozwiązaniu synchronicznym i problem rozwiązany.  
  
 Aby uzyskać więcej informacji dotyczących asynchroniczności w poprzednich wersjach programu .NET Framework, zobacz [TPL i tradycyjnym .NET Framework Asynchronous Programming](https://msdn.microsoft.com/library/e7b31170-a156-433f-9f26-b1fc7cd1776f).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Co się dzieje w metodzie Async  
 Ważne jest, aby rozumieć programowanie asynchroniczne jako przepływ sterowania od metody do metody. Poniższy diagram ilustruje ten proces.  
  
 ![Śledzenie programu async](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Liczby w diagramie odpowiadają poniższym krokom.  
  
1.  Program obsługi zdarzeń wywołuje i czeka `AccessTheWebAsync` metody asynchronicznej.  
  
2.  `AccessTheWebAsync` Tworzy <xref:System.Net.Http.HttpClient> wystąpienie i wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronicznej metody do pobierania zawartości witryny sieci Web jako ciąg.  
  
3.  Coś się dzieje w `GetStringAsync` , co wstrzymuje jej postęp. Być może metoda musi czekać na pobranie strony internetowej lub inne działanie blokujące. Aby uniknąć blokowania zasobów,, `GetStringAsync` oddaje kontrole wywołującemu, `AccessTheWebAsync`.  
  
     `GetStringAsync` Zwraca <xref:System.Threading.Tasks.Task%601> gdzie TResult jest ciągiem, a `AccessTheWebAsync` przypisuje zadania `getStringTask` zmiennej. Zadanie przedstawia ciągły proces wywołania metody `GetStringAsync`, z zobowiązaniem utworzenia faktycznej wartości ciągu po ukończeniu pracy.  
  
4.  Ponieważ `getStringTask` nie miało jeszcze, `AccessTheWebAsync` można kontynuować inne prace, które nie są zależne od wyniku końcowego `GetStringAsync`. Że praca jest reprezentowana przez wywołanie metody synchronicznej `DoIndependentWork`.  
  
5.  `DoIndependentWork` jest metodą synchroniczną, która działa i wraca do.  
  
6.  `AccessTheWebAsync` ma za mało pracy, która może wykonywać bez wyniku z `getStringTask`. `AccessTheWebAsync` dalej chce obliczyć i zwracać długość pobranego ciągu, ale metoda nie może obliczyć tej wartości dopóki metoda ma ciąg.  
  
     W związku z tym `AccessTheWebAsync` stosuje await operator, aby zawiesić postęp i oddać kontrolę do metody, która wywołała `AccessTheWebAsync`. `AccessTheWebAsync` Zwraca `Task<int>` (`Task(Of Integer)` w języku Visual Basic) do obiektu wywołującego. Zadanie przedstawia obietnicę utworzenia w wyniku liczby całkowitej, która jest długością pobranego ciągu.  
  
    > [!NOTE]
    >  Jeśli `GetStringAsync` (i w związku z tym `getStringTask`) zostanie zakończona, zanim `AccessTheWebAsync` czeka na jego, sterowanie pozostanie w `AccessTheWebAsync`. Wydatków, a następnie powrotu do `AccessTheWebAsync` zostałby zmarnowany, gdyby wywołany proces asynchroniczny (`getStringTask`) został już ukończony i AccessTheWebSync nie musiałby czekać na wynik końcowy.  
  
     Przetwarzanie wzorca jest kontynuowane wewnątrz elementu wywołującego (programu obsługi zdarzeń w tym przykładzie). Obiekt wywołujący może wykonywać inne czynności, które nie są zależne od wyników `AccessTheWebAsync` przed oczekiwaniem na wynik lub obiekt wywołujący może czekać natychmiast.   Program obsługi zdarzeń oczekuje na `AccessTheWebAsync`, i `AccessTheWebAsync` oczekuje na `GetStringAsync`.  
  
7.  `GetStringAsync` kończy i produkuje wynik w postaci ciągu. Wynikowy ciąg nie jest zwracany przez wywołanie `GetStringAsync` w taki sposób, jakiego można by oczekiwać. (Należy pamiętać, że metoda zwróciła już zadanie w kroku 3). Zamiast tego wynikowy ciąg jest zapisywany w zadaniu, które reprezentuje ukończenie metody, `getStringTask`. Operator "await" pobiera wyniki z `getStringTask`. Instrukcja przypisania przypisuje wynik pobrany `urlContents`.  
  
8.  Gdy `AccessTheWebAsync` ma wynik ciągu, metoda może obliczyć długość ciągu. Następnie praca `AccessTheWebAsync` jest również zakończona i czekający program obsługi zdarzenia może wznowić działanie. W pełnym przykładzie na końcu tematu można zobaczyć, że program obsługi zdarzeń pobiera i drukuje wynikową wartość długości.  
  
 Jeśli dopiero zaczynasz przygodę z programowaniem asynchronicznym, zastanów się przez chwilę, jaka jest różnica między zachowaniem synchronicznym i asynchronicznym. Metoda synchroniczna kończy działanie, gdy praca jest zakończona (krok 5), natomiast metoda asynchroniczna zwraca wartość zadania, gdy jej praca jest zawieszona (kroki 3 i 6). Gdy metoda async ukończy pracę, zadanie jest oznaczane jako ukończone, a wynik, o ile istnieje, jest zapisywany w zadaniu.  
  
 Aby uzyskać więcej informacji na temat formantów flow, zobacz [przepływ sterowania w programach Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> Metody Async interfejsu API  
 Użytkownik może się zastanawiać, gdzie można znaleźć metody takie jak `GetStringAsync` które obsługują programowanie async. .NET Framework 4.5 lub nowszej zawiera wiele elementów członkowskich, które działają z `Async` i `Await`. Możesz rozpoznać te elementy członkowskie po przyrostku "Async", który jest dołączony do nazwy elementu członkowskiego i zwracanego typu <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Na przykład `System.IO.Stream` klasa zawiera metody <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, i <xref:System.IO.Stream.WriteAsync%2A> synchroniczne metody <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, i <xref:System.IO.Stream.Write%2A>.  
  
 Środowisko wykonawcze Windows zawiera również wiele metod, których można używać z `Async` i `Await` w aplikacji Windows. Aby uzyskać więcej informacji i obejrzeć przykładowe metody, zobacz [wywołanie asynchroniczne API w języku C# lub Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [(aplikacje Windows Runtime) programowanie asynchroniczne](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)), i [WhenAny: łączenie platformy .NET Struktura i środowisko uruchomieniowe Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).  
  
##  <a name="BKMK_Threads"></a> Wątki  
 Metody async mają być operacjami niepowodującymi blokowania. `Await` Wyrażenia w metodzie async nie blokuje bieżącego wątku, gdy oczekiwane zadanie jest uruchomione. Zamiast tego, wyrażenie rejestruje pozostałą część metody jako kontynuację i przekazuje sterowanie do obiektu wywołującego metody async.  
  
 `Async` i `Await` słów kluczowych nie powodują dodatkowe wątki nie ma zostać utworzony. Metody komunikacji async nie wymagają wielowątkowości, ponieważ nie działają we własnym wątku. Metoda działa w bieżącym kontekście synchronizacji i używa czasu wątku, tylko wtedy, gdy jest aktywna. Możesz użyć <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> przenieść zadań intensywnie angażujących Procesor do wątku w tle, ale tło wątku nie pomóc procesu, który tylko oczekuje na wyniki staną się dostępne.  
  
 Podejście async do programowania asynchronicznego jest preferowane prawie w każdym przypadku. W szczególności, to podejście jest lepsze niż <xref:System.ComponentModel.BackgroundWorker> dla I/O-operacji, ponieważ kod jest prostszy i nie masz zabezpieczyć się przed sytuacjami wyścigu. W połączeniu z <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>, programowanie async jest lepsze niż <xref:System.ComponentModel.BackgroundWorker> dla Procesora CPU, operacji ponieważ asynchroniczne programowanie oddziela szczegóły dotyczące koordynacji uruchomienia kodu z pracy `Task.Run` przenosi do puli wątków.  
  
##  <a name="BKMK_AsyncandAwait"></a> Async i Await  
 Jeśli określisz, że metoda jest metodą asynchroniczną za pomocą [Async](../../../../visual-basic/language-reference/modifiers/async.md) modyfikator, włączysz następujące dwie możliwości.  
  
-   Można użyć oznaczonej metody asynchronicznej [Await](../../../../visual-basic/language-reference/operators/await-operator.md) do wskazania punktów zawieszenia. Operator await informuje kompilator, że metoda async nie może kontynuować działania do chwili zakończenia procesu asynchronicznego, na który oczekuje. W międzyczasie sterowanie powraca do obiektu wywołującego metodę async.  
  
     Zawieszenie metody async na `Await` wyrażenie nie stanowi wyjścia z metody i `Finally` bloki nie są wykonywane.  
  
-   Metoda oznaczona jako async sama może być oczekiwana przez metody, które ją wywołują.  
  
 Metoda async zazwyczaj zawiera jeden lub więcej wystąpień `Await` operatora, ale brak `Await` wyrażeń nie powoduje błędu kompilatora. Jeśli metoda async nie używa `Await` operator, aby oznaczyć punkt zawieszenia, metoda jest wykonywana jak metoda synchroniczna, pomimo `Async` modyfikator. Kompilator generuje ostrzeżenia dla takich metod.  
  
 `Async` i `Await` są kontekstowymi słowami kluczowymi. Aby uzyskać więcej informacji i przykładów, zobacz następujący temat:  
  
-   [Async](../../../../visual-basic/language-reference/modifiers/async.md)  
  
-   [Await, operator](../../../../visual-basic/language-reference/operators/await-operator.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Typy zwracane i parametry  
 W programowaniu .NET Framework, metoda async zwykle zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Wewnątrz metody asynchronicznej `Await` operator jest stosowany do zadania, który jest zwracany z wywołania do innej metody async.  
  
 Należy określić <xref:System.Threading.Tasks.Task%601> jako typ zwracany, jeśli metoda zawiera [zwracają](../../../../visual-basic/language-reference/statements/return-statement.md) instrukcję, która określa operandę typu `TResult`.  
  
 Możesz użyć `Task` jako typ zwracany, jeśli metoda nie zawiera instrukcji return lub zawiera instrukcję return, która nie zwraca operandu.  
  
 W poniższym przykładzie pokazano, jak deklarować i wywoływać metodę zwracającą <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>.  
  
```vb  
' Signature specifies Task(Of Integer)  
Async Function TaskOfTResult_MethodAsync() As Task(Of Integer)  
  
    Dim hours As Integer  
    ' . . .  
    ' Return statement specifies an integer result.  
    Return hours  
End Function  
  
' Calls to TaskOfTResult_MethodAsync  
Dim returnedTaskTResult As Task(Of Integer) = TaskOfTResult_MethodAsync()  
Dim intResult As Integer = Await returnedTaskTResult  
' or, in a single statement  
Dim intResult As Integer = Await TaskOfTResult_MethodAsync()  
  
' Signature specifies Task  
Async Function Task_MethodAsync() As Task  
  
    ' . . .  
    ' The method has no return statement.  
End Function  
  
' Calls to Task_MethodAsync  
Task returnedTask = Task_MethodAsync()  
Await returnedTask  
' or, in a single statement  
Await Task_MethodAsync()  
```  
  
 Każde zwracane zadanie reprezentuje zadanie pracy w toku. Zadanie zawiera informacje o stanie procesu asynchronicznego i, ostatecznie, albo ostatecznego wyniku procesu lub wyjątku, który zgłasza proces, jeśli się nie powiedzie.  
  
 Metoda asynchroniczna może być również `Sub` metody. Ten typ zwracany jest używany głównie do definiowania programów obsługi zdarzeń, których typem zwracanym jest wymagany. Programy async obsługi zdarzeń często służą jako punkt wejścia dla programów async.  
  
 Metoda asynchroniczna to `Sub` procedura nie może być oczekiwany, a obiekt wywołujący nie może przechwytywać wyjątków, które metoda wygeneruje.  
  
 Nie można zadeklarować metody asynchronicznej [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametrów, ale metodę można wywołać metody, które mają takie parametry.  
  
 Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md). Aby uzyskać więcej informacji dotyczących wyjątków CATCH w metodach asynchronicznych, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Asynchroniczne API w programowaniu Windows Runtime mieć jedną z następujących typów zwrotu, które są podobne do zadań:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, która odnosi się do <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, która odnosi się do <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
  
 Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [wywołanie asynchroniczne API w języku C# lub Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).  
  
##  <a name="BKMK_NamingConvention"></a> Konwencje nazewnictwa  
 Umownie, dołączasz "Asynchroniczny" do nazw metod mających `Async` modyfikator.  
  
 Można zignorować konwencję, gdy zdarzenie, klasa bazowa lub kontrakt interfejsu sugeruje inną nazwę. Na przykład nie należy zmieniać nazw wspólnej procedury obsługi zdarzeń, takich jak `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> Tematy pokrewne i przykłady (Visual Studio)  
  
|Tytuł|Opis|Przykład|  
|-----------|-----------------|------------|  
|[Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Przedstawia, w jaki sposób konwertować synchroniczne rozwiązanie WPF do asynchronicznego rozwiązania WPF. Ta aplikacja pobiera szereg witryn sieci Web.|[Próbka asynchroniczna: Dostęp do instruktażu sieci Web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Dodaje <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do poprzedniego przewodnika. Korzystanie z `WhenAll` rozpoczyna wszystkie akcje pobierania w tym samym czasie.||  
|[Porady: wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ilustruje, jak uruchomić kilka zadań w tym samym czasie.|[Próbka asynchroniczna: Złożyć wiele żądań sieci Web równolegle](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)|Ilustruje typy zwracane przez metody async i wyjaśnia, kiedy poszczególne typy są odpowiednie.||  
|[Przepływ sterowania w programach Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)|Śledzi szczegółowo przepływ sterowania w serii wyrażeń await w programie asynchronicznym.|[Próbka asynchroniczna: Przepływ sterowania w aplikacjach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[Dostrajanie aplikacji Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Przedstawia, w jaki sposób dodać następujące funkcje do rozwiązania async:<br /><br /> -   [Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Anulowanie zadań asynchronicznych po upływie określonego czasu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich po ich zakończeniu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Próbka asynchroniczna: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Przedstawia, w jaki sposób obsługiwać przypadki, w których podczas działania uruchamiana jest ponownie aktywna operacja asynchroniczna.||  
|[WhenAny: Łączenie platformy .NET Framework i środowiska uruchomieniowego Windows](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)|Pokazuje, jak typy zadań w .NET Framework i IAsyncOperations w [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby można było używać <xref:System.Threading.Tasks.Task.WhenAny%2A> z [!INCLUDE[wrt](~/includes/wrt-md.md)] metody.|[Próbka Asynchroniczae: Pomostu między .NET i programem obsługi Windows (AsTask i WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|  
|Anulowanie asynchroniczne: łączenie platformy .NET Framework ze środowiskiem wykonawczym systemu Windows|Pokazuje, jak typy zadań w .NET Framework i IAsyncOperations w [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby można było używać <xref:System.Threading.CancellationTokenSource> z [!INCLUDE[wrt](~/includes/wrt-md.md)] metody.|[Próbka Asynchroniczae: Pomostu między .NET i programem obsługi Windows (AsTask i anulowania)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[Użycie Async do uzyskiwania dostępu do plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/using-async-for-file-access.md)|Wyświetla listę korzyści wynikających ze stosowania słów kluczowych async i await przy uzyskiwaniu dostępu do plików.||  
|[Wzorzec asynchroniczny oparty na zadaniach (TAP)](https://msdn.microsoft.com/library/8cef1fcf-6f9f-417c-b21f-3fd8bac75007)|Opisano nowy wzorzec asynchronii w .NET Framework. Wzorzec jest oparty na <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> typów.||  
|[Asynchroniczne wideo w witrynie Channel 9](https://channel9.msdn.com/search?term=async+&type=All)|Oferuje łącza do różnych plików wideo dotyczących programowania asynchronicznego.||  
  
##  <a name="BKMK_CompleteExample"></a> Kompletny przykład  
 Następujący kod to plik MainWindow.xaml.vb z aplikacji Windows Presentation Foundation (WPF), która w tym temacie omówiono. Możesz pobrać próbkę z [przykład Async: przykład z "Programowania asynchronicznego z Async i Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```vb  
' Add an Imports statement and a reference for System.Net.Http  
Imports System.Net.Http  
  
Class MainWindow  
  
    ' Mark the event handler with async so you can use Await in it.  
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Call and await separately.  
        'Task<int> getLengthTask = AccessTheWebAsync();  
        '' You can do independent work here.  
        'int contentLength = await getLengthTask;  
  
        Dim contentLength As Integer = Await AccessTheWebAsync()  
  
        ResultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
    End Sub  
  
    ' Three things to note in the signature:  
    '  - The method has an Async modifier.   
    '  - The return type is Task or Task(Of T). (See "Return Types" section.)  
    '    Here, it is Task(Of Integer) because the return statement returns an integer.  
    '  - The method name ends in "Async."  
    Async Function AccessTheWebAsync() As Task(Of Integer)  
  
        ' You need to add a reference to System.Net.Http to declare client.  
        Dim client As HttpClient = New HttpClient()  
  
        ' GetStringAsync returns a Task(Of String). That means that when you await the  
        ' task you'll get a string (urlContents).  
        Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' You can do work here that doesn't rely on the string from GetStringAsync.  
        DoIndependentWork()  
  
        ' The Await operator suspends AccessTheWebAsync.  
        '  - AccessTheWebAsync can't continue until getStringTask is complete.  
        '  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
        '  - Control resumes here when getStringTask is complete.   
        '  - The Await operator then retrieves the string result from getStringTask.  
        Dim urlContents As String = Await getStringTask  
  
        ' The return statement specifies an integer result.  
        ' Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
        Return urlContents.Length  
    End Function  
  
    Sub DoIndependentWork()  
        ResultsTextBox.Text &= "Working . . . . . . ." & vbCrLf  
    End Sub  
End Class  
  
' Sample Output:  
  
' Working . . . . . . .  
  
' Length of the downloaded string: 41763.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Await, operator](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md)
