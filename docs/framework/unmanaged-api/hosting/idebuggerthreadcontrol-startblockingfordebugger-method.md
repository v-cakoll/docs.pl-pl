---
title: "IDebuggerThreadControl::StartBlockingForDebugger — Metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99c0bc78705fa07883d92bf0cc1d90300c5ac549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="4cedf-102">IDebuggerThreadControl::StartBlockingForDebugger — Metoda</span><span class="sxs-lookup"><span data-stu-id="4cedf-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="4cedf-103">Powiadamia host czy usług debugowania rozpoczęcia blokuje wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="4cedf-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cedf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cedf-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cedf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cedf-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="4cedf-106">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="4cedf-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cedf-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4cedf-107">Remarks</span></span>  
 <span data-ttu-id="4cedf-108">`StartBlockingForDebugger` Można można wywołać metody dla wątku czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4cedf-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cedf-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4cedf-109">Requirements</span></span>  
 <span data-ttu-id="4cedf-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cedf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cedf-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4cedf-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cedf-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4cedf-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cedf-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cedf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cedf-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cedf-114">See Also</span></span>  
 [<span data-ttu-id="4cedf-115">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="4cedf-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
