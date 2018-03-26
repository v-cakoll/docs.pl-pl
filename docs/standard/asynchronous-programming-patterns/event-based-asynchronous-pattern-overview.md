---
title: Asynchroniczny wzorzec oparty na zdarzeniach — przegląd
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
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 792aa8da-918b-458e-b154-9836b97735f3
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: efe136ceb87213c5f9911b24a8a522b29a37b384
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="event-based-asynchronous-pattern-overview"></a>Asynchroniczny wzorzec oparty na zdarzeniach — przegląd
Aplikacje, których wykonywanie wielu zadań jednocześnie, ale nadal odbierać interakcji z użytkownikiem, często wymagają projekt, który używa wielu wątków. <xref:System.Threading> Przestrzeń nazw zawiera wszystkie narzędzia niezbędne do utworzenia aplikacji wielowątkowych wysokiej wydajności, ale efektywne używanie tych narzędzi wymaga znaczących środowisko z wielowątkowe engineering oprogramowania. Dla aplikacji wielowątkowych stosunkowo proste <xref:System.ComponentModel.BackgroundWorker> składnika rozwiązaniem jest proste. Dla bardziej zaawansowanych aplikacji asynchronicznego rozważ zaimplementowanie zgodnego ze wzorca asynchronicznego opartego na zdarzeniach klasy.  
  
 Asynchroniczny wzorzec oparty na zdarzeniach udostępnia zalety aplikacji wielowątkowych wiele złożonych problemów w wielowątkowe projektu są ukryte. Przy użyciu klasy, która obsługuje ten wzorzec umożliwia:  
  
-   Wykonywanie zadania czasochłonne, takie jak pliki do pobrania i operacje bazy danych "w tle" bez zakłócania pracy aplikacji.  
  
-   Wykonania wielu operacji jednocześnie odbieranie powiadomień po zakończeniu każdej.  
  
-   Poczekaj, aż zasobów na udostępnienie bez zatrzymywania ("wiszące") aplikacji.  
  
-   Komunikować się z oczekujących operacji asynchronicznych przy użyciu znanego modelu zdarzeń i delegatów. Aby uzyskać więcej informacji na temat używania programów obsługi zdarzeń i delegatów, zobacz [zdarzenia](../../../docs/standard/events/index.md).  
  
 Klasa obsługującego wzorzec asynchroniczny oparty na zdarzeniach będzie mieć co najmniej jedną metodę o nazwie *MethodName ***Async**. Te metody mogą duplikatów synchroniczne wersje, które do tej samej operacji w bieżącym wątku. Klasa może być również *MethodName *** Ukończono**  zdarzeń i może mieć *MethodName *** AsyncCancel** (lub po prostu **CancelAsync**) metody.  
  
 <xref:System.Windows.Forms.PictureBox> to typowy składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach. Pobranie obrazu synchronicznie przez wywołanie jego <xref:System.Windows.Forms.PictureBox.Load%2A> metody, ale jeśli obraz jest duży, lub jeśli połączenie sieciowe jest powolne, dla aplikacji zostanie zatrzymana ("zawiesza się"), aż do zakończenia operacji pobierania i wywołania w celu <xref:System.Windows.Forms.PictureBox.Load%2A> zwraca.  
  
 Jeśli chcesz, aby aplikacja nadal działać podczas obrazu jest ładowany, można wywołać <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> — metoda i dojście <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzeń, tak samo jak będzie obsługiwać inne zdarzenia. Podczas wywoływania <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metody, aplikacja będzie nadal działać podczas pobierania będzie kontynuowana w oddzielnym wątku ("w tle"). Obsługi zdarzenia będzie wywoływana po wykonaniu operacji ładowania obrazu i obsługi zdarzenia można sprawdzić <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr, aby określić, czy pobierania zakończyła się pomyślnie.  
  
 Asynchroniczny wzorzec oparty na zdarzeniach wymaga, aby można anulować operację asynchroniczną i <xref:System.Windows.Forms.PictureBox> sterowanie obsługuje to wymaganie z jego <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> metody. Wywoływanie <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> przesyła żądanie zatrzymania pobierania oczekujące, i gdy zadanie zostało anulowane, <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzenia.  
  
> [!CAUTION]
>  Istnieje możliwość, że pobieranie zakończy się podobnie jak <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> żądań, dlatego <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> mogą nie uwzględniać żądanie anulowania. Ta metoda jest wywoływana *sytuację wyścigu* i jest typowym problemem w programowaniu wielowątkowych. Aby uzyskać więcej informacji o problemach w programowaniu wielowątkowe, zobacz [zarządzanych wątków najlepsze rozwiązania w zakresie](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Właściwości wzorca asynchronicznego opartego na zdarzeniach  
 Asynchroniczny wzorzec oparty na zdarzeniach może potrwać kilka formularzy, w zależności od złożoności operacji obsługiwanych przez konkretnej klasy. Najprostsza klas może mieć pojedynczy *MethodName *** Async** metoda i odpowiadające mu *MethodName *** Ukończono** zdarzeń. Bardziej złożone klasy może mieć kilka *MethodName *** Async** z odpowiedniej metody *MethodName *** Ukończono** zdarzeń, a także synchroniczne wersji tych metod. Klasy może opcjonalnie obsługiwać anulowania, raportowania postępu i przyrostowych wyniki dla każdej metody asynchronicznej.  
  
 Metody asynchronicznej mogą obsługiwać wiele wywołań oczekujących (wiele współbieżnych wywołań), dzięki czemu kod w celu wywołania go dowolną liczbę razy przed zakończeniem działania innych oczekujących operacji. Poprawnie obsługi tej sytuacji może wymagać aplikacji do śledzenia zakończeniu każdej operacji.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Przykłady wzorca asynchronicznego opartego na zdarzeniach  
 <xref:System.Media.SoundPlayer> i <xref:System.Windows.Forms.PictureBox> prostych implementacji wzorca asynchronicznego opartego na zdarzeniach reprezentują składników. <xref:System.Net.WebClient> i <xref:System.ComponentModel.BackgroundWorker> bardziej złożonych implementacji wzorca asynchronicznego opartego na zdarzeniach reprezentują składników.  
  
 Poniżej znajduje się przykład deklaracji klasy, który jest zgodny z wzorcem:  
  
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
  
 Fikcyjne `AsyncExample` klasa ma dwie metody, które obsługuje wywołania synchroniczne i asynchroniczne. Synchroniczne przeciążeń przypominają każde wywołanie metody i wykonanie operacji w wątku wywołującym; Jeśli operacja jest czasochłonne, może istnieć zauważalnego opóźnienia przed wywołanie zwraca. Asynchroniczne przeciążeń uruchomi operacji na inny wątek i zwracany jest od razu, dzięki czemu wątek wywołujący kontynuować, podczas gdy wykonuje operację "w"tle.  
  
### <a name="asynchronous-method-overloads"></a>Przeciążenia metod asynchronicznych  
 Istnieją potencjalnie dwa przeciążenia dla asynchronicznych operacji: wywołanie jednym i wielu wywołania. Te dwie formy można wyróżnić przy ich podpisów — metoda: wywołanie wielu formularz zawiera dodatkowy parametr o nazwie `userState`. Ten formularz umożliwia wywołania `Method1Async(string param, object userState)` wiele razy bez oczekiwania na wszelkie oczekujące operacje asynchroniczne, aby zakończyć. Jeśli z drugiej strony, zostanie podjęta próba wywołania `Method1Async(string param)` przed ukończeniu poprzedniego wywołania metody zgłasza <xref:System.InvalidOperationException>.  
  
 `userState` Parametr dla wywołania wielu przeciążeń służy do rozróżnienia operacji asynchronicznych. Podaj unikatową wartość (na przykład kod identyfikatora GUID lub skrót) dla każdego wywołania `Method1Async(string param, object userState)`, a po zakończeniu każdej operacji obsługi zdarzenia można określić, które wystąpienie operacji wywołane zdarzenie ukończenia.  
  
### <a name="tracking-pending-operations"></a>Śledzenie oczekujące operacje  
 Jeśli używasz wielu wywołania przeciążenia kod musi śledzić `userState` obiektów (identyfikatorów zadań) dla zadań w toku. Dla każdego wywołania `Method1Async(string param, object userState)`, zwykle wygeneruje nowy, unikatowy `userState` obiektu i dodać go do kolekcji. Podczas zadania odpowiadający to `userState` obiektu wywołuje zdarzenie ukończenia, zbada implementacji metody ukończenia <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> i usunąć go z kolekcji. Używane w ten sposób `userState` Parametr przyjmuje rolę identyfikator zadania.  
  
> [!NOTE]
>  Należy zachować ostrożność zapewnić unikatową wartość `userState` w wywołaniami wywołania wielu przeciążeń. Nieunikatowy identyfikatorów zadań spowoduje, że throw asynchroniczne klasy <xref:System.ArgumentException>.  
  
### <a name="canceling-pending-operations"></a>Oczekujące operacje  
 Należy mieć możliwość anulowania operacji asynchronicznych w dowolnym momencie przed jego ukończeniem. Klasy, które implementują wzorzec asynchroniczny oparty na zdarzeniach będą miały `CancelAsync` — metoda (jeśli istnieje tylko jedna metoda asynchroniczna) lub *MethodName *** AsyncCancel** — metoda (jeśli istnieje wiele metod asynchronicznych).  
  
 Metody, które umożliwiają wielu wywołań przyjmują `userState` parametr, który może służyć do śledzenia ważności każdego zadania. `CancelAsync` Trwa `userState` parametru, dzięki czemu można anulować określonego oczekujące zadania.  
  
 Metody, które obsługują tylko jeden oczekującą operację naraz, tak samo, jak `Method1Async(string param)`, nie są można anulować.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Otrzymywanie aktualizacji postęp i wyniki przyrostowe  
 Klasa, która działa zgodnie z wzorca asynchronicznego opartego na zdarzeniach może opcjonalnie pozwala podać zdarzenia śledzenia postęp i wyniki przyrostowe. Będzie to zazwyczaj nazwany `ProgressChanged` lub * MethodName ***ProgressChanged**, a trwa jego odpowiedni program obsługi zdarzeń <xref:System.ComponentModel.ProgressChangedEventArgs> parametru.  
  
 Program obsługi zdarzeń dla `ProgressChanged` zdarzeń można sprawdzić <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> właściwości w celu określenia, jaki procent zadanie asynchroniczne została ukończona. Ta właściwość będzie należeć do zakresu od 0 do 100 i może posłużyć do zaktualizowania <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość <xref:System.Windows.Forms.ProgressBar>. W przypadku oczekujących operacji asynchronicznych wielu służy <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> właściwości odróżnienie która operacja raport z postępów.  
  
 Niektóre klasy może zgłaszać przyrostowe wyników jako operacji asynchronicznej. Te wyniki będą przechowywane w klasie, która jest pochodną <xref:System.ComponentModel.ProgressChangedEventArgs> i będą one wyświetlane jako właściwości w klasie pochodnej. Dostęp można uzyskać te wyniki do obsługi zdarzeń dla `ProgressChanged` zdarzeń, tak samo jak może uzyskać dostępu do <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> właściwości. W przypadku oczekujących operacji asynchronicznych wielu służy <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> właściwości do odróżnienia operacji, które jest raportowaniu wyników przyrostowe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 [Instrukcje: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
