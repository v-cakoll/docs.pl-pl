---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804391"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="1c147-101">Nazwy zdarzeń ETW nie mogą różnić się tylko sufiksem "Start" lub "Stop"</span><span class="sxs-lookup"><span data-stu-id="1c147-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1c147-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1c147-102">Details</span></span>|<span data-ttu-id="1c147-103">W programie .NET Framework 4.6 i 4.6.1 <xref:System.ArgumentException> środowisko wykonawcze zgłasza, gdy dwie nazwy zdarzeń śledzenia &quot;&quot; zdarzeń &quot;&quot; dla systemu Windows (ETW) <code>LogUser</code> różnią się <code>LogUserStart</code>tylko sufiksem Start lub Stop (jak wtedy, gdy jedno zdarzenie jest nazwane, a inne ma nazwę ).</span><span class="sxs-lookup"><span data-stu-id="1c147-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix (as when one event is named <code>LogUser</code> and another is named <code>LogUserStart</code>).</span></span> <span data-ttu-id="1c147-104">W takim przypadku środowisko wykonawcze nie może skonstruować źródła zdarzeń, które nie może emitować żadnych rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="1c147-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>|
|<span data-ttu-id="1c147-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1c147-105">Suggestion</span></span>|<span data-ttu-id="1c147-106">Aby zapobiec wyjątek, upewnij się, że &quot;żadne&quot; &quot;dwie&quot; nazwy zdarzeń różnią się tylko przez start lub stop sufiks. To wymaganie jest usuwane począwszy od programu .NET Framework 4.6.2; środowisko wykonawcze może rozróżniać nazwy zdarzeń,&quot; &quot;które&quot; różnią się tylko sufiksem &quot;Start i Stop.</span><span class="sxs-lookup"><span data-stu-id="1c147-106">To prevent the exception, ensure that no two event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the &quot;Start&quot; and &quot;Stop&quot; suffix.</span></span>|
|<span data-ttu-id="1c147-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="1c147-107">Scope</span></span>|<span data-ttu-id="1c147-108">Brzeg</span><span class="sxs-lookup"><span data-stu-id="1c147-108">Edge</span></span>|
|<span data-ttu-id="1c147-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="1c147-109">Version</span></span>|<span data-ttu-id="1c147-110">4.6</span><span class="sxs-lookup"><span data-stu-id="1c147-110">4.6</span></span>|
|<span data-ttu-id="1c147-111">Typ</span><span class="sxs-lookup"><span data-stu-id="1c147-111">Type</span></span>|<span data-ttu-id="1c147-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="1c147-112">Retargeting</span></span>|
