---
ms.openlocfilehash: 7d50962b518c15875a5f1a82f5b89ab87a1db02e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620237"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>EventListeners ETW nie przechwytuje zdarzeń z dostawców z jawnymi słowami kluczowymi (takimi jak dostawca TPL)

#### <a name="details"></a>Szczegóły

EventListeners ETW z pustą maską słowa kluczowego niepoprawnie przechwytuje zdarzenia z dostawców z jawnymi słowami kluczowymi. W .NET Framework 4,5 dostawca TPL rozpoczął dostarczanie jawnych słów kluczowych i wyzwolił ten problem. W .NET Framework 4,6 EventListeners zostały zaktualizowane, aby nie miały już tego problemu.

#### <a name="suggestion"></a>Sugestia

Aby obejść ten problem, Zastąp wywołania wywołaniami <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> przeciążenia EnableEvents, które jawnie określa &quot; maskę słów kluczowych &quot; do użycia: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code> . Alternatywnie ten problem został rozwiązany w .NET Framework 4,6 i może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|
