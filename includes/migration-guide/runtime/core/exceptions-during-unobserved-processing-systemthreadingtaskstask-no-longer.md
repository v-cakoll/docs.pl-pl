---
ms.openlocfilehash: b0e6d6f228647148083d3df64e65f817dc3455d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235648"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>Wyjątki podczas niewidocznego przetwarzania w System.Threading.Tasks.Task nie będzie propagowany w wątku finalizatora

|   |   |
|---|---|
|Szczegóły|Ponieważ <xref:System.Threading.Tasks.Task?displayProperty=name> klasa reprezentuje operację asynchroniczną, przechwytuje wszystkie Niekrytyczne wyjątki, które występują podczas przetwarzania asynchronicznego. W .NET Framework 4.5 Jeśli wyjątek nie zostanie wykryty, a kod nigdy nie czeka podczas zadania, wyjątek nie będzie propagowany w wątku finalizatora i spowoduje awarię procesu podczas wyrzucania elementów bezużytecznych. Ta zmiana zwiększa niezawodność aplikacji używających klasy zadań w celu wykonywania niewidocznego przetwarzania asynchronicznego.|
|Sugestia|Jeśli aplikacja jest zależna od niewidocznego wyjątki asynchroniczne propagowania na wątek finalizatora, można przywrócić poprzednie zachowanie, dostarczając odpowiedni program obsługi <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> zdarzenia lub poprzez skonfigurowanie [element konfiguracji środowiska uruchomieniowego ](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
