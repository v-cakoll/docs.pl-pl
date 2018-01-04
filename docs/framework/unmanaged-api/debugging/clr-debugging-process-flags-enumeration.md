---
title: "CLR_DEBUGGING_PROCESS_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_PROCESS_FLAGS
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords: CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c6d66f9a11f28ca572e0f1eddc74f3a5197a19d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="clrdebuggingprocessflags-enumeration"></a><span data-ttu-id="89b58-102">CLR_DEBUGGING_PROCESS_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="89b58-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="89b58-103">Udostępnia wartości, które są używane przez [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="89b58-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89b58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89b58-104">Syntax</span></span>  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="89b58-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="89b58-105">Members</span></span>  
  
|<span data-ttu-id="89b58-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="89b58-106">Member</span></span>|<span data-ttu-id="89b58-107">Opis</span><span class="sxs-lookup"><span data-stu-id="89b58-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="89b58-108">To środowisko wykonawcze ma zdarzeń debugera zarządzanych z systemem innym niż up catch do wysłania.</span><span class="sxs-lookup"><span data-stu-id="89b58-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="89b58-109">W sekcji uwag różnicy między zdarzeniami wyrównującej i pracy z systemem innym niż catch.</span><span class="sxs-lookup"><span data-stu-id="89b58-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="89b58-110">Zarządzane zdarzenia, które jest w stanie oczekiwania jest <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> żądania.</span><span class="sxs-lookup"><span data-stu-id="89b58-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89b58-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89b58-111">Remarks</span></span>  
 <span data-ttu-id="89b58-112">Przechwycenie zdarzeń to proces, domeny aplikacji zestawu, modułu i powiadomień Tworzenie wątków, które dostosowania debugera do bieżącego stanu po został dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="89b58-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="89b58-113">Non-catch-up zdarzenia, które są oznaczone `CLR_DEBUGGING_MANAGED_EVENT_PENDING` Flaga, obejmują wszystkie inne zdarzenia debugera, takie jak wyjątków i zarządzanego debugowania (MDA) Asystenta powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="89b58-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="89b58-114">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Flaga umożliwia środowiska uruchomieniowego w celu rozróżnienia wyjątek powodujący przerwanie i żądanie, aby dołączyć debuger zarządzany, które mogą zostać anulowane.</span><span class="sxs-lookup"><span data-stu-id="89b58-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89b58-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89b58-115">Requirements</span></span>  
 <span data-ttu-id="89b58-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89b58-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89b58-117">**Nagłówek:** Metahost.idl, Metahost.h</span><span class="sxs-lookup"><span data-stu-id="89b58-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="89b58-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89b58-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89b58-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89b58-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b58-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89b58-120">See Also</span></span>  
 [<span data-ttu-id="89b58-121">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="89b58-121">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="89b58-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="89b58-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
