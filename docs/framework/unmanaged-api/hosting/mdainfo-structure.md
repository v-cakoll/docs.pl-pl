---
title: MDAInfo — Struktura
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
ms.openlocfilehash: 9a2f513d40d722f1b0aad823ac7c0d93bda5615f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123257"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="1b8af-102">MDAInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="1b8af-102">MDAInfo Structure</span></span>
<span data-ttu-id="1b8af-103">Zawiera szczegółowe informacje o zdarzeniu `Event_MDAFired`, które wyzwala tworzenie zarządzanego asystenta debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="1b8af-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b8af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b8af-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="1b8af-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1b8af-105">Members</span></span>  
  
|<span data-ttu-id="1b8af-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1b8af-106">Member</span></span>|<span data-ttu-id="1b8af-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1b8af-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="1b8af-108">Tytuł bieżącego elementu MDA.</span><span class="sxs-lookup"><span data-stu-id="1b8af-108">The title of the current MDA.</span></span> <span data-ttu-id="1b8af-109">Tytuł opisuje rodzaj błędu, który wyzwolił zdarzenie `Event_MDAFired`.</span><span class="sxs-lookup"><span data-stu-id="1b8af-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="1b8af-110">Komunikat wyjściowy dostarczony przez bieżące zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="1b8af-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b8af-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b8af-111">Remarks</span></span>  
 <span data-ttu-id="1b8af-112">Zarządzane Asystenci debugowania (MDA) to pomoce debugowania, które działają w połączeniu ze środowiskiem uruchomieniowym języka wspólnego (CLR) do wykonywania zadań, takich jak identyfikowanie nieprawidłowych warunków w aparacie wykonawczym środowiska uruchomieniowego lub zatopienie dodatkowych informacji o stanie wyszukiwarce.</span><span class="sxs-lookup"><span data-stu-id="1b8af-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="1b8af-113">MDA generuje komunikaty XML o zdarzeniach, które w przeciwnym razie trudno jest Zalewka.</span><span class="sxs-lookup"><span data-stu-id="1b8af-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="1b8af-114">Są one szczególnie przydatne do debugowania przejść między zarządzanym i niezarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="1b8af-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="1b8af-115">Środowisko uruchomieniowe wykonuje następujące czynności, gdy zostanie wyzwolone zdarzenie wyzwalające utworzenie elementu MDA:</span><span class="sxs-lookup"><span data-stu-id="1b8af-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="1b8af-116">Jeśli host nie zarejestrował wystąpienia [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) przez wywołanie [ICLROnEventManager:: RegisterActionOnEvent —](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) w celu powiadomienia o zdarzeniu `Event_MDAFired`, środowisko uruchomieniowe kontynuuje działanie z domyślnym, nieobsługiwanym zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="1b8af-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="1b8af-117">Jeśli host zarejestrował procedurę obsługi dla tego zdarzenia, środowisko uruchomieniowe sprawdzi, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="1b8af-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="1b8af-118">Jeśli tak jest, środowisko uruchomieniowe jest przerywane w debugerze.</span><span class="sxs-lookup"><span data-stu-id="1b8af-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="1b8af-119">Gdy debuger kontynuuje działanie, wywołuje hosta.</span><span class="sxs-lookup"><span data-stu-id="1b8af-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="1b8af-120">Jeśli debuger nie jest dołączony, wywołania środowiska uruchomieniowego `IActionOnCLREvent::OnEvent` i przekazują wskaźnik do wystąpienia `MDAInfo` jako parametru `data`.</span><span class="sxs-lookup"><span data-stu-id="1b8af-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="1b8af-121">Host może zdecydować się na aktywację MDA i otrzymywanie powiadomień, gdy zostanie uaktywnione zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="1b8af-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="1b8af-122">Dzięki temu host może przesłonić domyślne zachowanie i przerwać zarządzany wątek, który wywołał zdarzenie, aby zapobiec uszkodzeniu stanu procesu.</span><span class="sxs-lookup"><span data-stu-id="1b8af-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="1b8af-123">Aby uzyskać więcej informacji na temat korzystania z programu MDA, zobacz [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="1b8af-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b8af-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b8af-124">Requirements</span></span>  
 <span data-ttu-id="1b8af-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b8af-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b8af-126">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="1b8af-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="1b8af-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1b8af-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b8af-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b8af-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b8af-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b8af-129">See also</span></span>

- [<span data-ttu-id="1b8af-130">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="1b8af-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="1b8af-131">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="1b8af-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
