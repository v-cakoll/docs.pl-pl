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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 198141545119976cb9107bc9c09b913572e266ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781128"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="5fff4-102">MDAInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="5fff4-102">MDAInfo Structure</span></span>
<span data-ttu-id="5fff4-103">Zawiera szczegółowe informacje na temat `Event_MDAFired` zdarzenia, co powoduje wyzwolenie tworzenia zarządzanego Asystenta debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="5fff4-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fff4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fff4-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="5fff4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5fff4-105">Members</span></span>  
  
|<span data-ttu-id="5fff4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5fff4-106">Member</span></span>|<span data-ttu-id="5fff4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5fff4-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="5fff4-108">Tytuł bieżącego MDA.</span><span class="sxs-lookup"><span data-stu-id="5fff4-108">The title of the current MDA.</span></span> <span data-ttu-id="5fff4-109">Tytuł w tym artykule opisano rodzaj błędu, który wyzwolił `Event_MDAFired` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5fff4-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="5fff4-110">Komunikatu wyjściowego dostarczane przez bieżącego MDA.</span><span class="sxs-lookup"><span data-stu-id="5fff4-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fff4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5fff4-111">Remarks</span></span>  
 <span data-ttu-id="5fff4-112">Debugowanie — pomoce, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR) do wykonywania zadań, np. zidentyfikowanie nieprawidłowe warunki w silnika wykonania środowiska uruchomieniowego lub zrzucania dodatkowe informacje na temat stanu asystentów zarządzanego debugowania (mda) aparat.</span><span class="sxs-lookup"><span data-stu-id="5fff4-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="5fff4-113">Mda generowania wiadomości XML o zdarzeniach, które w przeciwnym razie są trudne do pułapki.</span><span class="sxs-lookup"><span data-stu-id="5fff4-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="5fff4-114">Są one szczególnie przydatne podczas debugowania przejścia między kodem zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="5fff4-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="5fff4-115">Po wyzwoleniu zdarzenia wyzwalającego tworzenia MDA, środowisko uruchomieniowe wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5fff4-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="5fff4-116">Jeśli host nie został zarejestrowany [iactiononclrevent —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) wystąpienia, wywołując [iclroneventmanager::registeractiononevent —](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) Aby otrzymywać powiadomienia o `Event_MDAFired` zdarzenia środowiska uruchomieniowego kontynuuje jego Domyślnie-hostowanej działania.</span><span class="sxs-lookup"><span data-stu-id="5fff4-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="5fff4-117">Jeśli host został zarejestrowany program obsługi dla tego zdarzenia, środowisko uruchomieniowe sprawdza, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="5fff4-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="5fff4-118">Jeśli tak jest, środowisko uruchomieniowe przerywa debugowanie.</span><span class="sxs-lookup"><span data-stu-id="5fff4-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="5fff4-119">Gdy debuger będzie nadal występował, wywoła hosta.</span><span class="sxs-lookup"><span data-stu-id="5fff4-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="5fff4-120">Jeśli debuger nie jest dołączony, środowisko wykonawcze wywołuje `IActionOnCLREvent::OnEvent` i przekazuje wskaźnik do `MDAInfo` wystąpienia jako `data` parametru.</span><span class="sxs-lookup"><span data-stu-id="5fff4-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="5fff4-121">Hosta można wybrać, aby aktywować MDA oraz otrzymywać powiadomienia, gdy zdarzenie MDA jest aktywowane.</span><span class="sxs-lookup"><span data-stu-id="5fff4-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="5fff4-122">Host daje szansę, aby zastąpić domyślne zachowanie i aby przerwać wątków zarządzanych, która wywołała zdarzenie, aby uniemożliwić uszkodzenia stan procesu.</span><span class="sxs-lookup"><span data-stu-id="5fff4-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="5fff4-123">Aby uzyskać więcej informacji na temat używania mda zobacz [diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="5fff4-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fff4-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5fff4-124">Requirements</span></span>  
 <span data-ttu-id="5fff4-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fff4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fff4-126">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="5fff4-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="5fff4-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5fff4-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fff4-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fff4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fff4-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fff4-129">See also</span></span>

- [<span data-ttu-id="5fff4-130">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="5fff4-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="5fff4-131">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="5fff4-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
