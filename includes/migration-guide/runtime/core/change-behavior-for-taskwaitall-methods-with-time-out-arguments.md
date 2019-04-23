---
ms.openlocfilehash: 94fad6fe910da6c528c5e13f529a6db274e07d5c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235698"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>Zmiana zachowania Task.WaitAll metod z argumentami limitu czasu

|   |   |
|---|---|
|Szczegóły|<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> zachowanie została wprowadzona spójniejsze w .NET Framework 4.5.In .NET Framework 4, te metody zachowywały się niespójnie. Po upływie limitu czasu, jeśli co najmniej jedno zadanie zostało ukończone lub anulowane przed wywołaniem metody, metoda zgłaszała <xref:System.AggregateException?displayProperty=name> wyjątku. Po upływie limitu czasu, jeśli zadania nie zostało ukończone lub anulowane przed wywołaniem metody, ale co najmniej jedno zadanie wprowadziło te stany po wywołaniu metody, Metoda zwróciła wartość false.<br/><br/>W .NET Framework 4.5, te przeciążenia metod teraz zwracają wartość false, jeśli wszystkie zadania są wciąż działają, gdy upłynął limit czasu, a wyjątek <xref:System.AggregateException?displayProperty=name> tylko wtedy, gdy wejściowy zadanie zostało anulowane (niezależnie od tego, czy serwer był przed lub po metodzie Wywołaj) i nie inne zadania nadal są uruchomione.|
|Sugestia|Jeśli <xref:System.AggregateException?displayProperty=name> został on zgłoszony jako sposób wykrywania zadanie, które zostało anulowane przed <xref:System.Threading.Tasks.Task.WaitAll%2A> wywołać wywoływanie kodu zrobić zamiast tego samego wykrywania za pośrednictwem <xref:System.Threading.Tasks.Task.IsCanceled%2A> właściwości (na przykład:. Any(t =&gt; t.IsCanceled)) od .NET Framework 4.6 tylko zgłosi w takim przypadku wszystkie oczekiwane czynności zostały wykonane przed limitu czasu.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|
