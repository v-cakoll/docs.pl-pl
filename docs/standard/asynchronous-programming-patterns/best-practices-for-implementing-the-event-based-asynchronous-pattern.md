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
ms.openlocfilehash: 561d0759af4f7557bae39540cbb00f8038726ddc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950811"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach
Wzorzec asynchroniczny oparty na zdarzeniach umożliwia efektywne udostępnianie zachowań asynchronicznych w klasach ze znaną semantyką zdarzeń i delegatów. Aby zaimplementować wzorzec asynchroniczny oparty na zdarzeniach, należy przestrzegać pewnych konkretnych wymagań zachowań. W poniższych sekcjach opisano wymagania i wskazówki, które należy wziąć pod uwagę podczas implementowania klasy, która następuje po asynchronicznym wzorcu opartym na zdarzeniach.  
  
 Aby zapoznać się z omówieniem, zobacz [implementowanie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Wymagane gwarancje zachowania  
 W przypadku zaimplementowania wzorca asynchronicznego opartego na zdarzeniach należy podać pewną liczbę gwarancji, aby upewnić się, że klasa będzie działać prawidłowo, a klienci klasy mogą polegać na takiej sytuacji.  
  
### <a name="completion"></a>Uzupełnianie  
 Zawsze Wywołaj procedurę obsługi zdarzeń zakończonych <em>MethodName</em> po pomyślnym ukończeniu, błędzie lub anulowaniu. Aplikacje nigdy nie powinny napotkać sytuacji, w której pozostają bezczynne, a ukończenie nie następuje. Jedynym wyjątkiem od tej reguły jest zaprojektowana operacja asynchroniczna, tak aby nigdy nie kończyła się.  
  
### <a name="completed-event-and-eventargs"></a>Zdarzenie ukończenia i EventArgs  
 Dla każdej oddzielnej metody asynchronicznej <em>MethodName</em> należy zastosować następujące wymagania dotyczące projektu:  
  
- Zdefiniuj zdarzenie**ukończenia** MethodName dla tej samej klasy co metoda.  
  
- Zdefiniuj klasę i towarzyszący delegat dla zdarzenia <em>MethodName</em>**ukończone** , które wynika z <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy. <xref:System.EventArgs> Domyślna nazwa klasy powinna mieć postać <em>MethodName</em>**CompletedEventArgs**.  
  
- Upewnij się, <xref:System.EventArgs> że Klasa jest specyficzna dla wartości zwracanych metody <em>MethodName</em> . W przypadku korzystania z <xref:System.EventArgs> klasy nigdy nie należy wymagać, aby deweloperzy mogli rzutować wynik.  
  
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
  
- Nie należy definiować <xref:System.EventArgs> klasy dla zwracanych metod `void`. Zamiast tego należy użyć wystąpienia <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy.  
  
- Upewnij się, że zawsze zostało zgłoszone zdarzenie**ukończenia** <em>MethodName</em>. To zdarzenie należy wymusić po pomyślnym zakończeniu, po błędzie lub po anulowaniu. Aplikacje nigdy nie powinny napotkać sytuacji, w której pozostają bezczynne, a ukończenie nie następuje.  
  
- Upewnij się, że przechwytujesz wszystkie wyjątki występujące w operacji asynchronicznej i przypisz przechwycony wyjątek do <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwości.  
  
- Jeśli wystąpił błąd podczas kończenia zadania, wyniki nie powinny być dostępne. Gdy właściwość nie `null`jest, upewnij się, że <xref:System.EventArgs> dostęp do dowolnej właściwości w strukturze zgłasza wyjątek. <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> Użyj metody <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> , aby przeprowadzić tę weryfikację.  
  
- Przekrocz limit czasu jako błąd. Po przekroczeniu limitu czasu zgłoś zdarzenie <em>MethodName</em>**ukończone** <xref:System.TimeoutException> i przypisz do <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwości.  
  
- Jeśli klasa obsługuje wiele współbieżnych wywołań, upewnij się, że zdarzenie <em>MethodName</em>**ukończone** zawiera odpowiedni `userSuppliedState` obiekt.  
  
- Upewnij się, że zdarzenie**ukończenia** <em>MethodName</em>zostało zgłoszone na odpowiednim wątku i w odpowiednim czasie w cyklu życia aplikacji. Aby uzyskać więcej informacji, zobacz sekcję wątkowość i konteksty.  
  
### <a name="simultaneously-executing-operations"></a>Jednoczesne wykonywanie operacji  
  
- Jeśli klasa obsługuje wiele współbieżnych wywołań, należy umożliwić deweloperowi śledzenie każdego wywołania osobno przez zdefiniowanie przeciążenia**Async** `userSuppliedState` <em>MethodName</em>, które przyjmuje parametr stanu o wartości obiektu lub identyfikator zadania o nazwie. Ten parametr powinien zawsze być ostatnim parametrem w sygnaturze metody asynchronicznej <em>MethodName</em> .  
  
- Jeśli klasa definiuje Przeciążenie Async <em>MethodName</em> , które przyjmuje parametr stanu o wartościach obiektu lub identyfikator zadania, należy śledzić okres istnienia operacji przy użyciu tego identyfikatora zadania i upewnić się, że jest on ponownie używany do obsługi uzupełniania. Istnieją klasy pomocnika, które mogą być pomocne. Aby uzyskać więcej informacji na temat zarządzania współbieżnością, zobacz [How to: Implementacja składnika obsługującego wzorzec](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)asynchroniczny oparty na zdarzeniach.  
  
- Jeśli klasa definiuje metodę asynchroniczną <em>MethodName</em> bez parametru State i nie obsługuje wielu współbieżnych wywołań, upewnij się, że każda próba wywołania**Async** <em>MethodName</em>przed wcześniejszym <em>MethodName</em>  **Asynchroniczne** wywołanie zostało zakończone <xref:System.InvalidOperationException>.  
  
- Ogólnie rzecz biorąc nie należy zgłaszać wyjątku, jeśli `userSuppliedState` Metoda asynchroniczna <em>MethodName</em> bez parametru jest wywoływana wiele razy, tak że istnieje wiele zaległych operacji. Można zgłosić wyjątek, gdy Klasa jawnie nie może obsłużyć tej sytuacji, ale zakłada, że deweloperzy mogą obsługiwać te wielokrotne wywołania zwrotne  
  
### <a name="accessing-results"></a>Uzyskiwanie dostępu do wyników  
  
- Jeśli wystąpił błąd podczas wykonywania operacji asynchronicznej, wyniki nie powinny być dostępne. Upewnij się, że dostęp do dowolnej <xref:System.ComponentModel.AsyncCompletedEventArgs> właściwości <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> w elemencie `null` when nie wywołuje wyjątku, <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>do którego odwołuje się. <xref:System.ComponentModel.AsyncCompletedEventArgs> Klasa<xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> zapewnia metodę do tego celu.  
  
- Upewnij się, że wszystkie próby uzyskania dostępu do wyniku <xref:System.InvalidOperationException> spowodują, że operacja została anulowana. Użyj metody <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> , aby przeprowadzić tę weryfikację.  
  
### <a name="progress-reporting"></a>Raportowanie postępu  
  
- Raportowanie postępu obsługi, jeśli jest to możliwe. Dzięki temu deweloperzy mogą zapewnić lepsze środowisko użytkownika aplikacji, gdy używają klasy.  
  
- Jeśli zaimplementowano zdarzenie**ProgressChanged** **ProgressChanged** lub <em>MethodName</em>, należy się upewnić, że nie ma takich zdarzeń zgłoszonych dla określonej operacji asynchronicznej po zdarzeniu**ukończenia** tej operacji <em>MethodName</em> zostało zgłoszone.  
  
- Jeśli jest wypełniany standard <xref:System.ComponentModel.ProgressChangedEventArgs> , upewnij się, <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> że zawsze można interpretować wartość procentową. Wartość procentowa nie musi być dokładna, ale powinna reprezentować wartość procentową. Jeśli Metryka raportowania postępu musi być inna niż wartość procentowa, należy utworzyć klasę z <xref:System.ComponentModel.ProgressChangedEventArgs> klasy i pozostawić <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> wartość 0. Unikaj używania metryki raportowania innej niż wartość procentowa.  
  
- Upewnij się, `ProgressChanged` że zdarzenie jest zgłaszane na odpowiednim wątku i w odpowiednim czasie w cyklu życia aplikacji. Aby uzyskać więcej informacji, zobacz sekcję wątkowość i konteksty.  
  
### <a name="isbusy-implementation"></a>Implementacja IsBusy  
  
- Nie ujawniaj właściwości `IsBusy` , jeśli klasa obsługuje wiele współbieżnych wywołań. Na przykład proxy usługi sieci Web XML nie uwidacznia właściwości, `IsBusy` ponieważ obsługują one wiele współbieżnych wywołań metod asynchronicznych.  
  
- `true` Właściwość powinna zostać zwrócona po wywołaniu metody asynchronicznej MethodName i przed podniesieniem zdarzenia MethodName ukończone. `IsBusy` W przeciwnym razie powinna `false`zostać zwrócona. Składniki <xref:System.ComponentModel.BackgroundWorker> `IsBusy` i <xref:System.Net.WebClient> są przykładami klas, które uwidaczniają właściwość.  
  
### <a name="cancellation"></a>Anulowanie  
  
- Obsługa anulowania, jeśli to możliwe. Dzięki temu deweloperzy mogą zapewnić lepsze środowisko użytkownika aplikacji, gdy używają klasy.  
  
- W przypadku anulowania Ustaw <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> flagę <xref:System.ComponentModel.AsyncCompletedEventArgs> w obiekcie.  
  
- Upewnij się, że wszystkie próby uzyskania dostępu do wyniku <xref:System.InvalidOperationException> spowodują, że operacja została anulowana. Użyj metody <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> , aby przeprowadzić tę weryfikację.  
  
- Upewnij się, że wywołania metody anulowania zawsze zwracają się pomyślnie i nigdy nie zgłaszaj wyjątku. Ogólnie rzecz biorąc klient nie zostanie powiadomiony o tym, czy w danym momencie operacja jest w prawdziwie anulowana, i nie zostanie powiadomiona o tym, czy wcześniej wystawione anulowanie zakończyło się pomyślnie. Jednak aplikacja będzie zawsze otrzymywać powiadomienie, gdy anulowanie zakończyło się pomyślnie, ponieważ aplikacja bierze udział w stanie ukończenia.  
  
- Zgłoś zdarzenie**ukończenia** MethodName, gdy operacja zostanie anulowana.  
  
### <a name="errors-and-exceptions"></a>Błędy i wyjątki  
  
- Przechwyć wszystkie wyjątki występujące w operacji asynchronicznej i ustaw wartość <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości na ten wyjątek.  
  
### <a name="threading-and-contexts"></a>Wątkowość i konteksty  
 W celu poprawnego działania klasy należy pamiętać, że procedury obsługi zdarzeń klienta są wywoływane w prawidłowym wątku lub kontekście dla danego modelu aplikacji, w tym aplikacji ASP.NET i Windows Forms. Dostępne są dwie ważne klasy pomocnika, aby zapewnić, że Klasa asynchroniczna zachowuje się prawidłowo w ramach <xref:System.ComponentModel.AsyncOperation> dowolnego <xref:System.ComponentModel.AsyncOperationManager>modelu aplikacji: i.  
  
 <xref:System.ComponentModel.AsyncOperationManager>zawiera jedną metodę, <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>która <xref:System.ComponentModel.AsyncOperation>zwraca. <xref:System.ComponentModel.AsyncOperation> Wywołania metody<xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> asynchronicznej MethodName i Klasa używają zwracanego do śledzenia okresu istnienia zadania asynchronicznego.  
  
 Aby zgłosić postęp, wyniki przyrostowe i zakończenie do klienta, wywołaj <xref:System.ComponentModel.AsyncOperation.Post%2A> metody i <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> w. <xref:System.ComponentModel.AsyncOperation> <xref:System.ComponentModel.AsyncOperation>jest odpowiedzialny za kierowanie wywołań do obsługi zdarzeń klienta do odpowiedniego wątku lub kontekstu.  
  
> [!NOTE]
> Można obejść te reguły, jeśli użytkownik jawnie chce przejść względem zasad modelu aplikacji, ale nadal korzysta z innych zalet użycia wzorca asynchronicznego opartego na zdarzeniach. Na przykład może być konieczne, aby Klasa działająca w Windows Forms była wolna wątków. Można utworzyć wolnie wielowątkową klasę, o ile deweloperzy będą zrozumieć implikowane ograniczenia. Aplikacje konsolowe nie synchronizują wykonywania <xref:System.ComponentModel.AsyncOperation.Post%2A> wywołań. Może to spowodować `ProgressChanged` , że zdarzenia zostaną wygenerowane poza kolejnością. Jeśli chcesz mieć serializowane wykonywanie <xref:System.ComponentModel.AsyncOperation.Post%2A> wywołań, zaimplementuj i <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> Zainstaluj klasę.  
  
 Aby uzyskać więcej informacji na <xref:System.ComponentModel.AsyncOperation> temat <xref:System.ComponentModel.AsyncOperationManager> używania i włączania operacji asynchronicznych [, zobacz How to: Implementacja składnika obsługującego wzorzec](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)asynchroniczny oparty na zdarzeniach.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
  
- W idealnym przypadku każde wywołanie metody powinno być niezależne od innych. Należy unikać sprzęgania wywołań z udostępnionymi zasobami. Jeśli zasoby mają być współdzielone między wywołaniami, należy zapewnić odpowiedni mechanizm synchronizacji w implementacji.  
  
- Projekty wymagające wdrożenia synchronizacji nie są zalecane. Na przykład można mieć metodę asynchroniczną, która odbiera globalny obiekt statyczny jako parametr; wiele współbieżnych wywołań tej metody może spowodować uszkodzenie lub zakleszczenie danych.  
  
- W przypadku zaimplementowania metody przy użyciu przeciążenia wielokrotnego wywołania (`userState` w podpisie) Klasa będzie musiała zarządzać kolekcją Stanów użytkowników lub zadań, a także odpowiadające im operacje oczekujące. Ta kolekcja powinna być chroniona `lock` za pomocą regionów, ponieważ różne wywołania dodają i usuwają `userState` obiekty w kolekcji.  
  
- Rozważ ponowne użycie `CompletedEventArgs` klas, gdy jest to możliwe i odpowiednie. W takim przypadku nazewnictwo nie jest spójne z nazwą metody, ponieważ dany delegat i <xref:System.EventArgs> typ nie są powiązane z pojedynczą metodą. Jednak wymuszanie, aby deweloperzy mogli rzutować wartość pobieraną z <xref:System.EventArgs> właściwości na wartość nie jest nigdy akceptowalna.  
  
- Jeśli tworzysz klasę, która pochodzi od <xref:System.ComponentModel.Component>, nie Wdrażaj ani nie instaluj własnej <xref:System.Threading.SynchronizationContext> klasy. Modele aplikacji, a <xref:System.Threading.SynchronizationContext> nie składniki, kontrolują, która jest używana.  
  
- Jeśli używasz wielowątkowości dowolnego sortowania, możesz ujawnić sobie bardzo poważne i złożone błędy. Przed zaimplementowaniem dowolnego rozwiązania korzystającego z wielowątkowości Zobacz sekcję [zarządzane wątki](../../../docs/standard/threading/managed-threading-best-practices.md)z najlepszymi praktykami.  
  
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
- [Instrukcje: Używanie składników, które obsługują wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
