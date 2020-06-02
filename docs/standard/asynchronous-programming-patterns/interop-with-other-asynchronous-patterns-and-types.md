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
ms.openlocfilehash: fe5d8321a62b67a54dc09507e8fd86ee8d5cf74d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276559"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Współdziałanie z innymi wzorcami asynchronicznymi i typami
W .NET Framework 1,0 został wprowadzony <xref:System.IAsyncResult> wzorzec, w zależności od [modelu programowania ASYNCHRONICZNEGO (APM)](asynchronous-programming-model-apm.md)lub `Begin/End` wzorzec.  .NET Framework 2,0 został dodany [wzorzec asynchroniczny oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md).  Począwszy od .NET Framework 4, [wzorzec asynchroniczny oparty na zadaniach (TAP)](task-based-asynchronous-pattern-tap.md) zastępuje zarówno APM, jak i EAP, ale umożliwia łatwe tworzenie procedur migracji z wcześniejszych wzorców.  
  
 W tym temacie:  
  
- [Zadania i APM](#APM) ([z poziomu APM do TAP](#ApmToTap) lub [z TAP do APM](#TapToApm))  
  
- [Zadania i protokół EAP](#EAP)  
  
- [Zadania i uchwyty oczekiwania](#WaitHandles) ([od dojścia oczekiwania do naciśnięcia](#WHToTap) lub [od naciśnij do uchwytów](#TapToWH)oczekiwania)  
  
<a name="APM"></a>
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Zadania i model programowania asynchronicznego (APM)  
  
<a name="ApmToTap"></a>
### <a name="from-apm-to-tap"></a>Z usługi APM do NACIŚNIĘCIa  
 Ze względu na to, że wzorzec [modelu programowania asynchronicznego (APM)](asynchronous-programming-model-apm.md) jest bardzo strukturalny, można łatwo utworzyć otokę, aby uwidocznić implementację APM jako implementację TAP. W rzeczywistości .NET Framework, zaczynając od .NET Framework 4, zawiera procedury pomocnika w postaci <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> przeciążeń metody, aby zapewnić to tłumaczenie.  
  
 Rozważmy <xref:System.IO.Stream> klasę i jej <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> metody, które reprezentują odpowiedniki APM do metody synchronicznej <xref:System.IO.Stream.Read%2A> :  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Można użyć <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody do zaimplementowania otoki TAP dla tej operacji w następujący sposób:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Ta implementacja jest podobna do następującej:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>
### <a name="from-tap-to-apm"></a>Od TAP do APM  
 Jeśli istniejąca infrastruktura oczekuje wzorca APM, należy również wykonać implementację TAP i użyć jej, w której oczekiwana jest implementacja APM.  Ponieważ zadania mogą być złożone, a <xref:System.Threading.Tasks.Task> Klasa implementuje <xref:System.IAsyncResult> , można użyć prostej funkcji pomocnika, aby to zrobić. Poniższy kod używa rozszerzenia <xref:System.Threading.Tasks.Task%601> klasy, ale można użyć prawie identycznej funkcji dla zadań innych niż ogólne.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Teraz Rozważmy przypadek, w którym masz następującą implementację TAP:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 i chcesz zapewnić tę implementację APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 Poniższy przykład ilustruje jedną migrację do APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Zadania i wzorzec asynchroniczny oparty na zdarzeniach (EAP)  
 Otoka implementacji [wzorca asynchronicznego opartego na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md) jest większa niż otoka wzorca APM, ponieważ wzorzec protokołu EAP ma większą odmianę i mniejszą strukturę niż wzorzec APM.  Aby przedstawić, poniższy kod otacza `DownloadStringAsync` metodę.  `DownloadStringAsync`akceptuje identyfikator URI, podnosi `DownloadProgressChanged` zdarzenie podczas pobierania, aby raportować wiele statystyk w toku i wywołuje `DownloadStringCompleted` zdarzenie po jego zakończeniu.  Końcowy wynik jest ciągiem zawierającym zawartość strony o określonym identyfikatorze URI.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>
## <a name="tasks-and-wait-handles"></a>Zadania i uchwyty oczekiwania  
  
<a name="WHToTap"></a>
### <a name="from-wait-handles-to-tap"></a>Z uchwytów oczekiwania na NACIŚNIĘCIe  
 Chociaż uchwyty oczekiwania nie implementują wzorca asynchronicznego, zaawansowani deweloperzy mogą używać <xref:System.Threading.WaitHandle> klasy i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody dla powiadomień asynchronicznych, gdy jest ustawiona obsługa oczekiwania.  Możesz otoczyć metodę, <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> Aby włączyć alternatywną dla wszystkich zadań w przypadku oczekiwania synchronicznego na dojście oczekiwania:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Za pomocą tej metody można używać istniejących <xref:System.Threading.WaitHandle> implementacji w metodach asynchronicznych.  Na przykład jeśli chcesz ograniczyć liczbę operacji asynchronicznych wykonywanych w dowolnym określonym czasie, możesz użyć semafora ( <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> obiektu).  Można ograniczyć do *n* liczbę operacji, które są uruchamiane współbieżnie, inicjując liczbę semaforów na *n*, czekając na semafor w dowolnym momencie, gdy chcesz wykonać operację, i zwolnij semafor po wykonaniu operacji:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Można również utworzyć semafor asynchroniczny, który nie bazuje na dojściach oczekiwania i zamiast tego działa całkowicie z zadaniami. Aby to zrobić, można użyć technik takich jak omówione w temacie [zużywanie wzorca asynchronicznego opartego na zadaniach](consuming-the-task-based-asynchronous-pattern.md) w celu kompilowania struktur danych w oparciu o <xref:System.Threading.Tasks.Task> .  
  
<a name="TapToWH"></a>
### <a name="from-tap-to-wait-handles"></a>Od NACIŚNIĘCIa do uchwytów oczekiwania  
 Jak wspomniano wcześniej, <xref:System.Threading.Tasks.Task> Klasa implementuje <xref:System.IAsyncResult> , a ta implementacja ujawnia <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> Właściwość, która zwraca dojście oczekiwania, który zostanie ustawiony po <xref:System.Threading.Tasks.Task> zakończeniu.  Możesz uzyskać w <xref:System.Threading.WaitHandle> <xref:System.Threading.Tasks.Task> następujący sposób:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Zobacz także

- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](task-based-asynchronous-pattern-tap.md)
- [Implementacja wzorca asynchronicznego opartego na zadaniach](implementing-the-task-based-asynchronous-pattern.md)
- [Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](consuming-the-task-based-asynchronous-pattern.md)
