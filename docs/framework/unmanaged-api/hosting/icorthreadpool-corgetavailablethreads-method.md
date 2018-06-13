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
ms.openlocfilehash: 7c4867760807af1bc16f7935923cc2b89c1bfba6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436897"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="d83b1-102">ICorThreadpool::CorGetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="d83b1-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="d83b1-103">Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d83b1-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d83b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d83b1-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d83b1-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d83b1-105">Requirements</span></span>  
 <span data-ttu-id="d83b1-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d83b1-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d83b1-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d83b1-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d83b1-108">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d83b1-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d83b1-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d83b1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83b1-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d83b1-110">See Also</span></span>  
 [<span data-ttu-id="d83b1-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="d83b1-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
