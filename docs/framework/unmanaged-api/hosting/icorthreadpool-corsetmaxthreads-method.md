---
title: ICorThreadpool::CorSetMaxThreads — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorSetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48d84d5c45ea8e1af1da44480410692d46162810
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198247"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="955ec-102">ICorThreadpool::CorSetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="955ec-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="955ec-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="955ec-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="955ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="955ec-104">Syntax</span></span>  
  
```  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="955ec-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="955ec-105">Requirements</span></span>  
 <span data-ttu-id="955ec-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="955ec-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="955ec-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="955ec-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="955ec-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="955ec-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="955ec-109">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="955ec-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="955ec-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="955ec-110">See also</span></span>

- [<span data-ttu-id="955ec-111">ICorThreadpool — Interfejs</span><span class="sxs-lookup"><span data-stu-id="955ec-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
