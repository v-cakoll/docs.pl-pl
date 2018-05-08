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
ms.openlocfilehash: c92725a43e43877488ff9ba93007530c794dd290
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Współdziałanie z innymi wzorcami asynchronicznymi i typami
.NET Framework 1.0 wprowadzone <xref:System.IAsyncResult> wzorzec, znanej także jako [asynchronicznego programowania modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), lub `Begin/End` wzorzec.  .NET Framework 2.0, dodać [oparty na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  Począwszy od programu .NET Framework 4, [opartego na zadaniach asynchronicznej wzorca (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) zastępuje zarówno APM, jak i EAP, ale umożliwia łatwe tworzenie procedury migracji z wcześniejszych wzorce.  
  
 W tym temacie:  
  
-   [Zadania i APM](#APM) ([z APM wybranie](#ApmToTap) lub [z NACIŚNIJ, aby APM](#TapToApm))  
  
-   [Zadania i EAP](#EAP)  
  
-   [Zadania i uchwyty oczekiwania](#WaitHandles) ([z uchwyty oczekiwania na wybranie](#WHToTap) lub [z NACIŚNIJ, aby uchwyty oczekiwania](#TapToWH))  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Zadania i Model programowania asynchronicznego (APM)  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a>Z APM wybranie  
 Ponieważ [asynchronicznego programowania modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) wzorzec jest bardzo strukturalnych, jest dość łatwe tworzenie otoki do udostępnienia implementacji APM jako implementację NACIŚNIJ. W rzeczywistości programu .NET Framework, począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], obejmuje procedury pomocnika w formie <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> przeciążenia metody w celu zapewnienia tłumaczenie.  
  
 Należy wziąć pod uwagę <xref:System.IO.Stream> klasy i jej <xref:System.IO.Stream.BeginRead%2A> i <xref:System.IO.Stream.EndRead%2A> metody, które reprezentują odpowiednikiem APM synchroniczne <xref:System.IO.Stream.Read%2A> metody:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Można użyć <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody do zaimplementowania otoka wybierz dla tej operacji w następujący sposób:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Ta implementacja jest podobny do następującego:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a>Z NACIŚNIJ, aby APM  
 Jeśli istniejącej infrastruktury oczekuje wzorzec APM, również należy podjąć implementacji NACIŚNIJ i użyć go, których można oczekiwać implementację APM.  Ponieważ zadania mogą być składane i <xref:System.Threading.Tasks.Task> klasa implementuje <xref:System.IAsyncResult>, funkcja prosta pomocnika służy w tym celu. W poniższym kodzie użyto rozszerzenie <xref:System.Threading.Tasks.Task%601> klasy, ale funkcja niemal identyczny nierodzajową zadań.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Rozważmy przypadek, w którym znajduje się następująca implementacja NACIŚNIJ:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 i chcesz zapewnić tej implementacji APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 W poniższym przykładzie pokazano jedną migrację do APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Zadania i oparty na zdarzeniach wzorca asynchronicznego (EAP)  
 Zawijanie [oparty na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementacja jest bardziej skomplikowane niż zawijania wzorzec APM, ponieważ wzorzec EAP ma więcej odmiany i struktura mniej niż wzorzec APM.  Aby zademonstrować, opakowuje następujący kod `DownloadStringAsync` metody.  `DownloadStringAsync` akceptuje identyfikator URI, zgłasza `DownloadProgressChanged` zdarzeń podczas pobierania w celu raportowania statystyk wiele w toku i zgłasza `DownloadStringCompleted` zdarzeń po jej zakończeniu.  Wynik końcowy jest ciąg znaków zawierający zawartość strony o określonym identyfikatorze URI.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a>Zadania i uchwyty oczekiwania  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a>Z uchwyty oczekiwania na wybranie  
 Mimo że uchwyty oczekiwania nie implementacji klienta wzorca asynchronicznego, zaawansowane deweloperzy mogą używać <xref:System.Threading.WaitHandle> klasy i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metodę asynchroniczną powiadomienia, gdy ustawiono dojścia oczekiwania.  Można zawijać <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> metodę umożliwiającą włączenie opartego na zadaniach zamiast żadnych synchroniczne oczekiwanie na dojście oczekiwania:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Przy użyciu tej metody można użyć istniejącego <xref:System.Threading.WaitHandle> implementacje metod asynchronicznych.  Na przykład, jeśli chcesz ograniczyć liczbę operacji asynchronicznych, które są wykonywane w dowolnym momencie w szczególności, możesz użyć semafora ( <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> obiektu).  Można ograniczyć do *N* liczby operacji, które są uruchamiane jednocześnie przez inicjowanie Licznik semafora do *N*, oczekiwanie na semafora dowolnej chwili, aby wykonać operację i zwalnianie Semafor po zakończeniu operacji:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Można również tworzyć asynchroniczne semafora nie bazuje na uchwyty oczekiwania, który działa całkowicie z zadaniami. Aby to zrobić, można użyć technik, takich jak omawiany w [wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) do tworzenia struktury danych, nad <xref:System.Threading.Tasks.Task>.  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a>Z NACIŚNIJ, aby uchwyty oczekiwania  
 Jak wcześniej wspomniano, <xref:System.Threading.Tasks.Task> klasa implementuje <xref:System.IAsyncResult>, i udostępnia tę implementację <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> właściwości, która zwraca dojście oczekiwania, który będzie można ustawić podczas <xref:System.Threading.Tasks.Task> zakończeniu.  Możesz uzyskać <xref:System.Threading.WaitHandle> dla <xref:System.Threading.Tasks.Task> w następujący sposób:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Implementowanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
