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
ms.openlocfilehash: 439b862612d7997c9277ffb2cf4f15b14bd0b106
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156052"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach
Wzorzec asynchroniczny oparty na zdarzeniach zapewnia skuteczny sposób uwidaczniania zachowania asynchronicznego w klasach, z opisem semantyki zdarzeń i delegować. Aby zaimplementować wzorzec asynchroniczny oparty na zdarzeniach, należy przestrzegać pewnych określonych wymagań behawioralnych. W poniższych sekcjach opisano wymagania i wskazówki, które należy wziąć pod uwagę podczas implementowania klasy, która następuje po wzorca asynchronicznego opartego na zdarzeniach.  
  
 Aby uzyskać omówienie, zobacz [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Wymagane gwarancje behawioralne  
 Jeśli zaimplementujesz wzorca asynchronicznego opartego na zdarzeniach, należy podać szereg gwarancji, aby upewnić się, że klasa będzie zachowywać się poprawnie, a klienci klasy mogą polegać na takim zachowaniu.  
  
### <a name="completion"></a>Ukończenie  
 Zawsze wywoływać <em>MethodName</em>**Completed** obsługi zdarzeń, gdy masz pomyślne zakończenie, błąd lub anulowanie. Aplikacje nigdy nie powinny wystąpić w sytuacji, w której pozostają bezczynne i zakończenie nigdy nie występuje. Jednym z wyjątków od tej reguły jest, jeśli sama operacja asynchroniczna jest zaprojektowany tak, że nigdy nie kończy.  
  
### <a name="completed-event-and-eventargs"></a>Ukończone wydarzenie i eventargs  
 Dla każdej oddzielnej metody**Asynia** <em>Nazwa metody</em>należy zastosować następujące wymagania projektowe:  
  
- Zdefiniuj <em>MethodName</em>**Complete** zdarzenie w tej samej klasie co metoda.  
  
- Zdefiniuj <xref:System.EventArgs> klasę i towarzyszącego delegata dla <em>MethodName</em>**Completed** zdarzenia, który pochodzi od <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy. Domyślną nazwą klasy powinna być forma <em>MethodName</em>**CompletedEventArgs**.  
  
- Upewnij się, że <xref:System.EventArgs> klasa jest specyficzna dla zwracanych wartości <em>MethodName</em> metody. Korzystając z <xref:System.EventArgs> klasy, nigdy nie należy wymagać od deweloperów rzutowanie wyniku.  
  
     Poniższy przykład kodu pokazuje dobre i złe wykonanie tego wymagania projektowego odpowiednio.  
  
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
  
- Nie należy <xref:System.EventArgs> definiować klasy dla `void`zwracanych metod, które zwracają . Zamiast tego należy użyć <xref:System.ComponentModel.AsyncCompletedEventArgs> wystąpienia klasy.  
  
- Upewnij się, że zawsze podnieść <em>MethodName</em>**Complete event.** To zdarzenie powinno zostać podniesione po pomyślnym zakończeniu, na błąd lub w przypadku anulowania. Aplikacje nigdy nie powinny wystąpić w sytuacji, w której pozostają bezczynne i zakończenie nigdy nie występuje.  
  
- Upewnij się, że można przechwycić wszelkie wyjątki, które występują w <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> operacji asynchronicznej i przypisać przechwyconego wyjątku do właściwości.  
  
- Jeśli wystąpił błąd podczas wykonywania zadania, wyniki nie powinny być dostępne. Gdy <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwość nie `null`jest , upewnij się, <xref:System.EventArgs> że dostęp do dowolnej właściwości w strukturze wywołuje wyjątek. Użyj <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> tej metody, aby przeprowadzić tę weryfikację.  
  
- Modeluj uchyłka czasu jako błąd. Gdy wystąpi uchyłaczasty czas, należy podnieść <xref:System.TimeoutException> <em>MethodName</em>**Completed** zdarzenia i przypisać do <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwości.  
  
- Jeśli klasa obsługuje wiele równoczesnych wywołań, upewnij się, że `userSuppliedState` <em>MethodName</em>**Completed** zdarzenie zawiera odpowiedni obiekt.  
  
- Upewnij się, że <em>MethodName</em>**Complete zdarzenie** jest wywoływane w odpowiednim wątku i w odpowiednim czasie w cyklu życia aplikacji. Aby uzyskać więcej informacji, zobacz wątków i kontekstów sekcji.  
  
### <a name="simultaneously-executing-operations"></a>Jednoczesne wykonywanie operacji  
  
- Jeśli klasa obsługuje wiele równoczesnych wywołań, włącz deweloperowi śledzenie każdego wywołania oddzielnie, definiując przeciążenie**Asynchroniczne** Nazwa `userSuppliedState` <em>metody,</em>które przyjmuje parametr stanu wartości obiektu lub identyfikator zadania o nazwie . Ten parametr powinien być zawsze ostatnim parametrem w podpisie metody <em>MethodName</em>**Async.**  
  
- Jeśli klasa definiuje przeciążenie**Asynchronia** <em>MethodName,</em>które przyjmuje parametr stanu wartości obiektu lub identyfikator zadania, należy śledzić okres istnienia operacji z tego identyfikatora zadania i upewnij się, aby zapewnić go z powrotem do obsługi zakończenia. Istnieją zajęcia pomocnicze dostępne do pomocy. Aby uzyskać więcej informacji na temat zarządzania współbieżnością, zobacz [Jak: Implementowanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
- Jeśli klasa definiuje <em>MethodName</em>**Async** metody bez parametru stanu i nie obsługuje wielu wywołań równoczesnych, upewnij się, że każda próba wywołania <em>MethodName</em> <xref:System.InvalidOperationException>**Async** przed ukończenia poprzedniego wywołania**Async** <em>MethodName</em>wywołuje .  
  
- Ogólnie rzecz biorąc nie zgłaszać wyjątek, jeśli <em>MethodName</em>**Async** metoda bez parametru `userSuppliedState` jest wywoływana wiele razy, tak aby istnieje wiele operacji zaległych. Można zgłosić wyjątek, gdy klasa jawnie nie może obsłużyć tej sytuacji, ale załóżmy, że deweloperzy mogą obsługiwać te wiele wywołań wywołań wywołań niedo odróżnienia  
  
### <a name="accessing-results"></a>Uzyskiwanie dostępu do wyników  
  
- Jeśli wystąpił błąd podczas wykonywania operacji asynchronicznej, wyniki nie powinny być dostępne. Upewnij się, że dostęp <xref:System.ComponentModel.AsyncCompletedEventArgs> <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> do `null` dowolnej właściwości w <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>when nie jest zgłasza wyjątek odwołuje się . Klasa <xref:System.ComponentModel.AsyncCompletedEventArgs> zapewnia <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> metodę w tym celu.  
  
- Upewnij się, że każda próba <xref:System.InvalidOperationException> uzyskania dostępu do wyniku wywołuje stwierdzające, że operacja została anulowana. Użyj <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> tej metody, aby przeprowadzić tę weryfikację.  
  
### <a name="progress-reporting"></a>Raportowanie postępów  
  
- Jeśli to możliwe, obsługa raportowania postępów. Dzięki temu deweloperzy zapewniają lepsze środowisko użytkownika aplikacji, gdy używają klasy.  
  
- Jeśli zaimplementujesz **ProgressChanged** lub <em>MethodName</em>**ProgressChanged** zdarzenia, upewnij się, że nie ma takich zdarzeń zgłoszonych dla określonej operacji asynchronicznej po tej operacji <em>MethodName</em>**Completed** zdarzenie zostało podniesione.  
  
- Jeśli standard <xref:System.ComponentModel.ProgressChangedEventArgs> jest wypełniany, upewnij <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> się, że zawsze można interpretować jako procent. Procent nie musi być dokładny, ale powinien reprezentować procent. Jeśli metryka raportowania postępu musi być czymś innym niż <xref:System.ComponentModel.ProgressChangedEventArgs> procent, <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> wyprowauj klasę z klasy i pozostaw na 0. Unikaj używania metryki raportowania innej niż procent.  
  
- Upewnij się, że `ProgressChanged` zdarzenie jest wywoływane w odpowiednim wątku i w odpowiednim czasie w cyklu życia aplikacji. Aby uzyskać więcej informacji, zobacz wątków i kontekstów sekcji.  
  
### <a name="isbusy-implementation"></a>Implementacja Isbusy  
  
- Nie uwidaczniać `IsBusy` właściwość, jeśli klasa obsługuje wiele równoczesnych wywołań. Na przykład serwery proxy usługi sieci Web `IsBusy` XML nie ujawniają właściwości, ponieważ obsługują wiele równoczesnych wywołań metod asynchronicznych.  
  
- Właściwość `IsBusy` powinna `true` zwrócić po <em>MethodName</em>**Async** metoda została wywołana i przed <em>MethodName</em>**Completed** zdarzenie zostało podniesione. W przeciwnym `false`razie powinien powrócić . I <xref:System.ComponentModel.BackgroundWorker> <xref:System.Net.WebClient> składniki są przykładami klas, `IsBusy` które uwidaczniają właściwość.  
  
### <a name="cancellation"></a>Anulowanie  
  
- Jeśli to możliwe, obsługa techniczna została anulowana. Dzięki temu deweloperzy zapewniają lepsze środowisko użytkownika aplikacji, gdy używają klasy.  
  
- W przypadku anulowania ustaw <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> flagę w <xref:System.ComponentModel.AsyncCompletedEventArgs> obiekcie.  
  
- Upewnij się, że każda próba <xref:System.InvalidOperationException> uzyskania dostępu do wyniku wywołuje stwierdzające, że operacja została anulowana. Użyj <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> tej metody, aby przeprowadzić tę weryfikację.  
  
- Upewnij się, że wywołania metody anulowania zawsze zwracają pomyślnie i nigdy nie zgłaszać wyjątek. Ogólnie rzecz biorąc klient nie jest powiadamiany o tym, czy operacja jest naprawdę anulowana w danym momencie i nie jest powiadamiany o tym, czy wcześniej wydane anulowanie powiodło się. Jednak aplikacja zawsze będzie otrzymywać powiadomienia, gdy anulowanie powiodło się, ponieważ aplikacja bierze udział w stanie ukończenia.  
  
- Podnieś <em>MethodName</em>**Complete** zdarzenie po anulowaniu operacji.  
  
### <a name="errors-and-exceptions"></a>Błędy i wyjątki  
  
- Przechwyć wszelkie wyjątki, które występują w operacji <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> asynchronicznej i ustawić wartość właściwości do tego wyjątku.  
  
### <a name="threading-and-contexts"></a>Wątkowanie i konteksty  
 Dla prawidłowego działania klasy, ważne jest, że programy obsługi zdarzeń klienta są wywoływane w odpowiednim wątku lub kontekstu dla danego modelu aplikacji, w tym ASP.NET i windows forms aplikacji. Dwie ważne klasy pomocnika są dostarczane w celu zapewnienia, że klasa asynchroniczna zachowuje się poprawnie w dowolnym modelu aplikacji: <xref:System.ComponentModel.AsyncOperation> i <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager>zapewnia jedną <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>metodę, która <xref:System.ComponentModel.AsyncOperation>zwraca . <em>Metoda MethodName</em>**Async** wywołuje <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> i klasy <xref:System.ComponentModel.AsyncOperation> używa zwracane do śledzenia okresu istnienia zadania asynchronicznego.  
  
 Aby zgłosić postęp, wyniki przyrostowe i zakończenie <xref:System.ComponentModel.AsyncOperation.Post%2A> do <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> klienta, <xref:System.ComponentModel.AsyncOperation>wywołać i metody na . <xref:System.ComponentModel.AsyncOperation>jest odpowiedzialny za organizowanie wywołań obsługi zdarzeń klienta do właściwego wątku lub kontekstu.  
  
> [!NOTE]
> Można obejść te reguły, jeśli jawnie chcesz przejść do zasad modelu aplikacji, ale nadal korzystać z innych zalet przy użyciu wzorca asynchronicznego opartego na zdarzeniach. Na przykład może chcesz klasy działających w formularzach systemu Windows być wolne wątków. Można utworzyć bezpłatną klasę wątkową, tak długo, jak deweloperzy rozumieją dorozumiane ograniczenia. Aplikacje konsoli nie synchronizują wykonywania wywołań. <xref:System.ComponentModel.AsyncOperation.Post%2A> Może to `ProgressChanged` spowodować zdarzenia, które mają być wywoływane poza kolejnością. Jeśli chcesz mieć serializowane <xref:System.ComponentModel.AsyncOperation.Post%2A> wykonywanie wywołań, <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> zaimplementuj i zainstaluj klasę.  
  
 Aby uzyskać więcej <xref:System.ComponentModel.AsyncOperation> <xref:System.ComponentModel.AsyncOperationManager> informacji na temat używania i włączania operacji asynchronicznych, zobacz [Jak: Implementowanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Wytyczne  
  
- W idealnym przypadku każde wywołanie metody powinno być niezależne od innych. Należy unikać wywołań sprzęgania z zasobami udostępnionymi. Jeśli zasoby mają być współużytkowane między wywołaniami, należy zapewnić mechanizm synchronizacji właściwego w implementacji.  
  
- Projekty, które wymagają od klienta do zaimplementowania synchronizacji są odradzane. Na przykład można mieć metodę asynchroniczną, która odbiera globalny obiekt statyczny jako parametr; wiele równoczesnych wywołań takiej metody może spowodować uszkodzenie danych lub zakleszczenia.  
  
- Jeśli zaimplementujesz metodę z przeciążeniem`userState` wielokrotnego wywołania (w podpisie), klasa będzie musiała zarządzać kolekcją stanów użytkowników lub identyfikatorów zadań i odpowiadających im operacji oczekujących. Ta kolekcja powinna `lock` być chroniona za pomocą regionów, `userState` ponieważ różne wywołania dodawać i usuwać obiekty w kolekcji.  
  
- Należy rozważyć ponowne użycie `CompletedEventArgs` klas, jeśli jest to możliwe i właściwe. W takim przypadku nazewnictwo nie jest zgodne z nazwą metody, <xref:System.EventArgs> ponieważ dany delegat i typ nie są powiązane z jedną metodą. Jednak zmuszając deweloperów do rzutować wartość pobraną z właściwości na nigdy nie <xref:System.EventArgs> jest dopuszczalne.  
  
- Jeśli autoryzujesz klasę, która <xref:System.ComponentModel.Component>wywodzi <xref:System.Threading.SynchronizationContext> się z , nie implementuj i instaluj własną klasę. Modele aplikacji, a nie <xref:System.Threading.SynchronizationContext> składniki, sterują, który jest używany.  
  
- Korzystając z wielowątkowości wszelkiego rodzaju, potencjalnie narażasz się na bardzo poważne i złożone błędy. Przed wdrożeniem dowolnego rozwiązania, które używa wielowątkowości, zobacz [Zarządzane wątki najlepsze rozwiązania](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
