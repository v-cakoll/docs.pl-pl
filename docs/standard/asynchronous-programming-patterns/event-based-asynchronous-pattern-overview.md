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
ms.openlocfilehash: dfc8e1cfa6050a6e45373ad023ee8f358e388735
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423867"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Asynchroniczny wzorzec oparty na zdarzeniach — przegląd
Aplikacje, które jednocześnie wykonywać wiele zadań, ale ciągle reagować na interakcję z użytkownikiem, często wymagają projektu, który korzysta z wielu wątków. <xref:System.Threading> Przestrzeń nazw zawiera wszystkie narzędzia niezbędne do utworzenia aplikacji wielowątkowych o wysokiej wydajności, ale za pomocą tych narzędzi skutecznie wymaga bogate doświadczenie z wielowątkowych inżynierii oprogramowania. W przypadku stosunkowo proste aplikacji wielowątkowych <xref:System.ComponentModel.BackgroundWorker> składnik udostępnia proste rozwiązanie. Dla bardziej zaawansowanych aplikacji asynchronicznych należy rozważyć zaimplementowanie klasę, która jest zgodna wzorca asynchronicznego opartego na zdarzeniach.  
  
 Asynchroniczny wzorzec oparty na zdarzeniach udostępnia zalety aplikacji wielowątkowych wiele skomplikowane problemy związane z wielowątkowych projektu są ukryte. Za pomocą klasy, która obsługuje ten wzorzec może umożliwiają:  
  
- Wykonywać czasochłonne zadania, takie jak pliki do pobrania i operacji bazy danych "w tle" bez zakłócania pracy aplikacji.  
  
- Wykonać wiele operacji równocześnie, otrzymywanie powiadomień po każdym zakończeniu.  
  
- Oczekiwania na zasoby staną się dostępne bez konieczności zatrzymywania ("blokuje") aplikacji.  
  
- Komunikować się z oczekujących operacji asynchronicznych za pomocą znanego modelu zdarzeń i delegatów. Aby uzyskać więcej informacji na temat korzystania z programów obsługi zdarzeń i delegatów, zobacz [zdarzenia](../../../docs/standard/events/index.md).  
  
 Klasa obsługującego wzorzec asynchroniczny oparty na zdarzeniach będzie mieć co najmniej jedną metodę o nazwie _MethodName_**Async**. Te metody mogą dublować synchroniczne wersjach, które do tej samej operacji w bieżącym wątku. Klasa może mieć również _MethodName_**Ukończono** zdarzeń i może mieć _MethodName_**AsyncCancel** (lub po prostu  **CancelAsync**) metody.  
  
 <xref:System.Windows.Forms.PictureBox> to typowa składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach. Pobierania obrazu synchronicznie przez wywołanie jego <xref:System.Windows.Forms.PictureBox.Load%2A> metody, ale jeśli obraz jest duży lub, jeśli połączenie sieciowe jest powolne, aplikacja przestanie odpowiadać, aż do zakończenia operacji pobierania i wywołania w celu <xref:System.Windows.Forms.PictureBox.Load%2A> zwraca.  
  
 Jeśli chcesz, aby aplikacja umożliwia kontynuowanie działania podczas obraz jest ładowany, można wywołać <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metody i obsługują <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzenia, tak jak będzie obsługiwać dowolne inne zdarzenie. Gdy wywołujesz <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metody, aplikacja będzie kontynuował działanie podczas pobierania rozpoczynające się w oddzielnym wątku ("w tle"). Procedury obsługi zdarzenia będzie wywoływana po zakończeniu operacji ładowania obrazu i obsługi zdarzenia można sprawdzić <xref:System.ComponentModel.AsyncCompletedEventArgs> parametru, aby określić, jeśli pliki do pobrania została ukończona pomyślnie.  
  
 Asynchroniczny wzorzec oparty na zdarzeniach wymaga, że można anulować operację asynchroniczną i <xref:System.Windows.Forms.PictureBox> kontrolka obsługuje ten wymóg z jego <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> metody. Wywoływanie <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> przesyła żądanie zatrzymania oczekujące pobierania, i kiedy zadanie zostanie anulowane, <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzenie jest wywoływane.  
  
> [!CAUTION]
>  Istnieje możliwość, że pliki do pobrania zakończy się podobnie jak <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> żądania, więc <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> mogą nie odzwierciedlać żądanie anulowania. Jest to nazywane *wyścigu* i jest to typowy problem w programowanie wielowątkowe. Aby uzyskać więcej informacji na temat problemów z programowanie wielowątkowe, zobacz [zarządzana wątkowość najlepsze](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Właściwości wzorca asynchronicznego opartego na zdarzeniach  
 Asynchroniczny wzorzec oparty na zdarzeniach może przyjąć kilka postaci, w zależności od złożoności operacji obsługiwanych przez określonej klasy. Najprostsza klasy mogą mieć pojedynczy _MethodName_**Async** metody i odpowiadający mu _MethodName_**Ukończono** zdarzeń. Bardziej złożone klasy może mieć kilka _MethodName_**Async** z odpowiednią metod _MethodName_**Ukończono** zdarzenia jako także synchroniczne wersji tych metod. Klasy może opcjonalnie obsługiwać anulowania, Raportowanie postępu i przyrostowe wyników dla każdej metody asynchronicznej.  
  
 Metoda asynchroniczna mogą także obsługiwać wiele wywołań oczekujące (wielu równoczesnych wywołań), dzięki czemu kod jej wywołania dowolną liczbę razy przed ukończeniem innych oczekujących operacji. Poprawnie obsługi tej sytuacji może wymagać aplikacja do śledzenia wykonania operacji.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Przykładem wzorca asynchronicznego opartego na zdarzeniach  
 <xref:System.Media.SoundPlayer> i <xref:System.Windows.Forms.PictureBox> składniki reprezentują prostych implementacji wzorca asynchronicznego opartego na zdarzeniach. <xref:System.Net.WebClient> i <xref:System.ComponentModel.BackgroundWorker> składniki reprezentują bardziej złożonych implementacji wzorca asynchronicznego opartego na zdarzeniach.  
  
 Poniżej przedstawiono przykład deklaracji klasy, który jest zgodny ze wzorcem:  
  
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
  
 Fikcyjnej `AsyncExample` klasa ma dwie metody, które obsługują wywołania synchroniczne i asynchroniczne. Synchroniczne przeciążenia zachowują się jak każde wywołanie metody i wykonywanie operacji na wątku wywołującym; Jeśli operacja jest czasochłonne, może istnieć zauważalnego opóźnienia, zanim to wywołanie zwraca. Asynchroniczne przeciążenia będzie rozpocząć tę operację w innym wątku i zwracany jest natychmiast, dzięki czemu wątek wywołujący kontynuować, podczas gdy operacja wykonuje "w tle."  
  
### <a name="asynchronous-method-overloads"></a>Przeciążenia metody asynchronicznej  
 Istnieją potencjalnie dwa przeciążenia dla operacji asynchronicznych: wywołanie jednym i wielu wywołań. Za ich podpisy metod można odróżnić tych dwóch formach: formularz wielu wywołań ma dodatkowy parametr o nazwie `userState`. Ta forma umożliwia wywołania `Method1Async(string param, object userState)` wiele razy bez konieczności oczekiwania na żadnych oczekujących operacji asynchronicznych, aby zakończyć. Jeśli, z drugiej strony, podczas próby wywołania `Method1Async(string param)` przed ukończeniem poprzedniego wywołania, metoda zgłasza <xref:System.InvalidOperationException>.  
  
 `userState` Parametr dla wielu wywołania przeciążenia umożliwia rozróżnienia operacji asynchronicznych. Podaj unikatową wartość (na przykład, kod identyfikatora GUID lub skrót) dla każdego wywołania `Method1Async(string param, object userState)`, a po zakończeniu każdej operacji obsługi zdarzenia można określić, które wystąpienie operacji zgłoszone zdarzenie zakończenia.  
  
### <a name="tracking-pending-operations"></a>Śledzenie oczekujące operacje  
 Jeśli używasz wielu wywołania przeciążenia, kod musi śledzić `userState` obiektów (identyfikatorów zadań) oczekujące zadania. Dla każdego wywołania `Method1Async(string param, object userState)`, zwykle wygeneruje nową, unikatowych `userState` obiektu i dodaj go do kolekcji. Gdy zadania odpowiadającego tej `userState` obiektu wywołuje zdarzenie ukończenia, sprawdzać Twoja implementacja metody ukończenia <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> i usunąć go z kolekcji. Używana w ten sposób `userState` Parametr przyjmuje rolę identyfikator zadania.  
  
> [!NOTE]
>  Musisz być ostrożnym zapewnić unikatową wartość dla `userState` w wywołania względem wielu wywołania przeciążenia. Nieunikatowy identyfikatorów zadań spowoduje, że throw asynchroniczne klasa <xref:System.ArgumentException>.  
  
### <a name="canceling-pending-operations"></a>Oczekujące operacje  
 Należy mieć możliwość anulowania operacji asynchronicznych w dowolnym momencie przed ich zakończeniu. Klasy, które implementują wzorzec asynchroniczny oparty na zdarzeniach będą miały `CancelAsync` metody (jeśli istnieje tylko jedna metoda asynchroniczna) lub _MethodName_**AsyncCancel** metody (jeśli istnieje wiele metody asynchroniczne).  
  
 Metody, które umożliwiają wielu wywołań przyjmują `userState` parametr, który może służyć do śledzenia okresu istnienia każdego zadania. `CancelAsync` Trwa `userState` parametr, który umożliwia anulowanie określonego oczekujące zadania.  
  
 Metody, które obsługują tylko jeden oczekującej operacji w czasie, takie jak `Method1Async(string param)`, nie są można anulować.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Otrzymywanie aktualizacji postęp i wyniki przyrostowe  
 Klasa, która jest zgodna wzorca asynchronicznego opartego na zdarzeniach może opcjonalnie podać zdarzenia do śledzenia postępu i wyniki przyrostowe. Będzie to zazwyczaj miała `ProgressChanged` lub _MethodName_**ProgressChanged**, i zajmie się jego odpowiedni program obsługi zdarzeń <xref:System.ComponentModel.ProgressChangedEventArgs> parametru.  
  
 Program obsługi zdarzeń dla `ProgressChanged` zbadać zdarzenia <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> właściwości w celu określenia, jaki procent asynchroniczne zadanie zostało ukończone. Ta właściwość będzie należeć do zakresu od 0 do 100 i może służyć do zaktualizowania <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość <xref:System.Windows.Forms.ProgressBar>. W przypadku oczekujących wiele operacji asynchronicznych umożliwia <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> właściwości w celu odróżnienia kolejnej operacji jest raportowania postępu.  
  
 Niektóre klasy mogą zgłaszać przyrostowe wyniki kontynuowaniem operacji asynchronicznych. Te wyniki będą przechowywane w klasie, która pochodzi od klasy <xref:System.ComponentModel.ProgressChangedEventArgs> i pojawią się one jako właściwości w klasie pochodnej. Dostęp można uzyskać te wyniki w program obsługi zdarzeń dla `ProgressChanged` zdarzenia, tak jak dostęp do <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> właściwości. W przypadku oczekujących wiele operacji asynchronicznych umożliwia <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> właściwości w celu odróżnienia kolejnej operacji zgłasza wyniki przyrostowe.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Instrukcje: Używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Instrukcje: Uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Instrukcje: Implementowanie formularza korzystającego z operacji w tle](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
