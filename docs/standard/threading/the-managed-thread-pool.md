---
title: Zarządzana pula wątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- thread pooling [.NET Framework]
- thread pools [.NET Framework]
- threading [.NET Framework], thread pool
- threading [.NET Framework], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3894229ff5561e50d42a36f576a89ee7bf01c067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="the-managed-thread-pool"></a>Zarządzana pula wątków
<xref:System.Threading.ThreadPool> Klasa udostępnia aplikacji dla puli wątków roboczych, które są zarządzane przez system, umożliwiając skoncentrować się na zadania aplikacji, a nie wątku zarządzania. Jeśli masz krótkie zadania, które wymagają przetwarzania w tle zarządzana Pula wątków to prosty sposób korzystać z wielu wątków. Na przykład, począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] można utworzyć <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiekty, do których wykonywania zadań asynchronicznych w wątku puli wątków.  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], znacznie zwiększona przepływność puli wątków trzy kluczowe, które zostały zidentyfikowane jako wąskich gardeł w poprzednich wersjach [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: Kolejkowanie zadań, wysyłki wątków z puli wątków i podczas wysyłania operacji We/Wy wątki ukończenia. Aby używać tej funkcji, należy docelowy aplikacji [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] lub nowszym.  
  
 Zadania w tle wchodzących w interakcję z interfejsem użytkownika, .NET Framework w wersji 2.0 zawiera także <xref:System.ComponentModel.BackgroundWorker> klasy, która komunikuje się za pomocą zdarzenia wywoływane w wątku interfejsu użytkownika.  
  
 .NET Framework używa wątków z puli wątków dla wielu celów, w tym asynchroniczne zakończenia We/Wy, wywołania zwrotne czasomierza, w zarejestrowany oczekiwania operacji, wywołań metod asynchronicznych przy użyciu delegatów, i <xref:System.Net> połączeń gniazda.  
  
## <a name="when-not-to-use-thread-pool-threads"></a>Kiedy nie należy używać wątków z puli wątków  
 Istnieje kilka scenariuszy, w których jest odpowiednie do tworzenia i zarządzania własnych wątków zamiast wątków z puli wątków:  
  
-   Wymagane jest wątku pierwszego planu.  
  
-   Wymagane jest wątku określonego priorytetem.  
  
-   Masz zadań, które powodują wątków, które mają być blokowane przez dłuższy czas. Pula wątków ma maksymalną liczbę wątków, więc duża liczba zablokowanych wątków z puli wątków może uniemożliwić uruchomienie zadania.  
  
-   Należy umieścić wątków w jednowątkowym apartamencie. Wszystkie <xref:System.Threading.ThreadPool> wątki są wielowątkowe apartamentu.  
  
-   Należy mieć skojarzony z wątkiem stabilna tożsamość lub przeznaczyć wątku zadania.  
  
## <a name="thread-pool-characteristics"></a>Właściwości puli wątków  
 Wątków z puli wątków są wątki w tle. Zobacz [pierwszego planu i tła wątki](../../../docs/standard/threading/foreground-and-background-threads.md). Każdy wątek używa domyślny rozmiar stosu, działa w domyślny priorytet i znajduje się w apartamencie wielowątkowych.  
  
 Brak puli tylko jeden wątek na proces.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Wyjątki w wątku puli wątków  
 Nieobsługiwane wyjątki w wątku puli wątków zakończenie procesu. Istnieją trzy wyjątki od tej reguły:  
  
-   A <xref:System.Threading.ThreadAbortException> jest zgłaszany w wątku puli wątków, ponieważ <xref:System.Threading.Thread.Abort%2A> została wywołana.  
  
-   <xref:System.AppDomainUnloadedException> Jest zgłaszany w wątku puli wątków, ponieważ Trwa zwalnianie domen aplikacji.  
  
-   Środowisko uruchomieniowe języka wspólnego lub procesu hosta kończy wątku.  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  W wersji systemu .NET Framework 1.0 i 1.1 środowisko uruchomieniowe języka wspólnego dyskretnie traps nieobsługiwanych wyjątków w wątku puli wątków. Może to doprowadzić do uszkodzenia aplikacji i może spowodować zawieszenie, aplikacje, które mogą być bardzo trudne do debugowania.  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Maksymalna liczba wątków z puli wątków  
 Liczba operacji, które mogą być umieszczone w kolejce do puli wątków jest ograniczona tylko przez ilość dostępnej pamięci; jednak puli wątków ogranicza liczbę wątków, które mogą być jednocześnie aktywne w procesie. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], domyślny rozmiar puli wątków procesu zależy od wielu czynników, takich jak rozmiar wirtualnej przestrzeni adresowej. Proces może wywołać <xref:System.Threading.ThreadPool.GetMaxThreads%2A> metodę, aby określić liczbę wątków.  
  
 Maksymalna liczba wątków można kontrolować przy użyciu <xref:System.Threading.ThreadPool.GetMaxThreads%2A> i <xref:System.Threading.ThreadPool.SetMaxThreads%2A> metody.  
  
> [!NOTE]
>  W wersji systemu .NET Framework 1.0 i 1.1 rozmiar puli wątków nie można ustawić z kodu zarządzanego. Kod, który obsługuje środowisko uruchomieniowe języka wspólnego można ustawić przy użyciu rozmiaru `CorSetMaxThreads`zdefiniowanej w mscoree.h.  
  
### <a name="thread-pool-minimums"></a>Minimów puli wątków  
 Puli wątków zapewnia nowy wątków roboczych lub wątków zakończenia We/Wy na żądanie, dopóki nie osiągnie określony co najmniej dla każdej kategorii. Można użyć <xref:System.Threading.ThreadPool.GetMinThreads%2A> metodę, aby uzyskać te wartości minimalnej.  
  
> [!NOTE]
>  Jeśli żądanie jest niska, rzeczywista liczba wątków z puli wątków można spadnie poniżej wartości minimalnej.  
  
 Po osiągnięciu minimum puli wątków można utworzyć dodatkowe wątki lub zaczekaj na zakończenie niektórych zadań. Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], pulą wątków tworzy i niszczy wątków roboczych w celu zoptymalizowania przepustowości, która jest zdefiniowana jako liczba zadań, kończące się na jednostkę czasu. Zbyt mało wątków może nie mieć optymalne wykorzystanie dostępnych zasobów, natomiast zbyt wiele wątków można zwiększyć rywalizacji.  
  
> [!CAUTION]
>  Można użyć <xref:System.Threading.ThreadPool.SetMinThreads%2A> metodę, aby zwiększyć minimalna liczba wątków bezczynności. Jednak niepotrzebnie zwiększenie tych wartości może spowodować problemy z wydajnością. Jeśli zbyt wiele zadań jest uruchomiona w tym samym czasie, wszystkie z nich wydaje się powoli. W większości przypadków puli wątków będą działać lepiej z własną algorytmu alokacji wątków.  
  
## <a name="skipping-security-checks"></a>Pomijanie sprawdzania zabezpieczeń  
 Udostępnia również puli wątków <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> i <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody. Użyj tych metod, tylko wtedy, gdy masz pewność, że stos wywołującego nie ma znaczenia kontroli zabezpieczeń wykonywane podczas wykonywania zadań w kolejce. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> zarówno przechwytywania wywołującego stosu, w którym jest scalany stosu wątku puli wątków, po rozpoczęciu wątku do wykonania zadania. Jeśli wymagana jest kontrola zabezpieczeń, cały stos musi być zaznaczone. Chociaż kontroli bezpieczeństwa, ma także na wydajność.  
  
## <a name="using-the-thread-pool"></a>Przy użyciu puli wątków  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], najłatwiejszym sposobem na korzystanie z puli wątków jest użycie [zadań biblioteki równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md). Domyślnie równoległych biblioteki typów, takich jak <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> umożliwia uruchamianie zadań wątków z puli wątków. Umożliwia także puli wątków wywołując <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> z kodu zarządzanego (lub `CorQueueUserWorkItem` z kodem niezarządzanym) i przekazywanie <xref:System.Threading.WaitCallback> delegata reprezentującego metodę, która wykonuje zadanie. Innym sposobem użycia puli wątków jest do kolejki elementów pracy, które są powiązane z operacją oczekiwania przy użyciu <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> — metoda i przekazywanie <xref:System.Threading.WaitHandle> , gdy sygnalizowane lub gdy został przekroczony, wywołuje metodę reprezentowany przez <xref:System.Threading.WaitOrTimerCallback> delegowanie. Wątków z puli wątków są używane do wywołania metody wywołania zwrotnego.  
  
## <a name="threadpool-examples"></a>Przykłady puli wątków  
 Przykłady kodu w tej sekcji prezentacja puli wątków za pomocą <xref:System.Threading.Tasks.Task> klasy, <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> metody i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody.  
  
-   [Wykonywanie zadania asynchronicznego z Biblioteka zadań równoległych](#TaskParallelLibrary)  
  
-   [Wykonywanie kodu asynchronicznie z QueueUserWorkItem](#ExecuteCodeWithQUWI)  
  
-   [Dostarczająca dane zadania dla QueueUserWorkItem](#TaskDataForQUWI)  
  
-   [Przy użyciu funkcji RegisterWaitForSingleObject](#RegisterWaitForSingleObject)  
  
<a name="TaskParallelLibrary"></a>   
### <a name="executing-asynchronous-tasks-with-the-task-parallel-library"></a>Wykonywanie zadania asynchronicznego z Biblioteka zadań równoległych  
 Poniższy przykład przedstawia sposób tworzenia i używania <xref:System.Threading.Tasks.Task> obiektu przez wywołanie metody <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody. Na przykład, który używa <xref:System.Threading.Tasks.Task%601> klasy zwracanie wartości z zadanie asynchroniczne, zobacz [porady: zwracanie wartości z zadania](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).  
  
 [!code-csharp[System.Threading.Tasks.Task#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.task/cs/startnew.cs#01)]
 [!code-vb[System.Threading.Tasks.Task#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.task/vb/startnew.vb#01)]  
  
<a name="ExecuteCodeWithQUWI"></a>   
### <a name="executing-code-asynchronously-with-queueuserworkitem"></a>Wykonywanie kodu asynchronicznie z QueueUserWorkItem  
 Poniższy przykład tworzy kolejki bardzo proste zadania, reprezentowany przez `ThreadProc` — metoda, za pomocą <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metody.  
  
 [!code-cpp[Conceptual.ThreadPool#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.ThreadPool#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source1.cs#1)]
 [!code-vb[Conceptual.ThreadPool#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source1.vb#1)]  
  
<a name="TaskDataForQUWI"></a>   
### <a name="supplying-task-data-for-queueuserworkitem"></a>Dostarczająca dane zadania dla QueueUserWorkItem  
 Poniższy przykład kodu wykorzystuje <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metodę w kolejce zadania i dostarczają dane do zadania.  
  
 [!code-cpp[Conceptual.ThreadPool#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.ThreadPool#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source2.cs#2)]
 [!code-vb[Conceptual.ThreadPool#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source2.vb#2)]  
  
<a name="RegisterWaitForSingleObject"></a>   
### <a name="using-registerwaitforsingleobject"></a>Przy użyciu funkcji RegisterWaitForSingleObject  
 W poniższym przykładzie pokazano kilka wątków funkcji.  
  
-   Usługi kolejkowania wiadomości zadań do wykonania przez <xref:System.Threading.ThreadPool> wątków, z <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> metody.  
  
-   Sygnalizowanie zadań do wykonania, z <xref:System.Threading.AutoResetEvent>. Zobacz [EventWaitHandle, autoresetevent —, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
-   Obsługa zarówno limity czasu i sygnały z <xref:System.Threading.WaitOrTimerCallback> delegowanie.  
  
-   Anulowanie zadania w kolejce z <xref:System.Threading.RegisteredWaitHandle>.  
  
 [!code-cpp[Conceptual.ThreadPool#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.ThreadPool#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source3.cs#3)]
 [!code-vb[Conceptual.ThreadPool#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.Tasks.Task>  
 <xref:System.Threading.Tasks.Task%601>  
 [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Instrukcje: zwracanie wartości z zadania](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)  
 [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [Czasomierze](../../../docs/standard/threading/timers.md)
