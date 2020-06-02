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
ms.openlocfilehash: f4aac5afbb13cafa7bb0e9c1eb6bbd92ac41bf8c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289424"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Asynchroniczny wzorzec oparty na zdarzeniach — przegląd
Aplikacje, które jednocześnie wykonują wiele zadań, jeszcze nie reagują na interakcję użytkownika, często wymagają projektu, który używa wielu wątków. <xref:System.Threading>Przestrzeń nazw zawiera wszystkie narzędzia niezbędne do tworzenia aplikacji wielowątkowych o wysokiej wydajności, ale używanie tych narzędzi skutecznie wymaga znaczących doświadczeń z obsługą wielowątkowych oprogramowania. W przypadku stosunkowo prostych aplikacji wielowątkowych składnik ten <xref:System.ComponentModel.BackgroundWorker> oferuje proste rozwiązanie. W przypadku bardziej zaawansowanych aplikacji asynchronicznych Rozważ zaimplementowanie klasy zgodnej ze wzorcem asynchronicznym opartym na zdarzeniach.  
  
 Wzorzec asynchroniczny oparty na zdarzeniach udostępnia zalety aplikacji wielowątkowych, jednocześnie ukrywając wiele złożonych problemów związanych z wielowątkowym projektem. Użycie klasy, która obsługuje ten wzorzec, może umożliwić:  
  
- Wykonywanie czasochłonnych zadań, takich jak pliki do pobrania i operacje bazy danych, "w tle" bez zakłócania pracy aplikacji.  
  
- Wykonywanie wielu operacji jednocześnie, otrzymywanie powiadomień po zakończeniu każdego z nich.  
  
- Poczekaj, aż zasoby staną się dostępne bez zatrzymywania ("blokowania") aplikacji.  
  
- Komunikuj się z oczekującymi operacjami asynchronicznymi przy użyciu znanych modeli Events i delegatów. Aby uzyskać więcej informacji na temat obsługi zdarzeń i delegatów, zobacz [zdarzenia](../events/index.md).  
  
 Klasa, która obsługuje wzorzec asynchroniczny oparty na zdarzeniach, będzie mieć co najmniej jedną metodę o nazwie _MethodName_**Async**. Te metody mogą dublować wersje synchroniczne, które wykonują tę samą operację na bieżącym wątku. Klasa może również mieć _MethodName_**ukończone** zdarzenie i może mieć metodę _MethodName_**AsyncCancel** (lub po prostu **CancelAsync**).  
  
 <xref:System.Windows.Forms.PictureBox>jest typowym składnikiem obsługującym wzorzec asynchroniczny oparty na zdarzeniach. Możesz pobrać obraz synchronicznie, wywołując jego <xref:System.Windows.Forms.PictureBox.Load%2A> metodę, ale jeśli obraz jest duży lub jeśli połączenie sieciowe działa wolno, aplikacja przestanie odpowiadać do momentu ukończenia operacji pobierania i wywołania <xref:System.Windows.Forms.PictureBox.Load%2A> zwrotnego.  
  
 Jeśli chcesz, aby aplikacja działała podczas ładowania obrazu, możesz wywołać <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metodę i obsłużyć <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzenie, podobnie jak w przypadku każdego innego zdarzenia. Po wywołaniu <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metody aplikacja będzie nadal działać, podczas gdy pobieranie jest kontynuowane w osobnym wątku ("w tle"). Procedura obsługi zdarzeń zostanie wywołana, gdy operacja ładowania obrazu zostanie zakończona, a program obsługi zdarzeń może sprawdzić <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr, aby określić, czy pobieranie zostało ukończone pomyślnie.  
  
 Wzorzec asynchroniczny oparty na zdarzeniach wymaga anulowania operacji asynchronicznej, a <xref:System.Windows.Forms.PictureBox> kontrolka obsługuje to wymaganie za pomocą <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> metody. Wywołanie <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> przesyła żądanie zatrzymania oczekującego pobrania i po anulowaniu zadania zostanie <xref:System.Windows.Forms.PictureBox.LoadCompleted> zgłoszone zdarzenie.  
  
> [!CAUTION]
> Możliwe jest, że pobieranie zakończy się tak samo jak <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> żądanie, dlatego <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> może nie odzwierciedlać żądania anulowania. Ta sytuacja jest nazywana *sytuacją wyścigu* i jest typowym problemem w programowaniu wielowątkowym. Aby uzyskać więcej informacji o problemach w programowaniu wielowątkowym, zobacz temat [zarządzane wątki z najlepszymi rozwiązaniami](../threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Charakterystyki wzorca asynchronicznego opartego na zdarzeniach  
 Wzorzec asynchroniczny oparty na zdarzeniach może potrwać kilka form, w zależności od złożoności operacji obsługiwanych przez konkretną klasę. Najprostsze klasy mogą mieć pojedynczą metodę _MethodName_**asynchroniczną** MethodName oraz odpowiednie zdarzenie _MethodName_**ukończenia** MethodName. Bardziej złożone klasy mogą mieć kilka metod**asynchronicznych** _MethodName_, z których każda ma odpowiednie zdarzenie _MethodName_**ukończone** , a także synchroniczne wersje tych metod. Klasy mogą opcjonalnie obsługiwać anulowanie, Raportowanie postępu i przyrostowe wyniki dla każdej metody asynchronicznej.  
  
 Metoda asynchroniczna może również obsługiwać wiele wywołań oczekujących (wiele współbieżnych połączeń), dzięki czemu kod może wywoływać dowolną liczbę razy, zanim ukończy inne oczekujące operacje. Prawidłowe obsłudze tej sytuacji może wymagać, aby aplikacja mogła śledzić ukończenie każdej operacji.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Przykłady wzorca asynchronicznego opartego na zdarzeniach  
 <xref:System.Media.SoundPlayer>Składniki i <xref:System.Windows.Forms.PictureBox> reprezentują proste implementacje wzorca asynchronicznego opartego na zdarzeniach. <xref:System.Net.WebClient>Składniki i <xref:System.ComponentModel.BackgroundWorker> reprezentują bardziej złożone implementacje wzorca asynchronicznego opartego na zdarzeniach.  
  
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
  
 Klasa fikcyjna `AsyncExample` ma dwie metody, które obsługują synchroniczne i asynchroniczne wywołania wywołań. Przeciążenia synchroniczne zachowują się jak dowolne wywołanie metody i wykonują operację w wątku wywołującym; Jeśli operacja jest czasochłonna, może wystąpić zauważalne opóźnienie, zanim wywołanie zwróci wartość. Przeciążenia asynchroniczne rozpoczną operację w innym wątku, a następnie zwracają natychmiast, zezwalając na kontynuowanie wątku wywołującego podczas wykonywania operacji "w tle".  
  
### <a name="asynchronous-method-overloads"></a>Przeciążenia metod asynchronicznych  
 Istnieją potencjalne dwa przeciążenia operacji asynchronicznych: jedno wywołanie i wiele wywołań. Można odróżnić te dwa formularze według ich sygnatur metod: formularz wielokrotnego wywołania ma dodatkowy parametr o nazwie `userState` . Dzięki temu kod może wywoływać `Method1Async(string param, object userState)` wiele razy bez oczekiwania na zakończenie oczekujących operacji asynchronicznych. Jeśli z drugiej strony próbujesz wywołać `Method1Async(string param)` przed ukończeniem poprzedniego wywołania, metoda wywołuje <xref:System.InvalidOperationException> .  
  
 `userState`Parametr przeciążenia wielokrotnego wywołania umożliwia rozróżnienie między operacjami asynchronicznymi. Podajesz unikatową wartość (na przykład identyfikator GUID lub kod skrótu) dla każdego wywołania do `Method1Async(string param, object userState)` , a po zakończeniu każdej operacji program obsługi zdarzeń może ustalić, które wystąpienie operacji wywołało zdarzenie ukończenia.  
  
### <a name="tracking-pending-operations"></a>Śledzenie operacji oczekujących  
 Jeśli używasz przeciążenia wielokrotnego wywołania, kod będzie musiał śledzić `userState` obiekty (identyfikatory zadań) dla oczekujących zadań. Dla każdego wywołania do `Method1Async(string param, object userState)` , zazwyczaj generowany jest nowy, unikatowy `userState` obiekt i dodaj go do kolekcji. Gdy zadanie odpowiadające temu `userState` obiektowi zgłosi zdarzenie ukończenia, implementacja metody zakończenia sprawdzi się <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> i usunie ją z kolekcji. Używany w ten sposób, `userState` parametr przyjmuje rolę identyfikatora zadania.  
  
> [!NOTE]
> Należy zachować ostrożność, aby podać unikatową wartość dla `userState` wywołań do przeciążenia wielokrotnego wywołania. Identyfikatory zadań nieunikatowych spowodują zgłoszenie klasy asynchronicznej <xref:System.ArgumentException> .  
  
### <a name="canceling-pending-operations"></a>Anulowanie operacji oczekujących  
 Ważne jest, aby można było anulować operacje asynchroniczne w dowolnym momencie przed ich ukończeniem. Klasy implementujące wzorzec asynchroniczny oparty na zdarzeniach będą miały `CancelAsync` metodę (jeśli istnieje tylko jedna Metoda asynchroniczna) lub metoda _MethodName_**AsyncCancel** (jeśli istnieje wiele metod asynchronicznych).  
  
 Metody zezwalające na wiele wywołań przyjmują `userState` parametr, który może służyć do śledzenia okresu istnienia każdego zadania. `CancelAsync`przyjmuje `userState` parametr, który umożliwia anulowanie konkretnych oczekujących zadań.  
  
 Metody, które obsługują tylko pojedynczą oczekującą operację w danym momencie, na przykład `Method1Async(string param)` nie są anulowane.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Otrzymywanie aktualizacji postępu i przyrostowych wyników  
 Klasa, która jest zgodna ze wzorcem asynchronicznym opartym na zdarzeniach, może opcjonalnie podać zdarzenie do śledzenia postępu i przyrostowych wyników. Zwykle jest to nazwana `ProgressChanged` lub _MethodName_**ProgressChanged**, a odpowiednia procedura obsługi zdarzeń przyjmuje <xref:System.ComponentModel.ProgressChangedEventArgs> parametr.  
  
 Procedura obsługi zdarzeń dla `ProgressChanged` zdarzenia może sprawdzić właściwość, <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> Aby określić, jaki procent zadania asynchronicznego zostało ukończone. Ta właściwość będzie zawierać zakres od 0 do 100 i może służyć do aktualizowania <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości <xref:System.Windows.Forms.ProgressBar> . Jeśli oczekuje wiele operacji asynchronicznych, można użyć właściwości, <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> Aby odróżnić, która operacja zgłasza postęp.  
  
 Niektóre klasy mogą raportować wyniki przyrostowe w miarę wykonywania operacji asynchronicznych. Te wyniki będą przechowywane w klasie, która pochodzi od <xref:System.ComponentModel.ProgressChangedEventArgs> i będą wyświetlane jako właściwości w klasie pochodnej. Dostęp do tych wyników można uzyskać w programie obsługi zdarzeń dla `ProgressChanged` zdarzenia, podobnie jak w przypadku uzyskania dostępu do <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> właściwości. Jeśli oczekuje wiele operacji asynchronicznych, można użyć właściwości, <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> Aby odróżnić, która operacja zgłasza przyrostowe wyniki.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Instrukcje: uruchamianie operacji w tle](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md)
- [Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
