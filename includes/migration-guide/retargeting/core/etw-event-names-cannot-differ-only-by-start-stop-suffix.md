---
ms.openlocfilehash: 9ad283af76085c228bedceb6db723a1d18b10210
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804391"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="04b94-101">Nazwy zdarzeń funkcji ETW nie różnią się jedynie sufiks "Start" lub "Zatrzymaj"</span><span class="sxs-lookup"><span data-stu-id="04b94-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

|   |   |
|---|---|
|<span data-ttu-id="04b94-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="04b94-102">Details</span></span>|<span data-ttu-id="04b94-103">W .NET Framework 4.6 i 4.6.1, środowisko wykonawcze zgłasza <xref:System.ArgumentException> gdy dwie nazwy zdarzeń śledzenie zdarzeń dla Windows (ETW) różniących się tylko &quot;Start&quot; lub &quot;zatrzymać&quot; sufiks (jako po nazwie jedno zdarzenie <code>LogUser</code>i nosi nazwę innego <code>LogUserStart</code>).</span><span class="sxs-lookup"><span data-stu-id="04b94-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix (as when one event is named <code>LogUser</code> and another is named <code>LogUserStart</code>).</span></span> <span data-ttu-id="04b94-104">W tym przypadku środowisko uruchomieniowe nie można utworzyć źródła zdarzeń, którego nie można wyemitować wszelkie rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="04b94-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>|
|<span data-ttu-id="04b94-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="04b94-105">Suggestion</span></span>|<span data-ttu-id="04b94-106">Aby zapobiec wyjątek, upewnij się, że żadne nazwy dwóch zdarzeń różniących się tylko &quot;Start&quot; lub &quot;zatrzymać&quot; sufiks. To wymaganie jest usuwany, począwszy od programu .NET Framework 4.6.2; środowisko uruchomieniowe można odróżnić nazwy zdarzeń, które różnią się tylko przez &quot;Start&quot; i &quot;zatrzymać&quot; sufiks.</span><span class="sxs-lookup"><span data-stu-id="04b94-106">To prevent the exception, ensure that no two event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the &quot;Start&quot; and &quot;Stop&quot; suffix.</span></span>|
|<span data-ttu-id="04b94-107">Scope</span><span class="sxs-lookup"><span data-stu-id="04b94-107">Scope</span></span>|<span data-ttu-id="04b94-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="04b94-108">Edge</span></span>|
|<span data-ttu-id="04b94-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="04b94-109">Version</span></span>|<span data-ttu-id="04b94-110">4.6</span><span class="sxs-lookup"><span data-stu-id="04b94-110">4.6</span></span>|
|<span data-ttu-id="04b94-111">Typ</span><span class="sxs-lookup"><span data-stu-id="04b94-111">Type</span></span>|<span data-ttu-id="04b94-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="04b94-112">Retargeting</span></span>|

