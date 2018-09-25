---
title: Współdziałanie z innymi wzorcami asynchronicznymi i typami
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05b53016712f75e45636979d77bfd27116ce8e14
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027716"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Współdziałanie z innymi wzorcami asynchronicznymi i typami
.NET Framework 1.0, wprowadzono <xref:System.IAsyncResult> wzorzec, znanych także jako [modelu programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), lub `Begin/End` wzorca.  .NET Framework 2.0, dodano [oparte na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  Począwszy od programu .NET Framework 4, [opartego na zadaniach asynchronicznej wzorca (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) zastępuje zarówno APM, jak i EAP, ale pozwala na łatwe tworzenie procedury migracji z wcześniejszych wzorców.  
  
 W tym temacie:  
  
-   [Zadania i APM](#APM) ([z APM do wzorca TAP](#ApmToTap) lub [z NACIŚNIJ, aby APM](#TapToApm))  
  
-   [Zadania i protokołu EAP](#EAP)  
  
-   [Zadania i uchwyty oczekiwania](#WaitHandles) ([z uchwytami oczekiwania do wzorca TAP](#WHToTap) lub [z NACIŚNIJ, aby uchwyty oczekiwania](#TapToWH))  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Zadania i Model programowania asynchronicznego (APM)  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a>Z APM do wzorca TAP  
 Ponieważ [modelu programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) wzorzec jest bardzo ze strukturą, tworzenie otoki, aby udostępnić implementację APM jako implementacja wzorca TAP jest bardzo łatwe. W rzeczywistości, .NET Framework, począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], obejmuje procedury pomocnika w formie <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> przeciążenia metody, aby zapewnić to tłumaczenie.  
  
 Należy wziąć pod uwagę <xref:System.IO.Stream> klasy i jego <xref:System.IO.Stream.BeginRead%2A> i <xref:System.IO.Stream.EndRead%2A> metody, które reprezentują synchronicznego odpowiednika APM <xref:System.IO.Stream.Read%2A> metody:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Możesz użyć <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody do zaimplementowania wzorca TAP otokę dla tej operacji w następujący sposób:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Ta implementacja jest podobna do następującej:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a>Z NACIŚNIJ, aby APM  
 Jeśli istniejącej infrastruktury oczekuje wzorzec APM, również należy podjąć implementacja wzorca TAP i używać go, których oczekuje się implementację APM.  Ponieważ zadania mogą być składane i <xref:System.Threading.Tasks.Task> klasy implementuje <xref:System.IAsyncResult>, można użyć funkcji pomocnika proste, w tym celu. W poniższym kodzie użyto rozszerzenie <xref:System.Threading.Tasks.Task%601> klasy, ale można użyć funkcji niemal identyczne dla zadań innych niż ogólne.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Rozważmy przypadek, w którym masz następujące implementacja wzorca TAP:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 i chcesz udostępnić tę implementację APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 Poniższy przykład przedstawia jedną migrację do APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Zadania i oparte na zdarzeniach wzorca asynchronicznego (EAP)  
 Zawijanie [oparte na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementacja jest bardziej skomplikowane niż zawijania wzorzec APM, ponieważ wzorzec EAP ma więcej zmian i struktury, mniej niż wzorzec APM.  Aby zademonstrować, poniższy kod jest zawijany `DownloadStringAsync` metody.  `DownloadStringAsync` akceptuje identyfikator URI, zgłasza `DownloadProgressChanged` zdarzenia podczas pobierania, aby wiele statystyki sporządzić raport na temat postępu i zgłasza `DownloadStringCompleted` zdarzenie, gdy wszystko będzie gotowe.  Wynik końcowy to ciąg, który zawiera zawartość strony o określonym identyfikatorze URI.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a>Zadania i uchwytami oczekiwania  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a>Z uchwytami oczekiwania do wzorca TAP  
 Mimo że uchwyty oczekiwania na nie implementuje wzorca asynchronicznego, zaawansowane deweloperzy mogą użyć <xref:System.Threading.WaitHandle> klasy i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metodę dla powiadomień asynchronicznych, gdy ustawiono dojście oczekiwania.  Można opakować <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> metodę, aby włączyć zadanie alternatywa wszelkie synchroniczne oczekiwanie na dojście oczekiwania:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Przy użyciu tej metody można użyć istniejącej <xref:System.Threading.WaitHandle> implementacje metod asynchronicznych.  Na przykład, jeśli chcesz ograniczyć liczbę operacji asynchronicznych, które są wykonywane w danym momencie, możesz użyć semafor ( <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> obiektu).  Możesz ograniczyć do *N* liczby operacji działać współbieżnie przez inicjowania semafora count *N*, trwa oczekiwanie na semafora w dowolnym momencie, którą chcesz wykonać operację i zwolnieniem Semafor po zakończeniu operacji:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Można także utworzyć semafora asynchronicznego, nie zależą od uchwytami oczekiwania, która działa w całkowicie z zadaniami. Aby to zrobić, należy użyć technik, takich jak omawiany w [wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) do tworzenia struktur danych, w górnej części <xref:System.Threading.Tasks.Task>.  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a>Z NACIŚNIJ, aby uchwyty oczekiwania  
 Jak wcześniej wspomniano, <xref:System.Threading.Tasks.Task> klasy implementuje <xref:System.IAsyncResult>, i udostępnia tę implementację <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> właściwość, która zwraca dojście oczekiwania, który będzie można ustawić podczas <xref:System.Threading.Tasks.Task> kończy.  Możesz uzyskać <xref:System.Threading.WaitHandle> dla <xref:System.Threading.Tasks.Task> w następujący sposób:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Zobacz także

- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
- [Implementowanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
- [Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
