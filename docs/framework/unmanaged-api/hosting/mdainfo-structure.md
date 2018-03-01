---
title: "MDAInfo — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 53a999028f2677599598caf55e62f10721f61fe3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mdainfo-structure"></a><span data-ttu-id="a9f50-102">MDAInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="a9f50-102">MDAInfo Structure</span></span>
<span data-ttu-id="a9f50-103">Zawiera szczegółowe informacje na temat `Event_MDAFired` zdarzenie, które wyzwala tworzenie zarządzany Asystent debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="a9f50-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9f50-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9f50-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="a9f50-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a9f50-105">Members</span></span>  
  
|<span data-ttu-id="a9f50-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a9f50-106">Member</span></span>|<span data-ttu-id="a9f50-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a9f50-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="a9f50-108">Tytuł bieżącego MDA.</span><span class="sxs-lookup"><span data-stu-id="a9f50-108">The title of the current MDA.</span></span> <span data-ttu-id="a9f50-109">Tytuł opisuje rodzaj awarii, która wyzwoliła `Event_MDAFired` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a9f50-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="a9f50-110">Dostarczone przez bieżący MDA komunikatu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a9f50-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9f50-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9f50-111">Remarks</span></span>  
 <span data-ttu-id="a9f50-112">Asystenci zarządzanego debugowania (mda) są debugowania pomocy, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR) do wykonywania zadań, takich jak identyfikujący nieprawidłowe warunki w aparacie wykonawczym środowiska uruchomieniowego lub zrzucanie dodatkowe informacje o stanie aparat.</span><span class="sxs-lookup"><span data-stu-id="a9f50-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="a9f50-113">Mda generowania komunikatów XML o zdarzeniach, które w przeciwnym razie są trudne do pułapki.</span><span class="sxs-lookup"><span data-stu-id="a9f50-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="a9f50-114">Są one szczególnie przydatne w przypadku przejścia między zarządzanymi i niezarządzanymi kodu do debugowania.</span><span class="sxs-lookup"><span data-stu-id="a9f50-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="a9f50-115">Środowisko uruchomieniowe wykonuje następujące czynności w przypadku jest generowane zdarzenie, które wyzwala tworzenie MDA:</span><span class="sxs-lookup"><span data-stu-id="a9f50-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
-   <span data-ttu-id="a9f50-116">Jeśli host nie został zarejestrowany [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) wystąpienia przez wywołanie metody [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) ma być powiadamiany o `Event_MDAFired` zdarzenia środowiska uruchomieniowego kontynuuje jego Domyślnie zachowanie nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a9f50-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
-   <span data-ttu-id="a9f50-117">Jeśli host został zarejestrowany obsługi dla tego zdarzenia, środowisko uruchomieniowe sprawdza, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="a9f50-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="a9f50-118">Jeśli tak jest, środowisko uruchomieniowe przechodzi do debugera.</span><span class="sxs-lookup"><span data-stu-id="a9f50-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="a9f50-119">Debuger będzie nadal występował, wywołuje do hosta.</span><span class="sxs-lookup"><span data-stu-id="a9f50-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="a9f50-120">Jeśli żaden debuger jest dołączony, środowisko urchomieniowe wywołuje `IActionOnCLREvent::OnEvent` i przekazuje wskaźnik do `MDAInfo` jako `data` parametru.</span><span class="sxs-lookup"><span data-stu-id="a9f50-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="a9f50-121">Aby aktywować mda i zgłaszane po aktywowaniu MDA, można wybrać hosta.</span><span class="sxs-lookup"><span data-stu-id="a9f50-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="a9f50-122">Host daje możliwość zastąpienie zachowania domyślnego i abort zarządzanego wątku, który wywołał zdarzenie, aby uniknąć uszkodzenia stan procesu.</span><span class="sxs-lookup"><span data-stu-id="a9f50-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="a9f50-123">Aby uzyskać więcej informacji na temat używania mda, zobacz [diagnozowanie problemów z Asystenci zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="a9f50-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9f50-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9f50-124">Requirements</span></span>  
 <span data-ttu-id="a9f50-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9f50-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9f50-126">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="a9f50-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a9f50-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9f50-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9f50-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9f50-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f50-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9f50-129">See Also</span></span>  
 [<span data-ttu-id="a9f50-130">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="a9f50-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="a9f50-131">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="a9f50-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
