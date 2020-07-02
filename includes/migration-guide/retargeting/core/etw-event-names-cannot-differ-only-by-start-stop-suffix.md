---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614675"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="1946a-101">Nazwy zdarzeń ETW nie mogą się różnić tylko sufiksem "Start" lub "Stop"</span><span class="sxs-lookup"><span data-stu-id="1946a-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

#### <a name="details"></a><span data-ttu-id="1946a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1946a-102">Details</span></span>

<span data-ttu-id="1946a-103">W .NET Framework 4,6 i 4.6.1 środowisko uruchomieniowe zgłasza, <xref:System.ArgumentException> kiedy dwa zdarzenia śledzenia zdarzeń dla systemu Windows (ETW) różnią się tylko sufiksem "Start" lub "Zatrzymaj" (tak, jakby jedno zdarzenie o nazwie zostało nazwane `LogUser` i ma nazwę `LogUserStart` ).</span><span class="sxs-lookup"><span data-stu-id="1946a-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a "Start" or "Stop" suffix (as when one event is named `LogUser` and another is named `LogUserStart`).</span></span> <span data-ttu-id="1946a-104">W tym przypadku środowisko uruchomieniowe nie może skonstruować źródła zdarzeń, co nie może emitować żadnego rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="1946a-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1946a-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1946a-105">Suggestion</span></span>

<span data-ttu-id="1946a-106">Aby zapobiec wyjątku, należy się upewnić, że żadne dwa nazwy zdarzeń nie różnią się tylko sufiksem "Start" lub "Stop". Ten wymóg jest usuwany, rozpoczynając od .NET Framework 4.6.2; środowisko uruchomieniowe może odróżnić nazwy zdarzeń, które różnią się tylko sufiksem "Start" i "Stop".</span><span class="sxs-lookup"><span data-stu-id="1946a-106">To prevent the exception, ensure that no two event names differ only by a "Start" or "Stop" suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the "Start" and "Stop" suffix.</span></span>

| <span data-ttu-id="1946a-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1946a-107">Name</span></span>    | <span data-ttu-id="1946a-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="1946a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1946a-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="1946a-109">Scope</span></span>   | <span data-ttu-id="1946a-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="1946a-110">Edge</span></span>        |
| <span data-ttu-id="1946a-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="1946a-111">Version</span></span> | <span data-ttu-id="1946a-112">4.6</span><span class="sxs-lookup"><span data-stu-id="1946a-112">4.6</span></span>         |
| <span data-ttu-id="1946a-113">Typ</span><span class="sxs-lookup"><span data-stu-id="1946a-113">Type</span></span>    | <span data-ttu-id="1946a-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="1946a-114">Retargeting</span></span> |
