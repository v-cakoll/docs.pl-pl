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
ms.openlocfilehash: 83a60e0e793f33b8b0a1cec8342942fd05c82f55
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289892"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach
W przypadku pisania klasy z niektórymi operacjami, które mogą mieć zauważalne opóźnienia, należy rozważyć udzielenie funkcji asynchronicznych przez implementację [asynchronicznego wzorca opartego na zdarzeniach](event-based-asynchronous-pattern-overview.md).  
  
 W tym instruktażu przedstawiono sposób tworzenia składnika implementującego wzorzec asynchroniczny oparty na zdarzeniach. Jest implementowana przy użyciu klas pomocników z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw, dzięki czemu składnik działa prawidłowo w ramach dowolnego modelu aplikacji, w tym ASP.NET, aplikacji konsolowych i aplikacji Windows Forms. Ten składnik jest również zaprojektowany przy użyciu <xref:System.Windows.Forms.PropertyGrid> kontrolki i własnych niestandardowych projektantów.  
  
 Gdy jesteś w programie, będziesz mieć aplikację, która będzie w sposób asynchroniczny obliczał numery bazowe. Aplikacja będzie mieć wątek głównego interfejsu użytkownika i wątek dla każdego obliczenia liczby podstawowej. Chociaż Testowanie dużej liczby może zająć dużo czasu, główny wątek interfejsu użytkownika nie zostanie przerwany w tym opóźnieniu, a formularz będzie odpowiadać podczas obliczeń. Będzie można uruchamiać dowolną liczbę obliczeń, tak jak współbieżne i wybiórczo anulować oczekujące obliczenia.  
  
 Zadania przedstawione w tym instruktażu obejmują:  
  
- Tworzenie składnika  
  
- Definiowanie publicznych zdarzeń asynchronicznych i delegatów  
  
- Definiowanie prywatnych delegatów  
  
- Implementowanie zdarzeń publicznych  
  
- Implementowanie metody ukończenia  
  
- Implementowanie metod roboczych  
  
- Implementowanie metod Start i Cancel  
  
 Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Implementuj klienta wzorca asynchronicznego opartego na zdarzeniach](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Tworzenie składnika  
 Pierwszym krokiem jest utworzenie składnika, który będzie implementował wzorzec asynchroniczny oparty na zdarzeniach.  
  
### <a name="to-create-the-component"></a>Aby utworzyć składnik  
  
- Utwórz klasę o nazwie `PrimeNumberCalculator` , która dziedziczy z <xref:System.ComponentModel.Component> .  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definiowanie publicznych zdarzeń asynchronicznych i delegatów  
 Składnik komunikuje się z klientami przy użyciu zdarzeń. Zdarzenie _MethodName_**zostało wykonane** przez klientów do ukończenia zadania asynchronicznego, a zdarzenie**ProgressChanged** _MethodName_informuje klientów o postępie zadania asynchronicznego.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Aby zdefiniować zdarzenia asynchroniczne dla klientów składnika:  
  
1. Zaimportuj <xref:System.Threading?displayProperty=nameWithType> <xref:System.Collections.Specialized?displayProperty=nameWithType> przestrzenie nazw i w górnej części pliku.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. Przed `PrimeNumberCalculator` definicją klasy Zadeklaruj delegatów dla zdarzeń postępu i ukończenia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. W `PrimeNumberCalculator` definicji klasy Zadeklaruj zdarzenia w celu raportowania postępu i ukończenia do klientów.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. Po `PrimeNumberCalculator` definicji klasy należy utworzyć `CalculatePrimeCompletedEventArgs` klasę do raportowania wyników każdego obliczenia do programu obsługi zdarzeń klienta dla `CalculatePrimeCompleted` zdarzenia. Oprócz `AsyncCompletedEventArgs` właściwości, ta Klasa pozwala klientowi określić, jaka liczba została przetestowana, czy jest, i co pierwszy dzielnik jest, jeśli nie jest.  
  
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
 Asynchroniczne aspekty `PrimeNumberCalculator` składnika są implementowane wewnętrznie z specjalnym delegatem znanym jako <xref:System.Threading.SendOrPostCallback> . <xref:System.Threading.SendOrPostCallback>Reprezentuje metodę wywołania zwrotnego, która jest wykonywana w <xref:System.Threading.ThreadPool> wątku. Metoda wywołania zwrotnego musi mieć sygnaturę, która przyjmuje pojedynczy parametr typu <xref:System.Object> , co oznacza, że należy przekazać stan między delegatami w klasie otoki. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Aby zaimplementować wewnętrzne zachowanie asynchroniczne składnika:  
  
1. Zadeklaruj i Utwórz <xref:System.Threading.SendOrPostCallback> delegatów w `PrimeNumberCalculator` klasie. Utwórz <xref:System.Threading.SendOrPostCallback> obiekty w metodzie narzędzia o nazwie `InitializeDelegates` .  
  
     Wymagane są dwa Delegaty: jeden do raportowania postępu dla klienta, a drugi do raportowania ukończenia do klienta programu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. Wywołaj `InitializeDelegates` metodę w konstruktorze składnika.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. Zadeklaruj delegat w `PrimeNumberCalculator` klasie, która obsługuje rzeczywistą służbę do wykonania asynchronicznie. Ten delegat otacza metodę procesu roboczego, która sprawdza, czy liczba jest podstawowa. Obiekt delegowany przyjmuje <xref:System.ComponentModel.AsyncOperation> parametr, który zostanie użyty do śledzenia okresu istnienia operacji asynchronicznej.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Utwórz kolekcję do zarządzania okresami istnienia oczekujących operacji asynchronicznych. Klient musi mieć możliwość śledzenia operacji, gdy są wykonywane i kończone, a to śledzenie jest wykonywane przez wymaganie, aby klient przeszedł unikatowy token, lub identyfikator zadania, gdy klient wysyła wywołanie do metody asynchronicznej. `PrimeNumberCalculator`Składnik musi śledzić każde wywołanie, kojarząc identyfikator zadania z odpowiednim wywołaniem. Jeśli klient przeszedł identyfikator zadania, który nie jest unikatowy, `PrimeNumberCalculator` składnik musi zgłosić wyjątek.  
  
     `PrimeNumberCalculator`Składnik śledzi identyfikator zadania za pomocą specjalnej klasy kolekcji o nazwie a <xref:System.Collections.Specialized.HybridDictionary> . W definicji klasy Utwórz <xref:System.Collections.Specialized.HybridDictionary> wywołana `userTokenToLifetime` .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implementowanie zdarzeń publicznych  
 Składniki implementujące wzorzec asynchroniczny oparty na zdarzeniach komunikują się z klientami przy użyciu zdarzeń. Te zdarzenia są wywoływane w odpowiednim wątku z pomocą <xref:System.ComponentModel.AsyncOperation> klasy.  
  
### <a name="to-raise-events-to-your-components-clients"></a>Aby zgłosić zdarzenia do klientów składnika:  
  
1. Zaimplementuj zdarzenia publiczne na potrzeby raportowania dla klientów. Konieczne będzie zdarzenie raportowania postępu i jeden dla ukończenia raportowania.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementowanie metody ukończenia  
 Delegat uzupełniający to metoda, którą podstawowe, wolne od wątku zachowanie asynchroniczne wywoła, gdy operacja asynchroniczna kończy się przez pomyślne zakończenie, błąd lub anulowanie. To wywołanie występuje w dowolnym wątku.  
  
 Ta metoda polega na tym, że identyfikator zadania klienta jest usuwany z wewnętrznej kolekcji unikatowych tokenów klienta. Ta metoda również końcowy okres istnienia określonej operacji asynchronicznej przez wywołanie <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> metody w odpowiedniej <xref:System.ComponentModel.AsyncOperation> . To wywołanie podnosi zdarzenie ukończenia w wątku, który jest odpowiedni dla modelu aplikacji. Po <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> wywołaniu metody to wystąpienie <xref:System.ComponentModel.AsyncOperation> nie może być już używane, a wszystkie kolejne próby jego użycia spowodują zgłoszenie wyjątku.  
  
 `CompletionMethod`Sygnatura musi zawierać wszystkie Stany wymagane do opisania wyniku operacji asynchronicznej. Przechowuje stan dla liczby, która została przetestowana przez tę konkretną operację asynchroniczną, niezależnie od tego, czy jest to liczba, i wartość pierwszego dzielnika, jeśli nie jest to liczba podstawowa. Zawiera również stan opisujący każdy wyjątek, który wystąpił, i <xref:System.ComponentModel.AsyncOperation> odpowiadający temu określonemu zadaniu.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Aby ukończyć operację asynchroniczną:  
  
- Zaimplementuj metodę ukończenia. Przyjmuje sześć parametrów, których używa do wypełniania `CalculatePrimeCompletedEventArgs` , który jest zwracany do klienta przez klienta `CalculatePrimeCompletedEventHandler` . Spowoduje to usunięcie tokenu identyfikatora zadania klienta z kolekcji wewnętrznej i zakończenie okresu istnienia operacji asynchronicznej z wywołaniem do <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> . <xref:System.ComponentModel.AsyncOperation>Kierowanie wywołania do wątku lub kontekstu, który jest odpowiedni dla modelu aplikacji.  
  
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
 Do tej pory wdrożono kod asynchroniczny dla `PrimeNumberCalculator` składnika. Teraz można zaimplementować kod, który wykonuje rzeczywistą prace. Zostaną zaimplementowane trzy metody: `CalculateWorker` , `BuildPrimeNumberList` , i `IsPrime` . Razem `BuildPrimeNumberList` i `IsPrime` składają się dobrze znany algorytm o nazwie Sit of Eratostenesa, który określa, czy liczba jest na początku, przez znalezienie wszystkich numerów głównych do pierwiastek kwadratowy numeru testu. Jeśli żaden dzielnik nie zostanie znaleziony przez ten punkt, numer testu jest podstawowy.  
  
 Jeśli ten składnik został zastosowany w celu uzyskania maksymalnej wydajności, Zapamiętaj wszystkie liczby podstawowe wykryte przez różne wywołania dla różnych numerów testów. Sprawdza również, czy istnieją proste dzielniki, takie jak 2, 3 i 5. Celem tego przykładu jest zademonstrowanie sposobu, w jaki operacje czasochłonne mogą być wykonywane asynchronicznie, jednak te optymalizacje są pozostawione jako ćwiczenie.  
  
 `CalculateWorker`Metoda jest opakowana w delegata i jest wywoływana asynchronicznie z wywołaniem do `BeginInvoke` .  
  
> [!NOTE]
> Raportowanie postępu jest zaimplementowane w `BuildPrimeNumberList` metodzie. Na szybkich komputerach `ProgressChanged` zdarzenia mogą być zgłaszane w krótkim pomyślnym sukcesie. Wątek klienta, na którym są wywoływane te zdarzenia, musi być w stanie obsłużyć tę sytuację. Kod interfejsu użytkownika może być zalewany komunikatem i nie można go zachować, co spowodowało brak odpowiedzi. Przykładowy interfejs użytkownika, który obsługuje tę sytuację, znajduje się w temacie [How to: Implementuj klienta wzorca asynchronicznego opartego na zdarzeniach](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Aby wykonać obliczenie liczby pierwszych asynchronicznie:  
  
1. Zaimplementuj `TaskCanceled` metodę narzędzia. Spowoduje to sprawdzenie kolekcji okresu istnienia zadania dla danego identyfikatora zadania i zwrócenie informacji o tym, `true` czy nie znaleziono identyfikatora zadania.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. Zaimplementuj `CalculateWorker` metodę. Przyjmuje dwa parametry: liczbę do przetestowania i <xref:System.ComponentModel.AsyncOperation> .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. Implementacja `BuildPrimeNumberList` . Przyjmuje dwa parametry: liczbę do przetestowania i <xref:System.ComponentModel.AsyncOperation> . Używa <xref:System.ComponentModel.AsyncOperation> do raportowania postępu i przyrostowych wyników. Gwarantuje to, że procedury obsługi zdarzeń klienta są wywoływane w odpowiednim wątku lub kontekście dla modelu aplikacji. W przypadku `BuildPrimeNumberList` znalezienia numeru głównego raport jest raportowany jako wynik przyrostowy do programu obsługi zdarzeń klienta dla `ProgressChanged` zdarzenia. Wymaga klasy pochodnej od <xref:System.ComponentModel.ProgressChangedEventArgs> , o nazwie `CalculatePrimeProgressChangedEventArgs` , która ma jedną dodaną właściwość o nazwie `LatestPrimeNumber` .  
  
     `BuildPrimeNumberList`Metoda okresowo wywołuje `TaskCanceled` metodę i kończy działanie, jeśli metoda zwraca `true` .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. Implementacja `IsPrime` . Przyjmuje trzy parametry: listę znanych numerów początkowych, liczbę do przetestowania oraz parametr wyjściowy pierwszego dzielnika znaleziony. Uwzględniając listę numerów pierwszych, określa, czy numer testu jest podstawowy.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. Pochodny `CalculatePrimeProgressChangedEventArgs` od <xref:System.ComponentModel.ProgressChangedEventArgs> . Ta klasa jest niezbędna do raportowania przyrostowych wyników do programu obsługi zdarzeń klienta dla `ProgressChanged` zdarzenia. Ma jedną dodaną właściwość o nazwie `LatestPrimeNumber` .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można skompilować składnik.  
  
### <a name="to-test-your-component"></a>Aby przetestować składnik  
  
- Kompiluj składnik.  
  
     Wszystkie te, które pozostały do zapisania, są metodami do uruchamiania i anulowania operacji asynchronicznych `CalculatePrimeAsync` oraz `CancelAsync` .  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementowanie metod Start i Cancel  
 Metoda Worker jest uruchamiana we własnym wątku przez wywołanie `BeginInvoke` obiektu delegowanego, który go otacza. Aby zarządzać okresem istnienia określonej operacji asynchronicznej, należy wywołać <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> metodę w <xref:System.ComponentModel.AsyncOperationManager> klasie pomocnika. Zwraca <xref:System.ComponentModel.AsyncOperation> , który kierujące wywołania do obsługi zdarzeń klienta do właściwego wątku lub kontekstu.  
  
 Użytkownik anulował określoną oczekującą operację, wywołując <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> odpowiedni element <xref:System.ComponentModel.AsyncOperation> . Spowoduje to zakończenie tej operacji, a wszelkie kolejne wywołania do niej <xref:System.ComponentModel.AsyncOperation> spowodują zgłoszenie wyjątku.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Aby zaimplementować funkcje Start i Cancel:  
  
1. Zaimplementuj `CalculatePrimeAsync` metodę. Upewnij się, że token dostarczony przez klienta (identyfikator zadania) jest unikatowy w odniesieniu do wszystkich tokenów reprezentujących aktualnie oczekujące zadania. Jeśli klient kończy się nieunikatowym tokenem, `CalculatePrimeAsync` zgłasza wyjątek. W przeciwnym razie token zostanie dodany do kolekcji identyfikatorów zadań.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. Zaimplementuj `CancelAsync` metodę. Jeśli `taskId` parametr istnieje w kolekcji tokenów, zostanie usunięty. Zapobiega to anulowaniu zadań, które nie zostały uruchomione. Jeśli zadanie jest uruchomione, Metoda zostanie `BuildPrimeNumberList` zakończona, gdy wykryje, że identyfikator zadania został usunięty z kolekcji okres istnienia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można skompilować składnik.  
  
### <a name="to-test-your-component"></a>Aby przetestować składnik  
  
- Kompiluj składnik.  
  
 `PrimeNumberCalculator`Składnik został już ukończony i gotowy do użycia.  
  
 Aby zapoznać się z przykładowym klientem korzystającym z `PrimeNumberCalculator` składnika, zobacz [How to: Implementuj klienta wzorca asynchronicznego opartego na zdarzeniach](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz wypełnić ten przykład, pisząc `CalculatePrime` , synchroniczną równoważność `CalculatePrimeAsync` metody. Dzięki temu składnik jest w `PrimeNumberCalculator` pełni zgodny ze wzorcem asynchronicznym opartym na zdarzeniach.  
  
 Możesz ulepszyć ten przykład, zachowując listę wszystkich pierwszych liczb odnalezionych przez różne wywołania dla różnych numerów testów. Korzystając z tej metody, każde zadanie będzie korzystać z pracy wykonanej przez poprzednie zadania. Należy zachować ostrożność, aby chronić tę listę z `lock` regionami, więc dostęp do listy przez różne wątki jest serializowany.  
  
 Możesz również ulepszyć ten przykład, testując dla prostych dzielników, takich jak 2, 3 i 5.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: uruchamianie operacji w tle](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](event-based-asynchronous-pattern-overview.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md)
