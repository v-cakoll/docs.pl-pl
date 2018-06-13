---
title: Synchronizacja wątku (C#)
ms.date: 07/20/2015
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
ms.openlocfilehash: 138b94ef8ae5fc54e42277127f9b22f88803457f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338614"
---
# <a name="thread-synchronization-c"></a>Synchronizacja wątku (C#)
W poniższych sekcjach opisano funkcje i klasy, które mogą służyć do synchronizowania dostęp do zasobów w aplikacjach wielowątkowych.  
  
 Jedną z korzyści wynikające ze stosowania wiele wątków w aplikacji jest asynchronicznie wykonuje każdy wątek. Dla aplikacji systemu Windows dzięki temu czasochłonnych zadań wykonywanych w tle podczas okna aplikacji a formanty pozostają reakcji. Dla serwera aplikacji wielowątkowość udostępnia możliwość obsługi każdego żądania przychodzącego z innego wątku. W przeciwnym razie wartość każdego nowego żądania nie będą uzyskać obsługiwane, dopóki nie zostały całkowicie spełnione poprzedniego żądania.  
  
 Jednak charakter asynchronicznych wątków oznacza, że dostęp do zasobów, takich jak dojścia do plików, połączeń sieciowych i pamięci musi być skoordynowany sposób. W przeciwnym razie dwie lub więcej wątków można uzyskać dostępu do tego samego zasobu w tym samym czasie, każdy zna drugiego akcje. Wynik jest uszkodzenia nieprzewidywalne danych.  
  
 Dla proste operacje na typy całkowite danych liczbowych, synchronizacja wątków można wykonywać z członkami <xref:System.Threading.Interlocked> klasy. Dla wszystkich innych danych typów i zasobów z systemem innym niż wielowątkowość wielowątkowość można bezpiecznie wykonać tylko przy użyciu konstrukcji w tym temacie.  
  
 Aby uzyskać ogólne informacje na temat programów wielowątkowych w zobacz:  
  
-   [Zarządzana wątkowość — podstawy](../../../../standard/threading/managed-threading-basics.md)  
  
-   [Używanie wątków i wątkowości](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Zarządzana wątkowość — najlepsze rozwiązania](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a>Lock — słowo kluczowe  
 C# `lock` instrukcja może być używana przez inne wątki aby upewnić się, że bloku kodu jest uruchamiane w celu ukończenia bez przeszkód. Jest to osiągane przez uzyskanie blokady wzajemnego wykluczeń dla danego obiektu w czasie trwania blok kodu.  
  
 A `lock` instrukcji jest podawana jako argument obiektu i następuje blok kodu, który ma zostać wykonana tylko jednego wątku naraz. Na przykład:  
  
```csharp  
public class TestThreading  
{  
    private System.Object lockThis = new System.Object();  
  
    public void Process()  
    {  
  
        lock (lockThis)  
        {  
            // Access thread-sensitive resources.  
        }  
    }  
  
}  
```  
  
 Argument dostarczony do `lock` — słowo kluczowe musi być obiektem typu odwołania i służy do definiowania zakresu blokady. W powyższym przykładzie zakres blokady jest ograniczony do tej funkcji, ponieważ nie odwołania do obiektu `lockThis` istnieje poza funkcją. Odniesienie został znaleziony, może rozszerzyć zakres blokady do tego obiektu. Mówiąc ściślej dostarczony obiekt jest używany wyłącznie do unikatowego identyfikowania udostępnianego między wiele wątków, więc można instancji klasy dowolnego zasobu. W praktyce jednak ten obiekt zazwyczaj reprezentuje zasobów, dla których wątku synchronizacji jest konieczne. Na przykład w przypadku obiektu kontenera ma być używany przez wiele wątków, następnie kontenera mogą zostać przekazane do zablokowania i blok kodu zsynchronizowane po blokady może uzyskać dostępu do kontenera. Tak długo, jak inne wątki blokuje na tym samym zawierają przed uzyskaniem dostępu do, a następnie bezpiecznie jest zsynchronizowany dostęp do obiektu.  
  
 Ogólnie rzecz biorąc, zaleca się unikać blokowania na `public` typu, lub do obiektów poza kontrolą aplikacji. Na przykład `lock(this)` może być problemem, jeśli wystąpienie jest dostępny publicznie, ponieważ kod poza kontrolą może zablokować obiektu również. To może utworzyć zakleszczenie sytuacji, gdy dwa lub więcej wątków oczekiwania na zwolnienie tego samego obiektu. Blokowanie typu publicznego danych, w przeciwieństwie do obiektu może spowodować problemy z tego samego powodu. Blokowanie na ciągi literału jest szczególnie ryzykowne, ponieważ ciągi literału *interned* przez środowisko uruchomieniowe języka wspólnego (CLR). Oznacza to, że istnieje jedno wystąpienie dowolnego ciągu literału dla całego programu, dokładnie tego samego obiektu reprezentuje literał we wszystkich uruchomionych domen aplikacji na wszystkie wątki. W związku z tym zablokować ciągu z tej samej zawartości dowolne miejsce w blokad procesu aplikacji wszystkich wystąpień tego ciągu w aplikacji. W związku z tym najlepiej do blokowania nie jest interned członkiem prywatne lub chronione. Niektóre klasy Podaj członków specjalnie z myślą o blokowania. <xref:System.Array> Typu, na przykład zawiera <xref:System.Array.SyncRoot%2A>. Podaj wiele typów kolekcji `SyncRoot` również elementu członkowskiego.  
  
 Aby uzyskać więcej informacji na temat `lock` instrukcji, zobacz następujące tematy:  
  
-   [lock, instrukcja](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a>Monitory  
 Podobnie jak `lock` — słowo kluczowe, monitory zapobiec bloki kodu z jednoczesne wykonywanie przez wiele wątków. <xref:System.Threading.Monitor.Enter%2A> Metoda pozwala jeden i tylko jeden wątek przejść do następujących instrukcji; wątki są zablokowane do czasu wykonywania wywołań wątku <xref:System.Threading.Monitor.Exit%2A>. Jest to tak samo jak przy użyciu `lock` — słowo kluczowe. Na przykład:  
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 Jest to równoważne:  
  
```csharp  
System.Object obj = (System.Object)x;  
System.Threading.Monitor.Enter(obj);  
try  
{  
    DoSomething();  
}  
finally  
{  
    System.Threading.Monitor.Exit(obj);  
}  
```  
  
 Przy użyciu `lock` — słowo kluczowe jest zazwyczaj preferowane przy użyciu <xref:System.Threading.Monitor> bezpośrednio, klasa, zarówno ponieważ `lock` jest bardziej zwięzły i dlatego `lock` temu zwolnienie monitora źródłowego, nawet jeśli chroniony kod powoduje wyjątek. Jest to realizowane przy użyciu `finally` — słowo kluczowe, który wykonuje jego blok kodu skojarzone niezależnie od tego, czy jest zgłaszany wyjątek.  
  
## <a name="synchronization-events-and-wait-handles"></a>Zdarzenia synchronizacji i uchwyty oczekiwania  
 Przy użyciu blokady lub monitor jest przydatne w przypadku uniemożliwia jednoczesne wykonywanie wątku wrażliwych bloki kodu, ale te konstrukcji nie zezwalaj na jeden wątek, aby komunikować się zdarzenia do innego. Wymaga to *zdarzenia synchronizacji*, które są obiektów, które mają jeden z dwóch stanów sygnałowego i cofanie sygnałowego, który może służyć do aktywowania i wstrzymać wątków. Wątki może zostać zawieszone przez wykonywane oczekiwania na zdarzenie synchronizacji unsignaled i można aktywować, zmieniając stanu zdarzenia do sygnalizowane. Próba oczekiwania na zdarzenie, które zostało już zasygnalizowane przez wątek wątek kontynuuje wykonywanie bez opóźnień.  
  
 Istnieją dwa rodzaje zdarzeń synchronizacji: <xref:System.Threading.AutoResetEvent>, i <xref:System.Threading.ManualResetEvent>. Różnią się tylko w tym <xref:System.Threading.AutoResetEvent> zmiany z sygnalizowane do unsignaled automatycznie każdy razem aktywuje wątku. Z drugiej strony <xref:System.Threading.ManualResetEvent> umożliwia dowolną liczbę wątków, aby być aktywowany przez stanu sygnałowego i tylko powróci do unsignaled jeśli jego <xref:System.Threading.EventWaitHandle.Reset%2A> metoda jest wywoływana.  
  
 Wątków jest możliwe oczekiwanie na zdarzenia przez wywołanie metody oczekiwania, takich jak <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, lub <xref:System.Threading.WaitHandle.WaitAll%2A>. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> powoduje, że wątek poczekać, aż sygnalizowane staje się pojedyncze zdarzenie, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> blokuje wątku, dopóki co najmniej jednego zdarzenia wskazanych stają się sygnalizuje, i <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> blokuje wątek, dopóki wszystkie zdarzenia wskazanych stają się sygnalizowane. Zdarzenie jest sygnalizowane po jego <xref:System.Threading.EventWaitHandle.Set%2A> metoda jest wywoływana.  
  
 W poniższym przykładzie jest tworzony i uruchomione przez wątek `Main` funkcji. Nowego wątku oczekiwania na zdarzenie przy użyciu <xref:System.Threading.WaitHandle.WaitOne%2A> metody. Wątek jest zawieszony aż do zdarzenia staje się zgłoszony przez podstawowy wątku, który jest wykonywany `Main` funkcji. Gdy zdarzenie jest sygnalizowane, zwraca wątek pomocniczy. W takim przypadku ponieważ zdarzenie jest używana tylko jeden wątek aktywacji, albo <xref:System.Threading.AutoResetEvent> lub <xref:System.Threading.ManualResetEvent> klasy może być używane.  
  
```csharp  
using System;  
using System.Threading;  
  
class ThreadingExample  
{  
    static AutoResetEvent autoEvent;  
  
    static void DoWork()  
    {  
        Console.WriteLine("   worker thread started, now waiting on event...");  
        autoEvent.WaitOne();  
        Console.WriteLine("   worker thread reactivated, now exiting...");  
    }  
  
    static void Main()  
    {  
        autoEvent = new AutoResetEvent(false);  
  
        Console.WriteLine("main thread starting worker thread...");  
        Thread t = new Thread(DoWork);  
        t.Start();  
  
        Console.WriteLine("main thread sleeping for 1 second...");  
        Thread.Sleep(1000);  
  
        Console.WriteLine("main thread signaling worker thread...");  
        autoEvent.Set();  
    }  
}  
```  
  
## <a name="mutex-object"></a>Obiekt mutex  
 A *obiektu mutex* jest podobny do monitora; uniemożliwia jednoczesne wykonywanie bloku kodu przez więcej niż jeden wątek na raz. W rzeczywistości nazwy "mutex" jest skrócona forma termin "wykluczają się wzajemnie." W przeciwieństwie do monitorów jednak obiektu mutex umożliwia synchronizację wątków procesów. Obiektu mutex jest reprezentowana przez <xref:System.Threading.Mutex> klasy.  
  
 W przypadku synchronizacji między procesami obiektu mutex jest nazywany *nazwanego obiektu mutex* ponieważ jest do użycia w innej aplikacji, i dlatego nie można udostępnić za pomocą zmiennej globalnej lub statycznej. Musi ona zawierać nazwę, aby obie aplikacje mają dostęp do tego samego obiektu mutex.  
  
 Chociaż wątek wewnątrz procesu synchronizacji można użyć obiektu mutex, przy użyciu <xref:System.Threading.Monitor> jest zazwyczaj preferowana, ponieważ monitory zostały zaprojektowane specjalnie dla programu .NET Framework i w związku z tym należy lepszego wykorzystania zasobów. Z kolei <xref:System.Threading.Mutex> klasy jest otoką elementu do konstrukcji Win32. Mimo że jest bardziej efektywne niż monitor, obiektu mutex wymaga międzyoperacyjnego przejścia, które są w praktyce bardziej kosztowne niż wymagane przez <xref:System.Threading.Monitor> klasy. Na przykład za pomocą obiektu mutex, zobacz [muteksy](../../../../standard/threading/mutexes.md).  
  
## <a name="interlocked-class"></a>Interlocked — klasa  
 Można użyć metody <xref:System.Threading.Interlocked> klasy, aby uniknąć problemów, które mogą wystąpić, gdy wiele wątków próbują jednocześnie aktualizacji lub porównywania taką samą wartość. Metody tej klasy pozwala bezpiecznie przyrostu, zmniejszyć programu exchange i porównuje wartości z dowolnego wątku.  
  
## <a name="readerwriter-locks"></a>ReaderWriter blokad  
 W niektórych przypadkach można zablokować zasobu tylko wtedy, gdy dane są zapisywane i zezwolenie na wielu klientów jednocześnie odczytać danych, gdy dane nie są aktualizowane. <xref:System.Threading.ReaderWriterLock> Klasy wymusza wyłącznego dostępu do zasobu, gdy wątek modyfikuje zasobu, ale pozwala dostępu otwarty podczas odczytu zasobu. ReaderWriter blokady są przydatne alternatywą dla blokady na wyłączność, które powodują inne wątki oczekiwania, nawet gdy te wątków nie trzeba aktualizacji danych.  
  
## <a name="deadlocks"></a>Zakleszczenie  
 Synchronizacja wątku jest nieocenione w aplikacjach wielowątkowych, ale zawsze zagrożenia tworzenia `deadlock`, gdzie wiele wątków oczekuje na siebie i pochodzi aplikacji do zatrzymania. Zakleszczenie jest analogiczna do sytuacji, w której samochodów zostały zatrzymane w ograniczniku czterech sposób i czeka na innych przejść każda osoba. Unikanie zakleszczenie jest ważne; klucz jest dokładne planowanie. Zakleszczenie sytuacjach można często prognozowania przez tworzenie diagramów aplikacje wielowątkowe, przed rozpoczęciem kodowania.  
  
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
 [Aplikacje wielowątkowe (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [lock, instrukcja](../../../../csharp/language-reference/keywords/lock-statement.md)  
 [Muteksy](../../../../standard/threading/mutexes.md)  
 [Operacje blokowane](../../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../../standard/threading/autoresetevent.md)  
 [Synchronizowanie danych na potrzeby wielowątkowości](../../../../standard/threading/synchronizing-data-for-multithreading.md)
