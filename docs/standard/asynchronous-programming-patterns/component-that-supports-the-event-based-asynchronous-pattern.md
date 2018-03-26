---
title: 'Wskazówki: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d42c1d4b58f5e2517ff8d8c504628c7aab6fd0d
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="walkthrough-implementing-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Wskazówki: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach
Podczas pisania klasy z niektórych operacji, które może pociągnąć za sobą zauważalnego opóźnienia, należy wziąć pod uwagę nadanie mu funkcji asynchroniczności zaimplementowanie [oparty na zdarzeniach asynchroniczny wzorzec — Przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 W tym przewodniku ilustruje sposób tworzenia składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach. Jest stosowana przy użyciu klasy pomocy z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw, który zapewnia składnika działa prawidłowo w modelu żadnych aplikacji, w tym [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konsoli aplikacji i aplikacjach formularzy systemu Windows. Ten składnik jest również designable z <xref:System.Windows.Forms.PropertyGrid> własne niestandardowe projektantów i kontroli.  
  
 Po zakończeniu wykonywania masz aplikację, która oblicza liczb pierwszych asynchronicznie. Aplikacja będzie mieć wątku interfejsu użytkownika głównego i wątków dla każdego obliczania liczba pierwsza. Chociaż sprawdzenie, czy jest dużą liczbą prime może zająć zauważalne ilość czasu, głównego wątku interfejsu użytkownika nie zostanie przerwana przez to opóźnienie i formularz będzie odpowiadać podczas obliczeń. Będzie można uruchomić zgodnie z wielu obliczeń, jak jednocześnie i selektywnie anulowania oczekującego obliczeń.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie składnika  
  
-   Definiowanie zdarzenia asynchroniczne publiczne i Delegaty  
  
-   Definiowanie obiektów delegowanych prywatnych  
  
-   Implementowanie zdarzenia publiczne  
  
-   Implementacja metody ukończenia  
  
-   Implementacja metody pracownika  
  
-   Implementowanie Start i metody Anuluj  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: implementacja klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Tworzenie składnika  
 Pierwszym krokiem jest utworzyć składnika, który będzie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach.  
  
#### <a name="to-create-the-component"></a>Aby utworzyć składnika  
  
-   Tworzenie klasy o nazwie `PrimeNumberCalculator` dziedziczący po <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definiowanie zdarzenia asynchroniczne publiczne i Delegaty  
 Składnik komunikuje się klientów przy użyciu zdarzenia. *MethodName *** Ukończono** alerty zdarzeń informujące o klientów do wykonania zadanie asynchroniczne i *MethodName *** ProgressChanged** zdarzeń poinformuje klientów postęp zadania asynchronicznego.  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Aby zdefiniować zdarzenia asynchroniczne dla klientów składnika:  
  
1.  Importuj <xref:System.Threading?displayProperty=nameWithType> i <xref:System.Collections.Specialized?displayProperty=nameWithType> przestrzeni nazw w górnej części pliku.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  Przed `PrimeNumberCalculator` klasy definicji, Zadeklaruj delegatów dla zdarzeń o postępie i zakończeniu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  W `PrimeNumberCalculator` definicji klasy, deklarowanie zdarzeń do raportowania postępie i zakończeniu do klientów.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  Po `PrimeNumberCalculator` definicji klasy, pochodzi `CalculatePrimeCompletedEventArgs` klasy raportowania w wyniku obliczenia każdego klienta programu obsługi zdarzeń dla `CalculatePrimeCompleted`.event. Oprócz `AsyncCompletedEventArgs` właściwości, ta klasa umożliwia klienta w celu określenia jakiego numeru przetestowano, czy jest zapisują i co to jest pierwszy dzielnik, jeśli nie jest podstawowym.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnika.  
  
#### <a name="to-test-your-component"></a>Aby przetestować składnika  
  
-   Kompiluj składnika.  
  
     Użytkownik otrzyma dwie ostrzeżenia kompilatora:  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Te ostrzeżenia dotyczące zostaną usunięte w następnej sekcji.  
  
## <a name="defining-private-delegates"></a>Definiowanie obiektów delegowanych prywatnych  
 Asynchroniczne aspektów `PrimeNumberCalculator` składnika są implementowane wewnętrznie z delegatem specjalne, znany jako <xref:System.Threading.SendOrPostCallback>. A <xref:System.Threading.SendOrPostCallback> reprezentuje metodę wywołania zwrotnego, która wykonuje na <xref:System.Threading.ThreadPool> wątku. Metoda wywołania zwrotnego musi mieć podpisie, który przyjmuje jeden parametr typu <xref:System.Object>, co oznacza należy przekazać stanu między delegatów klasy otoki. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.SendOrPostCallback>.  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Aby zaimplementować wewnętrzne zachowanie asynchroniczne danego składnika:  
  
1.  Deklarowanie i tworzenie <xref:System.Threading.SendOrPostCallback> deleguje w `PrimeNumberCalculator` klasy. Utwórz <xref:System.Threading.SendOrPostCallback> obiektów w metodzie narzędzie `InitializeDelegates`.  
  
     Konieczne będzie dwóch delegatów: jeden dla raportowania postępu do klienta, a drugi dla raportowania uzupełniania do klienta.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  Wywołanie `InitializeDelegates` metody w Konstruktorze danego składnika.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  Zadeklarować obiektu delegowanego w `PrimeNumberCalculator` klasa, która obsługuje rzeczywiste pracy asynchronicznie. Ten delegat jest zawijana metody pracownika, który umożliwia sprawdzenie, czy liczba jest pierwsze. Delegat przyjmuje <xref:System.ComponentModel.AsyncOperation> parametr, który będzie służyć do śledzenia okres istnienia operację asynchroniczną.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  Utwórz kolekcję do zarządzania okresy istnienia oczekujących operacji asynchronicznych. Klient musi mieć możliwość śledzenia operacji są wykonane i ukończone, a to śledzenie odbywa się wymagając od klienta do przekazywania tokenu unikatowy lub identyfikator zadania, gdy klient wysyła wywołania do metody asynchronicznej. `PrimeNumberCalculator` Składnika musi zachować informacje o każdym wywołaniu przez skojarzenie Identyfikatora zadania z odpowiedniego wywołania. Jeśli klient przechodzi Identyfikatora zadania, która nie jest unikatowa, `PrimeNumberCalculator` składnika należy zgłosić wyjątek.  
  
     `PrimeNumberCalculator` Składnika przechowuje informacje o identyfikatorze zadania przy użyciu klasy specjalne kolekcji o nazwie <xref:System.Collections.Specialized.HybridDictionary>. W definicji klasy, należy utworzyć <xref:System.Collections.Specialized.HybridDictionary> o nazwie `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implementowanie zdarzenia publiczne  
 Składniki, które implementują wzorzec asynchroniczny oparty na zdarzeniach komunikują się klientów przy użyciu zdarzenia. Te zdarzenia są wywoływane w wątku prawidłowego za pomocą <xref:System.ComponentModel.AsyncOperation> klasy.  
  
#### <a name="to-raise-events-to-your-components-clients"></a>Aby wywołać zdarzenia do danego składnika klientów:  
  
1.  Implementuje publicznego zdarzeń do raportowania do klientów. Konieczne będzie zdarzenia do raportowania postępu i jeden dla raportowania zakończenia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementacja metody ukończenia  
 Delegat zakończenia jest metody, wywołujący podstawowej, bezwątkowe zachowanie asynchronicznych po zakończeniu operacji asynchronicznej ukończone pomyślnie, błąd lub anulowania. To wywołanie odbywa się dla dowolnego wątku.  
  
 Ta metoda jest, gdzie zadania o identyfikatorze klienta zostanie usunięty z wewnętrznej kolekcji tokeny unikatowych klientów. Ta metoda kończy się okres istnienia określonej operacji asynchronicznej wywołując <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> metody w odpowiedniej <xref:System.ComponentModel.AsyncOperation>. To wywołanie zgłasza zdarzenie ukończenia w wątku, który jest odpowiedni dla modelu aplikacji. Po <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> metoda jest wywoływana, to wystąpienie <xref:System.ComponentModel.AsyncOperation> nie mogą być używane, a wszystkie kolejne próby, aby użyć go spowoduje zgłoszenie wyjątku.  
  
 `CompletionMethod` Podpis musi, przytrzymaj wszystkich stanów będzie niezbędne do opisywania wynik operacji asynchronicznej. Przechowuje stan liczba, która została testowała tej asynchronicznej operacji, czy jest pierwsze i wartość jego pierwszy dzielnik, jeśli nie jest liczba pierwsza. Posiada opisujące każdy wyjątek, który wystąpił, stanu i <xref:System.ComponentModel.AsyncOperation> odpowiadający to konkretne zadanie.  
  
#### <a name="to-complete-an-asynchronous-operation"></a>Aby zakończyć operację asynchroniczną:  
  
-   Implementuje metody ukończenia. Trwa sześć parametrów, których używa do wypełnienia `CalculatePrimeCompletedEventArgs` która jest zwracana do klienta przez klienta `CalculatePrimeCompletedEventHandler`. Usuwa token Identyfikatora zadania klienta z wewnętrznej kolekcji i zakończenia okresu istnienia operację asynchroniczną z wywołaniem do <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. <xref:System.ComponentModel.AsyncOperation> Marshals wywołanie thread lub context, który jest odpowiedni dla modelu aplikacji.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnika.  
  
#### <a name="to-test-your-component"></a>Aby przetestować składnika  
  
-   Kompiluj składnika.  
  
     Zostanie wyświetlone ostrzeżenie kompilatora co:  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     To ostrzeżenie zostanie rozwiązany w następnej sekcji.  
  
## <a name="implementing-the-worker-methods"></a>Implementacja metody pracownika  
 Do tej pory zaimplementowano obsługi kod asynchroniczne `PrimeNumberCalculator` składnika. Teraz można wdrożyć kod, który wykonuje całą pracę. Wdroży trzy metody: `CalculateWorker`, `BuildPrimeNumberList`, i `IsPrime`. Razem `BuildPrimeNumberList` i `IsPrime` obejmują dobrze znanym algorytmem o nazwie sito Eratosthenes, która określa, czy liczba jest pierwsze znajdując liczb pierwszych maksymalnie pierwiastek kwadratowy liczby testów. Jeśli nie zostaną znalezione nie divisors przez ten punkt, liczba testów jest pierwsze.  
  
 Ten składnik zostały napisane z maksymalną wydajnością, czy należy pamiętać liczb pierwszych odnalezione przez różnych wywołań numerów innego testu. Będzie on również sprawdzić trivial divisors jak 2, 3 i 5. Celem tego przykładu jest pokazują, jak czas operacji mogą być wykonywane asynchronicznie, jednak tak te optymalizacje pozostało jako wykonywania dla Ciebie.  
  
 `CalculateWorker` Metody jest ujęte w delegata i została wywołana asynchronicznie przy wywołaniu `BeginInvoke`.  
  
> [!NOTE]
>  Raportowanie postępu jest zaimplementowana w `BuildPrimeNumberList` metody. Na komputerach szybkiego `ProgressChanged` zdarzeń może być wywoływany w krótkim odstępie czasu. Wątek klienta, na którym te zdarzenia są generowane, musi mieć możliwość obsługi tej sytuacji. Kod interfejsu użytkownika może być przeciążony wiadomości i nie można przechowywać, co powoduje zachowanie wysunięcie. Dla interfejsu użytkownika przykład obsługująca tej sytuacji, zobacz [porady: implementacja klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Można wykonać obliczania liczba pierwsza asynchronicznie:  
  
1.  Implementowanie `TaskCanceled` narzędzie metody. To sprawdza kolekcji cykl życia zadania dla Identyfikatora danego zadania i zwraca `true` Jeżeli nie znaleziono Identyfikatora zadania.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  Implementowanie `CalculateWorker` metody. Trwa dwa parametry: numer do testowania oraz usługi <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  Implementowanie `BuildPrimeNumberList`. Trwa dwa parametry: numer, aby przetestować i <xref:System.ComponentModel.AsyncOperation>. Używa <xref:System.ComponentModel.AsyncOperation> raportu postęp i wyniki przyrostowe. Gwarantuje to, że obsługi zdarzeń klienckich są nazywane na właściwy wątku lub kontekst dla modelu aplikacji. Gdy `BuildPrimeNumberList` znajduje liczbę pierwszych, zgłasza to przyrostowe wyniku do klienta programu obsługi zdarzeń dla `ProgressChanged` zdarzeń. Wymaga to klasy pochodzącej od <xref:System.ComponentModel.ProgressChangedEventArgs>o nazwie `CalculatePrimeProgressChangedEventArgs`, która ma jeden dodawana właściwość o nazwie `LatestPrimeNumber`.  
  
     `BuildPrimeNumberList` Okresowo wywołuje metodę `TaskCanceled` — metoda i wyjściach, jeśli metoda zwraca `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  Implementowanie `IsPrime`. Trwa trzy parametry: lista znanych liczb pierwszych, numer do testowania i parametru wyjściowego dla pierwszego dzielnik znaleziono. Podana lista liczb pierwszych, jego Określa, czy kod testu jest pierwsze.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  Pochodzi `CalculatePrimeProgressChangedEventArgs` z <xref:System.ComponentModel.ProgressChangedEventArgs>. Ta klasa jest niezbędne do raportowania wyników przyrostowe do klienta programu obsługi zdarzeń dla `ProgressChanged` zdarzeń. Ma on jeden dodanych właściwości o nazwie `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnika.  
  
#### <a name="to-test-your-component"></a>Aby przetestować składnika  
  
-   Kompiluj składnika.  
  
     Wszystkie opcje, które pozostaną do zapisania są metody służące do uruchomienia i anulować operacji asynchronicznych `CalculatePrimeAsync` i `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementacja punktu początkowego i metod Anuluj  
 Start — metoda procesu roboczego w jego własnym wątku przez wywołanie metody `BeginInvoke` na delegata, który opakowuje go. Aby zarządzać okres istnienia określonej operacji asynchronicznej, należy wywołać <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> metoda <xref:System.ComponentModel.AsyncOperationManager> klasy pomocy. To polecenie zwróci <xref:System.ComponentModel.AsyncOperation>, który marshals wywołania dla klienta programu obsługi zdarzeń do właściwego thread lub context.  
  
 Anuluj określonego oczekującą operację wywołując <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> na odpowiednie <xref:System.ComponentModel.AsyncOperation>. Kończy operację tej i kolejnych wywołań jego <xref:System.ComponentModel.AsyncOperation> spowoduje zgłoszenie wyjątku.  
  
#### <a name="to-implement-start-and-cancel-functionality"></a>Aby zaimplementować Start i anulować funkcji:  
  
1.  Implementowanie `CalculatePrimeAsync` metody. Upewnij się, że token dostarczony przez klienta (identyfikator zadania) jest unikatowa względem wszystkich tokenów reprezentujący aktualnie oczekujących zadań. Jeśli klient przechodzi do tokenu nie jest unikatowa, `CalculatePrimeAsync` zgłasza wyjątek. W przeciwnym razie wartość tokenu jest dodawany do kolekcji identyfikator zadania.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  Implementowanie `CancelAsync` metody. Jeśli `taskId` parametr istnieje w kolekcji tokenu, zostanie ono usunięte. Zapobiega to anulowanych zadań, które nie rozpoczęły uruchamianie. Jeśli zadanie jest uruchomione, `BuildPrimeNumberList` — metoda kończy działanie, gdy wykryje, że identyfikator zadania został usunięty z kolekcji okres istnienia.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można utworzyć składnika.  
  
#### <a name="to-test-your-component"></a>Aby przetestować składnika  
  
-   Kompiluj składnika.  
  
 `PrimeNumberCalculator` Składnika jest teraz gotowy do użycia.  
  
 Na przykład klienta, który używa `PrimeNumberCalculator` składników, zobacz [porady: implementacja klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz też wypełnić w tym przykładzie pisząc `CalculatePrime`, synchroniczne odpowiednikiem `CalculatePrimeAsync` metody. Spowoduje to `PrimeNumberCalculator` składnika w pełni zgodne, za pomocą wzorca asynchronicznego opartego na zdarzeniach.  
  
 W tym przykładzie można zwiększyć, zachowując listy liczb pierwszych odnalezione przez różnych wywołań numerów innego testu. W ten sposób każdego zadania będą korzystać z pracy wykonanej przez poprzednich zadań. Chroń tej listy z `lock` regionach, więc jest serializowany dostęp do listy przez inne wątki.  
  
 W tym przykładzie można również poprawić przez testowanie pod kątem trivial divisors, takie jak 2, 3 i 5.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [NIE w kompilacji: Wielowątkowość w języku Visual Basic](http://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
