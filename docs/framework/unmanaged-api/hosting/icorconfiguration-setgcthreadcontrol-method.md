---
title: "ICorConfiguration::SetGCThreadControl — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.SetGCThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1dfcff8a12f808c75a9e69486f802f8b886c468b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="1cfcf-102">ICorConfiguration::SetGCThreadControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="1cfcf-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="1cfcf-103">Określa interfejs wywołania zwrotnego dla planowania wątków dla zadań z systemem innym niż środowisko uruchomieniowe, które można zablokować dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1cfcf-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cfcf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1cfcf-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cfcf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cfcf-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="1cfcf-106">[in] Wskaźnik do [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) obiekt, który powiadamia hosta o zawieszenie wątków dla zadań innych niż środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="1cfcf-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cfcf-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1cfcf-107">Remarks</span></span>  
 <span data-ttu-id="1cfcf-108">Host może wybrać w ramach [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) wywołania zwrotnego czy należy zaplanować wątku.</span><span class="sxs-lookup"><span data-stu-id="1cfcf-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cfcf-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1cfcf-109">Requirements</span></span>  
 <span data-ttu-id="1cfcf-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cfcf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cfcf-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1cfcf-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1cfcf-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1cfcf-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1cfcf-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cfcf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cfcf-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1cfcf-114">See Also</span></span>  
 [<span data-ttu-id="1cfcf-115">ICorConfiguration — interfejs</span><span class="sxs-lookup"><span data-stu-id="1cfcf-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
