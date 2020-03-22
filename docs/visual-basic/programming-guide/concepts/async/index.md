---
title: Programowanie asynchroniczne z Async i Await
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: cbcdd48571855e168f563585088f1210eb6410eb
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266498"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Programowanie asynchroniczne z async i await (Visual Basic)

Możesz uniknąć problemów z wydajnością i poprawić ogólny czas odpowiedzi aplikacji, stosując programowanie asynchroniczne. Jednak tradycyjne techniki pisania aplikacji asynchronicznych mogą być skomplikowane, przez co trudne do pisania, debugowania i konserwacji.

Visual Studio 2012 wprowadzono uproszczone podejście, programowanie asynchroniczne, które wykorzystuje obsługę asynchroniiową w programie .NET Framework 4.5 i nowszym, a także w czasie wykonywania systemu Windows. Kompilator wykonuje trudną pracę, którą kiedyś wykonywał programista, a aplikacja zachowuje strukturę logiczną przypominającą kod synchroniczny. W efekcie masz wszystkie korzyści wynikające z programowania asynchronicznego przy ułamkowym nakładzie pracy.

Ten temat zawiera omówienie, kiedy i jak stosować programowanie async oraz zawiera łącza do tematów zawierających szczegółowe informacje oraz przykłady.

## <a name="async-improves-responsiveness"></a><a name="BKMK_WhentoUseAsynchrony"></a>Async poprawia responsywność

Asynchroniczność jest istotna dla działań, które mogą powodować blokowanie, na przykład, gdy aplikacja uzyskuje dostęp do sieci Web. Dostęp do zasobów sieci Web bywa powolny lub opóźniony. Jeśli takie działanie jest zablokowane w procesie synchronicznym, cała aplikacji musi czekać. W procesie asynchronicznym aplikacja może kontynuować wykonywanie innych zadań, które nie są zależne od zasobów sieci Web, do momentu zakończeniem zadania mogącego powodować blokowanie.

W poniższej tabeli przedstawiono typowe obszary, w których programowanie asynchroniczne poprawia czas odpowiedzi. Wymienione interfejsy API z platformy .NET Framework 4.5 i środowiska wykonawczego systemu Windows zawierają metody obsługujące programowanie asynchroniowe.

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

## <a name="async-methods-are-easier-to-write"></a><a name="BKMK_HowtoWriteanAsyncMethod"></a>Metody asynchronizowe są łatwiejsze do zapisania

Słowa kluczowe [Async](../../../../visual-basic/language-reference/modifiers/async.md) i [Await](../../../../visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic są sercem programowania asynchroniowego. Za pomocą tych dwóch słów kluczowych, można użyć zasobów w programie .NET Framework lub środowiska wykonawczego systemu Windows, aby utworzyć metodę asynchroniiową prawie tak łatwo, jak utworzyć metodę synchroniową. Metody asynchroniczne, które `Async` można `Await` zdefiniować przy użyciu i są określane jako metody asynchroniczne.

W poniższym przykładzie przedstawiono metodę async. Prawie wszystko w kodzie powinno wyglądać znajomo. Komentarze wywołują funkcje dodawane przez użytkownika w celu uzyskania asynchroniczności.

Na końcu tego tematu można znaleźć kompletny przykładowy plik programu Windows Presentation Foundation (WPF) i pobrać próbkę z [przykładu Asynchnc: Przykład z "Programowanie asynchroniczne z Async i Await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

```vb
' Three things to note about writing an Async Function:
'  - The function has an Async modifier.
'  - Its return type is Task or Task(Of T). (See "Return Types" section.)
'  - As a matter of convention, its name ends in "Async".
Async Function AccessTheWebAsync() As Task(Of Integer)
    Using client As New HttpClient()
        ' Call and await separately.
        '  - AccessTheWebAsync can do other things while GetStringAsync is also running.
        '  - getStringTask stores the task we get from the call to GetStringAsync.
        '  - Task(Of String) means it is a task which returns a String when it is done.
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://docs.microsoft.com/dotnet")
        ' You can do other work here that doesn't rely on the string from GetStringAsync.
        DoIndependentWork()
        ' The Await operator suspends AccessTheWebAsync.
        '  - AccessTheWebAsync does not continue until getStringTask is complete.
        '  - Meanwhile, control returns to the caller of AccessTheWebAsync.
        '  - Control resumes here when getStringTask is complete.
        '  - The Await operator then retrieves the String result from getStringTask.
        Dim urlContents As String = Await getStringTask
        ' The Return statement specifies an Integer result.
        ' A method which awaits AccessTheWebAsync receives the Length value.
        Return urlContents.Length

    End Using

End Function
```

Jeśli `AccessTheWebAsync` nie ma żadnej pracy, które `GetStringAsync` można wykonać między wywołaniem i oczekiwania na jego ukończenie, można uprościć kod, wywołując i oczekując w poniższej instrukcji pojedynczej.

```vb
Dim urlContents As String = Await client.GetStringAsync()
```

Następujące cechy podsumowują, co sprawia, że poprzedni przykład jest metodą asynchronizową:

- Podpis metody zawiera `Async` modyfikator.
- Nazwa metody async kończy się zwyczajowo sufiksem „Async”.
- Zwracany typ może być jednym z następujących:

  - [Task(Of TResult),](xref:System.Threading.Tasks.Task%601) jeśli metoda ma return instrukcji, w którym operand ma typu TResult.
  - <xref:System.Threading.Tasks.Task>jeśli metoda nie ma instrukcji zwrotu lub ma instrukcję zwrotu bez operandu.
  - [Sub,](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) jeśli piszesz program obsługi zdarzeń asynchroniiowych.

  Aby uzyskać więcej informacji, zobacz „Typy zwracane i parametry” w dalszej części tego tematu.

- Metoda zazwyczaj zawiera co najmniej jedno wyrażenie „await”, które oznacza punkt, w którym metoda nie może kontynuować pracy do czasu ukończenia operacji asynchronicznej. W tym czasie metoda jest zawieszona, a sterowanie powraca do obiektu wywołującego metodę. Następna sekcji tego tematu przedstawia, co się dzieje w punkcie zawieszenia.

W metodzie asynchronicznej używasz podanych słów kluczowych i typów w celu wskazania, co chcesz zrobić, a kompilator zajmie się resztą, w tym śledzeniem tego, co musi się zdarzyć, gdy sterowanie powraca do punktu oczekiwania w metodzie zawieszonej. Niektóre procesy, takie jak pętle i obsługa wyjątków, mogą być trudne do obsłużenia w tradycyjnym kodzie asynchronicznym. W metodzie asynchronicznej wpisujesz te elementy podobnie jak w rozwiązaniu synchronicznym i problem rozwiązany.

Aby uzyskać więcej informacji na temat asynchrony w poprzednich wersjach programu .NET Framework, zobacz [TPL i tradycyjne programowanie asynchroniczne .NET Framework](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="what-happens-in-an-async-method"></a><a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Co dzieje się w metodzie Asynchronii

Ważne jest, aby rozumieć programowanie asynchroniczne jako przepływ sterowania od metody do metody. Poniższy diagram prowadzi przez proces:

![Diagram, który pokazuje śledzenie programu asynchroniiowego.](./media/index/navigation-trace-async-program.png)

Liczby na diagramie odpowiadają następującym krokom:

1. Program obsługi zdarzeń wywołuje `AccessTheWebAsync` i oczekuje na metodę asynchroniiową.

2. `AccessTheWebAsync`tworzy <xref:System.Net.Http.HttpClient> wystąpienie i <xref:System.Net.Http.HttpClient.GetStringAsync%2A> wywołuje metodę asynchronizacę, aby pobrać zawartość witryny sieci Web jako ciąg.

3. Dzieje się `GetStringAsync` coś, co zawiesza jego postęp. Być może metoda musi czekać na pobranie strony internetowej lub inne działanie blokujące. Aby uniknąć blokowania `GetStringAsync` zasobów, daje kontrolę `AccessTheWebAsync`jego wywołującego, .

     `GetStringAsync`zwraca [Task(Of TResult),](xref:System.Threading.Tasks.Task%601) gdzie TResult jest `AccessTheWebAsync` ciągiem i `getStringTask` przypisuje zadanie do zmiennej. Zadanie reprezentuje trwający proces wywołania `GetStringAsync`, z zobowiązaniem do uzyskania rzeczywistej wartości ciągu po zakończeniu pracy.

4. Ponieważ `getStringTask` nie był jeszcze oczekiwany, `AccessTheWebAsync` można kontynuować inne prace, które `GetStringAsync`nie zależą od ostatecznego wyniku z . Ta praca jest reprezentowana przez wywołanie metody `DoIndependentWork`synchronicznie.

5. `DoIndependentWork`jest metodą synchroniczne, która wykonuje swoją pracę i zwraca do jego obiektu wywołującego.

6. `AccessTheWebAsync`zabrakło pracy, że może to zrobić `getStringTask`bez wyniku z . `AccessTheWebAsync`next chce obliczyć i zwrócić długość pobranego ciągu, ale metoda nie może obliczyć tej wartości, dopóki metoda nie ma ciągu.

     W związku `AccessTheWebAsync` z tym używa await operatora, aby zawiesić jego `AccessTheWebAsync`postęp i wydajność kontroli do metody, która wywoływana . `AccessTheWebAsync`zwraca `Task(Of Integer)` a do wywołującego. Zadanie przedstawia obietnicę utworzenia w wyniku liczby całkowitej, która jest długością pobranego ciągu.

    > [!NOTE]
    > Jeśli `GetStringAsync` (i `getStringTask`dlatego) zostanie `AccessTheWebAsync` zakończona przed czeka, `AccessTheWebAsync`kontrola pozostaje w . Koszt zawieszenia, a następnie powrót `AccessTheWebAsync` do zostaną zmarnowane, jeśli wywołany`getStringTask`proces asynchroniczne ( ) został już ukończony i AccessTheWebSync nie trzeba czekać na wynik końcowy.

     Przetwarzanie wzorca jest kontynuowane wewnątrz elementu wywołującego (programu obsługi zdarzeń w tym przykładzie). Obiekt wywołujący może wykonać inną pracę, która `AccessTheWebAsync` nie zależy od wyniku sprzed oczekiwania na ten wynik lub obiekt wywołujący może czekać natychmiast.   Program obsługi zdarzeń oczekuje `AccessTheWebAsync`na `AccessTheWebAsync` program i `GetStringAsync`oczekuje na program .

7. `GetStringAsync`kończy i daje wynik ciągu. Wynik ciągu nie jest zwracany `GetStringAsync` przez wywołanie w sposób, który można oczekiwać. (Należy pamiętać, że metoda zwróciła już zadanie w kroku 3.) Zamiast tego wynik ciągu jest przechowywany w zadaniu, które `getStringTask`reprezentuje ukończenie metody, . Operator await pobiera wynik `getStringTask`z . Instrukcja przypisania przypisuje pobrany `urlContents`wynik do pliku .

8. Gdy `AccessTheWebAsync` ma wynik ciągu, metoda może obliczyć długość ciągu. Następnie praca `AccessTheWebAsync` jest również zakończona, a program obsługi zdarzeń oczekiwania można wznowić. W pełnym przykładzie na końcu tematu można zobaczyć, że program obsługi zdarzeń pobiera i drukuje wynikową wartość długości.

Jeśli dopiero zaczynasz przygodę z programowaniem asynchronicznym, zastanów się przez chwilę, jaka jest różnica między zachowaniem synchronicznym i asynchronicznym. Metoda synchroniczna kończy działanie, gdy praca jest zakończona (krok 5), natomiast metoda asynchroniczna zwraca wartość zadania, gdy jej praca jest zawieszona (kroki 3 i 6). Gdy metoda async ukończy pracę, zadanie jest oznaczane jako ukończone, a wynik, o ile istnieje, jest zapisywany w zadaniu.

Aby uzyskać więcej informacji na temat przepływu sterowania, zobacz [Przepływ sterowania w programach Asynchronii (Visual Basic)](control-flow-in-async-programs.md).

## <a name="api-async-methods"></a><a name="BKMK_APIAsyncMethods"></a>Metody asynchronizowe API

Możesz się zastanawiać, gdzie `GetStringAsync` można znaleźć metody, takie jak obsługa programowania asynchroniowego. Program .NET Framework 4.5 lub nowszy zawiera wiele elementów członkowskich, które współpracują z programem `Async` i . `Await` Można rozpoznać tych członków przez "Async" sufiks, który jest dołączony <xref:System.Threading.Tasks.Task> do nazwy elementu członkowskiego i typu zwrotu lub [Task (Of TResult)](xref:System.Threading.Tasks.Task%601). Na przykład `System.IO.Stream` klasa zawiera metody, <xref:System.IO.Stream.ReadAsync%2A>takie <xref:System.IO.Stream.WriteAsync%2A> jak <xref:System.IO.Stream.CopyToAsync%2A>, i obok <xref:System.IO.Stream.CopyTo%2A> <xref:System.IO.Stream.Read%2A>metod <xref:System.IO.Stream.Write%2A>synchronicznych , i .

Środowisko wykonawcze systemu Windows zawiera również `Async` wiele `Await` metod, których można używać z aplikacjami systemu Windows i w nich. Aby uzyskać więcej informacji i przykładowych metod, zobacz [Wywołanie asynchronicznych interfejsów API w języku C# lub Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [programowanie asynchroniczne (aplikacje środowiska wykonawczego systemu Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10))i [WhenAny: Mostkowanie między programem .NET Framework a czasem wykonywania systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).

## <a name="threads"></a><a name="BKMK_Threads"></a>Wątków

Metody async mają być operacjami niepowodującymi blokowania. Wyrażenie `Await` w metodzie asynchronicznego nie blokuje bieżącego wątku, gdy oczekiwane zadanie jest uruchomione. Zamiast tego, wyrażenie rejestruje pozostałą część metody jako kontynuację i przekazuje sterowanie do obiektu wywołującego metody async.

I `Async` `Await` słowa kluczowe nie powodują tworzenia dodatkowych wątków. Metody asynchroniczne nie wymagają wielowątkowego wątku, ponieważ metoda asynchroniza nie jest uruchamiana na własnym wątku. Metoda działa w bieżącym kontekście synchronizacji i używa czasu wątku, tylko wtedy, gdy jest aktywna. Można użyć <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> do przeniesienia pracy związanej z procesorem CPU do wątku w tle, ale wątek w tle nie pomaga w procesie, który tylko czeka na wyniki stają się dostępne.

Podejście async do programowania asynchronicznego jest preferowane prawie w każdym przypadku. W szczególności to podejście <xref:System.ComponentModel.BackgroundWorker> jest lepsze niż w przypadku operacji związanych z we/wy, ponieważ kod jest prostszy i nie trzeba chronić przed warunkami wyścigu. W połączeniu <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>z programowaniem asynchroniowym jest lepsze niż <xref:System.ComponentModel.BackgroundWorker> w przypadku operacji związanych z procesorem `Task.Run` CPU, ponieważ programowanie asynchroniowe oddziela szczegóły koordynacji uruchamiania kodu od pracy, która jest transferowa do wątku.

## <a name="async-and-await"></a><a name="BKMK_AsyncandAwait"></a>Async i Czekają

Jeśli określisz, że metoda jest metodą asynchronizacjową przy użyciu modyfikatora [Asynchronii,](../../../../visual-basic/language-reference/modifiers/async.md) należy włączyć następujące dwie możliwości.

- Oznaczona metoda asynchronii może użyć [Await](../../../../visual-basic/language-reference/operators/await-operator.md) do wyznaczenia punktów zawieszenia. Operator await informuje kompilator, że metoda async nie może kontynuować działania do chwili zakończenia procesu asynchronicznego, na który oczekuje. W międzyczasie sterowanie powraca do obiektu wywołującego metodę async.

  Zawieszenie metody asynchronii `Await` w wyrażeniu nie stanowi wyjścia `Finally` z metody i bloki nie są uruchamiane.

- Metoda oznaczona jako async sama może być oczekiwana przez metody, które ją wywołują.

Metoda asynchronizowana zazwyczaj zawiera jedno `Await` lub więcej wystąpień `Await` operatora, ale brak wyrażeń nie powoduje błędu kompilatora. Jeśli metoda asynchroniza nie `Await` używa operatora do oznaczania punktu zawieszenia, metoda jest wykonywana jako `Async` metoda synchroniczne, pomimo modyfikatora. Kompilator generuje ostrzeżenia dla takich metod.

`Async`i `Await` są kontekstowymi słowami kluczowymi. Aby uzyskać więcej informacji i przykładów, zobacz następujący temat:

- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Poczekaj na operatora](../../../../visual-basic/language-reference/operators/await-operator.md)

## <a name="return-types-and-parameters"></a><a name="BKMK_ReturnTypesandParameters"></a>Typy i parametry zwrotu

W programowaniu .NET Framework metoda asynchroniza zazwyczaj zwraca zadanie <xref:System.Threading.Tasks.Task> lub [zadanie(TResult)](xref:System.Threading.Tasks.Task%601). Wewnątrz metody asynchronicznego `Await` operator jest stosowany do zadania, które jest zwracane z wywołania do innej metody asynchronicznego.

[Zadanie(TResult)](xref:System.Threading.Tasks.Task%601) należy określić jako typ zwracany, jeśli metoda zawiera instrukcję `TResult` [Return,](../../../../visual-basic/language-reference/statements/return-statement.md) która określa operę typu .

Typ `Task` zwracany jest używany jako typ zwracany, jeśli metoda nie ma instrukcji return lub ma instrukcję return, która nie zwraca operandu.

Poniższy przykład pokazuje, jak zadeklarować i wywołać metodę, która <xref:System.Threading.Tasks.Task>zwraca [Task(Of TResult)](xref:System.Threading.Tasks.Task%601) lub:

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

Metoda asynchroniowa może `Sub` być również metodą. Ten typ zwracany jest używany głównie do definiowania programów obsługi zdarzeń, gdzie wymagany jest typ zwracany. Programy async obsługi zdarzeń często służą jako punkt wejścia dla programów async.

Metoda asynchronizacza, `Sub` która jest procedura nie można oczekiwać, a wywołujący nie można złapać żadnych wyjątków, które zgłasza metoda.

Metoda asynchroniowa nie może zadeklarować parametrów [ByRef,](../../../../visual-basic/language-reference/modifiers/byref.md) ale metoda może wywoływać metody, które mają takie parametry.

Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types (Visual Basic)](async-return-types.md). Aby uzyskać więcej informacji na temat sposobu wychwytuj wyjątki w metodach asynchronizacyjnych, zobacz [Wypróbuj... Złapać... Wreszcie Oświadczenie](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Asynchroniczne interfejsy API w programowaniu środowiska wykonawczego systemu Windows mają jeden z następujących typów zwracanych, które są podobne do zadań:

- [IAsyncOperation(Of TResult),](xref:Windows.Foundation.IAsyncOperation%601)który odpowiada [Task(Of TResult)](xref:System.Threading.Tasks.Task%601)
- <xref:Windows.Foundation.IAsyncAction>, co odpowiada<xref:System.Threading.Tasks.Task>
- [IAsyncActionWithProgress(Of TProgress)](xref:Windows.Foundation.IAsyncActionWithProgress%601)
- [IAsyncOperationWithProgress(Of TResult, TProgress)](xref:Windows.Foundation.IAsyncOperationWithProgress%602)

Aby uzyskać więcej informacji i przykład, zobacz [Wywołanie asynchronicznych interfejsów API w języku C# lub Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).

## <a name="naming-convention"></a><a name="BKMK_NamingConvention"></a>Konwencja nazewnictwa

Zgodnie z konwencją należy dołączyć "Async" do `Async` nazw metod, które mają modyfikator.

Można zignorować konwencję, gdy zdarzenie, klasa bazowa lub kontrakt interfejsu sugeruje inną nazwę. Na przykład nie należy zmieniać nazwy typowych programów obsługi zdarzeń, takich jak `Button1_Click`.

## <a name="related-topics-and-samples-visual-studio"></a><a name="BKMK_RelatedTopics"></a>Tematy pokrewne i przykłady (Visual Studio)

|Tytuł|Opis|Sample|
|-----------|-----------------|------------|
|[Przewodnik: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwania (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)|Przedstawia, w jaki sposób konwertować synchroniczne rozwiązanie WPF do asynchronicznego rozwiązania WPF. Ta aplikacja pobiera szereg witryn sieci Web.|[Przykład asynchronii: uzyskiwanie dostępu do przewodnika sieci Web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Jak: Rozszerzenie przewodnika Async za pomocą task.whenall (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Dodaje <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do poprzedniego przewodnika. Korzystanie z `WhenAll` rozpoczyna wszystkie pliki do pobrania w tym samym czasie.||
|[Jak: Tworzenie wielu żądań sieci Web równolegle przy użyciu asynchronii i oczekiwania (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ilustruje, jak uruchomić kilka zadań w tym samym czasie.|[Przykład asynchronii: równoczesne żądania sieci Web](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Typy zwrotów asynchronii (Visual Basic)](async-return-types.md)|Ilustruje typy zwracane przez metody async i wyjaśnia, kiedy poszczególne typy są odpowiednie.||
|[Przepływ sterowania w programach Asynchronii (Visual Basic)](control-flow-in-async-programs.md)|Śledzi szczegółowo przepływ sterowania w serii wyrażeń await w programie asynchronicznym.|[Próbka asynchroniowa: przepływ sterowania w programach asynchronizowych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Dostrajanie aplikacji asynchronii (Visual Basic)](fine-tuning-your-async-application.md)|Przedstawia, w jaki sposób dodać następujące funkcje do rozwiązania async:<br /><br /> - [Anulowanie zadania asynchronicznego lub listy zadań (visual basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Anulowanie zadań asynchronizacyjnych po pewnym czasie (visual basic)](cancel-async-tasks-after-a-period-of-time.md)<br />- [Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Uruchamianie wielu zadań asynchronizowania i przetwarzanie ich po ich zakończeniu (visual basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Przykład asynchronii: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Obsługa reentrancy w aplikacjach Async (Visual Basic)](handling-reentrancy-in-async-apps.md)|Pokazuje, jak obsługiwać przypadki, w których aktywna operacja asynchroniza jest ponownie uruchamiana podczas jej uruchamiania.||
|[WhenAny: Łączenie między programem .NET Framework a czasem wykonywania systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Pokazuje, jak łączyć typy zadań w programie .NET Framework i IAsyncOperations w czasie wykonywania systemu Windows, dzięki czemu można używać z <xref:System.Threading.Tasks.Task.WhenAny%2A> metodą środowiska wykonawczego systemu Windows.|[Przykład asynchronii: Łączenie między .NET i Windows Runtime (AsTask i WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|
|Anulowanie asynchroniczne: łączenie platformy .NET Framework ze środowiskiem wykonawczym systemu Windows|Pokazuje, jak łączyć typy zadań w programie .NET Framework i IAsyncOperations w czasie wykonywania systemu Windows, dzięki czemu można używać z <xref:System.Threading.CancellationTokenSource> metodą środowiska wykonawczego systemu Windows.|[Przykład asynchronii: Mostkowanie między .NET i Windows Runtime (AsTask & Cancellation)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Korzystanie z asynchronii dla dostępu do plików (Visual Basic)](using-async-for-file-access.md)|Wyświetla listę korzyści wynikających ze stosowania słów kluczowych async i await przy uzyskiwaniu dostępu do plików.||
|[Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Opisano nowy wzorzec asynchronii w .NET Framework. Wzorzec jest <xref:System.Threading.Tasks.Task> oparty na typach i [Task(Of TResult).](xref:System.Threading.Tasks.Task%601)||
|[Async Filmy na kanale 9](https://channel9.msdn.com/search?term=async+&type=All)|Oferuje łącza do różnych plików wideo dotyczących programowania asynchronicznego.||

## <a name="complete-example"></a><a name="BKMK_CompleteExample"></a>Kompletny przykład

Poniższy kod to plik MainWindow.xaml.vb z aplikacji Windows Presentation Foundation (WPF), który omówiono w tym temacie. Przykład można pobrać z [przykładu Asynchnc: Przykład z "Programowanie asynchroniczne z Async i Await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

[!code-vb[async](~/samples/snippets/standard/async/async-and-await/vb/MainWindow.xaml.vb)]

## <a name="see-also"></a>Zobacz też

- [Poczekaj na operatora](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
