---
title: 'Porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
ms.openlocfilehash: 44a1019ac8169138aa95b03e2027d9539cbf8391
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957370"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach
W przypadku pisania klasy z niektórymi operacjami, które mogą mieć zauważalne opóźnienia, należy rozważyć udzielenie funkcji asynchronicznych przez implementację [asynchronicznego wzorca opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 W tym instruktażu przedstawiono sposób tworzenia składnika implementującego wzorzec asynchroniczny oparty na zdarzeniach. Jest implementowana przy użyciu klas pomocnika z przestrzeni nazw <xref:System.ComponentModel?displayProperty=nameWithType>, dzięki czemu składnik działa prawidłowo w ramach dowolnego modelu aplikacji, w tym ASP.NET, aplikacji konsolowych i aplikacji Windows Forms. Ten składnik jest również zaprojektowany przy użyciu kontrolki <xref:System.Windows.Forms.PropertyGrid> i własnych niestandardowych projektantów.  
  
 Gdy jesteś w programie, będziesz mieć aplikację, która będzie w sposób asynchroniczny obliczał numery bazowe. Aplikacja będzie mieć wątek głównego interfejsu użytkownika i wątek dla każdego obliczenia liczby podstawowej. Chociaż Testowanie dużej liczby może zająć dużo czasu, główny wątek interfejsu użytkownika nie zostanie przerwany w tym opóźnieniu, a formularz będzie odpowiadać podczas obliczeń. Będzie można uruchamiać dowolną liczbę obliczeń, tak jak współbieżne i wybiórczo anulować oczekujące obliczenia.  
  
 Zadania przedstawione w tym instruktażu obejmują:  
  
- Tworzenie składnika  
  
- Definiowanie publicznych zdarzeń asynchronicznych i delegatów  
  
- Definiowanie prywatnych delegatów  
  
- Implementowanie zdarzeń publicznych  
  
- Implementowanie metody ukończenia  
  
- Implementowanie metod roboczych  
  
- Implementowanie metod Start i Cancel  
  
 Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Implementuj klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Tworzenie składnika  
 Pierwszym krokiem jest utworzenie składnika, który będzie implementował wzorzec asynchroniczny oparty na zdarzeniach.  
  
### <a name="to-create-the-component"></a>Aby utworzyć składnik  
  
- Utwórz klasę o nazwie `PrimeNumberCalculator` która dziedziczy po <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definiowanie publicznych zdarzeń asynchronicznych i delegatów  
 Składnik komunikuje się z klientami przy użyciu zdarzeń. Zdarzenie _MethodName_**zostało wykonane** przez klientów do ukończenia zadania asynchronicznego, a zdarzenie**ProgressChanged** _MethodName_informuje klientów o postępie zadania asynchronicznego.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Aby zdefiniować zdarzenia asynchroniczne dla klientów składnika:  
  
1. Zaimportuj <xref:System.Threading?displayProperty=nameWithType> i <xref:System.Collections.Specialized?displayProperty=nameWithType> przestrzenie nazw w górnej części pliku.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. Przed definicją klasy `PrimeNumberCalculator` Zadeklaruj delegatów dla zdarzeń postępu i ukończenia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. W definicji klasy `PrimeNumberCalculator` deklaruj zdarzenia w celu raportowania postępu i ukończenia na klientach.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. Po definicji klasy `PrimeNumberCalculator` należy utworzyć klasę `CalculatePrimeCompletedEventArgs` do raportowania wyników każdego obliczenia do programu obsługi zdarzeń klienta dla zdarzenia `CalculatePrimeCompleted`. Oprócz właściwości `AsyncCompletedEventArgs`, ta klasa umożliwia klientowi określenie, która liczba została przetestowana, niezależnie od tego, czy jest, i co pierwszy dzielnik jest niepodstawowy.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można skompilować składnik.  
  
### <a name="to-test-your-component"></a>Aby przetestować składnik  
  
- Kompiluj składnik.  
  
     Zostaną wyświetlone dwa ostrzeżenia kompilatora:  
  
    ```console  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Te ostrzeżenia zostaną wyczyszczone w następnej sekcji.  
  
## <a name="defining-private-delegates"></a>Definiowanie prywatnych delegatów  
 Asynchroniczne aspekty składnika `PrimeNumberCalculator` są implementowane wewnętrznie z specjalnym delegatem znanym jako <xref:System.Threading.SendOrPostCallback>. <xref:System.Threading.SendOrPostCallback> reprezentuje metodę wywołania zwrotnego, która jest wykonywana w wątku <xref:System.Threading.ThreadPool>. Metoda wywołania zwrotnego musi mieć sygnaturę, która przyjmuje jeden parametr typu <xref:System.Object>, co oznacza, że należy przekazać stan między delegatami w klasie otoki. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Aby zaimplementować wewnętrzne zachowanie asynchroniczne składnika:  
  
1. Zadeklaruj i Utwórz delegatów <xref:System.Threading.SendOrPostCallback> w klasie `PrimeNumberCalculator`. Utwórz obiekty <xref:System.Threading.SendOrPostCallback> w metodzie narzędzia o nazwie `InitializeDelegates`.  
  
     Wymagane są dwa Delegaty: jeden do raportowania postępu dla klienta, a drugi do raportowania ukończenia do klienta programu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. Wywołaj metodę `InitializeDelegates` w konstruktorze składnika.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. Zadeklaruj delegat w klasie `PrimeNumberCalculator`, który obsługuje rzeczywistą służbę do wykonania asynchronicznie. Ten delegat otacza metodę procesu roboczego, która sprawdza, czy liczba jest podstawowa. Delegat przyjmuje <xref:System.ComponentModel.AsyncOperation> parametr, który zostanie użyty do śledzenia okresu istnienia operacji asynchronicznej.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Utwórz kolekcję do zarządzania okresami istnienia oczekujących operacji asynchronicznych. Klient musi mieć możliwość śledzenia operacji, gdy są wykonywane i kończone, a to śledzenie jest wykonywane przez wymaganie, aby klient przeszedł unikatowy token, lub identyfikator zadania, gdy klient wysyła wywołanie do metody asynchronicznej. Składnik `PrimeNumberCalculator` musi śledzić każde wywołanie, kojarząc identyfikator zadania z odpowiednim wywołaniem. Jeśli klient przeszedł identyfikator zadania, który nie jest unikatowy, składnik `PrimeNumberCalculator` musi zgłosić wyjątek.  
  
     Składnik `PrimeNumberCalculator` śledzi identyfikator zadania za pomocą specjalnej klasy kolekcji zwanej <xref:System.Collections.Specialized.HybridDictionary>. W definicji klasy Utwórz <xref:System.Collections.Specialized.HybridDictionary> o nazwie `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implementowanie zdarzeń publicznych  
 Składniki implementujące wzorzec asynchroniczny oparty na zdarzeniach komunikują się z klientami przy użyciu zdarzeń. Te zdarzenia są wywoływane w odpowiednim wątku za pomocą klasy <xref:System.ComponentModel.AsyncOperation>.  
  
### <a name="to-raise-events-to-your-components-clients"></a>Aby zgłosić zdarzenia do klientów składnika:  
  
1. Zaimplementuj zdarzenia publiczne na potrzeby raportowania dla klientów. Konieczne będzie zdarzenie raportowania postępu i jeden dla ukończenia raportowania.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementowanie metody ukończenia  
 Delegat uzupełniający to metoda, którą podstawowe, wolne od wątku zachowanie asynchroniczne wywoła, gdy operacja asynchroniczna kończy się przez pomyślne zakończenie, błąd lub anulowanie. To wywołanie występuje w dowolnym wątku.  
  
 Ta metoda polega na tym, że identyfikator zadania klienta jest usuwany z wewnętrznej kolekcji unikatowych tokenów klienta. Ta metoda również końcowy okres istnienia określonej operacji asynchronicznej przez wywołanie metody <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> na odpowiadającej <xref:System.ComponentModel.AsyncOperation>. To wywołanie podnosi zdarzenie ukończenia w wątku, który jest odpowiedni dla modelu aplikacji. Po wywołaniu metody <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> nie można już używać tego wystąpienia <xref:System.ComponentModel.AsyncOperation>, a wszystkie kolejne próby jego użycia spowodują zgłoszenie wyjątku.  
  
 Sygnatura `CompletionMethod` musi przechowywać wszystkie Stany niezbędne do opisania wyniku operacji asynchronicznej. Przechowuje stan dla liczby, która została przetestowana przez tę konkretną operację asynchroniczną, niezależnie od tego, czy jest to liczba, i wartość pierwszego dzielnika, jeśli nie jest to liczba podstawowa. Zawiera również stan opisujący każdy wyjątek, który wystąpił, i <xref:System.ComponentModel.AsyncOperation> odpowiadające temu określonemu zadaniu.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Aby ukończyć operację asynchroniczną:  
  
- Zaimplementuj metodę ukończenia. Przyjmuje sześć parametrów, których używa do wypełniania `CalculatePrimeCompletedEventArgs`, który jest zwracany do klienta za pośrednictwem `CalculatePrimeCompletedEventHandler`klienta. Spowoduje to usunięcie tokenu identyfikatora zadania klienta z kolekcji wewnętrznej i zakończenie okresu istnienia operacji asynchronicznej z wywołaniem do <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. <xref:System.ComponentModel.AsyncOperation> kierowanie wywołania do wątku lub kontekstu, który jest odpowiedni dla modelu aplikacji.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można skompilować składnik.  
  
### <a name="to-test-your-component"></a>Aby przetestować składnik  
  
- Kompiluj składnik.  
  
     Zostanie wyświetlone jedno Ostrzeżenie kompilatora:  
  
    ```console  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     To ostrzeżenie zostanie rozwiązane w następnej sekcji.  
  
## <a name="implementing-the-worker-methods"></a>Implementowanie metod roboczych  
 Do tej pory zaimplementowano kod asynchroniczny dla składnika `PrimeNumberCalculator`. Teraz można zaimplementować kod, który wykonuje rzeczywistą prace. Zostaną zaimplementowane trzy metody: `CalculateWorker`, `BuildPrimeNumberList`i `IsPrime`. Razem `BuildPrimeNumberList` i `IsPrime` obejmują dobrze znany algorytm o nazwie Sit of Eratostenesa, który określa, czy jest to liczba, przez znalezienie wszystkich numerów głównych do pierwiastek kwadratowy numeru testu. Jeśli żaden dzielnik nie zostanie znaleziony przez ten punkt, numer testu jest podstawowy.  
  
 Jeśli ten składnik został zastosowany w celu uzyskania maksymalnej wydajności, Zapamiętaj wszystkie liczby podstawowe wykryte przez różne wywołania dla różnych numerów testów. Sprawdza również, czy istnieją proste dzielniki, takie jak 2, 3 i 5. Celem tego przykładu jest zademonstrowanie sposobu, w jaki operacje czasochłonne mogą być wykonywane asynchronicznie, jednak te optymalizacje są pozostawione jako ćwiczenie.  
  
 Metoda `CalculateWorker` jest opakowana w delegata i jest wywoływana asynchronicznie z wywołaniem `BeginInvoke`.  
  
> [!NOTE]
> Raportowanie postępu jest implementowane w metodzie `BuildPrimeNumberList`. Na szybkich komputerach zdarzenia `ProgressChanged` mogą być zgłaszane w krótkim sukcesie. Wątek klienta, na którym są wywoływane te zdarzenia, musi być w stanie obsłużyć tę sytuację. Kod interfejsu użytkownika może być zalewany komunikatem i nie można go zachować, co spowodowało brak odpowiedzi. Przykładowy interfejs użytkownika, który obsługuje tę sytuację, znajduje się w temacie [How to: Implementuj klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Aby wykonać obliczenie liczby pierwszych asynchronicznie:  
  
1. Zaimplementuj metodę narzędzia `TaskCanceled`. Spowoduje to sprawdzenie kolekcji okresu istnienia zadania dla danego identyfikatora zadania i zwrócenie `true`, jeśli nie można odnaleźć identyfikatora zadania.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. Zaimplementuj metodę `CalculateWorker`. Przyjmuje dwa parametry: liczbę do przetestowania i <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. Zaimplementuj `BuildPrimeNumberList`. Przyjmuje dwa parametry: liczbę do przetestowania i <xref:System.ComponentModel.AsyncOperation>. Używa <xref:System.ComponentModel.AsyncOperation> do raportowania postępu i przyrostowych wyników. Gwarantuje to, że procedury obsługi zdarzeń klienta są wywoływane w odpowiednim wątku lub kontekście dla modelu aplikacji. Gdy `BuildPrimeNumberList` odnajdzie numer podstawowy, Raport ten jest raportowany jako wynikowy składnik obsługi zdarzeń klienta dla zdarzenia `ProgressChanged`. Wymaga klasy pochodzącej od <xref:System.ComponentModel.ProgressChangedEventArgs>o nazwie `CalculatePrimeProgressChangedEventArgs`, która ma jedną dodaną właściwość o nazwie `LatestPrimeNumber`.  
  
     Metoda `BuildPrimeNumberList` okresowo wywołuje również metodę `TaskCanceled` i kończy działanie, jeśli metoda zwróci `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. Zaimplementuj `IsPrime`. Przyjmuje trzy parametry: listę znanych numerów początkowych, liczbę do przetestowania oraz parametr wyjściowy pierwszego dzielnika znaleziony. Uwzględniając listę numerów pierwszych, określa, czy numer testu jest podstawowy.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. `CalculatePrimeProgressChangedEventArgs` pochodne od <xref:System.ComponentModel.ProgressChangedEventArgs>. Ta klasa jest niezbędna do raportowania przyrostowych wyników do programu obsługi zdarzeń klienta dla zdarzenia `ProgressChanged`. Ma jedną dodaną właściwość o nazwie `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można skompilować składnik.  
  
### <a name="to-test-your-component"></a>Aby przetestować składnik  
  
- Kompiluj składnik.  
  
     Wszystkie te, które pozostały do zapisania, to metody uruchamiania i anulowania operacji asynchronicznych, `CalculatePrimeAsync` i `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementowanie metod Start i Cancel  
 Metoda Worker jest uruchamiana we własnym wątku, wywołując `BeginInvoke` na delegatze, który go otacza. Aby zarządzać okresem istnienia określonej operacji asynchronicznej, należy wywołać metodę <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> w klasie pomocnika <xref:System.ComponentModel.AsyncOperationManager>. Spowoduje to zwrócenie <xref:System.ComponentModel.AsyncOperation>, która kierowanie wywołań do obsługi zdarzeń klienta do odpowiedniego wątku lub kontekstu.  
  
 Użytkownik anulował określoną oczekującą operację, wywołując <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> na odpowiednim <xref:System.ComponentModel.AsyncOperation>. Spowoduje to zakończenie tej operacji, a wszelkie kolejne wywołania <xref:System.ComponentModel.AsyncOperation> spowodują zgłoszenie wyjątku.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Aby zaimplementować funkcje Start i Cancel:  
  
1. Zaimplementuj metodę `CalculatePrimeAsync`. Upewnij się, że token dostarczony przez klienta (identyfikator zadania) jest unikatowy w odniesieniu do wszystkich tokenów reprezentujących aktualnie oczekujące zadania. Jeśli klient kończy się nieunikatowym tokenem, `CalculatePrimeAsync` zgłasza wyjątek. W przeciwnym razie token zostanie dodany do kolekcji identyfikatorów zadań.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. Zaimplementuj metodę `CancelAsync`. Jeśli parametr `taskId` istnieje w kolekcji tokenów, zostanie usunięty. Zapobiega to anulowaniu zadań, które nie zostały uruchomione. Jeśli zadanie jest uruchomione, Metoda `BuildPrimeNumberList` zostanie zakończona, gdy wykryje, że identyfikator zadania został usunięty z kolekcji okres istnienia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można skompilować składnik.  
  
### <a name="to-test-your-component"></a>Aby przetestować składnik  
  
- Kompiluj składnik.  
  
 Składnik `PrimeNumberCalculator` jest teraz kompletny i gotowy do użycia.  
  
 Przykład klienta korzystającego ze składnika `PrimeNumberCalculator` można znaleźć w temacie [How to: Implementuj klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz wypełnić ten przykład, pisząc `CalculatePrime`, synchroniczny odpowiednik metody `CalculatePrimeAsync`. Dzięki temu składnik `PrimeNumberCalculator` jest w pełni zgodny ze wzorcem asynchronicznym opartym na zdarzeniach.  
  
 Możesz ulepszyć ten przykład, zachowując listę wszystkich pierwszych liczb odnalezionych przez różne wywołania dla różnych numerów testów. Korzystając z tej metody, każde zadanie będzie korzystać z pracy wykonanej przez poprzednie zadania. Należy zachować ostrożność, aby chronić tę listę za pomocą regionów `lock`, więc dostęp do listy przez różne wątki jest serializowany.  
  
 Możesz również ulepszyć ten przykład, testując dla prostych dzielników, takich jak 2, 3 i 5.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
