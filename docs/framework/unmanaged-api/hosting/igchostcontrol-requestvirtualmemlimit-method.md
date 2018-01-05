---
title: "IGCHostControl::RequestVirtualMemLimit — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHostControl.RequestVirtualMemLimit
api_location: mscoree.dll
api_type: COM
f1_keywords: RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a14cb0d2d34db4ea0e5f9abf6fba6efc5e5a950c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="c3d07-102">IGCHostControl::RequestVirtualMemLimit — Metoda</span><span class="sxs-lookup"><span data-stu-id="c3d07-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="c3d07-103">Żąda hosta, aby zmienić limit pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c3d07-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d07-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3d07-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3d07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3d07-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="c3d07-106">[in] Żądany rozmiar pamięci do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="c3d07-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="c3d07-107">[w, out] Wskaźnik do rzeczywistego rozmiaru przydzielonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="c3d07-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3d07-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3d07-108">Requirements</span></span>  
 <span data-ttu-id="c3d07-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3d07-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3d07-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c3d07-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3d07-111">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3d07-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3d07-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3d07-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d07-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3d07-113">See Also</span></span>  
 [<span data-ttu-id="c3d07-114">IGCHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3d07-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
