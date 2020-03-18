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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71957370"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach
Jeśli piszesz klasę z niektórych operacji, które mogą ponosić zauważalne opóźnienia, należy rozważyć nadanie jej funkcji asynchronicznych, implementując [omówienie asynchronicznego wzorca opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 W tym instruktażem przedstawiono sposób tworzenia składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach. Jest on implementowany przy użyciu <xref:System.ComponentModel?displayProperty=nameWithType> klas pomocnika z obszaru nazw, co zapewnia, że składnik działa poprawnie w dowolnym modelu aplikacji, w tym ASP.NET, aplikacji konsoli i aplikacji Windows Forms. Ten komponent można również <xref:System.Windows.Forms.PropertyGrid> zaprojektować za pomocą formantu i własnych niestandardowych projektantów.  
  
 Podczas przechodzenia, będziesz miał aplikację, która oblicza liczby pierwsze asynchronicznie. Aplikacja będzie miała wątek głównego interfejsu użytkownika (UI) i wątek dla każdego obliczenia liczby pierwszej. Chociaż testowanie, czy duża liczba jest pierwszą, może zająć zauważalną ilość czasu, główny wątek interfejsu użytkownika nie zostanie przerwany przez to opóźnienie, a formularz będzie responsywny podczas obliczeń. Będzie można uruchomić dowolną liczbę obliczeń jednocześnie i selektywnie anulować oczekujące obliczenia.  
  
 Zadania przedstawione w tym instruktacie obejmują:  
  
- Tworzenie komponentu  
  
- Definiowanie publicznych zdarzeń asynchronicznych i delegatów  
  
- Definiowanie pełnomocników prywatnych  
  
- Wdrażanie wydarzeń publicznych  
  
- Implementowanie metody uzupełniania  
  
- Wdrażanie metod pracownika  
  
- Implementowanie metod uruchamiania i anulowania  
  
 Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [Jak: Zaimplementować klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Tworzenie komponentu  
 Pierwszym krokiem jest utworzenie składnika, który zaimplementuje wzorzec asynchroniczny oparty na zdarzeniach.  
  
### <a name="to-create-the-component"></a>Aby utworzyć komponent  
  
- Utwórz klasę `PrimeNumberCalculator` o nazwie, która dziedziczy z <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definiowanie publicznych zdarzeń asynchronicznych i delegatów  
 Składnik komunikuje się z klientami przy użyciu zdarzeń. _Zdarzenie MethodName_**Completed** ostrzega klientów przed zakończeniem zadania asynchronicznego, a zdarzenie _MethodName_**ProgressChanged** informuje klientów o postępie zadania asynchronicznego.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Aby zdefiniować zdarzenia asynchroniczne dla klientów składnika:  
  
1. <xref:System.Threading?displayProperty=nameWithType> Zaimportuj <xref:System.Collections.Specialized?displayProperty=nameWithType> obszary nazw i obszary nazw u góry pliku.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. Przed `PrimeNumberCalculator` definicją klasy deklaruj delegatów dla postępów i zdarzeń zakończenia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. W `PrimeNumberCalculator` definicji klasy zadeklarować zdarzenia do raportowania postępu i zakończenia do klientów.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. Po `PrimeNumberCalculator` definicji klasy, należy `CalculatePrimeCompletedEventArgs` uzyskać klasę do raportowania wyników każdego obliczenia `CalculatePrimeCompleted`do obsługi zdarzeń klienta dla .event. Oprócz `AsyncCompletedEventArgs` właściwości ta klasa umożliwia klientowi określenie, jaka liczba została przetestowana, czy jest ona pierwszorzędna i jaki jest pierwszy dzielnik, jeśli nie jest prime.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnik.  
  
### <a name="to-test-your-component"></a>Aby przetestować komponent  
  
- Skompiluj składnik.  
  
     Otrzymasz dwa ostrzeżenia kompilatora:  
  
    ```console  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Ostrzeżenia te zostaną wyczyszczone w następnej sekcji.  
  
## <a name="defining-private-delegates"></a>Definiowanie pełnomocników prywatnych  
 Asynchroniczne aspekty składnika `PrimeNumberCalculator` są implementowane wewnętrznie za pomocą <xref:System.Threading.SendOrPostCallback>specjalnego delegata znanego jako . A <xref:System.Threading.SendOrPostCallback> reprezentuje metodę wywołania odwoływanego, która jest wykonywana w wątku. <xref:System.Threading.ThreadPool> Metoda wywołania wywołania wywołania musi mieć <xref:System.Object>podpis, który przyjmuje pojedynczy parametr typu, co oznacza, że należy przekazać stan między delegatów w klasie otoki. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Aby zaimplementować wewnętrzne zachowanie asynchroniczne składnika:  
  
1. Deklaruj <xref:System.Threading.SendOrPostCallback> i `PrimeNumberCalculator` utwórz delegatów w klasie. Utwórz <xref:System.Threading.SendOrPostCallback> obiekty w metodzie narzędzia o nazwie `InitializeDelegates`.  
  
     Będziesz potrzebował dwóch delegatów: jeden do raportowania postępu do klienta i jeden do raportowania ukończenia do klienta.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. Wywołaj `InitializeDelegates` metodę w konstruktorze składnika.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. Deklaruj delegata `PrimeNumberCalculator` w klasie, która obsługuje rzeczywistą pracę do wykonania asynchronicznie. Ten pełnomocnik zawija metodę procesu roboczego, która sprawdza, czy liczba jest pierwszorzędna. Delegat przyjmuje parametr, <xref:System.ComponentModel.AsyncOperation> który będzie używany do śledzenia okresu istnienia operacji asynchronicznej.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Utwórz kolekcję do zarządzania okresami istnienia oczekujących operacji asynchronicznych. Klient potrzebuje sposobu śledzenia operacji, ponieważ są one wykonywane i wykonywane, a to śledzenie odbywa się przez wymaganie od klienta przekazania unikatowego tokenu lub identyfikatora zadania, gdy klient wykonuje wywołanie metody asynchronicznej. Składnik `PrimeNumberCalculator` musi śledzić każde wywołanie, kojarząc identyfikator zadania z jego odpowiednim wywołaniem. Jeśli klient przekazuje identyfikator zadania, który nie `PrimeNumberCalculator` jest unikatowy, składnik musi zgłosić wyjątek.  
  
     Składnik `PrimeNumberCalculator` śledzi identyfikator zadania przy użyciu specjalnej klasy <xref:System.Collections.Specialized.HybridDictionary>kolekcji o nazwie . W definicji klasy <xref:System.Collections.Specialized.HybridDictionary> utwórz `userTokenToLifetime`nazwę .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Wdrażanie wydarzeń publicznych  
 Składniki implementujące wzorzec asynchroniczny oparty na zdarzeniach komunikują się z klientami przy użyciu zdarzeń. Te zdarzenia są wywoływane w odpowiednim wątku za pomocą <xref:System.ComponentModel.AsyncOperation> klasy.  
  
### <a name="to-raise-events-to-your-components-clients"></a>Aby podnieść zdarzenia do klientów twojego składnika:  
  
1. Implementowanie zdarzeń publicznych do raportowania do klientów. Będziesz potrzebować zdarzenia do raportowania postępu i jednego do raportowania zakończenia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementowanie metody uzupełniania  
 Delegat zakończenia jest metodą, że podstawowe, wolne wątków zachowanie asynchroniczne wywoła po zakończeniu operacji asynchronicznej przez pomyślne zakończenie, błąd lub anulowanie. To wywołanie dzieje się w dowolnym wątku.  
  
 Ta metoda jest, gdy identyfikator zadania klienta jest usuwany z wewnętrznej kolekcji unikatowych tokenów klienta. Ta metoda kończy również okres istnienia określonej operacji <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> asynchronicznej, wywołując metodę na odpowiednim <xref:System.ComponentModel.AsyncOperation>. To wywołanie wywołuje zdarzenie completion w wątku, który jest odpowiedni dla modelu aplikacji. Po <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> wywołaniu metody to <xref:System.ComponentModel.AsyncOperation> wystąpienie nie może być już używane, a wszelkie kolejne próby użycia go zwyżenia wyjątku.  
  
 Podpis `CompletionMethod` musi zawierać wszystkie stany niezbędne do opisania wyniku operacji asynchronicznej. Przechowuje stan dla liczby, która została przetestowana przez tę konkretną operację asynchroniczną, czy liczba jest pierwsza, a wartość jego pierwszego dzielnika, jeśli nie jest liczbą pierwszą. Posiada również stan opisujący wszelkie wyjątki, <xref:System.ComponentModel.AsyncOperation> które wystąpiły i odpowiadające temu konkretnemu zadaniu.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Aby ukończyć operację asynchroniczną:  
  
- Zaimplementuj metodę uzupełniania. Trwa sześć parametrów, których używa do `CalculatePrimeCompletedEventArgs` wypełniania a, który jest zwracany `CalculatePrimeCompletedEventHandler`do klienta za pośrednictwem klienta . Usuwa token identyfikatora zadania klienta z kolekcji wewnętrznej i kończy okres istnienia operacji asynchronicznej <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>wywołaniem . Organizuje <xref:System.ComponentModel.AsyncOperation> wywołanie wątku lub kontekstu, który jest odpowiedni dla modelu aplikacji.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnik.  
  
### <a name="to-test-your-component"></a>Aby przetestować komponent  
  
- Skompiluj składnik.  
  
     Otrzymasz jedno ostrzeżenie kompilatora:  
  
    ```console  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     To ostrzeżenie zostanie rozwiązane w następnej sekcji.  
  
## <a name="implementing-the-worker-methods"></a>Wdrażanie metod pracownika  
 Do tej pory zaimplementowano pomocniczy kod asynchroniczny dla składnika. `PrimeNumberCalculator` Teraz można zaimplementować kod, który wykonuje rzeczywistą pracę. Zaimplementujesz trzy `CalculateWorker`metody: `BuildPrimeNumberList`, `IsPrime`, i . Razem `BuildPrimeNumberList` i `IsPrime` obejmują dobrze znany algorytm o nazwie Sito Eratostenów, który określa, czy liczba jest pierwsza, znajdując wszystkie liczby pierwsze aż do pierwiastka kwadratowego numeru testowego. Jeśli w tym momencie nie zostaną znalezione żadne dzielniki, numer badania jest pierwszorzędny.  
  
 Jeśli ten składnik został napisany dla maksymalnej wydajności, zapamiętałby wszystkie liczby pierwsze wykryte przez różne wywołania dla różnych numerów testów. Byłoby to również sprawdzić, dla trywialnych dzielników, takich jak 2, 3 i 5. Celem tego przykładu jest wykazanie, jak czasochłonne operacje mogą być wykonywane asynchronicznie, jednak, więc te optymalizacje są pozostawione jako ćwiczenie dla Ciebie.  
  
 Metoda `CalculateWorker` jest opakowana w pełnomocnika i jest wywoływana asynchronicznie z wywołaniem `BeginInvoke`.  
  
> [!NOTE]
> Raportowanie postępu jest `BuildPrimeNumberList` implementowane w metodzie. Na szybkich `ProgressChanged` komputerach zdarzenia mogą być wywoływane w krótkim odstępie czasu. Wątek klienta, na którym te zdarzenia są wywoływane, musi być w stanie obsłużyć tę sytuację. Kod interfejsu użytkownika może być zalany wiadomościami i nie może nadążyć, co powoduje brak odpowiedzi. Przykładowy interfejs użytkownika, który obsługuje tę sytuację, zobacz [Jak: Implementowanie klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Aby wykonać obliczenie liczby pierwszej asynchronicznie:  
  
1. Zaimplementuj `TaskCanceled` metodę narzędzia. Spowoduje to sprawdzenie kolekcji okresu istnienia zadania `true` dla danego identyfikatora zadania i zwraca, jeśli nie zostanie znaleziony identyfikator zadania.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. Zaimplementuj `CalculateWorker` metodę. Do przetestowania potrzebne są dwa parametry: <xref:System.ComponentModel.AsyncOperation>liczba i parametr .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. Wdrożenie `BuildPrimeNumberList`. Trwa dwa parametry: liczba do przetestowania <xref:System.ComponentModel.AsyncOperation>i . Używa do <xref:System.ComponentModel.AsyncOperation> raportowania postępu i wyników przyrostowych. Zapewnia to, że programy obsługi zdarzeń klienta są wywoływane na odpowiednim wątku lub kontekstu dla modelu aplikacji. Po `BuildPrimeNumberList` znalezieniu liczby pierwszej, zgłasza to jako wynik przyrostowy do `ProgressChanged` obsługi zdarzeń klienta dla zdarzenia. Wymaga to klasy pochodzącej <xref:System.ComponentModel.ProgressChangedEventArgs> `CalculatePrimeProgressChangedEventArgs`od , o nazwie `LatestPrimeNumber`, która ma jedną dodaną właściwość o nazwie .  
  
     Metoda `BuildPrimeNumberList` również okresowo wywołuje `TaskCanceled` metodę i kończy działanie, jeśli metoda zwraca `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. Wdrożenie `IsPrime`. Potrzeba trzech parametrów: listy znanych liczb pierwszych, liczby do przetestowania i parametru wyjściowego dla pierwszego znalezionego dzielnika. Biorąc pod uwagę listę liczb pierwszych, określa, czy numer badania jest pierwszy.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. `CalculatePrimeProgressChangedEventArgs` Wyprowadzić <xref:System.ComponentModel.ProgressChangedEventArgs>z . Ta klasa jest niezbędna do raportowania wyników przyrostowych `ProgressChanged` do programu obsługi zdarzeń klienta dla zdarzenia. Ma jedną dodaną `LatestPrimeNumber`właściwość o nazwie .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnik.  
  
### <a name="to-test-your-component"></a>Aby przetestować komponent  
  
- Skompiluj składnik.  
  
     Wszystko, co pozostaje do zapisania są metody uruchamiania i `CalculatePrimeAsync` `CancelAsync`anulowania operacji asynchronicznych i .  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementowanie metod uruchamiania i anulowania  
 Metoda procesu roboczego można uruchomić `BeginInvoke` we własnym wątku, wywołując pełnomocnika, który opakowuje go. Aby zarządzać okres istnienia określonej operacji asynchronicznej, należy wywołać <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> metodę w klasie <xref:System.ComponentModel.AsyncOperationManager> pomocnika. Zwraca <xref:System.ComponentModel.AsyncOperation>, które marshals wywołuje obsługi zdarzeń klienta do właściwego wątku lub kontekstu.  
  
 Możesz anulować określoną oczekującą operację, wywołując <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> odpowiadającą jej . <xref:System.ComponentModel.AsyncOperation> Spowoduje to zakończenie tej operacji, <xref:System.ComponentModel.AsyncOperation> a wszelkie kolejne wywołania jego zrzuci wyjątek.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Aby zaimplementować funkcje Start i Cancel:  
  
1. Zaimplementuj `CalculatePrimeAsync` metodę. Upewnij się, że token dostarczony przez klienta (identyfikator zadania) jest unikatowy w odniesieniu do wszystkich tokenów reprezentujących aktualnie oczekujące zadania. Jeśli klient przekazuje w tokennie `CalculatePrimeAsync` nieunikatowym, wywołuje wyjątek. W przeciwnym razie token jest dodawany do kolekcji identyfikatora zadania.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. Zaimplementuj `CancelAsync` metodę. Jeśli `taskId` parametr istnieje w kolekcji tokenów, jest usuwany. Zapobiega to anulowaniu zadań, które nie zostały uruchomione. Jeśli zadanie jest uruchomione, `BuildPrimeNumberList` metoda kończy działanie, gdy wykryje, że identyfikator zadania został usunięty z kolekcji okresu istnienia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnik.  
  
### <a name="to-test-your-component"></a>Aby przetestować komponent  
  
- Skompiluj składnik.  
  
 Komponent `PrimeNumberCalculator` jest teraz kompletny i gotowy do użycia.  
  
 Przykładowy klient, który `PrimeNumberCalculator` używa składnika, zobacz [Jak: Implementowanie klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przykładzie można `CalculatePrime`wypełnić, pisząc synchroniczny odpowiednik `CalculatePrimeAsync` metody. Spowoduje to, `PrimeNumberCalculator` że składnik będzie w pełni zgodny z wzorcem asynchronicznym opartym na zdarzeniach.  
  
 W tym przykładzie można poprawić, zachowując listę wszystkich liczb pierwszych odnalezionych przez różne wywołania dla różnych numerów testów. Przy użyciu tego podejścia, każde zadanie będzie korzystać z pracy wykonanej przez poprzednie zadania. Należy zachować ostrożność, `lock` aby chronić tę listę z regionów, więc dostęp do listy przez różne wątki jest serializowany.  
  
 Można również poprawić ten przykład, testując dla trywialnych dzielników, takich jak 2, 3 i 5.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
