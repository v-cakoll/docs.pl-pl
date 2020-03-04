---
title: Asynchroniczny wzorzec oparty na zdarzeniach — przegląd
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
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 792aa8da-918b-458e-b154-9836b97735f3
ms.openlocfilehash: cce01a7c87f6f20b5e6c46881b8c863bb5a72a88
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160071"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Asynchroniczny wzorzec oparty na zdarzeniach — przegląd
Aplikacje, które jednocześnie wykonują wiele zadań, jeszcze nie reagują na interakcję użytkownika, często wymagają projektu, który używa wielu wątków. Przestrzeń nazw <xref:System.Threading> zawiera wszystkie narzędzia niezbędne do tworzenia aplikacji wielowątkowych o wysokiej wydajności, ale używanie tych narzędzi skutecznie wymaga znacznego doświadczenia z obsługą wielowątkowych oprogramowania. W przypadku stosunkowo prostych aplikacji wielowątkowych składnik <xref:System.ComponentModel.BackgroundWorker> zapewnia proste rozwiązanie. W przypadku bardziej zaawansowanych aplikacji asynchronicznych Rozważ zaimplementowanie klasy zgodnej ze wzorcem asynchronicznym opartym na zdarzeniach.  
  
 Wzorzec asynchroniczny oparty na zdarzeniach udostępnia zalety aplikacji wielowątkowych, jednocześnie ukrywając wiele złożonych problemów związanych z wielowątkowym projektem. Użycie klasy, która obsługuje ten wzorzec, może umożliwić:  
  
- Wykonywanie czasochłonnych zadań, takich jak pliki do pobrania i operacje bazy danych, "w tle" bez zakłócania pracy aplikacji.  
  
- Wykonywanie wielu operacji jednocześnie, otrzymywanie powiadomień po zakończeniu każdego z nich.  
  
- Poczekaj, aż zasoby staną się dostępne bez zatrzymywania ("blokowania") aplikacji.  
  
- Komunikuj się z oczekującymi operacjami asynchronicznymi przy użyciu znanych modeli Events i delegatów. Aby uzyskać więcej informacji na temat obsługi zdarzeń i delegatów, zobacz [zdarzenia](../../../docs/standard/events/index.md).  
  
 Klasa, która obsługuje wzorzec asynchroniczny oparty na zdarzeniach, będzie mieć co najmniej jedną metodę o nazwie _MethodName_**Async**. Te metody mogą dublować wersje synchroniczne, które wykonują tę samą operację na bieżącym wątku. Klasa może również mieć _MethodName_**ukończone** zdarzenie i może mieć metodę _MethodName_**AsyncCancel** (lub po prostu **CancelAsync**).  
  
 <xref:System.Windows.Forms.PictureBox> jest typowym składnikiem obsługującym wzorzec asynchroniczny oparty na zdarzeniach. Możesz pobrać obraz synchronicznie, wywołując jego metodę <xref:System.Windows.Forms.PictureBox.Load%2A>, ale jeśli obraz jest duży lub jeśli połączenie sieciowe jest powolne, aplikacja przestanie odpowiadać do momentu ukończenia operacji pobierania, a wywołanie <xref:System.Windows.Forms.PictureBox.Load%2A> zwraca wartość.  
  
 Jeśli chcesz, aby aplikacja była uruchomiona podczas ładowania obrazu, możesz wywołać metodę <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> i obsłużyć zdarzenie <xref:System.Windows.Forms.PictureBox.LoadCompleted>, tak jak w przypadku każdego innego zdarzenia. Gdy wywołasz metodę <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>, aplikacja będzie nadal działać, podczas gdy pobieranie jest kontynuowane w osobnym wątku ("w tle"). Procedura obsługi zdarzeń zostanie wywołana, gdy operacja ładowania obrazu zostanie ukończona, a procedura obsługi zdarzeń może sprawdzić parametr <xref:System.ComponentModel.AsyncCompletedEventArgs>, aby określić, czy pobieranie zostało ukończone pomyślnie.  
  
 Wzorzec asynchroniczny oparty na zdarzeniach wymaga anulowania operacji asynchronicznej, a kontrolka <xref:System.Windows.Forms.PictureBox> obsługuje to wymaganie przy użyciu metody <xref:System.Windows.Forms.PictureBox.CancelAsync%2A>. Wywołanie <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> przesłania żądanie zatrzymania pobierania oczekujące i po anulowaniu zadania zostanie zgłoszone zdarzenie <xref:System.Windows.Forms.PictureBox.LoadCompleted>.  
  
> [!CAUTION]
> Możliwe jest, że pobieranie zakończy się tak samo jak żądanie <xref:System.Windows.Forms.PictureBox.CancelAsync%2A>, więc <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> może nie odzwierciedlać żądania anulowania. Ta sytuacja jest nazywana *sytuacją wyścigu* i jest typowym problemem w programowaniu wielowątkowym. Aby uzyskać więcej informacji o problemach w programowaniu wielowątkowym, zobacz temat [zarządzane wątki z najlepszymi rozwiązaniami](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Charakterystyki wzorca asynchronicznego opartego na zdarzeniach  
 Wzorzec asynchroniczny oparty na zdarzeniach może potrwać kilka form, w zależności od złożoności operacji obsługiwanych przez konkretną klasę. Najprostsze klasy mogą mieć pojedynczą metodę**asynchroniczną** MethodName oraz odpowiednie zdarzenie**ukończenia** MethodName. Bardziej złożone klasy mogą mieć kilka metod**asynchronicznych** _MethodName_, z których każda ma odpowiednie zdarzenie _MethodName_**ukończone** , a także synchroniczne wersje tych metod. Klasy mogą opcjonalnie obsługiwać anulowanie, Raportowanie postępu i przyrostowe wyniki dla każdej metody asynchronicznej.  
  
 Metoda asynchroniczna może również obsługiwać wiele wywołań oczekujących (wiele współbieżnych połączeń), dzięki czemu kod może wywoływać dowolną liczbę razy, zanim ukończy inne oczekujące operacje. Prawidłowe obsłudze tej sytuacji może wymagać, aby aplikacja mogła śledzić ukończenie każdej operacji.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Przykłady wzorca asynchronicznego opartego na zdarzeniach  
 Składniki <xref:System.Media.SoundPlayer> i <xref:System.Windows.Forms.PictureBox> reprezentują proste implementacje wzorca asynchronicznego opartego na zdarzeniach. Składniki <xref:System.Net.WebClient> i <xref:System.ComponentModel.BackgroundWorker> reprezentują bardziej złożone implementacje wzorca asynchronicznego opartego na zdarzeniach.  
  
 Poniżej znajduje się przykładowa deklaracja klasy, która jest zgodna ze wzorcem:  
  
```vb  
Public Class AsyncExample  
    ' Synchronous methods.  
    Public Function Method1(ByVal param As String) As Integer
    Public Sub Method2(ByVal param As Double)
  
    ' Asynchronous methods.  
    Overloads Public Sub Method1Async(ByVal param As String)
    Overloads Public Sub Method1Async(ByVal param As String, ByVal userState As Object)
    Public Event Method1Completed As Method1CompletedEventHandler  
  
    Overloads Public Sub Method2Async(ByVal param As Double)
    Overloads Public Sub Method2Async(ByVal param As Double, ByVal userState As Object)
    Public Event Method2Completed As Method2CompletedEventHandler  
  
    Public Sub CancelAsync(ByVal userState As Object)
  
    Public ReadOnly Property IsBusy () As Boolean  
  
    ' Class implementation not shown.  
End Class  
```  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 Fikcyjna Klasa `AsyncExample` ma dwie metody, które obsługują synchroniczne i asynchroniczne wywołania wywołań. Przeciążenia synchroniczne zachowują się jak dowolne wywołanie metody i wykonują operację w wątku wywołującym; Jeśli operacja jest czasochłonna, może wystąpić zauważalne opóźnienie, zanim wywołanie zwróci wartość. Przeciążenia asynchroniczne rozpoczną operację w innym wątku, a następnie zwracają natychmiast, zezwalając na kontynuowanie wątku wywołującego podczas wykonywania operacji "w tle".  
  
### <a name="asynchronous-method-overloads"></a>Przeciążenia metod asynchronicznych  
 Istnieją potencjalne dwa przeciążenia operacji asynchronicznych: jedno wywołanie i wiele wywołań. Można odróżnić te dwa formularze według ich sygnatur metod: formularz wielokrotnego wywołania ma dodatkowy parametr o nazwie `userState`. Dzięki temu kod może wywoływać `Method1Async(string param, object userState)` wiele razy bez oczekiwania na zakończenie oczekujących operacji asynchronicznych. Jeśli z drugiej strony próbujesz wywołać `Method1Async(string param)` przed ukończeniem poprzedniego wywołania, metoda wywołuje <xref:System.InvalidOperationException>.  
  
 `userState` parametr dla przeciążenia wielu wywołań umożliwia rozróżnienie operacji asynchronicznych. Podajesz unikatową wartość (na przykład identyfikator GUID lub kod skrótu) dla każdego wywołania do `Method1Async(string param, object userState)`i po zakończeniu każdej operacji procedura obsługi zdarzeń może ustalić, które wystąpienie operacji wywołało zdarzenie ukończenia.  
  
### <a name="tracking-pending-operations"></a>Śledzenie operacji oczekujących  
 Jeśli używasz przeciążenia wielokrotnego wywołania, kod będzie musiał śledzić `userState` obiekty (identyfikatory zadań) dla oczekujących zadań. Dla każdego wywołania `Method1Async(string param, object userState)`zwykle generowany jest nowy, unikatowy obiekt `userState` i dodaj go do kolekcji. Gdy zadanie odpowiadające temu obiektowi `userState` podnosi zdarzenie ukończenia, implementacja metody zakończenia sprawdzi <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> i usunie ją z kolekcji. Używany w ten sposób, `userState` parametr przyjmuje rolę identyfikatora zadania.  
  
> [!NOTE]
> Należy zachować ostrożność, aby zapewnić unikatową wartość `userState` w wywołaniach do przeciążenia wielu wywołań. Identyfikatory zadań nieunikatowych spowodują wygenerowanie <xref:System.ArgumentException>w klasie asynchronicznej.  
  
### <a name="canceling-pending-operations"></a>Anulowanie operacji oczekujących  
 Ważne jest, aby można było anulować operacje asynchroniczne w dowolnym momencie przed ich ukończeniem. Klasy implementujące wzorzec asynchroniczny oparty na zdarzeniach będą miały metodę `CancelAsync` (jeśli istnieje tylko jedna Metoda asynchroniczna) lub metoda _MethodName_**AsyncCancel** (jeśli istnieje wiele metod asynchronicznych).  
  
 Metody zezwalające wielu wywołań pobierają `userState` parametr, który może służyć do śledzenia okresu istnienia każdego zadania. `CancelAsync` pobiera parametr `userState`, który umożliwia anulowanie konkretnych oczekujących zadań.  
  
 Metody, które obsługują tylko jedną oczekującą operację naraz, na przykład `Method1Async(string param)`, nie mogą być anulowane.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Otrzymywanie aktualizacji postępu i przyrostowych wyników  
 Klasa, która jest zgodna ze wzorcem asynchronicznym opartym na zdarzeniach, może opcjonalnie podać zdarzenie do śledzenia postępu i przyrostowych wyników. Zwykle jest to nazwana `ProgressChanged` lub _MethodName_**ProgressChanged**, a odpowiadająca jej procedura obsługi zdarzeń będzie przyjmować parametr <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Program obsługi zdarzeń dla zdarzenia `ProgressChanged` może sprawdzić Właściwość <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType>, aby określić, jaki procent zadania asynchronicznego zostało ukończone. Ta właściwość będzie zawierać zakres od 0 do 100 i może służyć do aktualizowania właściwości <xref:System.Windows.Forms.ProgressBar.Value%2A> <xref:System.Windows.Forms.ProgressBar>. Jeśli oczekuje wiele operacji asynchronicznych, można użyć właściwości <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType>, aby odróżnić, która operacja zgłasza postęp.  
  
 Niektóre klasy mogą raportować wyniki przyrostowe w miarę wykonywania operacji asynchronicznych. Te wyniki będą przechowywane w klasie, która pochodzi od <xref:System.ComponentModel.ProgressChangedEventArgs> i będą wyświetlane jako właściwości w klasie pochodnej. Możesz uzyskać dostęp do tych wyników w programie obsługi zdarzeń dla zdarzenia `ProgressChanged`, tak jak w przypadku dostępu do właściwości <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A>. Jeśli oczekuje wiele operacji asynchronicznych, można użyć właściwości <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A>, aby odróżnić, która operacja zgłasza przyrostowe wyniki.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Instrukcje: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
