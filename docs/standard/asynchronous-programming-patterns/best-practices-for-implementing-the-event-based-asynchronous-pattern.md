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
ms.openlocfilehash: eaf410fa198fdb38a39a0474e9e147542919df8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach
Asynchroniczny wzorzec oparty na zdarzeniach udostępnia efektywny sposób ujawniać asynchroniczne zachowanie w klasach ze zdarzeniem znanych i delegowanie semantyki. Do implementacji klienta wzorca asynchronicznego opartego na zdarzeniach, należy wykonać niektóre określone wymagania funkcjonalne. W poniższych sekcjach opisano wymagania i wskazówki, które należy rozważyć podczas implementowania klasę, która wykonuje asynchroniczny wzorzec oparty na zdarzeniach.  
  
 Aby uzyskać ogólne informacje, zobacz [implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Wymagane gwarancje behawioralnej  
 Jeśli implementacji klienta wzorca asynchronicznego opartego na zdarzeniach, należy podać numer gwarancji, aby klasy będzie działać prawidłowo, a klienci klasy może polegać na takie zachowanie.  
  
### <a name="completion"></a>Zakończenie  
 Zawsze wywołania *MethodName *** Ukończono** Obsługa zdarzeń po pomyślnym ukończeniu, błąd lub anulowania. Aplikacji nigdy nie powinna wystąpić sytuacja, w którym pozostają w stanie bezczynności i uzupełniania nigdy nie występuje. Jedynym wyjątkiem od tej reguły jest, jeśli operacja asynchroniczna, sama go tak zaprojektowane, że nigdy się nie kończy.  
  
### <a name="completed-event-and-eventargs"></a>Zakończonego zdarzenia i EventArgs  
 Dla każdej szczegółowej *MethodName *** Async** metody, zastosuj następujące wymagania:  
  
-   Zdefiniuj *MethodName *** Ukończono** zdarzenia w tej samej klasy jako metodę.  
  
-   Zdefiniuj <xref:System.EventArgs> klasy i towarzyszące delegowanie dla *MethodName *** Ukończono** zdarzeń, która jest pochodną <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy. Domyślna nazwa klasy powinna mieć postać * MethodName ***CompletedEventArgs**.  
  
-   Upewnij się, że <xref:System.EventArgs> klasy jest specyficzna dla wartości zwracanych metody *MethodName* metody. Jeśli używasz <xref:System.EventArgs> klasy, należy nigdy nie wymagać deweloperom Rzutuj wynik.  
  
     Poniższy przykład kodu pokazuje odpowiednio dobrej i zły wdrożenia to wymaganie projektowe.  
  
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
  
-   Nie definiują <xref:System.EventArgs> klasy dla zwracania metody, które zwracają `void`. Użyj wystąpienia <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy.  
  
-   Upewnij się, że należy zawsze podnieść *MethodName *** Ukończono** zdarzeń. To zdarzenie zostanie zgłoszony na pomyślne zakończenie, błąd lub anulowania. Aplikacji nigdy nie powinna wystąpić sytuacja, w którym pozostają w stanie bezczynności i uzupełniania nigdy nie występuje.  
  
-   Upewnij się, że zostaną wychwycone wszelkie wyjątki, które występują w operacji asynchronicznej i przypisz zgłoszony wyjątek do <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwości.  
  
-   Wystąpił błąd podczas wykonywania zadania, wyniki powinny być niedostępne. Gdy <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwość nie jest `null`, upewnij się, że podczas uzyskiwania dostępu do żadnej właściwości w <xref:System.EventArgs> struktury zgłasza wyjątek. Użyj <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> metodę w celu weryfikacji.  
  
-   Model limit czasu jako błąd. W przypadku przekroczenia limitu czasu podnieść *MethodName *** Ukończono** zdarzenie i przypisz <xref:System.TimeoutException> do <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwości.  
  
-   Jeśli klasa obsługuje wiele równoczesnych wywołań, upewnij się, że *MethodName *** Ukończono** zdarzenie zawiera odpowiednie `userSuppliedState` obiektu.  
  
-   Upewnij się, że *MethodName *** Ukończono** zdarzenie jest wywoływane w wątku odpowiednie i w odpowiednim czasie w cyklu życia aplikacji. Aby uzyskać więcej informacji zobacz sekcję wątki i konteksty.  
  
### <a name="simultaneously-executing-operations"></a>Jednocześnie wykonywania operacji  
  
-   Jeśli klasa obsługuje wiele równoczesnych wywołań, Włącz projektanta do śledzenia każdego wywołania oddzielnie, definiując *MethodName *** Async** przeciążenia, które przyjmuje parametr zwracającej obiekt stanu lub identyfikator zadania, nazywany `userSuppliedState`. Ten parametr powinien zawsze być ostatnim parametrem *MethodName *** Async** podpis metody.  
  
-   Jeśli klasa definiuje *MethodName *** Async** przeciążenia, które przyjmuje parametr zwracającej obiekt stanu lub identyfikator zadania, pamiętaj śledzić okres istnienia operację, podając identyfikator tego zadania i należy podać go do programu obsługi zakończenia . Brak pomagające klasy pomocy. Aby uzyskać więcej informacji dotyczących zarządzania współbieżności, zobacz [wskazówki: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
-   Jeśli klasa definiuje *MethodName *** Async** metody bez parametru stanu który nie obsługuje wiele równoczesnych wywołań, upewnij się, że próby wywołania *MethodName *** Async** przed wcześniej *MethodName *** Async** wywołanie zostało ukończone zgłasza <xref:System.InvalidOperationException>.  
  
-   Ogólnie rzecz biorąc, nie zgłaszał wyjątku, jeśli *MethodName *** Async** metody bez `userSuppliedState` parametru jest wywołana kilka razy, tak aby były wiele oczekujących operacji. Należy zgłosić wyjątek, klasy jawnie nie może obsłużyć tej sytuacji, kiedy założono, że deweloperzy mogą obsługiwać te wielu wywołań zwrotnych nierozróżnialne  
  
### <a name="accessing-results"></a>Uzyskiwanie dostępu do wyników  
  
-   Wystąpił błąd podczas wykonywania operacji asynchronicznej, wyniki powinny być niedostępne. Upewnij się, że podczas uzyskiwania dostępu do żadnej właściwości w <xref:System.ComponentModel.AsyncCompletedEventArgs> podczas <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> nie jest `null` zgłasza wyjątek odwołuje się <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>. <xref:System.ComponentModel.AsyncCompletedEventArgs> Klasa udostępnia <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> metody w tym celu.  
  
-   Upewnij się, że wszelkie próbują uzyskać dostęp generuje wynik <xref:System.InvalidOperationException> informujący, że operacja została anulowana. Użyj <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> metodę w celu weryfikacji.  
  
### <a name="progress-reporting"></a>Raportowanie postępu  
  
-   Obsługuje raportowania postępu, jeśli to możliwe. Dzięki temu deweloperzy mogą podać lepsze środowisko aplikacji w przypadku korzystania z klasy.  
  
-   W przypadku zastosowania **ProgressChanged** lub *MethodName *** ProgressChanged** zdarzeń, upewnij się, że nie istnieją żadne zgłoszone dla określonej operacji asynchronicznych po tej operacji zdarzenia*MethodName *** Ukończono** zdarzeń został zgłoszony.  
  
-   Jeśli standardowa <xref:System.ComponentModel.ProgressChangedEventArgs> jest wypełniony, upewnij się, że <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> zawsze może zostać zinterpretowany jako procent. Wartość procentowa musi być dokładne, ale powinien on reprezentować procent. Jeśli postęp raportowania Metryka musi być inną niż procent, klasa wyprowadzona z <xref:System.ComponentModel.ProgressChangedEventArgs> klasy i pozostawić <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> w lokalizacji 0. Unikaj używania raportowania Metryka niż procent.  
  
-   Upewnij się, że `ProgressChanged` zdarzenie jest wywoływane w wątku odpowiednie i w odpowiednim czasie w cyklu życia aplikacji. Aby uzyskać więcej informacji zobacz sekcję wątki i konteksty.  
  
### <a name="isbusy-implementation"></a>Implementacja IsBusy  
  
-   Nie ujawniaj `IsBusy` właściwości, jeśli klasa obsługuje wiele równoczesnych wywołań. Na przykład serwery proxy usługi XML sieci Web nie ujawniaj `IsBusy` właściwości ponieważ obsługują wiele współbieżnych wywołań metod asynchronicznych.  
  
-   `IsBusy` Ma zwracać właściwość `true` po *MethodName *** Async** zostanie wywołana metoda i przed *MethodName *** Ukończono** zdarzeń został zgłoszony. W przeciwnym razie powinien zwrócić `false`. <xref:System.ComponentModel.BackgroundWorker> i <xref:System.Net.WebClient> składniki są przykłady klas, które udostępniają `IsBusy` właściwości.  
  
### <a name="cancellation"></a>Anulowanie  
  
-   Obsługuje anulowania, jeśli to możliwe. Dzięki temu deweloperzy mogą podać lepsze środowisko aplikacji w przypadku korzystania z klasy.  
  
-   W przypadku anulowania, ustaw <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> oflagowane w <xref:System.ComponentModel.AsyncCompletedEventArgs> obiektu.  
  
-   Upewnij się, że wszelkie próbują uzyskać dostęp generuje wynik <xref:System.InvalidOperationException> informujący, że operacja została anulowana. Użyj <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> metodę w celu weryfikacji.  
  
-   Upewnij się, że wywołania metody anulowania zawsze zwracają pomyślnie i nigdy nie zgłaszał wyjątku. Ogólnie rzecz biorąc klient nie jest powiadamiany o operacji jest w pełni można anulować w dowolnym momencie i nie jest powiadamiany o określające, czy wcześniej wydanych anulowania zakończyła się pomyślnie. Jednak aplikacja zawsze otrzymają powiadomienie podczas anulowania zakończyło się pomyślnie, ponieważ aplikacja uczestniczy w stan ukończenia.  
  
-   Zgłoś *MethodName *** Ukończono** zdarzenie, gdy operacja została anulowana.  
  
### <a name="errors-and-exceptions"></a>Błędy i wyjątki  
  
-   CATCH wszelkie wyjątki, które występują w ramach operacji asynchronicznej i ustaw wartość <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości tego wyjątku.  
  
### <a name="threading-and-contexts"></a>Wątki i konteksty  
 Do poprawnego działania klasy jest krytyczny, że obsługi zdarzeń klienta są wywoływane na właściwy wątku lub kontekst dla modelu danej aplikacji, w tym [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] i aplikacji formularzy systemu Windows. Aby zapewnić poprawne działanie asynchroniczne klasy w dowolnej aplikacji modelu znajdują się dwie klasy pomocy ważne: <xref:System.ComponentModel.AsyncOperation> i <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager> zawiera jedną metodę <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, która zwraca wartość <xref:System.ComponentModel.AsyncOperation>. Twoje *MethodName *** Async** wywołania metody <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> i klasy używa zwróconego <xref:System.ComponentModel.AsyncOperation> śledzić okres istnienia zadanie asynchroniczne.  
  
 Aby zgłosić postęp, wyniki przyrostowych i uzupełniania do klienta, należy wywołać <xref:System.ComponentModel.AsyncOperation.Post%2A> i <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> metody <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation> jest odpowiedzialny za organizowanie wywołań obsługi zdarzeń klienckich do właściwego thread lub context.  
  
> [!NOTE]
>  Te reguły można ominąć, jeśli chcesz jawnie go przed zasady modelu aplikacji, ale nadal korzystać z innych zalety korzystania z wzorca asynchronicznego opartego na zdarzeniach. Można na przykład hiperwątkowe klasy działających w formularzach systemu Windows jako wolne. Tak długo, jak deweloperzy poznać domniemanych ograniczenia, można utworzyć klasę wolnych wątków. Aplikacje konsoli nie Synchronizuj wykonywanie <xref:System.ComponentModel.AsyncOperation.Post%2A> wywołania. Może to spowodować `ProgressChanged` zdarzenia, które mają zostać wywołane poza kolejnością. Jeśli chcesz mieć serializacji wykonywanie <xref:System.ComponentModel.AsyncOperation.Post%2A> wywołań, wdrożenia i zainstalować <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> klasy.  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:System.ComponentModel.AsyncOperation> i <xref:System.ComponentModel.AsyncOperationManager> umożliwia asynchroniczne operacje, zobacz [wskazówki: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
  
-   W idealnym przypadku każdego wywołania metody powinny być niezależne od innych użytkowników. Należy unikać sprzężenia wywołań z udostępnionymi zasobami. Jeśli zasoby mają być współużytkowane przez wywołań, konieczne będzie mechanizm właściwego synchronizacji w implementacji.  
  
-   Projekty, które wymagają klienta do zaimplementowania synchronizacji nie są zalecane. Na przykład można mieć metody asynchronicznej otrzymuje globalny obiekt statycznych jako parametr; wiele współbieżnych wywołań taka metoda może spowodować uszkodzenie danych lub zakleszczenia.  
  
-   W przypadku zastosowania metody z wieloma wywołania przeciążenia (`userState` w podpisie), klasy będą musieli zarządzać kolekcję stanów użytkownika lub identyfikatorów zadań i odpowiednie oczekujących operacji. Ta kolekcja powinny być chronione przy użyciu `lock` regionach, ponieważ różnych wywołań Dodawanie i usuwanie `userState` obiektów w kolekcji.  
  
-   Należy rozważyć ponowne użycie `CompletedEventArgs` klas, gdzie to możliwe i właściwe. W takim przypadku nazewnictwo nie jest spójna z nazwą metody, ponieważ danego obiektu delegowanego i <xref:System.EventArgs> typu nie są związane z pojedynczej metody. Jednak wymuszania deweloperom rzutowania pobrać z właściwości na wartość <xref:System.EventArgs> nigdy nie jest akceptowany.  
  
-   W przypadku tworzenia klasy pochodnej z <xref:System.ComponentModel.Component>nie implementuje i zainstalować własne <xref:System.Threading.SynchronizationContext> klasy. Modele aplikacji, a nie składników, sterowanie <xref:System.Threading.SynchronizationContext> używany.  
  
-   Jeśli używasz wielowątkowość jakiegokolwiek rodzaju potencjalnie naraża samodzielnie do usterki bardzo poważne i złożone. Przed wdrożeniem dowolnego rozwiązania, które używa wielowątkowości, zobacz [zarządzanych wątków najlepsze rozwiązania w zakresie](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 [Przewodnik: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
