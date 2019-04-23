---
title: IDebuggerThreadControl::StartBlockingForDebugger — Metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfc94c2de1a14842cc017e5c4ef6023154c20f2a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194035"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="902c4-102">IDebuggerThreadControl::StartBlockingForDebugger — Metoda</span><span class="sxs-lookup"><span data-stu-id="902c4-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="902c4-103">Powiadamia hosta, że usług debugowania zamiar start blokuje wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="902c4-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="902c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="902c4-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="902c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="902c4-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="902c4-106">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="902c4-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="902c4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="902c4-107">Remarks</span></span>  
 <span data-ttu-id="902c4-108">`StartBlockingForDebugger` w wątku środowiska uruchomieniowego można wywołać metody.</span><span class="sxs-lookup"><span data-stu-id="902c4-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="902c4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="902c4-109">Requirements</span></span>  
 <span data-ttu-id="902c4-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="902c4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="902c4-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="902c4-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="902c4-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="902c4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="902c4-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="902c4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902c4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="902c4-114">See also</span></span>

- [<span data-ttu-id="902c4-115">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="902c4-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
