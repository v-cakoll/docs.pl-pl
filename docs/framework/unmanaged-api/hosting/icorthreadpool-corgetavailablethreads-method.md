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
ms.openlocfilehash: 20b600eb50ca4992e20b991406d18a91feae5c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574459"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="28b43-102">ICorThreadpool::CorGetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="28b43-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="28b43-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="28b43-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b43-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28b43-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="28b43-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28b43-105">Requirements</span></span>  
 <span data-ttu-id="28b43-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28b43-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28b43-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28b43-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28b43-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28b43-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28b43-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28b43-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b43-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28b43-110">See also</span></span>
- [<span data-ttu-id="28b43-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="28b43-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
