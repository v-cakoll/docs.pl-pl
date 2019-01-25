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
ms.openlocfilehash: 609bb050bb9c5addb5250f65a059a70d3ce32428
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662247"
---
# <a name="clrdebuggingprocessflags-enumeration"></a><span data-ttu-id="c0326-102">CLR_DEBUGGING_PROCESS_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c0326-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="c0326-103">Zawiera wartości, które są używane przez [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c0326-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0326-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0326-104">Syntax</span></span>  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c0326-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c0326-105">Members</span></span>  
  
|<span data-ttu-id="c0326-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c0326-106">Member</span></span>|<span data-ttu-id="c0326-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c0326-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="c0326-108">To środowisko uruchomieniowe ma zdarzenia-się w górę catch zarządzanego debugera do wysłania.</span><span class="sxs-lookup"><span data-stu-id="c0326-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="c0326-109">Zobacz sekcję Uwagi w celu dokonania rozróżnienia między zdarzeniami zapoznać się ze zmianami i się w górę catch.</span><span class="sxs-lookup"><span data-stu-id="c0326-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="c0326-110">To zdarzenie zarządzane, który jest w stanie oczekiwania <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> żądania.</span><span class="sxs-lookup"><span data-stu-id="c0326-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0326-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0326-111">Remarks</span></span>  
 <span data-ttu-id="c0326-112">Zdarzenia — wyrównywanie obejmują procesu domeny aplikacji, zestawu, modułu i powiadomienia o tworzenia wątku, które ożywiają debugera do bieżącego stanu po został on dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="c0326-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="c0326-113">Zdarzenia non-catch-up, które są wskazywane przez `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flagi, zawierają wszystkie inne zdarzenia debugera, takie jak wyjątki i zarządzanego debugowania (MDA) Asystenta ustawień powiadomień.</span><span class="sxs-lookup"><span data-stu-id="c0326-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="c0326-114">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Flagi włącza środowisko uruchomieniowe do rozróżniania wyjątek powodujący przerwanie oraz żądanie dołączenia zarządzanych debugerów, który może być anulowany.</span><span class="sxs-lookup"><span data-stu-id="c0326-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0326-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0326-115">Requirements</span></span>  
 <span data-ttu-id="c0326-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0326-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0326-117">**Nagłówek:** Metahost.IDL, Metahost.h</span><span class="sxs-lookup"><span data-stu-id="c0326-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="c0326-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0326-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0326-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0326-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0326-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0326-120">See also</span></span>
- [<span data-ttu-id="c0326-121">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c0326-121">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="c0326-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c0326-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
