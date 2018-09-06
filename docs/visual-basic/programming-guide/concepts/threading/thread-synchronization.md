---
title: Synchronizacja wątku (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 04f485d1-8333-4510-9e72-c334e7427e7e
ms.openlocfilehash: 3278ed1e98f71e11d47f55a0d4cb50f44ae02027
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862997"
---
# <a name="thread-synchronization-visual-basic"></a>Synchronizacja wątku (Visual Basic)
W następujących sekcjach opisano funkcje i klasy, które mogą służyć do synchronizowania dostępu do zasobów w aplikacjach wielowątkowych.  
  
 Jedną z zalet korzystania z wielu wątków w aplikacji jest asynchronicznie wykonuje każdy wątek. Dla aplikacji Windows dzięki temu czasochłonne zadania, które mają być wykonywane w tle podczas okna aplikacji, a formanty czas reakcji. Dla serwera aplikacji wielowątkowość oferuje możliwość obsługi danego żądania przychodzące z innym wątku. W przeciwnym razie każdego nowego żądania nie będą Pobierz obsługiwane, dopóki nie był całkowicie spełnione poprzedniego żądania.  
  
 Jednak charakter asynchronicznego oznacza wątków, że dostęp do zasobów, takich jak dojścia do plików, połączeń sieciowych i pamięci musi być koordynowane. W przeciwnym razie dwa lub więcej wątków można uzyskać dostępu do tego samego zasobu w tym samym czasie każdego niezależnych od funkcji, z drugiej strony czynności. Powoduje to uszkodzenie danych nieprzewidywalne.  
  
 Dla prostych operacji na typy całkowite danych liczbowych, synchronizacja wątków może się odbywać z członkami <xref:System.Threading.Interlocked> klasy. Wszystkie pozostałe dane typów i zasobów innych niż wielowątkowość wielowątkowość można bezpiecznie wykonać tylko przy użyciu konstrukcje w tym temacie.  
  
 Aby uzyskać ogólne informacje na programowanie wielowątkowe zobacz:  
  
-   [Zarządzana wątkowość — podstawy](../../../../standard/threading/managed-threading-basics.md)  
  
-   [Używanie wątków i wątkowości](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Zarządzana wątkowość — najlepsze rozwiązania](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-and-synclock-keywords"></a>Blokowanie i słów kluczowych SyncLock  
 Visual Basic `SyncLock` instrukcji może służyć do zapewnienia, że blok kodu zostaje ukończone bez przerwy przez inne wątki. Jest to osiągane, uzyskując blokadę wykluczania wzajemnego dla danego obiektu w czasie trwania bloku kodu.  
  
 A `SyncLock` Instrukcja znajduje się obiekt jako argument i następuje blok kodu, który ma zostać wykonana przez tylko jeden wątek jednocześnie. Na przykład:  
  
```vb  
Public Class TestThreading  
    Dim lockThis As New Object  
  
    Public Sub Process()  
        SyncLock lockThis  
            ' Access thread-sensitive resources.  
        End SyncLock  
    End Sub  
End Class  
```  
  
 Argument podany do `SyncLock` — słowo kluczowe musi być obiektem, na podstawie typu odwołania i jest używany do definiowania zakresu blokady. W powyższym przykładzie zakres blokady jest ograniczony do tej funkcji, ponieważ nie odwołania do obiektu `lockThis` istnieje poza funkcją. Jeśli istniał takie odwołanie, zakres blokady będą dotyczyć tego obiektu. Ściśle rzecz ujmując obiekt udostępniany służy wyłącznie do jednoznacznej identyfikacji udostępnianego między wieloma wątkami aby mogło być ono wystąpienia klasy dowolnego zasobu. W praktyce, jednak ten obiekt zazwyczaj reprezentuje zasobów, które wątku synchronizacji jest konieczne. Na przykład jeśli obiekt kontenera jest używane przez wiele wątków, kontener może być następnie przekazywany do blokowania i blok kodu zsynchronizowane po blokadę dostępu do kontenera. Tak długo, jak inne wątki blokuje się na tym samym zawierają przed uzyskaniem dostępu do niego dostępu do obiektu bezpiecznie jest zsynchronizowany.  
  
 Ogólnie rzecz biorąc, zaleca się unikać blokowania na `public` typu, lub wystąpienia obiektów poza kontrolą aplikacji. Na przykład `lockThis` może być problematyczne, jeśli wystąpienie jest możliwy publicznie, powodując, ponieważ kod poza Twoją kontrolą może zablokować obiektu, jak również. To może utworzyć zakleszczenia sytuacji, w której dwa lub więcej wątków poczekaj, aż wersji tego samego obiektu. Blokowanie na typ danych publicznego, w przeciwieństwie do obiektu może spowodować problemy z tego samego powodu. Blokowanie na ciągi literałowe jest szczególnie ryzykowne, ponieważ są ciągami tekstowymi *interned* przez środowisko uruchomieniowe języka wspólnego (CLR). Oznacza to, że istnieje jedno wystąpienie dowolnego ciągu literału dla całego programu, dokładnie ten sam obiekt reprezentuje literał we wszystkich systemem domen aplikacji wszystkich wątków. Co w efekcie zablokować na ciąg przy użyciu tej samej zawartości dowolnym miejscu w blokad procesu aplikacji wszystkich wystąpień tego ciągu w aplikacji. W rezultacie najlepiej jest do blokowania prywatnych lub chronionych składowej, która nie jest interned. Niektóre klasy dostarczenia elementów członkowskich, specjalnie pod kątem blokowania. <xref:System.Array> Typu, na przykład zapewnia <xref:System.Array.SyncRoot%2A>. Wiele typów kolekcji zapewniają `SyncRoot` również element członkowski.  
  
 Aby uzyskać więcej informacji na temat `SyncLock` poufności informacji, zobacz następujące tematy:  
  
-   [SyncLock, instrukcja](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a>Monitory  
 Podobnie jak `SyncLock` — słowo kluczowe, monitorów zapobiec bloków kodu z jednoczesne wykonywanie wielu wątków. <xref:System.Threading.Monitor.Enter%2A> Metoda umożliwia jeden i tylko jeden wątek przejść do następujących instrukcji; inne wątki są zablokowane do czasu wykonywania wywołań wątku <xref:System.Threading.Monitor.Exit%2A>. Jest to tak, jak za pomocą `SyncLock` — słowo kluczowe. Na przykład:  
  
```vb  
SyncLock x  
    DoSomething()  
End SyncLock  
```  
  
 Jest to równoważne:  
  
```vb  
Dim obj As Object = CType(x, Object)  
System.Threading.Monitor.Enter(obj)  
Try  
    DoSomething()  
Finally  
    System.Threading.Monitor.Exit(obj)  
End Try  
```  
  
 Za pomocą `SyncLock` — słowo kluczowe jest ogólnie metoda preferowana za pośrednictwem za pomocą <xref:System.Threading.Monitor> klasy bezpośrednio, zarówno ponieważ `SyncLock` jest bardziej zwięzłe i dlatego `SyncLock` ubezpieczycielom podstawowy monitor jest zwolnienie, nawet jeśli chroniony kod zgłasza wyjątek. Jest to realizowane przy `Finally` słowo kluczowe, które uruchamia jego blok skojarzonego kodu, niezależnie od tego, czy wyjątek jest zgłaszany.  
  
## <a name="synchronization-events-and-wait-handles"></a>Zdarzenia synchronizacji i uchwytami oczekiwania  
 Przy użyciu blokady lub monitor jest użyteczne w rozwiązywaniu jednoczesne wykonywanie wątku z uwzględnieniem bloków kodu, ale te konstrukcje nie zezwalają na jeden wątek do komunikowania się zdarzenia do innego. Wymaga to *zdarzenia synchronizacji*, które są obiekty, które mają jeden z trzech stanów sygnałowego i niezaznaczone zasygnalizowany, który może służyć do aktywowania i wstrzymać wątków. Wątki może zostać zawieszone przez wysyłanych do oczekiwania na zdarzenie synchronizacji, która jest unsignaled i można uaktywnić przez zmianę stanu zdarzenia do zasygnalizowane. Jeśli wątek próbował oczekiwanie na zdarzenie, które już jest sygnalizowane, wątek kontynuuje wykonywanie bez opóźnień.  
  
 Istnieją dwa rodzaje zdarzeń synchronizacji: <xref:System.Threading.AutoResetEvent>, i <xref:System.Threading.ManualResetEvent>. Różnią się tylko w tym <xref:System.Threading.AutoResetEvent> zmian z sygnalizowane do unsignaled automatycznie dowolnym momencie aktywuje wątku. Z drugiej strony <xref:System.Threading.ManualResetEvent> umożliwia dowolną liczbę wątków można uaktywniać przez jego sygnalizowanego stanu i tylko przywróci unsignaled stanu, gdy jego <xref:System.Threading.EventWaitHandle.Reset%2A> metoda jest wywoływana.  
  
 Wątki, można wprowadzać oczekiwanie na zdarzenia przez wywołania metod oczekiwania, takich jak <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, lub <xref:System.Threading.WaitHandle.WaitAll%2A>. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> powoduje, że wątek poczekać, aż pojedyncze zdarzenie jest sygnalizowane, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> blokuje wątek, dopóki nie zasygnalizowane jednego lub wielu zdarzeń wskazanego, i <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> blokuje wątek, aż wszystkie zdarzenia wskazany zasygnalizowane. Zdarzenie jest sygnalizowane po jego <xref:System.Threading.EventWaitHandle.Set%2A> metoda jest wywoływana.  
  
 W poniższym przykładzie jest tworzony i uruchamiane przez wątek `Main` funkcji. Nowy wątek czeka na zdarzenia przy użyciu <xref:System.Threading.WaitHandle.WaitOne%2A> metody. Wątek jest zawieszony, aż zdarzenie stanie się zasygnalizowane przez wątek główny, który jest wykonywany `Main` funkcji. Gdy zdarzenie jest sygnalizowane, zwraca pomocniczego wątku. W tym przypadku ponieważ zdarzenie jest używana tylko jeden wątek aktywacji, albo <xref:System.Threading.AutoResetEvent> lub <xref:System.Threading.ManualResetEvent> klasy mogą być używane.  
  
```vb  
Imports System.Threading  
  
Module Module1  
    Dim autoEvent As AutoResetEvent  
  
    Sub DoWork()  
        Console.WriteLine("   worker thread started, now waiting on event...")  
        autoEvent.WaitOne()  
        Console.WriteLine("   worker thread reactivated, now exiting...")  
    End Sub  
  
    Sub Main()  
        autoEvent = New AutoResetEvent(False)  
  
        Console.WriteLine("main thread starting worker thread...")  
        Dim t As New Thread(AddressOf DoWork)  
        t.Start()  
  
        Console.WriteLine("main thread sleeping for 1 second...")  
        Thread.Sleep(1000)  
  
        Console.WriteLine("main thread signaling worker thread...")  
        autoEvent.Set()  
    End Sub  
End Module  
```  
  
## <a name="mutex-object"></a>Obiekt wzajemnego wykluczania mutex  
 A *mutex* jest podobny do monitorowania; zapobiega jednoczesne wykonywanie bloku kodu przez więcej niż jeden wątek jednocześnie. W rzeczywistości name "elementu mutex" jest skrócona forma termin "wzajemnie się wykluczają." W przeciwieństwie do monitorów jednak mutex może służyć do synchronizacji wątków między procesami. Mutex jest reprezentowany przez <xref:System.Threading.Mutex> klasy.  
  
 W przypadku używane na potrzeby synchronizacji między procesami, nosi nazwę obiektu mutex *o nazwie obiektu mutex* ponieważ jest do użycia w innej aplikacji, a w związku z tym nie może być współużytkowana przez zmienną globalną lub statyczną. Musisz nadać nazwę, aby obie aplikacje mają dostęp do tego samego obiektu mutex.  
  
 Mimo że mutex może służyć do synchronizacji wewnątrzprocesową wątku, przy użyciu <xref:System.Threading.Monitor> jest ogólnie metoda preferowana, ponieważ monitory zostały zaprojektowane specjalnie dla programu .NET Framework i w związku z tym lepiej wykorzystać możliwości zasobów. Z kolei <xref:System.Threading.Mutex> klasy jest otoką do konstrukcji systemu Win32. Mimo że jest bardziej wydajne niż monitor, mutex wymaga międzyoperacyjny przejścia, które są bardziej obliczeniowo kosztowne niż wymagane przez <xref:System.Threading.Monitor> klasy. Aby uzyskać przykład użycia elementu mutex, zobacz [muteksy](../../../../standard/threading/mutexes.md).  
  
## <a name="interlocked-class"></a>Interlocked — klasa  
 Można użyć metody <xref:System.Threading.Interlocked> klasy, aby uniknąć problemów, które mogą wystąpić, gdy wiele wątków próbują jednocześnie aktualizacji lub porównywania taką samą wartość. Metody tej klasy pozwalają bezpiecznie inkrementacja, dekrementacja, exchange i porównywania wartości z żadnym z wątków.  
  
## <a name="readerwriter-locks"></a>ReaderWriter blokad  
 W niektórych przypadkach można zablokować zasobu, tylko wtedy, gdy dane są zapisywane i umożliwić wielu klientów jednocześnie odczytu danych, gdy dane nie są aktualizowane. <xref:System.Threading.ReaderWriterLock> Klasy wymusza wyłącznego dostępu do zasobów, podczas gdy wątek jest modyfikowanie tych zasobów, ale pozwala niewyłączne dostępu podczas odczytywania zasobu. ReaderWriter blokady są przydatną alternatywą do blokady na wyłączność, które powodują innych wątków czekać, nawet gdy te wątki nie trzeba aktualizować dane.  
  
## <a name="deadlocks"></a>Zakleszczenia  
 Synchronizacji wątków jest bezcenne w aplikacjach wielowątkowych, ale zawsze istnieje zagrożenie tworzenia `deadlock`, gdy wiele wątków oczekują na siebie nawzajem i aplikacji, który jest dostarczany do zatrzymania. Zakleszczenie jest analogiczne do sytuacji, w której samochodów zostały zatrzymane w stop czterokierunkowego i każda osoba oczekuje na inne przejść. Unikanie zakleszczenia jest ważny; klucz jest starannego planowania. Można często prognozowania sytuacjach zakleszczenia na podstawie diagramów aplikacji wielowątkowych, przed rozpoczęciem kodowania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.WaitHandle.WaitOne%2A>  
 <xref:System.Threading.WaitHandle.WaitAny%2A>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.Thread.Join%2A>  
 <xref:System.Threading.Thread.Start%2A>  
 <xref:System.Threading.Thread.Sleep%2A>  
 <xref:System.Threading.Monitor>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.Monitor>  
 [SyncLock, instrukcja](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
 [Muteksy](../../../../standard/threading/mutexes.md)  
 [Operacje blokowane](../../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../../standard/threading/autoresetevent.md)  
 [Synchronizowanie danych na potrzeby wielowątkowości](../../../../standard/threading/synchronizing-data-for-multithreading.md)
