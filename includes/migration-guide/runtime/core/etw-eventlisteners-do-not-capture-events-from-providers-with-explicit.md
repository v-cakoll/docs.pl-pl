---
ms.openlocfilehash: 1ef31202d7c072ca27c21fc22db102aafa6b8de7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858414"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>Etw EventListeners nie przechwytują zdarzeń od dostawców z jawnymi słowami kluczowymi (takich jak dostawca TPL)

|   |   |
|---|---|
|Szczegóły|Etw EventListeners z pustą maską słowa kluczowego nie poprawnie przechwytują zdarzenia od dostawców z jawnymi słowami kluczowymi. W .NET Framework 4.5 dostawca TPL zaczął dostarczać jawne słowa kluczowe i wyzwolił ten problem. W .NET Framework 4.6 EventListeners zostały zaktualizowane, aby nie mieć już tego problemu.|
|Sugestia|Aby obejść ten problem, <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> zastąp wywołania przeciążenia EnableEvents,&quot; które jawnie <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>określa &quot;maskę słów kluczowych do użycia: . Alternatywnie ten problem został rozwiązany w .NET Framework 4.6 i może zostać rozwiązany przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|
