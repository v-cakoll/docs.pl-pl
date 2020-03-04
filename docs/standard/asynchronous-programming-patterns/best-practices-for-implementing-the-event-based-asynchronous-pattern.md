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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156052"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach
Wzorzec asynchroniczny oparty na zdarzeniach umożliwia efektywne udostępnianie zachowań asynchronicznych w klasach ze znaną semantyką zdarzeń i delegatów. Aby zaimplementować wzorzec asynchroniczny oparty na zdarzeniach, należy przestrzegać pewnych konkretnych wymagań zachowań. W poniższych sekcjach opisano wymagania i wskazówki, które należy wziąć pod uwagę podczas implementowania klasy, która następuje po asynchronicznym wzorcu opartym na zdarzeniach.  
  
 Aby zapoznać się z omówieniem, zobacz [implementowanie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Wymagane gwarancje zachowania  
 W przypadku zaimplementowania wzorca asynchronicznego opartego na zdarzeniach należy podać pewną liczbę gwarancji, aby upewnić się, że klasa będzie działać prawidłowo, a klienci klasy mogą polegać na takiej sytuacji.  
  
### <a name="completion"></a>Ukończenie  
 Zawsze Wywołaj procedurę obsługi zdarzeń**zakończonych** <em>MethodName</em>po pomyślnym ukończeniu, błędzie lub anulowaniu. Aplikacje nigdy nie powinny napotkać sytuacji, w której pozostają bezczynne, a ukończenie nie następuje. Jedynym wyjątkiem od tej reguły jest zaprojektowana operacja asynchroniczna, tak aby nigdy nie kończyła się.  
  
### <a name="completed-event-and-eventargs"></a>Zdarzenie ukończenia i EventArgs  
 Dla każdej oddzielnej metody**asynchronicznej** <em>MethodName</em>należy zastosować następujące wymagania dotyczące projektu:  
  
- Zdefiniuj zdarzenie**ukończenia** MethodName dla tej samej klasy co metoda.  
  
- Zdefiniuj klasę <xref:System.EventArgs> i towarzyszący delegat dla zdarzenia <em>MethodName</em>**ukończone** , które wynika z klasy <xref:System.ComponentModel.AsyncCompletedEventArgs>. Domyślna nazwa klasy powinna mieć postać <em>MethodName</em>**CompletedEventArgs**.  
  
- Upewnij się, że Klasa <xref:System.EventArgs> jest specyficzna dla wartości zwracanych metody <em>MethodName</em> . W przypadku korzystania z klasy <xref:System.EventArgs> nigdy nie należy wymagać, aby deweloperzy mogli rzutować wynik.  
  
     Poniższy przykład kodu pokazuje dobry i niewłaściwy implementację tego wymagania projektowego.  
  
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
  
- Nie należy definiować klasy <xref:System.EventArgs> dla zwracanych metod, które zwracają `void`. Zamiast tego należy użyć wystąpienia klasy <xref:System.ComponentModel.AsyncCompletedEventArgs>.  
  
- Upewnij się, że zawsze zostało zgłoszone zdarzenie**ukończenia** <em>MethodName</em>. To zdarzenie należy wymusić po pomyślnym zakończeniu, po błędzie lub po anulowaniu. Aplikacje nigdy nie powinny napotkać sytuacji, w której pozostają bezczynne, a ukończenie nie następuje.  
  
- Upewnij się, że przechwytujesz wszystkie wyjątki występujące w operacji asynchronicznej i przypisz przechwycony wyjątek do właściwości <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>.  
  
- Jeśli wystąpił błąd podczas kończenia zadania, wyniki nie powinny być dostępne. Gdy właściwość <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> nie jest `null`, upewnij się, że dostęp do dowolnej właściwości w strukturze <xref:System.EventArgs> zgłasza wyjątek. Użyj metody <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A>, aby przeprowadzić tę weryfikację.  
  
- Przekrocz limit czasu jako błąd. Po przekroczeniu limitu czasu wywołaj zdarzenie <em>MethodName</em>**ukończone** i przypisz <xref:System.TimeoutException> do właściwości <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>.  
  
- Jeśli klasa obsługuje wiele współbieżnych wywołań, upewnij się, że zdarzenie <em>MethodName</em>**ukończone** zawiera odpowiedni obiekt `userSuppliedState`.  
  
- Upewnij się, że zdarzenie**ukończenia** <em>MethodName</em>zostało zgłoszone na odpowiednim wątku i w odpowiednim czasie w cyklu życia aplikacji. Aby uzyskać więcej informacji, zobacz sekcję wątkowość i konteksty.  
  
### <a name="simultaneously-executing-operations"></a>Jednoczesne wykonywanie operacji  
  
- Jeśli klasa obsługuje wiele współbieżnych wywołań, należy umożliwić deweloperowi śledzenie każdego wywołania osobno przez zdefiniowanie przeciążenia**Async** <em>MethodName</em>, które przyjmuje parametr stanu o wartości obiektu lub identyfikator zadania o nazwie `userSuppliedState`. Ten parametr powinien zawsze być ostatnim parametrem w sygnaturze metody**asynchronicznej** <em>MethodName</em>.  
  
- Jeśli klasa definiuje Przeciążenie Async <em>MethodName</em> , które przyjmuje parametr stanu o wartościach obiektu lub identyfikator zadania, należy śledzić okres istnienia operacji przy użyciu tego identyfikatora zadania i upewnić się, że jest on ponownie używany do obsługi uzupełniania. Istnieją klasy pomocnika, które mogą być pomocne. Aby uzyskać więcej informacji na temat zarządzania współbieżnością, zobacz [How to: Implementuj składnik, który obsługuje wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
- Jeśli klasa definiuje metodę**asynchroniczną** <em>MethodName</em>bez parametru State i nie obsługuje wielu współbieżnych wywołań, należy upewnić się, że każda próba wywołania**asynchronicznej** <em>MethodName</em>przed zapełnieniem poprzedniego wywołania**asynchronicznego** <em>MethodName</em>wywoła <xref:System.InvalidOperationException>.  
  
- Ogólnie rzecz biorąc nie należy zgłaszać wyjątku, jeśli metoda**asynchroniczna** <em>MethodName</em>bez parametru `userSuppliedState` jest wywoływana wiele razy, tak że istnieje wiele zaległych operacji. Można zgłosić wyjątek, gdy Klasa jawnie nie może obsłużyć tej sytuacji, ale zakłada, że deweloperzy mogą obsługiwać te wielokrotne wywołania zwrotne  
  
### <a name="accessing-results"></a>Uzyskiwanie dostępu do wyników  
  
- Jeśli wystąpił błąd podczas wykonywania operacji asynchronicznej, wyniki nie powinny być dostępne. Upewnij się, że dostęp do dowolnej właściwości w <xref:System.ComponentModel.AsyncCompletedEventArgs>, gdy <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> nie jest `null` wywołuje wyjątek, do którego odwołuje się <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>. Klasa <xref:System.ComponentModel.AsyncCompletedEventArgs> udostępnia metodę <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> do tego celu.  
  
- Upewnij się, że każda próba uzyskania dostępu do wyniku spowoduje wystąpienie <xref:System.InvalidOperationException> informującego, że operacja została anulowana. Użyj metody <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType>, aby przeprowadzić tę weryfikację.  
  
### <a name="progress-reporting"></a>Raportowanie postępu  
  
- Raportowanie postępu obsługi, jeśli jest to możliwe. Dzięki temu deweloperzy mogą zapewnić lepsze środowisko użytkownika aplikacji, gdy używają klasy.  
  
- Jeśli zaimplementowano zdarzenie**ProgressChanged** **ProgressChanged** lub <em>MethodName</em>, należy się upewnić, że nie ma takich zdarzeń zgłoszonych dla określonej operacji asynchronicznej, gdy zostanie zgłoszone zdarzenie**ukończenia** <em>MethodName</em>przez tę operację.  
  
- Jeśli <xref:System.ComponentModel.ProgressChangedEventArgs> jest wypełniana, upewnij się, że <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> można zawsze interpretować jako wartość procentową. Wartość procentowa nie musi być dokładna, ale powinna reprezentować wartość procentową. Jeśli Metryka raportowania postępu musi być inna niż wartość procentowa, należy utworzyć klasę z klasy <xref:System.ComponentModel.ProgressChangedEventArgs> i pozostawić <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> o wartości 0. Unikaj używania metryki raportowania innej niż wartość procentowa.  
  
- Upewnij się, że zdarzenie `ProgressChanged` jest zgłaszane na odpowiednim wątku i w odpowiednim czasie w cyklu życia aplikacji. Aby uzyskać więcej informacji, zobacz sekcję wątkowość i konteksty.  
  
### <a name="isbusy-implementation"></a>Implementacja IsBusy  
  
- Nie ujawniaj właściwości `IsBusy`, jeśli klasa obsługuje wiele współbieżnych wywołań. Na przykład serwery proxy usługi sieci Web XML nie uwidaczniają właściwości `IsBusy`, ponieważ obsługują wiele współbieżnych wywołań metod asynchronicznych.  
  
- Właściwość `IsBusy` powinna zwracać `true` po wywołaniu metody**asynchronicznej** MethodName i przed podniesieniem zdarzenia <em>MethodName</em>**ukończone** . W przeciwnym razie powinna zwrócić `false`. Składniki <xref:System.ComponentModel.BackgroundWorker> i <xref:System.Net.WebClient> są przykładami klas, które uwidaczniają Właściwość `IsBusy`.  
  
### <a name="cancellation"></a>Anulowanie  
  
- Obsługa anulowania, jeśli to możliwe. Dzięki temu deweloperzy mogą zapewnić lepsze środowisko użytkownika aplikacji, gdy używają klasy.  
  
- W przypadku anulowania Ustaw flagę <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> w obiekcie <xref:System.ComponentModel.AsyncCompletedEventArgs>.  
  
- Upewnij się, że każda próba uzyskania dostępu do wyniku spowoduje wystąpienie <xref:System.InvalidOperationException> informującego, że operacja została anulowana. Użyj metody <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType>, aby przeprowadzić tę weryfikację.  
  
- Upewnij się, że wywołania metody anulowania zawsze zwracają się pomyślnie i nigdy nie zgłaszaj wyjątku. Ogólnie rzecz biorąc klient nie zostanie powiadomiony o tym, czy w danym momencie operacja jest w prawdziwie anulowana, i nie zostanie powiadomiona o tym, czy wcześniej wystawione anulowanie zakończyło się pomyślnie. Jednak aplikacja będzie zawsze otrzymywać powiadomienie, gdy anulowanie zakończyło się pomyślnie, ponieważ aplikacja bierze udział w stanie ukończenia.  
  
- Zgłoś zdarzenie**ukończenia** MethodName, gdy operacja zostanie anulowana.  
  
### <a name="errors-and-exceptions"></a>Błędy i wyjątki  
  
- Przechwyć wszystkie wyjątki występujące w operacji asynchronicznej i ustaw wartość właściwości <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> na ten wyjątek.  
  
### <a name="threading-and-contexts"></a>Wątkowość i konteksty  
 W celu poprawnego działania klasy należy pamiętać, że procedury obsługi zdarzeń klienta są wywoływane w prawidłowym wątku lub kontekście dla danego modelu aplikacji, w tym aplikacji ASP.NET i Windows Forms. Podano dwie ważne klasy pomocnika, aby zapewnić, że Klasa asynchroniczna działa prawidłowo w ramach dowolnego modelu aplikacji: <xref:System.ComponentModel.AsyncOperation> i <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager> zawiera jedną metodę <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, która zwraca <xref:System.ComponentModel.AsyncOperation>. Wywołania metody**asynchronicznej** <em>MethodName</em><xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> a klasa używa zwróconego <xref:System.ComponentModel.AsyncOperation> do śledzenia okresu istnienia zadania asynchronicznego.  
  
 Aby zgłosić postęp, wyniki przyrostowe i zakończenie do klienta, wywołaj metody <xref:System.ComponentModel.AsyncOperation.Post%2A> i <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> w <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation> jest odpowiedzialny za kierowanie wywołań do obsługi zdarzeń klienta do właściwego wątku lub kontekstu.  
  
> [!NOTE]
> Można obejść te reguły, jeśli użytkownik jawnie chce przejść względem zasad modelu aplikacji, ale nadal korzysta z innych zalet użycia wzorca asynchronicznego opartego na zdarzeniach. Na przykład może być konieczne, aby Klasa działająca w Windows Forms była wolna wątków. Można utworzyć wolnie wielowątkową klasę, o ile deweloperzy będą zrozumieć implikowane ograniczenia. Aplikacje konsolowe nie synchronizują wykonywania wywołań <xref:System.ComponentModel.AsyncOperation.Post%2A>. Może to spowodować nieuporządkowanie zdarzeń `ProgressChanged`. Jeśli chcesz mieć serializowane wykonywanie wywołań <xref:System.ComponentModel.AsyncOperation.Post%2A>, zaimplementuj i zainstaluj klasę <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType>.  
  
 Aby uzyskać więcej informacji na temat używania <xref:System.ComponentModel.AsyncOperation> i <xref:System.ComponentModel.AsyncOperationManager> do włączania operacji asynchronicznych, zobacz [How to: Implementuj składnik, który obsługuje wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Wytyczne  
  
- W idealnym przypadku każde wywołanie metody powinno być niezależne od innych. Należy unikać sprzęgania wywołań z udostępnionymi zasobami. Jeśli zasoby mają być współdzielone między wywołaniami, należy zapewnić odpowiedni mechanizm synchronizacji w implementacji.  
  
- Projekty wymagające wdrożenia synchronizacji nie są zalecane. Na przykład można mieć metodę asynchroniczną, która odbiera globalny obiekt statyczny jako parametr; wiele współbieżnych wywołań tej metody może spowodować uszkodzenie lub zakleszczenie danych.  
  
- W przypadku zaimplementowania metody przy użyciu przeciążenia wielokrotnego wywołania (`userState` w podpisie) Klasa będzie musiała zarządzać kolekcją Stanów użytkowników lub identyfikatorów zadań oraz odpowiednimi oczekującymi operacjami. Ta kolekcja powinna być chroniona za pomocą regionów `lock`, ponieważ różne wywołania dodają i usuwają obiekty `userState` w kolekcji.  
  
- Rozważ ponowne użycie klas `CompletedEventArgs`, jeśli jest to możliwe i odpowiednie. W takim przypadku nazewnictwo jest niespójne z nazwą metody, ponieważ dany typ delegata i <xref:System.EventArgs> nie są powiązane z pojedynczą metodą. Jednak zmuszanie deweloperów do rzutowania wartości pobranej z właściwości na <xref:System.EventArgs> nie jest nigdy akceptowalne.  
  
- W przypadku tworzenia klasy pochodzącej od <xref:System.ComponentModel.Component>nie należy implementować i instalować własnej klasy <xref:System.Threading.SynchronizationContext>. Modele aplikacji, a nie składniki, sterują używanym <xref:System.Threading.SynchronizationContext>.  
  
- Jeśli używasz wielowątkowości dowolnego sortowania, możesz ujawnić sobie bardzo poważne i złożone błędy. Przed zaimplementowaniem dowolnego rozwiązania korzystającego z wielowątkowości Zobacz sekcję [zarządzane wątki z najlepszymi praktykami](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Zobacz też

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
