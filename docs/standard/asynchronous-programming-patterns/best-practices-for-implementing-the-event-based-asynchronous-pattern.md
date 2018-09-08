---
title: Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 4acd2094-4f46-4eff-9190-92d0d9ff47db
ms.openlocfilehash: e50f455ab83b0b057f8ce3c32f874e6856632d70
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133626"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach
Asynchroniczny wzorzec oparty na zdarzeniach zapewnia skuteczny sposób udostępnienia zachowanie asynchroniczne w klasach, za pomocą dobrze znanych zdarzenia i delegować semantyki. Aby zaimplementować wzorzec asynchroniczny oparty na zdarzeniach, należy wykonać niektóre szczególne wymagania funkcjonalne. W poniższych sekcjach opisano wymagania i wskazówki, które należy wziąć pod uwagę podczas implementowania klasę, która następuje po wzorca asynchronicznego opartego na zdarzeniach.  
  
 Aby uzyskać przegląd, zobacz [implementacja wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Wymagane zachowania gwarancji  
 W przypadku zastosowania wzorca asynchronicznego opartego na zdarzeniach, należy podać liczbę gwarancje w celu zapewnienia, że klasa będzie działać prawidłowo, a klientów klasy może polegać na takie zachowanie.  
  
### <a name="completion"></a>Uzupełnianie  
 Zawsze wywołuje <em>MethodName</em>**Ukończono** program obsługi zdarzeń w przypadku pomyślnego zakończenia, błędu lub anulowania. Aplikacje nigdy nie powinny wystąpić sytuacja, w którym mogą pozostawać bezczynne i uzupełniania nigdy nie następuje. Jedynym wyjątkiem od tej reguły jest, jeśli operacja asynchroniczna, sama go tak zaprojektowane, aby nigdy nie zostanie zakończona.  
  
### <a name="completed-event-and-eventargs"></a>Zdarzenie ukończone i EventArgs  
 Dla każdego oddzielnego <em>MethodName</em>**Async** metody, zastosuj następujące wymagania:  
  
-   Zdefiniuj <em>MethodName</em>**Ukończono** zdarzenia na tej samej klasy jako metody.  
  
-   Zdefiniuj <xref:System.EventArgs> klasy i towarzyszące delegata <em>MethodName</em>**Ukończono** zdarzeń, która pochodzi od klasy <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy. Domyślna nazwa klasy powinna mieć postać <em>MethodName</em>**CompletedEventArgs**.  
  
-   Upewnij się, że <xref:System.EventArgs> klasy dotyczy wartości zwracanych metody <em>MethodName</em> metody. Kiedy używasz <xref:System.EventArgs> klasy, należy nigdy nie wymagać deweloperom Rzutuj wynik metody.  
  
     Poniższy przykład kodu pokazuje implementację dobre i złe to wymaganie projektowe można spełnić odpowiednio.  
  
```csharp  
// Good design  
private void Form1_MethodNameCompleted(object sender, xxxCompletedEventArgs e)   
{   
    DemoType result = e.Result;  
}  
  
// Bad design  
private void Form1_MethodNameCompleted(object sender, MethodNameCompletedEventArgs e)   
{   
    DemoType result = (DemoType)(e.Result);  
}  
```  
  
-   Nie definiują <xref:System.EventArgs> klasy dla zwracania metody, które zwracają `void`. Zamiast tego należy użyć wystąpienia <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy.  
  
-   Upewnij się, że zawsze podniesieniu <em>MethodName</em>**Ukończono** zdarzeń. To zdarzenie powinien być wywoływany po pomyślnym ukończeniu, błędu lub anulowania. Aplikacje nigdy nie powinny wystąpić sytuacja, w którym mogą pozostawać bezczynne i uzupełniania nigdy nie następuje.  
  
-   Upewnij się, że zostaną wychwycone wszelkie wyjątki, które występują w operacji asynchronicznej i przypisz przechwycony wyjątek do <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwości.  
  
-   Wystąpił błąd podczas wykonywania zadania, wyniki powinny być niedostępne. Gdy <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwość nie jest `null`, upewnij się, że uzyskiwania dostępu do wszystkich właściwości w <xref:System.EventArgs> struktury zgłasza wyjątek. Użyj <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> metodę, aby przeprowadzić tę weryfikację.  
  
-   Model przekroczenia limitu czasu jako błąd. W przypadku przekroczenia limitu czasu podnieść <em>MethodName</em>**Ukończono** zdarzenie i przypisz <xref:System.TimeoutException> do <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwości.  
  
-   Jeśli klasa obsługuje wiele równoczesnych wywołań, upewnij się, że <em>MethodName</em>**Ukończono** zdarzenie zawiera odpowiednie `userSuppliedState` obiektu.  
  
-   Upewnij się, że <em>MethodName</em>**Ukończono** zdarzenie jest zgłaszane w odpowiednich wątku i w odpowiednim czasie w cyklu życia aplikacji. Aby uzyskać więcej informacji zobacz sekcję wątki i kontekstów.  
  
### <a name="simultaneously-executing-operations"></a>Jednocześnie wykonywania operacji  
  
-   Jeśli klasa obsługuje wiele równoczesnych wywołań, należy włączyć dla deweloperów śledzić każdego wywołania oddzielnie, definiując <em>MethodName</em>**Async** przeciążenia przyjmującego zwracającej obiekt stanu parametr lub identyfikator zadania o nazwie `userSuppliedState`. Ten parametr powinien zawsze być ostatnim parametrem <em>MethodName</em>**Async** podpis metody.  
  
-   Jeśli klasa definiuje <em>MethodName</em>**Async** przeciążenia przyjmującego parametr zwracającej obiekt stanu lub identyfikator zadania: Pamiętaj śledzić okres istnienia operację, podając identyfikator tego zadania i pamiętaj podać go ponownie do procedury obsługi zakończenia. Brak klasy pomocy jest dostępny. Aby uzyskać więcej informacji na temat zarządzania współbieżności, zobacz [porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
-   Jeśli klasa definiuje <em>MethodName</em>**Async** metody bez parametru stanu, a nie obsługuje wielu równoczesnych wywołań, upewnij się, że dowolne próba wywołania <em>MethodName</em>  **Async** przed wcześniej <em>MethodName</em>**Async** wywołanie zostało zakończone zgłasza <xref:System.InvalidOperationException>.  
  
-   Ogólnie rzecz biorąc, nie zgłosić wyjątek, jeśli <em>MethodName</em>**Async** metody bez `userSuppliedState` parametru jest wywoływana wiele razy, aby były wiele oczekujących operacji. Można zgłosić wyjątek, gdy klasa jawnie nie obsługiwać takiej sytuacji, ale przyjęto założenie, że deweloperzy mogą obsługiwać te wielu nie do odróżnienia wywołania zwrotne  
  
### <a name="accessing-results"></a>Uzyskiwanie dostępu do wyników  
  
-   Wystąpił błąd podczas wykonywania operacji asynchronicznej, wyniki powinny być niedostępne. Upewnij się, że uzyskiwania dostępu do wszystkich właściwości w <xref:System.ComponentModel.AsyncCompletedEventArgs> podczas <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> nie `null` zgłasza wyjątek, odwołuje się <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>. <xref:System.ComponentModel.AsyncCompletedEventArgs> Klasa udostępnia <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> metody, w tym celu.  
  
-   Upewnij się, dowolne próba dostępu zgłasza wyniki <xref:System.InvalidOperationException> informujący, że operacja została anulowana. Użyj <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> metodę, aby przeprowadzić tę weryfikację.  
  
### <a name="progress-reporting"></a>Raportowanie postępu  
  
-   Obsługa raportowania postępu, jeśli jest to możliwe. Dzięki temu deweloperzy mogą zapewnić lepsze środowisko użytkownika aplikacji, podczas korzystania z klasy.  
  
-   W przypadku zaimplementowania **ProgressChanged** lub <em>MethodName</em>**ProgressChanged** zdarzeń, upewnij się, że nie istnieją żadne takie zdarzenia wywoływane dla określonej operacji asynchronicznej Po zakończeniu tej operacji <em>MethodName</em>**Ukończono** spowodował zdarzenie.  
  
-   Jeśli standardowe <xref:System.ComponentModel.ProgressChangedEventArgs> jest wypełniona, upewnij się, że <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> zawsze mogą być interpretowane jako wartość procentowa. Wartość procentowa musi być dokładne, ale powinien on reprezentować wartość procentową. Jeśli postęp raportowania metryki musi znajdować się coś innego niż wartość procentową, należy wyprowadzić klasę z <xref:System.ComponentModel.ProgressChangedEventArgs> klasy i pozostawić <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> w lokalizacji 0. Należy unikać używania raportowania metryk inne niż wartości procentowej.  
  
-   Upewnij się, że `ProgressChanged` zdarzenie jest zgłaszane w odpowiednich wątku i w odpowiednim czasie w cyklu życia aplikacji. Aby uzyskać więcej informacji zobacz sekcję wątki i kontekstów.  
  
### <a name="isbusy-implementation"></a>Implementacja IsBusy  
  
-   Nie ujawniaj `IsBusy` właściwość klasy obsługuje wiele równoczesnych wywołań. Na przykład serwery proxy usługi sieci Web XML nie ujawniaj `IsBusy` właściwość ponieważ obsługują wiele współbieżnych wywołań metod asynchronicznych.  
  
-   `IsBusy` Ma zwracać właściwość `true` po <em>MethodName</em>**Async** metoda została wywołana i przed <em>MethodName</em>  **Ukończono** spowodował zdarzenie. W przeciwnym razie powinien zwrócić `false`. <xref:System.ComponentModel.BackgroundWorker> i <xref:System.Net.WebClient> składniki są przykłady klas, które udostępniają `IsBusy` właściwości.  
  
### <a name="cancellation"></a>Anulowanie  
  
-   Zapewnić obsługę anulowania, jeśli jest to możliwe. Dzięki temu deweloperzy mogą zapewnić lepsze środowisko użytkownika aplikacji, podczas korzystania z klasy.  
  
-   W przypadku anulowania, ustaw <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> znacznik w <xref:System.ComponentModel.AsyncCompletedEventArgs> obiektu.  
  
-   Upewnij się, dowolne próba dostępu zgłasza wyniki <xref:System.InvalidOperationException> informujący, że operacja została anulowana. Użyj <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> metodę, aby przeprowadzić tę weryfikację.  
  
-   Należy upewnić się, że wywołania metody anulowania zawsze zwracają pomyślnie i nigdy nie zgłaszała wyjątku. Ogólnie rzecz biorąc klient nie jest powiadamiany o operacji jest naprawdę można anulować w dowolnym momencie i nie jest powiadamiany o dotyczące tego, czy wcześniej wydanych anulowania zakończyła się pomyślnie. Jednak aplikacja zawsze otrzymają powiadomienie po pomyślnym anulowania, ponieważ aplikacja bierze udział w stan ukończenia.  
  
-   Wywoływanie <em>MethodName</em>**Ukończono** zdarzenie, gdy operacja została anulowana.  
  
### <a name="errors-and-exceptions"></a>Błędy i wyjątki  
  
-   Przechwytywać wszystkie wyjątki, które występują w operacji asynchronicznej, a następnie ustaw wartość elementu <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości tego wyjątku.  
  
### <a name="threading-and-contexts"></a>Wątki i konteksty  
 Do poprawnego działania klasy jest krytyczny, że procedury obsługi zdarzeń klienta są wywoływane w wątku lub kontekstu dla modelu danej aplikacji, w tym [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] i aplikacjach Windows Forms. Aby zapewnić poprawne działanie asynchroniczne klasy pod dowolnego modelu aplikacji znajdują się dwie klasy pomocnika ważne: <xref:System.ComponentModel.AsyncOperation> i <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager> udostępnia pojedynczą metodę, <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, co powoduje zwrócenie <xref:System.ComponentModel.AsyncOperation>. Twoje <em>MethodName</em>**Async** wywołania metody <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> i klasa używa zwracanego <xref:System.ComponentModel.AsyncOperation> śledzić okres istnienia zadania asynchronicznego.  
  
 Aby raport postęp, wyniki przyrostowych i uzupełniania do klienta, należy wywołać <xref:System.ComponentModel.AsyncOperation.Post%2A> i <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> metod <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation> jest odpowiedzialny za kierowanie wywołań do klienta programu obsługi zdarzeń do wątku lub kontekstu.  
  
> [!NOTE]
>  Te reguły mogą omijać, jeśli chcesz jawnie korzystać z zobowiązania zasady modelu aplikacji, ale nadal korzystać z zalet używania wzorca asynchronicznego opartego na zdarzeniach. Można na przykład, że Threading klasy działających w formularzach Windows Forms będzie bezpłatne. Możesz utworzyć bezpłatne klasy wątków, tak długo, jak deweloperzy poznać dorozumianych ograniczenia. Aplikacje konsoli nie są synchronizowane wykonywania <xref:System.ComponentModel.AsyncOperation.Post%2A> wywołania. Może to spowodować `ProgressChanged` zdarzenia wywoływane, poza kolejnością. Jeśli chcesz mieć serializacji wykonywania <xref:System.ComponentModel.AsyncOperation.Post%2A> wywołań, wdrożyć i zainstalować <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> klasy.  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:System.ComponentModel.AsyncOperation> i <xref:System.ComponentModel.AsyncOperationManager> Aby włączyć operacji asynchronicznych, zobacz [porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
  
-   W idealnym przypadku każdego wywołania metody powinny być niezależne od innych użytkowników. Należy unikać sprzężenia wywołania z udostępnionymi zasobami. Jeśli zasoby mają być współużytkowane przez wywołania, konieczne będzie mechanizm synchronizacji odpowiednich w danej implementacji.  
  
-   Zaleca się projekty, które wymagają klienta do zaimplementowania synchronizacji. Na przykład można mieć metody asynchronicznej, które odbiera globalnego obiektu statycznego jako parametr; wiele współbieżnych wywołań taka metoda może spowodować uszkodzenie danych lub zakleszczenie.  
  
-   W przypadku zastosowania metody z wielokrotnego wywołania przeciążenia (`userState` w podpisie), klasy będą musieli zarządzać kolekcją stanów użytkowników lub identyfikatory zadań podrzędnych i odpowiadające im oczekujących operacji. Ta kolekcja powinny być chronione przy użyciu `lock` regionów, ponieważ wywołań różnych dodawać i usuwać `userState` obiektów w kolekcji.  
  
-   Należy rozważyć ponowne użycie `CompletedEventArgs` klasy, gdzie to możliwe i odpowiednie. W tym przypadku nazewnictwo nie jest spójna z nazwą metody, ponieważ danego delegata i <xref:System.EventArgs> typu nie są związane z jednej metody. Jednak wymuszanie deweloperom rzutować wartości pobierana z właściwości na <xref:System.EventArgs> nigdy nie jest dopuszczalna.  
  
-   W przypadku tworzenia klasę, która pochodzi od klasy <xref:System.ComponentModel.Component>nie Implementowanie i instalowanie własnych <xref:System.Threading.SynchronizationContext> klasy. Modele aplikacji, a nie składników, formant <xref:System.Threading.SynchronizationContext> używany.  
  
-   Kiedy używać wielowątkowości jakiegokolwiek rodzaju, możesz potencjalnie się narazić na bardzo poważne i złożone usterek. Przed zaimplementowaniem dowolne rozwiązanie używa wielowątkowości, wyświetlanego [zarządzana wątkowość najlepsze](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.AsyncOperation>  
- <xref:System.ComponentModel.AsyncOperationManager>  
- <xref:System.ComponentModel.AsyncCompletedEventArgs>  
- <xref:System.ComponentModel.ProgressChangedEventArgs>  
- <xref:System.ComponentModel.BackgroundWorker>  
- [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
- [Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
- [Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
- [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
