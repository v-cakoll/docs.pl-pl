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
ms.openlocfilehash: 981c13c68eaf1eb0c19f95eb1b097935ea02a16d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159757"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Współdziałanie z innymi wzorcami asynchronicznymi i typami
.NET Framework 1.0 <xref:System.IAsyncResult> wprowadzono wzorzec, inaczej znany jako [Asynchroniczny model programowania (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)lub `Begin/End` wzorzec.  Program .NET Framework 2.0 dodał [wzorca asynchronicznego opartego na zdarzeniach (EAP).](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  Począwszy od .NET Framework 4, [oparty na zadaniach wzorzec asynchroniczny (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) zastępuje zarówno APM, jak i EAP, ale zapewnia możliwość łatwego tworzenia procedur migracji z wcześniejszych wzorców.  
  
 W tym temacie:  
  
- [Zadania i APM](#APM) ([od APM do TAP](#ApmToTap) lub z TAP do [APM](#TapToApm))  
  
- [Zadania i EAP](#EAP)  
  
- [Zadania i uchwyty oczekiwania](#WaitHandles) [(od uchwytów oczekiwania do tap](#WHToTap) lub z [TAP, aby czekać uchwyty](#TapToWH))  
  
<a name="APM"></a>
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Zadania i asynchroniczny model programowania (APM)  
  
<a name="ApmToTap"></a>
### <a name="from-apm-to-tap"></a>Z APM do TAP  
 Ponieważ [wzorzec asynchronicznego modelu programowania (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) jest bardzo zorganizowany, dość łatwo jest utworzyć otokę, aby udostępnić implementację APM jako implementację TAP. W rzeczywistości .NET Framework, począwszy od .NET Framework 4, zawiera <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> procedury pomocnika w postaci przeciążenia metody, aby zapewnić to tłumaczenie.  
  
 Należy <xref:System.IO.Stream> wziąć pod <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> uwagę klasę i jej metody, które reprezentują <xref:System.IO.Stream.Read%2A> odpowiednik APM do metody synchronicznej:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> Metoda ta służy do implementowania otoki TAP dla tej operacji w następujący sposób:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Ta implementacja jest podobna do następującej:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>
### <a name="from-tap-to-apm"></a>Od TAP do APM  
 Jeśli istniejąca infrastruktura oczekuje wzorca APM, należy również podjąć implementacji TAP i używać go tam, gdzie oczekuje się implementacji apm.  Ponieważ zadania mogą być <xref:System.Threading.Tasks.Task> składane <xref:System.IAsyncResult>i implementuje klasy , można użyć funkcji pomocnika proste, aby to zrobić. Poniższy kod używa rozszerzenia <xref:System.Threading.Tasks.Task%601> klasy, ale można użyć prawie identyczną funkcję dla zadań nieogólnych.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Teraz rozważ przypadek, w którym masz następującą implementację TAP:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 i chcesz zapewnić tę implementację APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 W poniższym przykładzie przedstawiono jedną migrację do apm:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Zadania i wzorzec asynchroniczny oparty na zdarzeniach (EAP)  
 Zawijanie implementacji [wzorca asynchronicznego (EAP) opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) jest bardziej zaangażowane niż zawijanie wzorca APM, ponieważ wzorzec EAP ma większą zmienność i mniejszą strukturę niż wzorzec APM.  Aby zademonstrować, poniższy `DownloadStringAsync` kod otacza metodę.  `DownloadStringAsync`akceptuje identyfikator URI, `DownloadProgressChanged` wywołuje zdarzenie podczas pobierania w celu raportowania wielu `DownloadStringCompleted` statystyk dotyczących postępu i wywołuje zdarzenie po jego zakończeniu.  Wynik końcowy jest ciągiem zawierającym zawartość strony przy określonym identyfikatorze URI.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>
## <a name="tasks-and-wait-handles"></a>Zadania i uchwyty oczekiwania  
  
<a name="WHToTap"></a>
### <a name="from-wait-handles-to-tap"></a>Od uchwytów oczekiwania do tap  
 Mimo że dojścia oczekiwania nie implementują wzorca <xref:System.Threading.WaitHandle> asynchronicznego, zaawansowani deweloperzy mogą używać klasy i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody powiadomień asynchronicznych po ustawieniu dojścia oczekiwania.  Można zawinąć metodę, <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> aby włączyć alternatywę dla dowolnego synchronicznego oczekiwania na dojście oczekiwania:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Za pomocą tej metody <xref:System.Threading.WaitHandle> można użyć istniejących implementacji w metodach asynchronicznych.  Na przykład jeśli chcesz ograniczyć liczbę operacji asynchronicznych, które są wykonywane w danym momencie, można wykorzystać semafora <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> (obiekt).  Można ograniczyć do *N* liczbę operacji, które są uruchamiane jednocześnie, inicjując liczbę semafora do *N,* czekając na semafora w dowolnym momencie, gdy chcesz wykonać operację, i zwalniając semafor po zakończeniu operacji:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Można również utworzyć asynchroniczny semafor, który nie opiera się na uchwyty oczekiwania i zamiast tego działa całkowicie z zadaniami. Aby to zrobić, można użyć technik, takich jak te omówione w [Korzystanie z wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) do tworzenia struktur danych na wierzchu <xref:System.Threading.Tasks.Task>.  
  
<a name="TapToWH"></a>
### <a name="from-tap-to-wait-handles"></a>Od TAP do uchwytów oczekiwania  
 Jak wcześniej wspomniano, <xref:System.Threading.Tasks.Task> implementuje <xref:System.IAsyncResult>klasy , a <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> implementacja udostępnia właściwość, która zwraca <xref:System.Threading.Tasks.Task> dojście oczekiwania, który zostanie ustawiony po zakończeniu.  Możesz otrzymać <xref:System.Threading.WaitHandle> for <xref:System.Threading.Tasks.Task> a w następujący sposób:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Zobacz też

- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Implementacja wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
