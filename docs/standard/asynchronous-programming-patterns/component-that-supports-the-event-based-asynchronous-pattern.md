---
title: 'Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach'
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
ms.openlocfilehash: d6c35398d54b91c9aa595ffdcde56004e59b7693
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882505"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach
Jeśli piszesz klasy z niektórych operacji, które może spowodować naliczenie zauważalnego opóźnienia, należy wziąć pod uwagę nadając mu funkcje asynchroniczne z zastosowaniem [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 W tym instruktażu pokazano, jak utworzyć składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach. Jej implementacji przy użyciu klas pomocy z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeń nazw, która zapewnia, że składnik działa prawidłowo w ramach dowolnego modelu aplikacji, w tym ASP.NET, aplikacji konsoli i aplikacji Windows Forms. Ten składnik jest również designable z <xref:System.Windows.Forms.PropertyGrid> kontroli i własnych niestandardowych projektantów.  
  
 Po zakończeniu wykonywania masz aplikację, która oblicza iloczyn liczb asynchronicznie. Twoja aplikacja będzie miała wątku interfejsu użytkownika głównego i wątku dla każdego obliczenia liczba pierwsza. Mimo że testowania, czy jest dużą liczbą prime może potrwać zauważalne ilość czasu, głównego wątku interfejsu użytkownika nie zostanie przerwana przez to opóźnienie i formularz będzie odpowiadać podczas obliczeń. Będzie można uruchomić, ponieważ wiele obliczeń, jak chcesz, aby jednocześnie i selektywnie anulowania oczekującego obliczeń.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
- Tworzenie składnika  
  
- Definiowanie zdarzenia asynchroniczne publiczne i delegatów  
  
- Definiowanie obiektów delegowanych prywatne  
  
- Implementowanie zdarzenia publiczne  
  
- Implementacja metody ukończenia  
  
- Implementacja metody pracownika  
  
- Implementowanie Start oraz Anuluj metod  
  
 Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Tworzenie składnika  
 Pierwszym krokiem jest można stworzyć komponentu, który będzie implementowany wzorca asynchronicznego opartego na zdarzeniach.  
  
#### <a name="to-create-the-component"></a>Aby utworzyć składnika  
  
- Utwórz klasę o nazwie `PrimeNumberCalculator` tej, która dziedziczy <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definiowanie zdarzenia asynchroniczne publiczne i delegatów  
 Składnik komunikuje się klientów przy użyciu zdarzeń. _MethodName_**Ukończono** alerty zdarzeń informujące o klientach do wykonania zadanie asynchroniczne, a _MethodName_**ProgressChanged**zdarzeń informuje klientów postęp zadania asynchronicznego.  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Aby zdefiniować zdarzenia asynchroniczne dla klientów składnika:  
  
1. Importuj <xref:System.Threading?displayProperty=nameWithType> i <xref:System.Collections.Specialized?displayProperty=nameWithType> przestrzeni nazw na początku pliku.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. Przed `PrimeNumberCalculator` definicji klasy zadeklarować delegatów dla zdarzeń o postępie i zakończeniu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. W `PrimeNumberCalculator` definicji klasy, deklarowanie zdarzeń do raportowania postępu i ukończenia dla klientów.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. Po `PrimeNumberCalculator` definicji klasy, pochodzi `CalculatePrimeCompletedEventArgs` klasy raportowania wyników dostosowywania obliczeń do obsługi zdarzeń klienta `CalculatePrimeCompleted`.event. Oprócz `AsyncCompletedEventArgs` właściwości, ta klasa umożliwia klientowi określenie, jakiego numeru został przetestowany, czy jest zainicjowanie i co to jest pierwszy dzielnik, jeśli nie jest podstawowym.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnika.  
  
#### <a name="to-test-your-component"></a>Aby przetestować składnika  
  
- Skompiluj składnika.  
  
     Otrzymasz dwa ostrzeżenia kompilatora:  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Ostrzeżenia te zostaną wyczyszczone w następnej sekcji.  
  
## <a name="defining-private-delegates"></a>Definiowanie obiektów delegowanych prywatne  
 Asynchroniczne aspektów `PrimeNumberCalculator` składnika są implementowane wewnętrznie z delegatem specjalne, znane jako <xref:System.Threading.SendOrPostCallback>. A <xref:System.Threading.SendOrPostCallback> reprezentuje metodę wywołania zwrotnego, który jest wykonywany na <xref:System.Threading.ThreadPool> wątku. Metoda wywołania zwrotnego musi mieć podpis, który przyjmuje jeden parametr typu <xref:System.Object>, co oznacza należy przekazać stan wśród delegatów klasy otoki. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.SendOrPostCallback>.  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Aby zaimplementować wewnętrznego zachowanie asynchroniczne danego składnika:  
  
1. Deklarowanie i tworzenie <xref:System.Threading.SendOrPostCallback> deleguje odpowiednie uprawnienia w `PrimeNumberCalculator` klasy. Tworzenie <xref:System.Threading.SendOrPostCallback> obiektów w metodzie narzędzia o nazwie `InitializeDelegates`.  
  
     Konieczne będzie dwa delegaty: jeden dla raportowania postępu do klienta i jeden dla raportowania uzupełniania do klienta.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. Wywołaj `InitializeDelegates` metody w Konstruktorze danego składnika.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. Zdeklarować delegatów w `PrimeNumberCalculator` klasa, która obsługuje faktyczną pracę do wykonania asynchronicznie. Ten delegat jest zawijany metodzie wątku roboczego, który umożliwia sprawdzenie, czy liczba jest pierwsze. Delegat przyjmuje <xref:System.ComponentModel.AsyncOperation> parametr, który będzie służyć do śledzenia okresu istnienia operację asynchroniczną.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Utwórz kolekcję do zarządzania okresy istnienia oczekujących operacji asynchronicznych. Klient musi mieć możliwość śledzenia operacji są wykonane i ukończone, a to śledzenie odbywa się przez wymaganie klientowi na przekazywanie unikatowy token lub identyfikator zadania, gdy klient wysyła wywołania metody asynchronicznej. `PrimeNumberCalculator` Składnik musi zachować informacje o każde wywołanie przez skojarzenie Identyfikatora zadania za pomocą jego odpowiedniego wywołania. Jeśli klient przekazuje identyfikator zadania, który nie jest unikatowa, `PrimeNumberCalculator` składnika należy zgłosić wyjątek.  
  
     `PrimeNumberCalculator` Składnika śledzi informacje o identyfikator zadania przy użyciu klasy specjalne kolekcji o nazwie <xref:System.Collections.Specialized.HybridDictionary>. W definicji klasy, należy utworzyć <xref:System.Collections.Specialized.HybridDictionary> o nazwie `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implementowanie zdarzenia publiczne  
 Składniki, które implementują wzorzec asynchroniczny oparty na zdarzeniach komunikowania się klientów przy użyciu zdarzeń. Te zdarzenia są wywoływane w wątku za pomocą <xref:System.ComponentModel.AsyncOperation> klasy.  
  
#### <a name="to-raise-events-to-your-components-clients"></a>Aby wywołać zdarzenia do klientów danego składnika:  
  
1. Implementowanie publicznych zdarzeń do raportowania do klientów. Konieczne będzie zdarzenia do raportowania postępu i jeden dla raportowania ukończenia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementacja metody ukończenia  
 Delegat zakończenia jest metoda, zachowanie asynchroniczne bazowego, bezwątkowy wywołujący podczas kończenia operacji asynchronicznej, pomyślne wykonanie, błędu lub anulowania. To wywołanie ma miejsce w dowolnego wątku.  
  
 Ta metoda jest, gdzie identyfikator zadania klienta zostanie usunięty z wewnętrznych kolekcję tokenów unikatowych klientów. Ta metoda kończy się na okres istnienia określonej operacji asynchronicznej, wywołując <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> metody w odpowiedniej <xref:System.ComponentModel.AsyncOperation>. To wywołanie zgłasza zdarzenie zakończenia w wątku, który jest odpowiedni dla modelu aplikacji. Po <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> metoda jest wywoływana, to wystąpienie <xref:System.ComponentModel.AsyncOperation> już nie mogą być używane, a wszystkie kolejne próby, aby użyć go spowoduje zgłoszenie wyjątku.  
  
 `CompletionMethod` Podpisu musi, przytrzymaj wszystkich stanów będzie konieczne do opisania wynik operacji asynchronicznej. Przechowuje stan numer który został przetestowany przez określoną operację asynchroniczną, czy jest pierwsze, a wartość jego pierwszym dzielnik, jeśli nie jest to liczba pierwsza. Również przechowuje stan opisujące każdy wyjątek, które wystąpiły, oraz <xref:System.ComponentModel.AsyncOperation> odpowiadający tego konkretnego zadania.  
  
#### <a name="to-complete-an-asynchronous-operation"></a>Aby ukończyć operację asynchroniczną:  
  
- Implementuje metody ukończenia. Trwa sześć parametrów, których używa, aby wypełnić `CalculatePrimeCompletedEventArgs` , jest zwracana do klienta za pomocą klienta programu `CalculatePrimeCompletedEventHandler`. Usuwa token identyfikator zadania klienta z wewnętrznego zbioru, a kończy się ona istnienia operację asynchroniczną z wywołaniem <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. <xref:System.ComponentModel.AsyncOperation> Kieruje wywołania wątku lub kontekstu, który jest odpowiedni dla modelu aplikacji.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnika.  
  
#### <a name="to-test-your-component"></a>Aby przetestować składnika  
  
- Skompiluj składnika.  
  
     Zostanie wyświetlony jeden ostrzeżenia kompilatora:  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     To ostrzeżenie zostanie rozwiązany w następnej sekcji.  
  
## <a name="implementing-the-worker-methods"></a>Implementacja metody pracownika  
 Do tej pory udało Ci się wdrożyć pomocnicze kod asynchroniczny `PrimeNumberCalculator` składnika. Teraz można zaimplementować kod, który wykonuje faktyczną pracę. Wdroży trzy metody: `CalculateWorker`, `BuildPrimeNumberList`, i `IsPrime`. Razem `BuildPrimeNumberList` i `IsPrime` składają się dobrze znanym algorytmem o nazwie sito Eratostenesa, który określa, czy liczba jest iloczyn, wyszukując liczb pierwszych maksymalnie pierwiastek kwadratowy liczby testów. Jeśli dzielników nie zostaną znalezione przez ten punkt, liczba testów znajduje się pierwsze.  
  
 Ten składnik zostały opracowane pod kątem maksymalnej efektywności, czy należy pamiętać liczb pierwszych odnalezione przez różne wywołania w przypadku liczb różnych testów. Może on także sprawdzić dzielników prosta, podobnie jak 2, 3 i 5. Celem tego przykładu jest pokazują, jak czas operacji może być wykonywany asynchronicznie, jednak dzięki Optymalizacje te są pozostawiane w charakterze ćwiczenia dla Ciebie.  
  
 `CalculateWorker` Metoda jest opakowana w obiekt delegowany i jest wywoływana asynchronicznie przy użyciu wywołania do `BeginInvoke`.  
  
> [!NOTE]
>  Raportowanie postępu jest zaimplementowana w `BuildPrimeNumberList` metody. Na komputerach szybkie `ProgressChanged` zdarzenia mogą być wywoływane w krótkim odstępie czasu. Wątek klienta, na którym te zdarzenia są wywoływane, musi mieć możliwość obsługi takiej sytuacji. Kod interfejsu użytkownika może być przeciążony wiadomości i nie może nadążyć, wynikiem zawiesza się zachowanie. Dla interfejsu użytkownika przykład obsługujący tę sytuację, zobacz [jak: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Asynchroniczne wykonywanie obliczeń liczba pierwsza:  
  
1. Implementowanie `TaskCanceled` metoda narzędzia. To sprawdza, czy kolekcja zadań okres istnienia dla Identyfikatora danego zadania i zwraca `true` Jeśli identyfikator zadania nie zostanie znaleziony.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. Implementowanie `CalculateWorker` metody. Trwa dwa parametry: numer do testowania oraz wiadomość <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. Implementowanie `BuildPrimeNumberList`. Trwa dwa parametry: numer, aby przetestować i <xref:System.ComponentModel.AsyncOperation>. Używa ona <xref:System.ComponentModel.AsyncOperation> raportować postęp i wyniki przyrostowe. Gwarantuje to, że klienta zdarzenia są wywoływane programy obsługi na wątku lub kontekstu dla modelu aplikacji. Gdy `BuildPrimeNumberList` napotka liczba pierwsza, zgłasza to przyrostowe wyniku do klienta programu obsługi zdarzeń dla `ProgressChanged` zdarzeń. Wymaga to klasy pochodzącej od <xref:System.ComponentModel.ProgressChangedEventArgs>, co jest nazywane `CalculatePrimeProgressChangedEventArgs`, która ma jeden dodawana właściwość o nazwie `LatestPrimeNumber`.  
  
     `BuildPrimeNumberList` Okresowo wywołania metod `TaskCanceled` metody i wyjścia, jeśli metoda zwraca `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. Implementowanie `IsPrime`. Zajmuje trzy parametry: lista znanych liczb pierwszych, numer do testowania i parametru wyjściowego dla dzielnik pierwszy znaleziono. Podana lista liczb pierwszych, ustala, czy iloczyn liczby testów.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. Pochodzi `CalculatePrimeProgressChangedEventArgs` z <xref:System.ComponentModel.ProgressChangedEventArgs>. Ta klasa jest niezbędne do raportowania wyników przyrostowe klienta programu obsługi zdarzeń dla `ProgressChanged` zdarzeń. Ma on jeden dodano właściwości o nazwie `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnika.  
  
#### <a name="to-test-your-component"></a>Aby przetestować składnika  
  
- Skompiluj składnika.  
  
     Wszystkie opcje, które pozostają do zapisania są metody, aby uruchomić i anulowania operacji asynchronicznych, `CalculatePrimeAsync` i `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementowanie Start oraz Anuluj metody  
 Rozpocznij metodzie wątku roboczego w jego własnym wątku, łącząc `BeginInvoke` na delegata, który otacza go. Aby zarządzać okresem istnienia określonej operacji asynchronicznej, należy wywołać <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> metody <xref:System.ComponentModel.AsyncOperationManager> klasy pomocy. Spowoduje to zwrócenie <xref:System.ComponentModel.AsyncOperation>, który kieruje wywołań na klienta programu obsługi zdarzeń do wątku lub kontekstu.  
  
 Anuluj określonego oczekującą operację, wywołując <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> na odpowiadającymi mu dostawcami <xref:System.ComponentModel.AsyncOperation>. To kończy się w tej operacji i kolejnych wywołań jej <xref:System.ComponentModel.AsyncOperation> spowoduje zgłoszenie wyjątku.  
  
#### <a name="to-implement-start-and-cancel-functionality"></a>Aby zaimplementować Start i anulować funkcji:  
  
1. Implementowanie `CalculatePrimeAsync` metody. Upewnij się, że token dostarczony przez klienta (identyfikator zadania) jest unikatowa w ramach wszystkich tokenów reprezentujący obecnie oczekujące zadania. Jeśli klient zakończy się pomyślnie w tokenie nie jest unikatowa, `CalculatePrimeAsync` zgłasza wyjątek. W przeciwnym razie token zostanie dodany do kolekcji identyfikator zadania.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. Implementowanie `CancelAsync` metody. Jeśli `taskId` parametr istnieje w kolekcji tokenu, zostaje usunięty. Zapobiega to anulowanych zadań, które nie rozpoczęły się uruchamianie. Jeśli zadanie jest uruchomione, `BuildPrimeNumberList` metoda kończy działanie po wykryciu, że identyfikator zadania został usunięty z kolekcji okresu istnienia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnika.  
  
#### <a name="to-test-your-component"></a>Aby przetestować składnika  
  
- Skompiluj składnika.  
  
 `PrimeNumberCalculator` Jest teraz gotowy do użycia.  
  
 Na przykład klienci, którzy korzystają `PrimeNumberCalculator` składników, zobacz [jak: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz też wypełnić ten przykład, pisząc `CalculatePrime`, synchroniczne wielokrotność `CalculatePrimeAsync` metody. Dzięki temu `PrimeNumberCalculator` składnika w pełni zgodne, za pomocą wzorca asynchronicznego opartego na zdarzeniach.  
  
 W tym przykładzie można poprawić, zachowując listę liczb pierwszych odnalezione przez różne wywołania w przypadku liczb różnych testów. Użycie tej metody, każde zadanie podrzędne będą mogli korzystać z pracy wykonanej przez poprzednich zadań. Uważaj chronić tej listy z `lock` regionach, dzięki czemu dostęp do listy przez inne wątki jest serializowana.  
  
 W tym przykładzie można również poprawić poprzez testowanie dzielników prosta, podobnie jak 2, 3 i 5.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
