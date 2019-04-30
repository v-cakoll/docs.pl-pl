---
title: ICorConfiguration::SetGCThreadControl — Metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b50c87efeb8ad2311a75886da677a9dc901bca1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763233"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="6eff7-102">ICorConfiguration::SetGCThreadControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="6eff7-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="6eff7-103">Określa interfejs wywołania zwrotnego, planowanie wątków dla zadań innych niż środowiska uruchomieniowego, które w przeciwnym razie zostałby zablokowany dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6eff7-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eff7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6eff7-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eff7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6eff7-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="6eff7-106">[in] Wskaźnik do [igcthreadcontrol —](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) obiektu, która powiadamia hosta, dotyczące zawieszenia wątki zadań innych niż środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6eff7-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eff7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6eff7-107">Remarks</span></span>  
 <span data-ttu-id="6eff7-108">Host może wybrać w ramach [igcthreadcontrol::threadisblockingforsuspension —](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) wywołania zwrotnego czy zmienić termin egzaminu wątku.</span><span class="sxs-lookup"><span data-stu-id="6eff7-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eff7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6eff7-109">Requirements</span></span>  
 <span data-ttu-id="6eff7-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eff7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eff7-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6eff7-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6eff7-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6eff7-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6eff7-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eff7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eff7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6eff7-114">See also</span></span>

- [<span data-ttu-id="6eff7-115">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="6eff7-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
