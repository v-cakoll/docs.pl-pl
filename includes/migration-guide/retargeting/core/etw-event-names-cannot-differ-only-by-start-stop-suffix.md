---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804391"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Nazwy zdarzeń ETW nie mogą różnić się tylko sufiksem "Start" lub "Stop"

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6 i 4.6.1 <xref:System.ArgumentException> środowisko wykonawcze zgłasza, gdy dwie nazwy zdarzeń śledzenia &quot;&quot; zdarzeń &quot;&quot; dla systemu Windows (ETW) <code>LogUser</code> różnią się <code>LogUserStart</code>tylko sufiksem Start lub Stop (jak wtedy, gdy jedno zdarzenie jest nazwane, a inne ma nazwę ). W takim przypadku środowisko wykonawcze nie może skonstruować źródła zdarzeń, które nie może emitować żadnych rejestrowania.|
|Sugestia|Aby zapobiec wyjątek, upewnij się, że &quot;żadne&quot; &quot;dwie&quot; nazwy zdarzeń różnią się tylko przez start lub stop sufiks. To wymaganie jest usuwane począwszy od programu .NET Framework 4.6.2; środowisko wykonawcze może rozróżniać nazwy zdarzeń,&quot; &quot;które&quot; różnią się tylko sufiksem &quot;Start i Stop.|
|Zakres|Brzeg|
|Wersja|4.6|
|Typ|Przekierowanie|
