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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160071"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Asynchroniczny wzorzec oparty na zdarzeniach — przegląd
Aplikacje, które wykonują wiele zadań jednocześnie, ale pozostają elastyczne do interakcji z użytkownikiem, często wymagają projektu, który używa wielu wątków. Obszar <xref:System.Threading> nazw zawiera wszystkie narzędzia niezbędne do tworzenia aplikacji wielowątkowych o wysokiej wydajności, ale korzystanie z tych narzędzi skutecznie wymaga znacznego doświadczenia z wielowątkową inżynierią oprogramowania. W przypadku stosunkowo prostych aplikacji <xref:System.ComponentModel.BackgroundWorker> wielowątkowych komponent zapewnia proste rozwiązanie. W przypadku bardziej zaawansowanych aplikacji asynchronicznych należy rozważyć zaimplementowanie klasy, która jest zgodna z wzorcem asynchronicznym opartym na zdarzeniach.  
  
 Wzorzec asynchroniczny oparty na zdarzeniach udostępnia zalety aplikacji wielowątkowych, ukrywając wiele złożonych problemów związanych z projektowaniem wielowątkowym. Użycie klasy obsługującej ten wzorzec umożliwia:  
  
- Wykonuj czasochłonne zadania, takie jak pliki do pobrania i operacje bazy danych "w tle", bez przerywania aplikacji.  
  
- Wykonuj wiele operacji jednocześnie, odbierając powiadomienia po zakończeniu każdego z nich.  
  
- Poczekaj, aż zasoby staną się dostępne bez zatrzymywania ("blokowanie") aplikacji.  
  
- Komunikuj się z oczekującymi operacjami asynchronicznymi przy użyciu modelu znanych zdarzeń i delegatów. Aby uzyskać więcej informacji na temat używania programów obsługi zdarzeń i delegatów, zobacz [Zdarzenia](../../../docs/standard/events/index.md).  
  
 Klasa obsługująca wzorzec asynchroniczny oparty na zdarzeniach będzie miała co najmniej jedną metodę o nazwie _MethodName_**Async**. Metody te mogą odzwierciedlać synchroniczne wersje, które wykonują tę samą operację w bieżącym wątku. Klasa może mieć również _MethodName_**Complete** zdarzenia i może mieć _MethodName_**AsyncCancel** (lub po prostu **CancelAsync)** metody.  
  
 <xref:System.Windows.Forms.PictureBox>jest typowym składnikiem, który obsługuje asynchroniczny wzorzec oparty na zdarzeniach. Obraz można pobrać synchronicznie, <xref:System.Windows.Forms.PictureBox.Load%2A> wywołując jego metodę, ale jeśli obraz jest duży lub jeśli połączenie sieciowe jest powolne, aplikacja przestanie odpowiadać, dopóki operacja pobierania nie zostanie zakończona, a wywołanie <xref:System.Windows.Forms.PictureBox.Load%2A> powrotu.  
  
 Jeśli chcesz, aby aplikacja działała podczas ładowania obrazu, <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> możesz wywołać metodę i obsługiwać <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzenie, tak jak można obsługiwać inne zdarzenie. Po wywołaniu <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metody aplikacja będzie nadal działać, gdy pobieranie będzie kontynuowane w oddzielnym wątku ("w tle"). Program obsługi zdarzeń zostanie wywołany po zakończeniu operacji ładowania obrazu, <xref:System.ComponentModel.AsyncCompletedEventArgs> a program obsługi zdarzeń może sprawdzić parametr, aby ustalić, czy pobieranie zostało zakończone pomyślnie.  
  
 Wzorzec asynchroniczny oparty na zdarzeniach wymaga anulowania operacji asynchronicznej, <xref:System.Windows.Forms.PictureBox> a <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> formant obsługuje to wymaganie za pomocą jego metody. Wywołanie <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> przesyła żądanie zatrzymania oczekujące pobieranie, a gdy zadanie <xref:System.Windows.Forms.PictureBox.LoadCompleted> zostanie anulowane, zdarzenie jest wywoływane.  
  
> [!CAUTION]
> Możliwe, że pobieranie zakończy się <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> tak samo, <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> jak żądanie jest wykonane, więc może nie odzwierciedlać żądania anulowania. Jest to tak zwany *stan wyścigu* i jest częstym problemem w programowaniu wielowątkowym. Aby uzyskać więcej informacji na temat problemów w programowaniu wielowątkowym, zobacz [Najlepsze rozwiązania dotyczące wątków zarządzanych](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Charakterystyka wzorca asynchronicznego opartego na zdarzeniach  
 Wzorzec asynchroniczny oparty na zdarzeniach może przybrać kilka form, w zależności od złożoności operacji obsługiwanych przez określoną klasę. Najprostsze klasy mogą mieć jedną metodę _MethodName_**Async** i odpowiednie _zdarzenie MethodName_**Completed.** Bardziej złożone klasy mogą mieć kilka _metod MethodName_**Async** metody, każdy z odpowiednim _MethodName_**Completed** zdarzenia, a także synchroniczne wersje tych metod. Klasy mogą opcjonalnie obsługiwać anulowanie, raportowanie postępu i wyniki przyrostowe dla każdej metody asynchronicznej.  
  
 Metoda asynchroniczna może również obsługiwać wiele oczekujących wywołań (wiele równoczesnych wywołań), umożliwiając kodowi wywołanie go dowolną liczbę razy przed zakończeniem innych oczekujących operacji. Poprawnie obsługi tej sytuacji może wymagać aplikacji do śledzenia zakończenia każdej operacji.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Przykłady wzorca asynchronicznego opartego na zdarzeniach  
 Składniki <xref:System.Media.SoundPlayer> <xref:System.Windows.Forms.PictureBox> i reprezentują proste implementacje wzorca asynchronicznego opartego na zdarzeniach. I <xref:System.Net.WebClient> <xref:System.ComponentModel.BackgroundWorker> składniki reprezentują bardziej złożone implementacje wzorca asynchronicznego opartego na zdarzeniach.  
  
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
  
 Fikcyjna `AsyncExample` klasa ma dwie metody, z których obie obsługują wywołania synchroniczne i asynchroniczne. Przeciążenia synchroniczne zachowują się jak każde wywołanie metody i wykonać operację w wątku wywołującego; jeśli operacja jest czasochłonna, może wystąpić zauważalne opóźnienie przed zwrotem połączenia. Przeciążenia asynchroniczne rozpocznie operację w innym wątku, a następnie powrócić natychmiast, dzięki czemu wątek wywołujący kontynuować, gdy operacja jest wykonywana "w tle."  
  
### <a name="asynchronous-method-overloads"></a>Przeciążenia metodą asynchroniczną  
 Istnieją potencjalnie dwa przeciążenia dla operacji asynchronicznych: wywołanie pojedyncze i wielokrotne wywołanie. Można rozróżnić te dwa formularze według ich podpisów metod: formularz `userState`wielokrotnego wywołania ma dodatkowy parametr o nazwie . Ten formularz umożliwia kod wywołać `Method1Async(string param, object userState)` wiele razy bez oczekiwania na wszelkie oczekujące operacje asynchroniczne, aby zakończyć. Jeśli z drugiej strony próbujesz `Method1Async(string param)` wywołać przed zakończeniem poprzedniego wywołania, <xref:System.InvalidOperationException>metoda wywołuje .  
  
 Parametr `userState` przeciążeń wielokrotnych wywołań umożliwia rozróżnienie między operacjami asynchronicznymi. Podana unikatowa wartość (na przykład identyfikator GUID `Method1Async(string param, object userState)`lub kod skrótu) dla każdego wywołania , a po zakończeniu każdej operacji program obsługi zdarzeń można określić, które wystąpienie operacji podniósł zdarzenie zakończenia.  
  
### <a name="tracking-pending-operations"></a>Śledzenie oczekujących operacji  
 Jeśli używasz przeciążeń wielokrotnego wywołania, kod będzie musiał `userState` śledzić obiekty (identyfikatory zadań) dla oczekujących zadań. Dla każdego `Method1Async(string param, object userState)`wywołania , zazwyczaj będzie generować nowy, unikatowy `userState` obiekt i dodać go do kolekcji. Gdy zadanie odpowiadające `userState` temu obiektowi wywołuje zdarzenie completion, <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> implementacja metody ukończenia zbada i usunie je z kolekcji. Używany w `userState` ten sposób parametr przyjmuje rolę identyfikatora zadania.  
  
> [!NOTE]
> Należy zachować ostrożność, aby `userState` zapewnić unikatową wartość w wywołaniach przeciążeń wielokrotnych wywołań. Nieunikatowe identyfikatory zadań spowoduje, że klasa <xref:System.ArgumentException>asynchroniczna wyrzuci plik .  
  
### <a name="canceling-pending-operations"></a>Anulowanie oczekujących operacji  
 Ważne jest, aby móc anulować operacje asynchroniczne w dowolnym momencie przed ich zakończeniem. Klasy implementują wzorzec asynchroniczny `CancelAsync` oparty na zdarzeniach będą miały metodę (jeśli istnieje tylko jedna metoda asynchroniczna) lub metodę _MethodName_**AsyncCancel** (jeśli istnieje wiele metod asynchronicznych).  
  
 Metody, które umożliwiają wiele wywołań podjąć `userState` parametr, który może służyć do śledzenia okresu istnienia każdego zadania. `CancelAsync`przyjmuje `userState` parametr, który umożliwia anulowanie określonych zadań oczekujących.  
  
 Metody, które obsługują tylko jedną oczekującą `Method1Async(string param)`operację w czasie, jak , nie można anulować.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Odbieranie aktualizacji postępu i wyników przyrostowych  
 Klasa, która jest zgodna z wzorcem asynchronicznym opartym na zdarzeniach, może opcjonalnie zapewnić zdarzenie do śledzenia postępu i wyników przyrostowych. Zazwyczaj będzie to `ProgressChanged` nazwane lub _MethodName_**ProgressChanged**, a <xref:System.ComponentModel.ProgressChangedEventArgs> odpowiedni program obsługi zdarzeń zajmie parametr.  
  
 Program obsługi zdarzeń dla `ProgressChanged` <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> zdarzenia można sprawdzić właściwość, aby określić, jaki procent zadania asynchronicznego została ukończona. Ta właściwość będzie się wahać od 0 do 100 i może służyć do aktualizacji <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości <xref:System.Windows.Forms.ProgressBar>. Jeśli wiele operacji asynchronicznych są oczekujące, można użyć <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> właściwości, aby odróżnić, która operacja jest raportowanie postępu.  
  
 Niektóre klasy mogą zgłaszać wyniki przyrostowe w miarę postępów operacji asynchronicznych. Wyniki te będą przechowywane w klasie, <xref:System.ComponentModel.ProgressChangedEventArgs> która pochodzi z i będą wyświetlane jako właściwości w klasie pochodnej. Można uzyskać dostęp do tych wyników w programie obsługi zdarzeń dla `ProgressChanged` zdarzenia, tak jak można uzyskać dostęp do <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> właściwości. Jeśli wiele operacji asynchronicznych są oczekujące, można użyć <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> właściwości, aby odróżnić, która operacja jest raportowanie wyników przyrostowych.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Instrukcje: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
