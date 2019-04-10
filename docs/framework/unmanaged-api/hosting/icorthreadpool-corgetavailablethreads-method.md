---
title: ICorThreadpool::CorGetAvailableThreads — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c929b9434507ea7cce936767f2ac72ff98fda7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215797"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="b3314-102">ICorThreadpool::CorGetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3314-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="b3314-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b3314-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3314-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3314-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b3314-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3314-105">Requirements</span></span>  
 <span data-ttu-id="b3314-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3314-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3314-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3314-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3314-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3314-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b3314-109">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b3314-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b3314-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3314-110">See also</span></span>

- [<span data-ttu-id="b3314-111">ICorThreadpool — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b3314-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
