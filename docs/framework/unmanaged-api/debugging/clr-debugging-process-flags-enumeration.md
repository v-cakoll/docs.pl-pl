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
ms.openlocfilehash: b9185600d9d8b2a33830d86642727ac54b87a9cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099655"
---
# <a name="clr_debugging_process_flags-enumeration"></a><span data-ttu-id="9d977-102">CLR_DEBUGGING_PROCESS_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9d977-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="9d977-103">Dostarcza wartości, które są używane przez metodę [ICLRDebugging:: OpenVirtualProcess —](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9d977-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d977-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d977-104">Syntax</span></span>  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="9d977-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9d977-105">Members</span></span>  
  
|<span data-ttu-id="9d977-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9d977-106">Member</span></span>|<span data-ttu-id="9d977-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9d977-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="9d977-108">To środowisko uruchomieniowe ma niecatche zarządzane zdarzenie debugera do wysłania.</span><span class="sxs-lookup"><span data-stu-id="9d977-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="9d977-109">Zapoznaj się z sekcją uwagi w celu rozróżnienia między zdarzeniami przechwytywania i niecatch.</span><span class="sxs-lookup"><span data-stu-id="9d977-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="9d977-110">Oczekujące zdarzenie zarządzane to żądanie <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d977-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d977-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d977-111">Remarks</span></span>  
 <span data-ttu-id="9d977-112">Zdarzenia dotyczące przechwytywania obejmują proces, domenę aplikacji, zestaw, moduł i powiadomienia o tworzeniu wątku, które umożliwiają debugerowi dostęp do bieżącego stanu po dołączeniu go do procesu.</span><span class="sxs-lookup"><span data-stu-id="9d977-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="9d977-113">Zdarzenia niecatch, które są wskazywane przez flagę `CLR_DEBUGGING_MANAGED_EVENT_PENDING`, obejmują wszystkie inne zdarzenia debugera, takie jak wyjątki i powiadomienia programu Managed Debug Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="9d977-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="9d977-114">Flaga `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` umożliwia rozróżnienie środowiska uruchomieniowego między wyjątkami kończącymi i żądaniem dołączenia zarządzanego debugera, który można anulować.</span><span class="sxs-lookup"><span data-stu-id="9d977-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d977-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d977-115">Requirements</span></span>  
 <span data-ttu-id="9d977-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d977-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d977-117">**Nagłówek:** Obiekt ServiceHost. idl, dbhost. h</span><span class="sxs-lookup"><span data-stu-id="9d977-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="9d977-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9d977-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d977-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d977-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d977-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d977-120">See also</span></span>

- [<span data-ttu-id="9d977-121">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9d977-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="9d977-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="9d977-122">Debugging</span></span>](index.md)
