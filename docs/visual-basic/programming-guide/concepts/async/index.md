---
title: Programowanie asynchroniczne z Async i Await (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18e3abb8d010d3766aa1b1239b3d22cc3cb9b47e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Programowanie asynchroniczne z Async i Await (Visual Basic)
Możesz uniknąć problemów z wydajnością i poprawić ogólny czas odpowiedzi aplikacji, stosując programowanie asynchroniczne. Jednak tradycyjne techniki pisania aplikacji asynchronicznych mogą być skomplikowane, przez co trudne do pisania, debugowania i konserwacji.  
  
 Program Visual Studio 2012 wprowadzono metoda uproszczona async — programowanie, wykorzystującego Obsługa komunikacji asynchronicznej w programie .NET Framework 4.5 lub nowszy oraz jak środowiska uruchomieniowego systemu Windows. Kompilator wykonuje trudną pracę, którą kiedyś wykonywał programista, a aplikacja zachowuje strukturę logiczną przypominającą kod synchroniczny. W efekcie masz wszystkie korzyści wynikające z programowania asynchronicznego przy ułamkowym nakładzie pracy.  
  
 Ten temat zawiera omówienie, kiedy i jak stosować programowanie async oraz zawiera łącza do tematów zawierających szczegółowe informacje oraz przykłady.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a>Asynchroniczne skraca czas odpowiedzi  
 Asynchroniczność jest istotna dla działań, które mogą powodować blokowanie, na przykład, gdy aplikacja uzyskuje dostęp do sieci Web. Dostęp do zasobów sieci Web bywa powolny lub opóźniony. Jeśli takie działanie jest zablokowane w procesie synchronicznym, cała aplikacji musi czekać. W procesie asynchronicznym aplikacja może kontynuować wykonywanie innych zadań, które nie są zależne od zasobów sieci Web, do momentu zakończeniem zadania mogącego powodować blokowanie.  
  
 W poniższej tabeli przedstawiono typowe obszary, w których programowanie asynchroniczne poprawia czas odpowiedzi. Interfejsy API na liście z programu .NET Framework 4.5 i środowiska wykonawczego systemu Windows zawiera metody, które obsługują programowanie asynchroniczne.  
  
|Obszar aplikacji|Obsługa interfejsów API, która obejmuje metody asynchroniczne|  
|----------------------|------------------------------------------------|  
|Web access|<xref:System.Net.Http.HttpClient>, [SyndicationClient](http://go.microsoft.com/fwlink/p/?LinkId=259441)|  
|Praca z plikami|[Pliku magazynu](http://go.microsoft.com/fwlink/p/?LinkId=248220), <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>,<xref:System.Xml.XmlReader>|  
|Praca z obrazami|[MediaCapture](http://go.microsoft.com/fwlink/p/?LinkId=261839), [element BitmapEncoder](http://go.microsoft.com/fwlink/p/?LinkId=261840), [BitmapDecoder](http://go.microsoft.com/fwlink/p/?LinkId=261841)|  
|Programowanie WCF|[Operacje synchroniczne i asynchroniczne](http://go.microsoft.com/fwlink/p/?LinkID=192382)|  
|||  
  
 Asynchroniczność okazuje się szczególnie cenna w przypadku aplikacji, które mają dostęp do wątku interfejsu użytkownika, ponieważ wszystkie działania związane z interfejsem użytkownika korzystają zazwyczaj z jednego wątku. Jeśli w aplikacji synchronicznej jest zablokowany jakikolwiek proces, zablokowane są wszystkie procesy. Aplikacja przestanie odpowiadać i możesz dojść do wniosku, że uległa awarii, a tymczasem może po prostu być w stanie oczekiwania.  
  
 Kiedy używasz metod asynchronicznych, aplikacja dalej odpowiada interfejsowi użytkownika. Możesz przykładowo zmienić rozmiar lub zminimalizować aplikację lub możesz ją zamknąć, jeżeli nie chcesz czekać aż zakończy zadanie.  
  
 Podejście async oferuje również odpowiednik automatycznego przejścia do listy opcji do wybrania przy projektowaniu operacji asynchronicznych. Oznacza to, że można korzystać z wszystkich zalet tradycyjnego programowania asynchronicznego, ale przy znacznie mniejszym nakładzie pracy programisty.  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a>Metody asynchroniczne są łatwiejsze do zapisu  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md) i [Await](../../../../visual-basic/language-reference/modifiers/async.md) słów kluczowych w języku Visual Basic są Puls programowania asynchronicznego. Przy użyciu tych dwóch słów kluczowych, można użyć zasobów w programie .NET Framework lub środowiska uruchomieniowego systemu Windows można utworzyć metody asynchronicznej prawie, jak łatwo utworzyć metoda synchroniczna. Metod asynchronicznych, które definiują przy użyciu `Async` i `Await` są określane jako metod asynchronicznych.  
  
 W poniższym przykładzie przedstawiono metodę async. Prawie wszystko w kodzie powinno wyglądać znajomo. Komentarze wywołują funkcje dodawane przez użytkownika w celu uzyskania asynchroniczności.  
  
 Pełny plik przykładowy Windows Presentation Foundation (WPF) na końcu tego tematu można znaleźć i pobrać przykładowy z [próbki Async: przykład z "Asynchronicznego programowania z Async i Await"](http://go.microsoft.com/fwlink/?LinkID=261549).  
  
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
  
 Jeśli `AccessTheWebAsync` nie ma żadnej pracy, które można wykonać między wywoływaniem `GetStringAsync` i oczekujące na jego ukończenie, można uprościć kodu przez wywołanie i oczekuje w następujących jednej instrukcji.  
  
```vb  
Dim urlContents As String = Await client.GetStringAsync()  
```  
  
 Poniższy opis podsumowuje, co sprawia, że poprzedni przykład jest metodą asynchroniczną.  
  
-   Podpis metody zawiera `Async` modyfikator.  
  
-   Nazwa metody async kończy się zwyczajowo sufiksem „Async”.  
  
-   Zwracany typ może być jednym z następujących:  
  
    -   <xref:System.Threading.Tasks.Task%601>Jeśli metodę zawiera instrukcję return, w którym argument operacji ma typ TResult.  
  
    -   <xref:System.Threading.Tasks.Task>Jeśli stosowana metoda ma nie instrukcji return lub instrukcji return zawierającej nie operandu.  
  
    -   [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) pisania asynchronicznej obsługi zdarzeń.  
  
     Aby uzyskać więcej informacji, zobacz „Typy zwracane i parametry” w dalszej części tego tematu.  
  
-   Metoda zazwyczaj zawiera co najmniej jedno wyrażenie „await”, które oznacza punkt, w którym metoda nie może kontynuować pracy do czasu ukończenia operacji asynchronicznej. W tym czasie metoda jest zawieszona, a sterowanie powraca do obiektu wywołującego metodę. Następna sekcji tego tematu przedstawia, co się dzieje w punkcie zawieszenia.  
  
 W metodzie asynchronicznej używasz podanych słów kluczowych i typów w celu wskazania, co chcesz zrobić, a kompilator zajmie się resztą, w tym śledzeniem tego, co musi się zdarzyć, gdy sterowanie powraca do punktu oczekiwania w metodzie zawieszonej. Niektóre procesy, takie jak pętle i obsługa wyjątków, mogą być trudne do obsłużenia w tradycyjnym kodzie asynchronicznym. W metodzie asynchronicznej wpisujesz te elementy podobnie jak w rozwiązaniu synchronicznym i problem rozwiązany.  
  
 Aby uzyskać więcej informacji na temat asynchrony w poprzednich wersjach programu .NET Framework, zobacz [TPL i tradycyjnych .NET Framework asynchronicznego programowania](http://msdn.microsoft.com/library/e7b31170-a156-433f-9f26-b1fc7cd1776f).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Co się stanie w metodzie Async  
 Ważne jest, aby rozumieć programowanie asynchroniczne jako przepływ sterowania od metody do metody. Poniższy diagram ilustruje ten proces.  
  
 ![Śledzenie programu async](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Liczby w diagramie odpowiadają poniższym krokom.  
  
1.  Wywołuje program obsługi zdarzeń i oczekujące na `AccessTheWebAsync` metody asynchronicznej.  
  
2.  `AccessTheWebAsync`Tworzy <xref:System.Net.Http.HttpClient> wystąpienia i wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2A> metod asynchronicznych w celu pobrania zawartości witryny sieci Web jako ciąg.  
  
3.  Wydarzy się coś w `GetStringAsync` który wstrzymuje postępu. Być może metoda musi czekać na pobranie strony internetowej lub inne działanie blokujące. Aby uniknąć zablokowania zasobów, `GetStringAsync` daje formantu do swojego obiektu wywołującego `AccessTheWebAsync`.  
  
     `GetStringAsync`Zwraca <xref:System.Threading.Tasks.Task%601> w przypadku, gdy TResult jest ciągiem, a `AccessTheWebAsync` przypisuje zadania do `getStringTask` zmiennej. Zadanie reprezentuje ciągły proces dla wywołania `GetStringAsync`, z zobowiązań wygenerowało rzeczywistą wartością ciągu, po zakończeniu pracy.  
  
4.  Ponieważ `getStringTask` nie zostały jeszcze, oczekiwane `AccessTheWebAsync` można kontynuować inne zadania, które nie są zależne od wyniku końcowego z `GetStringAsync`. Czy praca jest reprezentowana przez wywołanie do metody synchroniczne `DoIndependentWork`.  
  
5.  `DoIndependentWork`Metoda synchroniczna nie jego pracy i zwraca go do swojego obiektu wywołującego jest.  
  
6.  `AccessTheWebAsync`Zabrakło pracy, który można zrobić bez wyników z `getStringTask`. `AccessTheWebAsync`dalej chce obliczania i zwraca długość ciągu pobrany, ale metoda nie może obliczyć tę wartość, dopóki metoda ma ciąg.  
  
     W związku z tym `AccessTheWebAsync` używa operatora await, aby zawiesić jego postęp i uzyskanie formantu do metody, która wywołuje `AccessTheWebAsync`. `AccessTheWebAsync`Zwraca `Task<int>` (`Task(Of Integer)` w języku Visual Basic) do obiektu wywołującego. Zadanie przedstawia obietnicę utworzenia w wyniku liczby całkowitej, która jest długością pobranego ciągu.  
  
    > [!NOTE]
    >  Jeśli `GetStringAsync` (i w związku z tym `getStringTask`) została ukończona przed `AccessTheWebAsync` oczekujące na jego sterowania pozostanie w `AccessTheWebAsync`. Wydatków wstrzymywania i następnie zwracany do `AccessTheWebAsync` może występować, jeśli proces asynchroniczny wywoływanego (`getStringTask`) zostało już ukończone i AccessTheWebSync nie musi czekać na wynik końcowy.  
  
     Przetwarzanie wzorca jest kontynuowane wewnątrz elementu wywołującego (programu obsługi zdarzeń w tym przykładzie). Obiekt wywołujący może wykonywanie innych zadań, które nie są zależne od wyników z `AccessTheWebAsync` przed oczekiwanie na wynik lub obiekt wywołujący może poczekać na natychmiast.   Program obsługi zdarzeń oczekuje na `AccessTheWebAsync`, i `AccessTheWebAsync` oczekuje na `GetStringAsync`.  
  
7.  `GetStringAsync`kończy i zwraca wynik ciągu. Wynik ciąg nie jest zwrócony przez wywołanie `GetStringAsync` w taki sposób, który może spodziewać się. (Należy pamiętać, że metoda zwróciła już zadania w kroku 3). Zamiast tego wyniku ciągu są przechowywane w zadanie reprezentujące zakończenie metody, `getStringTask`. Operatora await pobiera wynik `getStringTask`. W instrukcji przypisania przypisuje pobrane wynik `urlContents`.  
  
8.  Gdy `AccessTheWebAsync` ma wynik ciąg metody można obliczyć długość ciągu. Następnie pracy `AccessTheWebAsync` również zostanie zakończone, i wznowić oczekiwania programu obsługi zdarzeń. W pełnym przykładzie na końcu tematu można zobaczyć, że program obsługi zdarzeń pobiera i drukuje wynikową wartość długości.  
  
 Jeśli dopiero zaczynasz przygodę z programowaniem asynchronicznym, zastanów się przez chwilę, jaka jest różnica między zachowaniem synchronicznym i asynchronicznym. Metoda synchroniczna kończy działanie, gdy praca jest zakończona (krok 5), natomiast metoda asynchroniczna zwraca wartość zadania, gdy jej praca jest zawieszona (kroki 3 i 6). Gdy metoda async ukończy pracę, zadanie jest oznaczane jako ukończone, a wynik, o ile istnieje, jest zapisywany w zadaniu.  
  
 Aby uzyskać więcej informacji na temat przepływu sterowania, zobacz [przepływ sterowania w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a>Metody asynchroniczne interfejsu API  
 Użytkownik może się zastanawiać, gdzie można znaleźć metody, takie jak `GetStringAsync` programowania asynchronicznego tej pomocy technicznej. .NET Framework 4.5 lub wyższej zawiera wiele elementów członkowskich, które współpracują z `Async` i `Await`. Elementy te można rozpoznać przez sufiks "Async", który jest dołączony do nazwy elementu członkowskiego i typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Na przykład `System.IO.Stream` klasa zawiera metody <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, i <xref:System.IO.Stream.WriteAsync%2A> obok metod synchronicznych <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, i <xref:System.IO.Stream.Write%2A>.  
  
 Środowisko wykonawcze systemu Windows zawiera także wiele metod, które można używać z `Async` i `Await` w aplikacjach systemu Windows. Uzyskać więcej informacji oraz przykład metody, zobacz [Szybki Start: przy użyciu operatora await programowania asynchronicznego](http://go.microsoft.com/fwlink/?LinkId=248545), [(aplikacje ze Sklepu Windows) programowanie asynchroniczne](http://go.microsoft.com/fwlink/?LinkId=259592), i [WhenAny: Łączenie platformy .NET Framework i środowiska wykonawczego systemu Windows](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx).  
  
##  <a name="BKMK_Threads"></a>Wątki  
 Metody async mają być operacjami niepowodującymi blokowania. `Await` Wyrażenie w metodzie asynchronicznej nie blokuje bieżącego wątku, podczas gdy oczekiwano zadanie jest uruchomione. Zamiast tego, wyrażenie rejestruje pozostałą część metody jako kontynuację i przekazuje sterowanie do obiektu wywołującego metody async.  
  
 `Async` i `Await` słów kluczowych nie powodują dodatkowe wątki ma zostać utworzony. Metody komunikacji async nie wymagają wielowątkowości, ponieważ nie działają we własnym wątku. Metoda działa w bieżącym kontekście synchronizacji i używa czasu wątku, tylko wtedy, gdy jest aktywna. Można użyć <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> można przenieść procesor do wątku w tle, ale tło wątku nie pomoże z procesem, które właśnie oczekuje na wyniki stają się dostępne.  
  
 Podejście async do programowania asynchronicznego jest preferowane prawie w każdym przypadku. W szczególności, ta metoda jest lepszym rozwiązaniem niż <xref:System.ComponentModel.BackgroundWorker> dla we/wy powiązane z operacji, ponieważ kod jest prostsze i nie trzeba chronić przed zastępować warunków. W połączeniu z <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>, programowania asynchronicznego jest lepszym rozwiązaniem niż <xref:System.ComponentModel.BackgroundWorker> dla procesora operacji ponieważ programowania asynchronicznego oddziela szczegóły koordynacji uruchomionych kodu z pracy `Task.Run` transferu do puli wątków.  
  
##  <a name="BKMK_AsyncandAwait"></a>Async i Await  
 Jeśli określisz, że metoda jest to metoda asynchroniczna przy użyciu [Async](../../../../visual-basic/language-reference/modifiers/async.md) modyfikator, zostanie włączone następujące dwie możliwości.  
  
-   Można użyć metody asynchronicznej oznaczone [Await](../../../../visual-basic/language-reference/operators/await-operator.md) do wyznaczenia punktów zawieszenia. Operator await informuje kompilator, że metoda async nie może kontynuować działania do chwili zakończenia procesu asynchronicznego, na który oczekuje. W międzyczasie sterowanie powraca do obiektu wywołującego metodę async.  
  
     Zawieszenie metody asynchronicznej w `Await` wyrażenia nie stanowią wyjście z metody i `Finally` bloków nie działają.  
  
-   Metoda oznaczona jako async sama może być oczekiwana przez metody, które ją wywołują.  
  
 Metoda asynchroniczna zwykle zawiera jeden lub więcej wystąpień `Await` operatora, ale brak `Await` wyrażeń nie powoduje błąd kompilatora. Jeśli metoda asynchroniczna nie używa `Await` operatora, aby oznaczyć punktu zawieszenie, metoda wykonuje jak metoda synchroniczna pomimo `Async` modyfikator. Kompilator generuje ostrzeżenia dla takich metod.  
  
 `Async`i `Await` są kontekstowe słowa kluczowe. Aby uzyskać więcej informacji i przykładów, zobacz następujący temat:  
  
-   [Asynchroniczne](../../../../visual-basic/language-reference/modifiers/async.md)  
  
-   [Await — Operator](../../../../visual-basic/language-reference/operators/await-operator.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a>Parametry i zwracane typy  
 W programowaniu .NET Framework, zwykle zwraca metody asynchronicznej <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Wewnątrz metody asynchronicznej `Await` operator jest stosowany do zadania, która jest zwracana z wywołania do innej metody asynchronicznej.  
  
 Należy określić <xref:System.Threading.Tasks.Task%601> jako typ zwracany, jeśli metoda zawiera [zwracać](../../../../visual-basic/language-reference/statements/return-statement.md) instrukcji, która określa argumentu operacji typu `TResult`.  
  
 Możesz użyć `Task` jako typ zwracany, jeśli metoda ma nie instrukcji return lub zawiera instrukcję return, która nie zwraca argumentu operacji.  
  
 W poniższym przykładzie pokazano, jak deklarowanie i wywoływanie metody, która zwraca <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>.  
  
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
  
 Można też to metoda asynchroniczna `Sub` metody. Ten typ zwracany jest używany głównie w celu definiowania metod obsługi zdarzeń, którym wymagany jest typ zwracany. Programy async obsługi zdarzeń często służą jako punkt wejścia dla programów async.  
  
 Metoda asynchroniczna to jest `Sub` procedury nie oczekiwane, a obiekt wywołujący nie może przechwycić wszelkie wyjątki, które metoda zgłasza wyjątek.  
  
 Nie można zadeklarować metody asynchronicznej [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametrów, ale metodę można wywołać metody, które mają takie parametry.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [Async zwracać typów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md). Aby uzyskać więcej informacji o sposobie przechwytywanie wyjątków w metodach asynchronicznych, zobacz [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Asynchroniczne interfejsów API w programowaniu środowiska wykonawczego systemu Windows mają jeden z następujących zwracane typy, które są podobne do zadań:  
  
-   [IAsyncOperation](http://go.microsoft.com/fwlink/p/?LinkId=261896), które odpowiada<xref:System.Threading.Tasks.Task%601>  
  
-   [IAsyncAction](http://go.microsoft.com/fwlink/p/?LinkId=261897), które odpowiada<xref:System.Threading.Tasks.Task>  
  
-   [IAsyncActionWithProgress](http://go.microsoft.com/fwlink/p/?LinkId=261898)  
  
-   [IAsyncOperationWithProgress](http://go.microsoft.com/fwlink/p/?LinkID=259454)  
  
 Na przykład i więcej informacji, zobacz [Szybki Start: przy użyciu operatora await programowania asynchronicznego](http://go.microsoft.com/fwlink/p/?LinkId=248545).  
  
##  <a name="BKMK_NamingConvention"></a>Konwencja nazewnictwa  
 Według konwencji "Async" można dołączyć do nazwy metody, które mają `Async` modyfikator.  
  
 Można zignorować konwencję, gdy zdarzenie, klasa bazowa lub kontrakt interfejsu sugeruje inną nazwę. Na przykład nie zmienisz typowych programów obsługi zdarzeń, takich jak `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a>Tematy pokrewne i przykłady (Visual Studio)  
  
|Tytuł|Opis|Przykład|  
|-----------|-----------------|------------|  
|[Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Przedstawia, w jaki sposób konwertować synchroniczne rozwiązanie WPF do asynchronicznego rozwiązania WPF. Ta aplikacja pobiera szereg witryn sieci Web.|[Przykład Async: Uzyskiwanie dostępu do wskazówki sieci Web](http://go.microsoft.com/fwlink/p/?LinkID=255191&clcid=0x409)|  
|[Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Dodaje <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do poprzedniego wskazówki. Korzystanie z `WhenAll` uruchamia wszystkie pobrane pliki w tym samym czasie.||  
|[Porady: wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ilustruje, jak uruchomić kilka zadań w tym samym czasie.|[Przykład Async: Należy żądania sieci Web równolegle](http://go.microsoft.com/fwlink/p/?LinkID=254906&clcid=0x409)|  
|[Asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)|Ilustruje typy zwracane przez metody async i wyjaśnia, kiedy poszczególne typy są odpowiednie.||  
|[Przepływ sterowania w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)|Śledzi szczegółowo przepływ sterowania w serii wyrażeń await w programie asynchronicznym.|[Przykład Async: Przepływ sterowania w aplikacjach asynchronicznych](http://go.microsoft.com/fwlink/p/?LinkID=255285&clcid=0x409)|  
|[Dostrajanie aplikacji Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Przedstawia, w jaki sposób dodać następujące funkcje do rozwiązania async:<br /><br /> -   [Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Anulowanie zadań asynchronicznych po upływie określonego czasu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Anulowanie pozostałych zadań asynchronicznych po jednym jest pełna (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Próbka asynchronicznych: Dostrajanie aplikacji dokładnej](http://go.microsoft.com/fwlink/p/?LinkID=255046&clcid=0x409)|  
|[Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Przedstawia, w jaki sposób obsługiwać przypadki, w których podczas działania uruchamiana jest ponownie aktywna operacja asynchroniczna.||  
|[WhenAny: Łączenie platformy .NET Framework i środowiska wykonawczego systemu Windows](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)|Pokazuje, jak połączenie między typami zadań w programie .NET Framework i IAsyncOperations w [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby można było używać <xref:System.Threading.Tasks.Task.WhenAny%2A> z [!INCLUDE[wrt](~/includes/wrt-md.md)] metody.|[Przykład asynchroniczne: Łączenie platformy .NET i środowiska wykonawczego systemu Windows (metody AsTask i WhenAny)](http://go.microsoft.com/fwlink/p/?LinkID=260638)|  
|Anulowanie asynchroniczne: łączenie platformy .NET Framework ze środowiskiem wykonawczym systemu Windows|Pokazuje, jak połączenie między typami zadań w programie .NET Framework i IAsyncOperations w [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby można było używać <xref:System.Threading.CancellationTokenSource> z [!INCLUDE[wrt](~/includes/wrt-md.md)] metody.|[Przykład asynchroniczne: Łączenie platformy .NET i środowiska wykonawczego systemu Windows (metody AsTask & anulowania)](http://go.microsoft.com/fwlink/p/?LinkId=263004)|  
|[Użycie Async do uzyskiwania dostępu do plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/using-async-for-file-access.md)|Wyświetla listę korzyści wynikających ze stosowania słów kluczowych async i await przy uzyskiwaniu dostępu do plików.||  
|[Asynchroniczny wzorzec oparty na zadaniach (TAP)](http://msdn.microsoft.com/library/8cef1fcf-6f9f-417c-b21f-3fd8bac75007)|Opisano nowy wzorzec asynchronii w .NET Framework. Wzorzec jest oparta na <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> typów.||  
|[Asynchroniczne filmów wideo w witrynie Channel 9](http://go.microsoft.com/fwlink/p/?LinkID=267466)|Oferuje łącza do różnych plików wideo dotyczących programowania asynchronicznego.||  
  
##  <a name="BKMK_CompleteExample"></a>Pełny przykład  
 Następujący kod to plik MainWindow.xaml.vb z aplikacji Windows Presentation Foundation (WPF), który w tym temacie omówiono. Możesz pobrać próbki z [próbki Async: przykład z "Asynchronicznego programowania z Async i Await"](http://go.microsoft.com/fwlink/p/?LinkID=261549).  
  
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
 [Await — Operator](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [Asynchroniczne](../../../../visual-basic/language-reference/modifiers/async.md)
