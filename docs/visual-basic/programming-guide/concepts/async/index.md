---
title: Programowanie asynchroniczne z Async i Await
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: b3ca0398936d257612b30828e3048797894ccc20
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163634"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Programowanie asynchroniczne z Async i Await (Visual Basic)

Możesz uniknąć problemów z wydajnością i poprawić ogólny czas odpowiedzi aplikacji, stosując programowanie asynchroniczne. Jednak tradycyjne techniki pisania aplikacji asynchronicznych mogą być skomplikowane, przez co trudne do pisania, debugowania i konserwacji.

W programie Visual Studio 2012 wprowadzono uproszczone podejście, programowanie asynchroniczne, które wykorzystuje obsługę asynchroniczną w .NET Framework 4,5 i wyższym, jak również w środowisko wykonawcze systemu Windows. Kompilator wykonuje trudną pracę, którą kiedyś wykonywał programista, a aplikacja zachowuje strukturę logiczną przypominającą kod synchroniczny. W efekcie masz wszystkie korzyści wynikające z programowania asynchronicznego przy ułamkowym nakładzie pracy.

Ten temat zawiera omówienie, kiedy i jak stosować programowanie async oraz zawiera łącza do tematów zawierających szczegółowe informacje oraz przykłady.

## <a name="BKMK_WhentoUseAsynchrony"></a>Asynchroniczne zwiększenie czasu odpowiedzi

Asynchroniczność jest istotna dla działań, które mogą powodować blokowanie, na przykład, gdy aplikacja uzyskuje dostęp do sieci Web. Dostęp do zasobów sieci Web bywa powolny lub opóźniony. Jeśli takie działanie jest zablokowane w procesie synchronicznym, cała aplikacji musi czekać. W procesie asynchronicznym aplikacja może kontynuować wykonywanie innych zadań, które nie są zależne od zasobów sieci Web, do momentu zakończeniem zadania mogącego powodować blokowanie.

W poniższej tabeli przedstawiono typowe obszary, w których programowanie asynchroniczne poprawia czas odpowiedzi. Wymienione interfejsy API z .NET Framework 4,5 i środowisko wykonawcze systemu Windows zawierają metody, które obsługują programowanie asynchroniczne.

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

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Metody asynchroniczne są łatwiejsze do zapisu

Słowa kluczowe [Async](../../../../visual-basic/language-reference/modifiers/async.md) i [await](../../../../visual-basic/language-reference/operators/await-operator.md) w Visual Basic są sercem programowania asynchronicznego. Korzystając z tych dwóch słów kluczowych, można użyć zasobów w .NET Framework lub środowisko wykonawcze systemu Windows do tworzenia asynchronicznej metody niemal możliwie jak w przypadku tworzenia metody synchronicznej. Metody asynchroniczne zdefiniowane przy użyciu `Async` i `Await` są nazywane metodami asynchronicznymi.

W poniższym przykładzie przedstawiono metodę async. Prawie wszystko w kodzie powinno wyglądać znajomo. Komentarze wywołują funkcje dodawane przez użytkownika w celu uzyskania asynchroniczności.

Kompletny przykładowy plik Windows Presentation Foundation (WPF) można znaleźć na końcu tego tematu i można pobrać przykład z [przykład Async: przykład z "programowania asynchronicznego z Async i await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

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

Jeśli `AccessTheWebAsync` nie ma żadnej pracy, którą może wykonać między wywołaniem `GetStringAsync` i oczekiwaniem na jego zakończenie, można uprościć kod, wywołując i await w następującej pojedynczej instrukcji.

```vb
Dim urlContents As String = Await client.GetStringAsync()
```

Poniższe cechy podsumowują, co sprawia, że w poprzednim przykładzie metoda async:

- Podpis metody zawiera modyfikator `Async`.
- Nazwa metody async kończy się zwyczajowo sufiksem „Async”.
- Zwracany typ może być jednym z następujących:

  - [Zadanie (of TResult)](xref:System.Threading.Tasks.Task%601) , jeśli metoda zawiera instrukcję return, w której argument operacji ma typ TResult.
  - <xref:System.Threading.Tasks.Task>, jeśli metoda nie zawiera instrukcji return lub zawiera instrukcję return bez operandu.
  - [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) , jeśli piszesz procedurę obsługi zdarzeń asynchronicznych.

  Aby uzyskać więcej informacji, zobacz „Typy zwracane i parametry” w dalszej części tego tematu.

- Metoda zazwyczaj zawiera co najmniej jedno wyrażenie „await”, które oznacza punkt, w którym metoda nie może kontynuować pracy do czasu ukończenia operacji asynchronicznej. W tym czasie metoda jest zawieszona, a sterowanie powraca do obiektu wywołującego metodę. Następna sekcji tego tematu przedstawia, co się dzieje w punkcie zawieszenia.

W metodzie asynchronicznej używasz podanych słów kluczowych i typów w celu wskazania, co chcesz zrobić, a kompilator zajmie się resztą, w tym śledzeniem tego, co musi się zdarzyć, gdy sterowanie powraca do punktu oczekiwania w metodzie zawieszonej. Niektóre procesy, takie jak pętle i obsługa wyjątków, mogą być trudne do obsłużenia w tradycyjnym kodzie asynchronicznym. W metodzie asynchronicznej wpisujesz te elementy podobnie jak w rozwiązaniu synchronicznym i problem rozwiązany.

Aby uzyskać więcej informacji na temat asynchroniczności w poprzednich wersjach .NET Framework, zobacz [TPL i tradycyjne .NET Framework programowanie asynchroniczne](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Co dzieje się w metodzie asynchronicznej

Ważne jest, aby rozumieć programowanie asynchroniczne jako przepływ sterowania od metody do metody. Poniższy diagram przeprowadzi Cię przez proces:

![Diagram przedstawiający śledzenie programów asynchronicznych.](./media/index/navigation-trace-async-program.png)

Liczby na diagramie odpowiadają następującym krokom:

1. Program obsługi zdarzeń wywołuje i czeka na metodę asynchroniczną `AccessTheWebAsync`.

2. `AccessTheWebAsync` tworzy wystąpienie <xref:System.Net.Http.HttpClient> i wywołuje <xref:System.Net.Http.HttpClient.GetStringAsync%2A> metodę asynchroniczną, aby pobrać zawartość witryny sieci Web jako ciąg.

3. Coś się dzieje w `GetStringAsync`, które zawiesza postępy. Być może metoda musi czekać na pobranie strony internetowej lub inne działanie blokujące. Aby uniknąć blokowania zasobów, `GetStringAsync` przekazuje kontrolę do obiektu wywołującego, `AccessTheWebAsync`.

     `GetStringAsync` zwraca [zadanie (z TResult)](xref:System.Threading.Tasks.Task%601) , gdzie TResult jest ciągiem, a `AccessTheWebAsync` przypisuje zadanie do zmiennej `getStringTask`. Zadanie reprezentuje proces trwającego wywołania `GetStringAsync`, z zobowiązaniem do utworzenia rzeczywistej wartości ciągu po zakończeniu pracy.

4. Ponieważ `getStringTask` nie została jeszcze zainicjowana, `AccessTheWebAsync` może kontynuować pracę z innymi zadaniami, które nie zależą od końcowego wyniku `GetStringAsync`. To działanie jest reprezentowane przez wywołanie metody synchronicznej `DoIndependentWork`.

5. `DoIndependentWork` to metoda synchroniczna, która wykonuje jej działanie i powraca do obiektu wywołującego.

6. `AccessTheWebAsync` zabrakło pracy, którą może wykonać bez wyniku z `getStringTask`. `AccessTheWebAsync` dalej chce obliczyć i zwrócić długość pobranego ciągu, ale metoda nie może obliczyć tej wartości, dopóki metoda nie ma ciągu.

     W związku z tym, `AccessTheWebAsync` używa operatora await, aby zawiesić postęp i przekazać kontrolę do metody, która wywołała `AccessTheWebAsync`. `AccessTheWebAsync` zwraca `Task(Of Integer)` do obiektu wywołującego. Zadanie przedstawia obietnicę utworzenia w wyniku liczby całkowitej, która jest długością pobranego ciągu.

    > [!NOTE]
    > Jeśli `GetStringAsync` (i w związku z tym `getStringTask`) zostało zakończone przed `AccessTheWebAsync` czeka na to, formant pozostanie w `AccessTheWebAsync`. Koszt zawieszenia, a następnie powrotu do `AccessTheWebAsync` byłby tracony, jeśli wywołany proces asynchroniczny (`getStringTask`) został już ukończony i AccessTheWebSync nie musi czekać na wynik końcowy.

     Przetwarzanie wzorca jest kontynuowane wewnątrz elementu wywołującego (programu obsługi zdarzeń w tym przykładzie). Obiekt wywołujący może wykonywać inne zadania, które nie są zależne od wyniku `AccessTheWebAsync` przed oczekiwaniem na ten wynik, lub obiekt wywołujący może natychmiast oczekiwać.   Program obsługi zdarzeń oczekuje na `AccessTheWebAsync`, a `AccessTheWebAsync` oczekuje na `GetStringAsync`.

7. `GetStringAsync` uzupełnia i generuje wynik w postaci ciągu. Wynik ciągu nie jest zwracany przez wywołanie do `GetStringAsync` w oczekiwany sposób. (Należy pamiętać, że metoda zwróciła już zadanie w kroku 3). Zamiast tego wynik w postaci ciągu jest przechowywany w zadaniu, które reprezentuje zakończenie metody, `getStringTask`. Operator await pobiera wynik z `getStringTask`. Instrukcja przypisania przypisuje pobrany wynik do `urlContents`.

8. Gdy `AccessTheWebAsync` ma wynik ciągu, Metoda może obliczyć długość ciągu. Następnie zakończenie pracy `AccessTheWebAsync` jest również możliwe, a procedura obsługi zdarzeń oczekujących może zostać wznowiona. W pełnym przykładzie na końcu tematu można zobaczyć, że program obsługi zdarzeń pobiera i drukuje wynikową wartość długości.

Jeśli dopiero zaczynasz przygodę z programowaniem asynchronicznym, zastanów się przez chwilę, jaka jest różnica między zachowaniem synchronicznym i asynchronicznym. Metoda synchroniczna kończy działanie, gdy praca jest zakończona (krok 5), natomiast metoda asynchroniczna zwraca wartość zadania, gdy jej praca jest zawieszona (kroki 3 i 6). Gdy metoda async ukończy pracę, zadanie jest oznaczane jako ukończone, a wynik, o ile istnieje, jest zapisywany w zadaniu.

Aby uzyskać więcej informacji o przepływie sterowania, zobacz [Flow Control in Async Programs (Visual Basic)](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>Metody asynchroniczne interfejsu API

Być może zastanawiasz się, gdzie można znaleźć metody, takie jak `GetStringAsync`, które obsługują programowanie asynchroniczne. .NET Framework 4,5 lub nowszy zawiera wiele elementów członkowskich, które współpracują z `Async` i `Await`. Można rozpoznać te składowe za pomocą sufiksu "Async", który jest dołączony do nazwy elementu członkowskiego i zwracanego typu <xref:System.Threading.Tasks.Task> lub [zadania (z TResult)](xref:System.Threading.Tasks.Task%601). Na przykład Klasa `System.IO.Stream` zawiera metody, takie jak <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>i <xref:System.IO.Stream.WriteAsync%2A> obok metod synchronicznych <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>i <xref:System.IO.Stream.Write%2A>.

Środowisko wykonawcze systemu Windows również zawiera wiele metod, których można używać z `Async` i `Await` w aplikacjach systemu Windows. Aby uzyskać więcej informacji i przykładowe metody, zobacz [wywoływanie asynchronicznych interfejsów API w C# programie lub Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [programowanie asynchroniczne (aplikacje środowisko wykonawcze systemu Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10))i [WhenAny: mostkowanie między .NET Framework i środowisko wykonawcze systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).

## <a name="BKMK_Threads"></a>Wątk

Metody async mają być operacjami niepowodującymi blokowania. Wyrażenie `Await` w metodzie asynchronicznej nie blokuje bieżącego wątku, gdy oczekiwane zadanie jest uruchomione. Zamiast tego, wyrażenie rejestruje pozostałą część metody jako kontynuację i przekazuje sterowanie do obiektu wywołującego metody async.

Słowa kluczowe `Async` i `Await` nie powodują tworzenia dodatkowych wątków. Metody asynchroniczne nie wymagają wielowątkowości, ponieważ Metoda async nie jest uruchamiana we własnym wątku. Metoda działa w bieżącym kontekście synchronizacji i używa czasu wątku, tylko wtedy, gdy jest aktywna. Za pomocą <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> można przenieść zadania powiązane z PROCESORem do wątku w tle, ale wątek w tle nie jest w stanie pomóc w przypadku procesu, który tylko oczekuje na dostępność wyników.

Podejście async do programowania asynchronicznego jest preferowane prawie w każdym przypadku. W szczególności ta metoda jest lepsza niż <xref:System.ComponentModel.BackgroundWorker> dla operacji we/wy, ponieważ kod jest prostszy i nie trzeba chronić przed warunkami wyścigu. W połączeniu z <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>programowanie asynchroniczne jest lepsze niż <xref:System.ComponentModel.BackgroundWorker> w przypadku operacji związanych z PROCESORem, ponieważ programowanie asynchroniczne oddziela szczegóły koordynacji uruchamiania kodu z pracy, która `Task.Run` transferuje do puli wątków.

## <a name="BKMK_AsyncandAwait"></a>Async i await

Jeśli określisz, że metoda jest metodą asynchroniczną przy użyciu modyfikatora [asynchronicznego](../../../../visual-basic/language-reference/modifiers/async.md) , włączasz następujące dwie możliwości.

- Oznaczona Metoda async może użyć [oczekiwania](../../../../visual-basic/language-reference/operators/await-operator.md) do wyznaczenia punktów zawieszenia. Operator await informuje kompilator, że metoda async nie może kontynuować działania do chwili zakończenia procesu asynchronicznego, na który oczekuje. W międzyczasie sterowanie powraca do obiektu wywołującego metodę async.

  Zawieszenie metody asynchronicznej w wyrażeniu `Await` nie stanowi wyjścia z metody, a bloki `Finally` nie są uruchamiane.

- Metoda oznaczona jako async sama może być oczekiwana przez metody, które ją wywołują.

Metoda async zwykle zawiera co najmniej jedno wystąpienie operatora `Await`, ale brak wyrażeń `Await` nie powoduje błędu kompilatora. Jeśli Metoda asynchroniczna nie używa operatora `Await`, aby oznaczyć punkt zawieszenia, metoda jest wykonywana jako metoda synchroniczna, pomimo modyfikatora `Async`. Kompilator generuje ostrzeżenia dla takich metod.

`Async` i `Await` są kontekstowymi słowami kluczowymi. Aby uzyskać więcej informacji i przykładów, zobacz następujący temat:

- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Await, operator](../../../../visual-basic/language-reference/operators/await-operator.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Typy zwracane i parametry

W .NET Framework programowaniu Metoda async zwykle zwraca <xref:System.Threading.Tasks.Task> lub [zadanie (z TResult)](xref:System.Threading.Tasks.Task%601). Wewnątrz metody asynchronicznej do zadania, które jest zwracane z wywołania innej metody asynchronicznej, jest stosowany operator `Await`.

Należy określić [zadanie (of TResult)](xref:System.Threading.Tasks.Task%601) jako typ zwracany, jeśli metoda zawiera instrukcję [Return](../../../../visual-basic/language-reference/statements/return-statement.md) , która określa operand typu `TResult`.

Użyj `Task` jako zwracanego typu, jeśli metoda nie ma instrukcji return lub zawiera instrukcję return, która nie zwraca operandu.

Poniższy przykład pokazuje, jak zadeklarować i wywołać metodę, która zwraca [zadanie (z TResult)](xref:System.Threading.Tasks.Task%601) lub <xref:System.Threading.Tasks.Task>:

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

Metoda async może być również metodą `Sub`. Ten typ zwracany jest używany głównie do definiowania programów obsługi zdarzeń, gdy wymagany jest typ zwracany. Programy async obsługi zdarzeń często służą jako punkt wejścia dla programów async.

Nie można oczekiwać metody asynchronicznej, która jest procedura `Sub`, a obiekt wywołujący nie może przechwycić żadnych wyjątków zgłaszanych przez metodę.

Metoda async nie może deklarować parametrów [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) , ale metoda może wywoływać metody, które mają takie parametry.

Aby uzyskać więcej informacji i przykładów, zobacz [asynchroniczne typy zwracane (Visual Basic)](async-return-types.md). Aby uzyskać więcej informacji o sposobie przechwytywania wyjątków w metodach asynchronicznych, zobacz [try... Catch... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Asynchroniczne interfejsy API w programowaniu środowisko wykonawcze systemu Windows mają jeden z następujących typów zwracanych, które są podobne do zadań:

- [IAsyncOperation (of TResult)](xref:Windows.Foundation.IAsyncOperation%601), który odnosi się do [zadania (of TResult)](xref:System.Threading.Tasks.Task%601)
- <xref:Windows.Foundation.IAsyncAction>, który odnosi się do <xref:System.Threading.Tasks.Task>
- [IAsyncActionWithProgress (z TProgress)](xref:Windows.Foundation.IAsyncActionWithProgress%601)
- [IAsyncOperationWithProgress (of TResult, TProgress)](xref:Windows.Foundation.IAsyncOperationWithProgress%602)

Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [wywoływanie asynchronicznych interfejsów API w programie C# lub Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).

## <a name="BKMK_NamingConvention"></a>Konwencja nazewnictwa

Zgodnie z Konwencją, należy dołączyć "Async" do nazw metod, które mają modyfikator `Async`.

Można zignorować konwencję, gdy zdarzenie, klasa bazowa lub kontrakt interfejsu sugeruje inną nazwę. Na przykład nie należy zmieniać nazw często używanych procedur obsługi zdarzeń, takich jak `Button1_Click`.

## <a name="BKMK_RelatedTopics"></a>Tematy pokrewne i przykłady (Visual Studio)

|Tytuł|Opis|Przykład|
|-----------|-----------------|------------|
|[Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)|Przedstawia, w jaki sposób konwertować synchroniczne rozwiązanie WPF do asynchronicznego rozwiązania WPF. Ta aplikacja pobiera szereg witryn sieci Web.|[Przykład asynchroniczny: uzyskiwanie dostępu do przewodnika dla sieci Web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Instrukcje: Rozszerzonie procedury asynchronicznej za pomocą Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Dodaje <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do poprzedniego przewodnika. Użycie `WhenAll` uruchamia wszystkie pliki do pobrania w tym samym czasie.||
|[Instrukcje: równoległe żądania sieci Web za pomocą Async i Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ilustruje, jak uruchomić kilka zadań w tym samym czasie.|[Przykład Async: równoległe wykonywanie wielu żądań sieci Web](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Asynchroniczne typy zwracane (Visual Basic)](async-return-types.md)|Ilustruje typy zwracane przez metody async i wyjaśnia, kiedy poszczególne typy są odpowiednie.||
|[Przepływ sterowania w programach asynchronicznych (Visual Basic)](control-flow-in-async-programs.md)|Śledzi szczegółowo przepływ sterowania w serii wyrażeń await w programie asynchronicznym.|[Przykład asynchroniczny: przepływ sterowania w programach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Dostrajanie aplikacji asynchronicznej (Visual Basic)](fine-tuning-your-async-application.md)|Przedstawia, w jaki sposób dodać następujące funkcje do rozwiązania async:<br /><br /> - [anulować zadanie asynchroniczne lub listę zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />- [anulować zadania asynchroniczne po upływie czasu (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)<br />- [anulować pozostałe zadania asynchroniczne po zakończeniu jednego (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [uruchomić wiele zadań asynchronicznych i przetworzyć je w miarę ich ukończenia (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Próbka asynchroniczna: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Obsługa współużytkowania wątkowości w aplikacjach asynchronicznych (Visual Basic)](handling-reentrancy-in-async-apps.md)|Pokazuje, jak obsługiwać przypadki, w których aktywna operacja asynchroniczna jest uruchamiana ponownie, gdy jest uruchomiona.||
|[WhenAny: mostkowanie między .NET Framework i środowisko wykonawcze systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Pokazuje, jak połączyć typy zadań w .NET Framework i IAsyncOperations w środowisko wykonawcze systemu Windows, aby można było używać <xref:System.Threading.Tasks.Task.WhenAny%2A> z metodą środowisko wykonawcze systemu Windows.|[Próbka asynchroniczna: mostkowanie między programami .NET i środowisko wykonawcze systemu Windows (AsTask i WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|
|Anulowanie asynchroniczne: łączenie platformy .NET Framework ze środowiskiem wykonawczym systemu Windows|Pokazuje, jak połączyć typy zadań w .NET Framework i IAsyncOperations w środowisko wykonawcze systemu Windows, aby można było używać <xref:System.Threading.CancellationTokenSource> z metodą środowisko wykonawcze systemu Windows.|[Próbka asynchroniczna: mostkowanie między programami .NET i środowisko wykonawcze systemu Windows (anulowanie & AsTask)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Używanie Async na potrzeby dostępu do plików (Visual Basic)](using-async-for-file-access.md)|Wyświetla listę korzyści wynikających ze stosowania słów kluczowych async i await przy uzyskiwaniu dostępu do plików.||
|[Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Opisano nowy wzorzec asynchronii w .NET Framework. Wzorzec jest oparty na typach <xref:System.Threading.Tasks.Task> i [Task (of TResult)](xref:System.Threading.Tasks.Task%601) .||
|[Asynchroniczne wideo w kanale 9](https://channel9.msdn.com/search?term=async+&type=All)|Oferuje łącza do różnych plików wideo dotyczących programowania asynchronicznego.||

## <a name="BKMK_CompleteExample"></a>Pełny przykład

Poniższy kod to plik MainWindow. XAML. vb z aplikacji Windows Presentation Foundation (WPF), którą omówiono w tym temacie. Możesz pobrać przykład z przykładu [asynchronicznego: przykład z "programowania asynchronicznego z Async i await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

[!code-vb[async](~/samples/async/async-and-await/vb/MainWindow.xaml.vb)]

## <a name="see-also"></a>Zobacz także

- [Await, operator](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
