---
ms.openlocfilehash: eab476a1d3f275e851e5af4198c30b60ad0c17b8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858414"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners nie należy przechwytywać zdarzenia od dostawców, za pomocą jawnego słowa kluczowe (na przykład dostawca TPL)

|   |   |
|---|---|
|Szczegóły|EventListeners ETW za pomocą maski puste — słowo kluczowe nie poprawnie przechwytywać zdarzenia od dostawców, za pomocą jawnego słów kluczowych. W .NET Framework 4.5 dostawcy TPL rozpoczęło się, podając jawne słów kluczowych i wyzwalane ten problem. W .NET Framework 4.6 EventListeners zostały zaktualizowanie, aby nie musieli tego problemu.|
|Sugestia|Aby obejść ten problem, należy zastąpić wywołania <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> za pomocą wywołania przeciążenia EnableEvents, które jawnie określa &quot;wszelkie słowa kluczowe&quot; maskę, aby używać: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Alternatywnie ten problem został rozwiązany w .NET Framework 4.6 i może zostać zlikwidowane przez uaktualnienie do wersji programu .NET Framework.|
|Scope|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

