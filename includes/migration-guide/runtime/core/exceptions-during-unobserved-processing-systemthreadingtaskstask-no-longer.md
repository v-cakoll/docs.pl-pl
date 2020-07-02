---
ms.openlocfilehash: 5ba2ddb76ab946339449246840667ba4a48e9c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620247"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>Wyjątki podczas niezauważalnego przetwarzania w wątku system. Threading. Tasks. Task nie są już propagowane na etapie finalizatora

#### <a name="details"></a>Szczegóły

Ponieważ <xref:System.Threading.Tasks.Task?displayProperty=fullName> Klasa reprezentuje operację asynchroniczną, przechwytuje wszystkie niepoważne wyjątki, które występują podczas przetwarzania asynchronicznego. W .NET Framework 4,5, jeśli wyjątek nie zostanie zaobserwowany i kod nigdy nie czeka na zadanie, wyjątek nie będzie już propagowany w wątku finalizatora i wystąpił awarię procesu podczas wyrzucania elementów bezużytecznych. Ta zmiana zwiększa niezawodność aplikacji, które używają klasy zadań do wykonywania niezauważalnego przetwarzania asynchronicznego.

#### <a name="suggestion"></a>Sugestia

Jeśli aplikacja jest zależna od nieobserwowanych wyjątków asynchronicznych propagowanych do wątku finalizatora, poprzednie zachowanie można przywrócić, dostarczając odpowiedni program obsługi <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> zdarzenia lub ustawiając [element konfiguracji środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
