---
title: CLR_DEBUGGING_PROCESS_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 292f6953fad0d65b368642543af107c73ec42ab5
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274113"
---
# <a name="clr_debugging_process_flags-enumeration"></a><span data-ttu-id="84298-102">CLR_DEBUGGING_PROCESS_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="84298-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="84298-103">Dostarcza wartości, które są używane przez metodę [ICLRDebugging:: OpenVirtualProcess —](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="84298-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84298-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84298-104">Syntax</span></span>  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="84298-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="84298-105">Members</span></span>  
  
|<span data-ttu-id="84298-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="84298-106">Member</span></span>|<span data-ttu-id="84298-107">Opis</span><span class="sxs-lookup"><span data-stu-id="84298-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="84298-108">To środowisko uruchomieniowe ma niecatche zarządzane zdarzenie debugera do wysłania.</span><span class="sxs-lookup"><span data-stu-id="84298-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="84298-109">Zapoznaj się z sekcją uwagi w celu rozróżnienia między zdarzeniami przechwytywania i niecatch.</span><span class="sxs-lookup"><span data-stu-id="84298-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="84298-110">Oczekiwane zdarzenie zarządzane to <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> żądanie.</span><span class="sxs-lookup"><span data-stu-id="84298-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84298-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84298-111">Remarks</span></span>  
 <span data-ttu-id="84298-112">Zdarzenia dotyczące przechwytywania obejmują proces, domenę aplikacji, zestaw, moduł i powiadomienia o tworzeniu wątku, które umożliwiają debugerowi dostęp do bieżącego stanu po dołączeniu go do procesu.</span><span class="sxs-lookup"><span data-stu-id="84298-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="84298-113">Zdarzenia niecatch, które są wskazywane przez `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flagę, obejmują wszystkie inne zdarzenia debugera, takie jak wyjątki i powiadomienia programu Managed Debug Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="84298-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="84298-114">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Flaga włącza środowisko uruchomieniowe, aby odróżnić między wyjątkami kończącymi i żądaniem dołączenia zarządzanego debugera, który można anulować.</span><span class="sxs-lookup"><span data-stu-id="84298-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84298-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84298-115">Requirements</span></span>  
 <span data-ttu-id="84298-116">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84298-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84298-117">**Nagłówki** Obiekt ServiceHost. idl, dbhost. h</span><span class="sxs-lookup"><span data-stu-id="84298-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="84298-118">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84298-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84298-119">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84298-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84298-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84298-120">See also</span></span>

- [<span data-ttu-id="84298-121">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="84298-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="84298-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="84298-122">Debugging</span></span>](index.md)
