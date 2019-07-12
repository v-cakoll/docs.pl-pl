---
ms.openlocfilehash: 9ad283af76085c228bedceb6db723a1d18b10210
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804391"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Nazwy zdarzeń funkcji ETW nie różnią się jedynie sufiks "Start" lub "Zatrzymaj"

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6 i 4.6.1, środowisko wykonawcze zgłasza <xref:System.ArgumentException> gdy dwie nazwy zdarzeń śledzenie zdarzeń dla Windows (ETW) różniących się tylko &quot;Start&quot; lub &quot;zatrzymać&quot; sufiks (jako po nazwie jedno zdarzenie <code>LogUser</code>i nosi nazwę innego <code>LogUserStart</code>). W tym przypadku środowisko uruchomieniowe nie można utworzyć źródła zdarzeń, którego nie można wyemitować wszelkie rejestrowania.|
|Sugestia|Aby zapobiec wyjątek, upewnij się, że żadne nazwy dwóch zdarzeń różniących się tylko &quot;Start&quot; lub &quot;zatrzymać&quot; sufiks. To wymaganie jest usuwany, począwszy od programu .NET Framework 4.6.2; środowisko uruchomieniowe można odróżnić nazwy zdarzeń, które różnią się tylko przez &quot;Start&quot; i &quot;zatrzymać&quot; sufiks.|
|Scope|Krawędź|
|Wersja|4.6|
|Typ|Przekierowanie|

