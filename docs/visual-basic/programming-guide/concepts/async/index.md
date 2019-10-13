---
title: Programowanie asynchroniczne z Async i Await (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: 9632ee7d275e6641bcd334aa12cded44920d2fda
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291654"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Programowanie asynchroniczne z Async i Await (Visual Basic)

Można uniknąć wąskich gardeł wydajności i zwiększyć całkowity czas odpowiedzi aplikacji przy użyciu programowania asynchronicznego. Jednak tradycyjne techniki pisania aplikacji asynchronicznych mogą być skomplikowane, co utrudnia ich pisanie, debugowanie i konserwowanie.

W programie Visual Studio 2012 wprowadzono uproszczone podejście, programowanie asynchroniczne, które wykorzystuje obsługę asynchroniczną w .NET Framework 4,5 i wyższym, jak również w środowisko wykonawcze systemu Windows. Kompilator wykonuje trudne działania wykonywane przez dewelopera, a aplikacja zachowuje strukturę logiczną przypominającą kod synchroniczny. W związku z tym uzyskujesz wszystkie zalety programowania asynchronicznego z częścią nakładu pracy.

Ten temat zawiera informacje o tym, kiedy i jak używać programowania asynchronicznego i zawiera linki do pomocy technicznej zawierającej szczegóły i przykłady.

## <a name="BKMK_WhentoUseAsynchrony"></a>Asynchroniczne zwiększenie czasu odpowiedzi

Asynchroniczności jest istotna dla działań, które są potencjalnie blokowane, na przykład gdy aplikacja uzyskuje dostęp do sieci Web. Dostęp do zasobu sieci Web czasami jest powolny lub opóźniony. Jeśli takie działanie jest zablokowane w procesie synchronicznym, cała aplikacja musi czekać. W procesie asynchronicznym aplikacja może kontynuować pracę z innymi zadaniami, które nie są zależne od zasobu sieci Web, dopóki nie zakończy się zadanie potencjalnie blokujące.

W poniższej tabeli przedstawiono typowe obszary, w których programowanie asynchroniczne poprawia czas odpowiedzi. Wymienione interfejsy API z .NET Framework 4,5 i środowisko wykonawcze systemu Windows zawierają metody, które obsługują programowanie asynchroniczne.

|Obszar aplikacji|Obsługa interfejsów API, które zawierają metody asynchroniczne|
|----------------------|------------------------------------------------|
|Dostęp do sieci Web|<xref:System.Net.Http.HttpClient>, <xref:Windows.Web.Syndication.SyndicationClient>|
|Praca z plikami|<xref:Windows.Storage.StorageFile>, <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|
|Praca z obrazami|<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|Programowanie WCF|[Operacje synchroniczne i asynchroniczne](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)|
|||

Asynchroniczności okazuje się szczególnie cenne dla aplikacji, które uzyskują dostęp do wątku interfejsu użytkownika, ponieważ wszystkie działania związane z interfejsem użytkownika zwykle współdzielą jeden wątek. W przypadku zablokowania dowolnego procesu w aplikacji synchronicznej wszystkie są blokowane. Aplikacja przestanie odpowiadać i może zakończyć się niepowodzeniem, gdy tylko oczekuje.

W przypadku używania metod asynchronicznych aplikacja nadal odpowiada na interfejs użytkownika. Można zmienić rozmiar lub zminimalizować okno, na przykład lub zamknąć aplikację, jeśli nie chcesz czekać na jej zakończenie.

Podejście asynchroniczne dodaje odpowiednik automatycznej transmisji do listy opcji, które można wybrać podczas projektowania operacji asynchronicznych. Oznacza to, że masz wszystkie zalety tradycyjnego programowania asynchronicznego, ale znacznie mniej wysiłku od dewelopera.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Metody asynchroniczne są łatwiejsze do zapisu

Słowa kluczowe [Async](../../../../visual-basic/language-reference/modifiers/async.md) i [await](../../../../visual-basic/language-reference/operators/await-operator.md) w Visual Basic są sercem programowania asynchronicznego. Korzystając z tych dwóch słów kluczowych, można użyć zasobów w .NET Framework lub środowisko wykonawcze systemu Windows do tworzenia asynchronicznej metody niemal możliwie jak w przypadku tworzenia metody synchronicznej. Metody asynchroniczne zdefiniowane przy użyciu `Async` i `Await` są nazywane metodami asynchronicznymi.

Poniższy przykład przedstawia metodę asynchroniczną. Prawie wszystko w kodzie powinno wyglądać całkowicie znajomo. Komentarze wywołują funkcje dodane do utworzenia asynchroniczności.

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
- Nazwa metody asynchronicznej według Konwencji kończąca się sufiksem "Async".
- Typ zwracany jest jednym z następujących typów:

  - <xref:System.Threading.Tasks.Task%601>, jeśli metoda zawiera instrukcję return, w której operand ma typ TResult.
  - <xref:System.Threading.Tasks.Task>, jeśli metoda nie zawiera instrukcji return lub zawiera instrukcję return bez operandu.
  - [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) , jeśli piszesz procedurę obsługi zdarzeń asynchronicznych.

  Aby uzyskać więcej informacji, zobacz sekcję "typy zwracane i parametry" w dalszej części tego tematu.

- Metoda zwykle zawiera co najmniej jedno wyrażenie await, które oznacza punkt, w którym metoda nie może kontynuować pracy, dopóki nie zostanie ukończona oczekująca operacja asynchroniczna. W międzyczasie Metoda jest zawieszona, a sterowanie powraca do obiektu wywołującego metody. Następna sekcja tego tematu przedstawia, co się dzieje w punkcie zawieszenia.

W metodach asynchronicznych należy użyć podanych słów kluczowych i typów w celu wskazania, co chcesz zrobić, a kompilator wykonuje resztę, w tym śledzenie tego, co musi się zdarzyć, gdy sterowanie powraca do punktu oczekiwania w metodzie zawieszonej. Niektóre rutynowe procesy, takie jak pętle i obsługa wyjątków, mogą być trudne do obsłużenia w tradycyjnym kodzie asynchronicznym. W metodzie asynchronicznej napiszesz te elementy podobnie jak w rozwiązaniu synchronicznym i problem zostanie rozwiązany.

Aby uzyskać więcej informacji na temat asynchroniczności w poprzednich wersjach .NET Framework, zobacz [TPL i tradycyjne .NET Framework programowanie asynchroniczne](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Co dzieje się w metodzie asynchronicznej

Najważniejszym aspektem zrozumienia w programowaniu asynchronicznym jest szybkość przepływu sterowania z metody do metody. Poniższy diagram przeprowadzi Cię przez proces:

![Diagram przedstawiający śledzenie programów asynchronicznych.](./media/index/navigation-trace-async-program.png)

Liczby na diagramie odpowiadają następującym krokom:

1. Program obsługi zdarzeń wywołuje i czeka na metodę asynchroniczną `AccessTheWebAsync`.

2. `AccessTheWebAsync` tworzy wystąpienie <xref:System.Net.Http.HttpClient> i wywołuje metodę asynchroniczną <xref:System.Net.Http.HttpClient.GetStringAsync%2A>, aby pobrać zawartość witryny sieci Web jako ciąg.

3. Coś się dzieje w `GetStringAsync`, który zawiesza postęp. Być może trzeba będzie poczekać na pobranie witryny sieci Web lub inne działanie blokujące. Aby uniknąć zablokowania zasobów, `GetStringAsync` daje formant do obiektu wywołującego, `AccessTheWebAsync`.

     `GetStringAsync` zwraca <xref:System.Threading.Tasks.Task%601>, gdzie TResult jest ciągiem, a `AccessTheWebAsync` przypisuje zadanie do zmiennej `getStringTask`. Zadanie reprezentuje proces trwającego wywołania do `GetStringAsync`, z zobowiązaniem do tworzenia rzeczywistej wartości ciągu po zakończeniu pracy.

4. Ponieważ `getStringTask` nie został jeszcze oczekiwany, `AccessTheWebAsync` może kontynuować wykonywanie innych zadań, które nie zależą od końcowego wyniku `GetStringAsync`. To działanie jest reprezentowane przez wywołanie metody synchronicznej `DoIndependentWork`.

5. `DoIndependentWork` to metoda synchroniczna, która wykonuje jej działanie i powraca do obiektu wywołującego.

6. `AccessTheWebAsync` zabrakło pracy, które może wykonać bez wyniku z `getStringTask`. `AccessTheWebAsync` dalej chce obliczyć i zwrócić długość pobranego ciągu, ale metoda nie może obliczyć tej wartości, dopóki metoda nie ma ciągu.

     W związku z tym `AccessTheWebAsync` używa operatora await, aby zawiesić postęp i przekazać kontrolę do metody, która została wywołana `AccessTheWebAsync`. `AccessTheWebAsync` zwraca `Task<int>` (`Task(Of Integer)` w Visual Basic) do obiektu wywołującego. Zadanie reprezentuje obietnicę do utworzenia wyniku całkowitego, który jest długością pobranego ciągu.

    > [!NOTE]
    > Jeśli `GetStringAsync` (i w związku z tym `getStringTask`) zostało zakończone przed `AccessTheWebAsync` czeka na to, formant pozostaje w `AccessTheWebAsync`. Koszt zawieszenia, a następnie powrotu do `AccessTheWebAsync` zostałby zatracony, jeśli wywołany proces asynchroniczny (`getStringTask`) został już ukończony i AccessTheWebSync nie musi czekać na wynik końcowy.

     Wewnątrz obiektu wywołującego (program obsługi zdarzeń w tym przykładzie), wzorzec przetwarzania jest kontynuowany. Obiekt wywołujący może wykonywać inne czynności, które nie są zależne od wyniku `AccessTheWebAsync` przed oczekiwaniem na ten wynik, lub obiekt wywołujący może natychmiast oczekiwać.   Program obsługi zdarzeń oczekuje na `AccessTheWebAsync`, a `AccessTheWebAsync` oczekuje na `GetStringAsync`.

7. `GetStringAsync` uzupełnia i generuje wynik w postaci ciągu. Wynik ciągu nie jest zwracany przez wywołanie `GetStringAsync` w oczekiwany sposób. (Należy pamiętać, że metoda zwróciła już zadanie w kroku 3). Zamiast tego wynik w postaci ciągu jest przechowywany w zadaniu, które reprezentuje zakończenie metody, `getStringTask`. Operator await pobiera wynik z `getStringTask`. Instrukcja przypisania przypisuje pobrany wynik do `urlContents`.

8. Gdy `AccessTheWebAsync` ma wynik ciągu, Metoda może obliczyć długość ciągu. Następnie należy wykonać pracę `AccessTheWebAsync`, a procedura obsługi zdarzeń oczekujących może zostać wznowiona. W pełnym przykładzie na końcu tematu można potwierdzić, że program obsługi zdarzeń pobiera i drukuje wartość wyniku długości.

Jeśli jesteś nowym programem do programowania asynchronicznego, poświęć kilka minut, aby rozważyć różnicę między zachowaniem synchronicznym i asynchronicznym. Metoda synchroniczna zwraca po zakończeniu pracy (krok 5), ale Metoda asynchroniczna zwraca wartość zadania, gdy jej pracę jest wstrzymana (kroki 3 i 6). Gdy metoda async ostatecznie zakończy pracę, zadanie zostanie oznaczone jako ukończone, a wynik, jeśli istnieje, jest przechowywany w zadaniu.

Aby uzyskać więcej informacji o przepływie sterowania, zobacz [Flow Control in Async Programs (Visual Basic)](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>Metody asynchroniczne interfejsu API

Być może zastanawiasz się, gdzie można znaleźć metody, takie jak `GetStringAsync`, które obsługują programowanie asynchroniczne. .NET Framework 4,5 lub nowszy zawiera wielu członków, którzy współpracują z `Async` i `Await`. Można rozpoznać te składowe za pomocą sufiksu "Async", który jest dołączony do nazwy elementu członkowskiego i zwracanego typu <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Na przykład Klasa `System.IO.Stream` zawiera metody takie jak <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A> i <xref:System.IO.Stream.WriteAsync%2A> obok metod synchronicznych <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A> i <xref:System.IO.Stream.Write%2A>.

Środowisko wykonawcze systemu Windows również zawiera wiele metod, których można użyć z `Async` i `Await` w aplikacjach systemu Windows. Aby uzyskać więcej informacji i przykładowe metody, zobacz [wywoływanie asynchronicznych interfejsów API w C# programie lub Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [programowanie asynchroniczne (aplikacje środowisko wykonawcze systemu Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10))i [WhenAny: mostkowanie między .NET Framework i środowisko wykonawcze systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).

## <a name="BKMK_Threads"></a>Wątk

Metody asynchroniczne mają być operacjami nieblokującymi. Wyrażenie `Await` w metodzie asynchronicznej nie blokuje bieżącego wątku, gdy oczekiwane zadanie jest uruchomione. Zamiast tego wyrażenie rejestruje resztę metody jako kontynuację i zwraca kontrolę do obiektu wywołującego metody asynchronicznej.

Słowa kluczowe `Async` i `Await` nie powodują tworzenia dodatkowych wątków. Metody asynchroniczne nie wymagają wielowątkowości, ponieważ Metoda async nie jest uruchamiana we własnym wątku. Metoda jest uruchamiana w bieżącym kontekście synchronizacji i używa czasu na wątku tylko wtedy, gdy metoda jest aktywna. @No__t-0 służy do przenoszenia pracy powiązanej z PROCESORem do wątku w tle, ale wątek w tle nie jest w stanie pomóc w przypadku procesu, który tylko oczekuje na dostępność wyników.

Podejście asynchroniczne do programowania asynchronicznego jest preferowane w przypadku istniejących podejścia niemal w każdym przypadku. W szczególności ta metoda jest lepsza niż <xref:System.ComponentModel.BackgroundWorker> dla operacji we/wy, ponieważ kod jest prostszy i nie trzeba chronić przed warunkami wyścigu. W połączeniu z <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> programowanie asynchroniczne jest lepsze niż <xref:System.ComponentModel.BackgroundWorker> w przypadku operacji związanych z PROCESORem, ponieważ programowanie asynchroniczne oddziela szczegóły koordynacji dotyczące uruchamiania kodu z pracy, która `Task.Run` transferuje do puli wątków.

## <a name="BKMK_AsyncandAwait"></a>Async i await

Jeśli określisz, że metoda jest metodą asynchroniczną przy użyciu modyfikatora [asynchronicznego](../../../../visual-basic/language-reference/modifiers/async.md) , włączasz następujące dwie możliwości.

- Oznaczona Metoda async może użyć [oczekiwania](../../../../visual-basic/language-reference/operators/await-operator.md) do wyznaczenia punktów zawieszenia. Operator await informuje kompilator, że metoda async nie może kontynuować tego punktu do momentu zakończenia procesu asynchronicznego oczekiwania. W międzyczasie sterowanie powraca do obiektu wywołującego metody asynchronicznej.

  Zawieszenie metody asynchronicznej w wyrażeniu `Await` nie stanowi wyjścia z metody, a bloki `Finally` nie są uruchamiane.

- Do oznaczonej metody asynchronicznej można się odczekać przez metody, które ją wywołują.

Metoda async zwykle zawiera co najmniej jedno wystąpienie operatora `Await`, ale brak wyrażeń `Await` nie powoduje błędu kompilatora. Jeśli Metoda asynchroniczna nie używa operatora `Await` do oznaczania punktu zawieszenia, metoda jest wykonywana jako metoda synchroniczna, pomimo modyfikatora `Async`. Kompilator generuje ostrzeżenie dotyczące tych metod.

`Async` i `Await` są kontekstowymi słowami kluczowymi. Aby uzyskać więcej informacji i przykładów, zobacz następujące tematy:

- [Asynchroniczne](../../../../visual-basic/language-reference/modifiers/async.md)
- [Operator await](../../../../visual-basic/language-reference/operators/await-operator.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Typy zwracane i parametry

W .NET Framework programowaniu Metoda async zwykle zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Wewnątrz metody asynchronicznej do zadania, które jest zwracane z wywołania innej metody asynchronicznej, jest stosowany operator `Await`.

Należy określić <xref:System.Threading.Tasks.Task%601> jako typ zwracany, jeśli metoda zawiera instrukcję [Return](../../../../visual-basic/language-reference/statements/return-statement.md) , która określa operand typu `TResult`.

Jeśli metoda nie zawiera instrukcji return lub zawiera instrukcję return, która nie zwraca operandu, należy użyć `Task` jako zwracanego typu.

Poniższy przykład pokazuje, jak zadeklarować i wywołać metodę, która zwraca <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>:

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

Każde zwrócone zadanie reprezentuje bieżące działanie. Zadanie hermetyzuje informacje o stanie procesu asynchronicznego i, ostatecznie, ostateczny wynik procesu lub wyjątek, który wywołuje proces, jeśli nie powiedzie się.

Metoda async może być również metodą `Sub`. Ten typ zwracany jest używany głównie do definiowania programów obsługi zdarzeń, gdy wymagany jest typ zwracany. Procedury obsługi zdarzeń asynchronicznych często służą jako punkt wyjścia dla programów asynchronicznych.

Nie można oczekiwać metody asynchronicznej, która jest procedurą `Sub`, a obiekt wywołujący nie może przechwycić żadnych wyjątków zgłaszanych przez metodę.

Metoda async nie może deklarować parametrów [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) , ale metoda może wywoływać metody, które mają takie parametry.

Aby uzyskać więcej informacji i przykładów, zobacz [asynchroniczne typy zwracane (Visual Basic)](async-return-types.md). Aby uzyskać więcej informacji o sposobie przechwytywania wyjątków w metodach asynchronicznych, zobacz [try... Catch... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Asynchroniczne interfejsy API w programowaniu środowisko wykonawcze systemu Windows mają jeden z następujących typów zwracanych, które są podobne do zadań:

- <xref:Windows.Foundation.IAsyncOperation%601>, który odnosi się do <xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>, który odnosi się do <xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [wywoływanie asynchronicznych interfejsów API w programie C# lub Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).

## <a name="BKMK_NamingConvention"></a>Konwencja nazewnictwa

Zgodnie z Konwencją, należy dołączyć "Async" do nazw metod, które mają modyfikator `Async`.

Można zignorować Konwencję, w której zdarzenie, Klasa bazowa lub kontrakt interfejsu sugeruje inną nazwę. Na przykład nie należy zmieniać nazw często używanych procedur obsługi zdarzeń, takich jak `Button1_Click`.

## <a name="BKMK_RelatedTopics"></a>Tematy pokrewne i przykłady (Visual Studio)

|Tytuł|Opis|Przykład|
|-----------|-----------------|------------|
|[Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)|Pokazuje, w jaki sposób konwertować synchroniczne rozwiązanie WPF do asynchronicznego rozwiązania WPF. Aplikacja pobiera szereg witryn sieci Web.|[Przykład asynchroniczny: uzyskiwanie dostępu do przewodnika dla sieci Web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Instrukcje: Rozszerzonie procedury asynchronicznej za pomocą Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Dodaje <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do poprzedniego przewodnika. Użycie `WhenAll` uruchamia wszystkie pliki do pobrania w tym samym czasie.||
|[Instrukcje: równoległe żądania sieci Web za pomocą Async i Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Pokazuje, jak uruchomić kilka zadań w tym samym czasie.|[Przykład Async: równoległe wykonywanie wielu żądań sieci Web](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Asynchroniczne typy zwracane (Visual Basic)](async-return-types.md)|Ilustruje typy, które metody async mogą zwrócić i wyjaśnia, kiedy każdy typ jest odpowiedni.||
|[Przepływ sterowania w programach asynchronicznych (Visual Basic)](control-flow-in-async-programs.md)|Śledzi szczegółowo przepływ sterowania przez pomyślne wyrażenie await w programie asynchronicznym.|[Przykład asynchroniczny: przepływ sterowania w programach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Dostrajanie aplikacji asynchronicznej (Visual Basic)](fine-tuning-your-async-application.md)|Pokazuje, w jaki sposób dodać następujące funkcje do rozwiązania asynchronicznego:<br /><br /> - [Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Anulowanie zadań asynchronicznych po upływie czasu (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)<br />- [Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w trakcie ich kończenia (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Próbka asynchroniczna: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Obsługa współużytkowania wątkowości w aplikacjach asynchronicznych (Visual Basic)](handling-reentrancy-in-async-apps.md)|Pokazuje, jak obsługiwać przypadki, w których aktywna operacja asynchroniczna jest uruchamiana ponownie, gdy jest uruchomiona.||
|[WhenAny: mostkowanie między .NET Framework i środowisko wykonawcze systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Pokazuje, jak połączyć typy zadań w .NET Framework i IAsyncOperations w środowisko wykonawcze systemu Windows, aby można było użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> z metodą środowisko wykonawcze systemu Windows.|[Próbka asynchroniczna: mostkowanie między programami .NET i środowisko wykonawcze systemu Windows (AsTask i WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|
|Anulowanie asynchroniczne: mostkowanie między .NET Framework i środowisko wykonawcze systemu Windows|Pokazuje, jak połączyć typy zadań w .NET Framework i IAsyncOperations w środowisko wykonawcze systemu Windows, aby można było użyć <xref:System.Threading.CancellationTokenSource> z metodą środowisko wykonawcze systemu Windows.|[Próbka asynchroniczna: mostkowanie między programami .NET i środowisko wykonawcze systemu Windows (anulowanie & AsTask)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Używanie Async na potrzeby dostępu do plików (Visual Basic)](using-async-for-file-access.md)|Wyświetla listę i pokazuje zalety korzystania z funkcji Async i await w celu uzyskania dostępu do plików.||
|[Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Opisuje nowy wzorzec dla asynchroniczności w .NET Framework. Wzorzec jest oparty na typach <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601>.||
|[Asynchroniczne wideo w kanale 9](https://channel9.msdn.com/search?term=async+&type=All)|Oferuje linki do różnych filmów wideo dotyczących programowania asynchronicznego.||

## <a name="BKMK_CompleteExample"></a>Pełny przykład

Poniższy kod to plik MainWindow. XAML. vb z aplikacji Windows Presentation Foundation (WPF), którą omówiono w tym temacie. Możesz pobrać przykład z przykładu [asynchronicznego: przykład z "programowania asynchronicznego z Async i await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

[!code-vb[async](~/samples/async/async-and-await/vb/MainWindow.xaml.vb)]

## <a name="see-also"></a>Zobacz także

- [Operator await](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Asynchroniczne](../../../../visual-basic/language-reference/modifiers/async.md)
