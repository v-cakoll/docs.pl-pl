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
ms.openlocfilehash: 6c7cb97acbf089221f498ce9edcafb114ddeef27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496901"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="44849-102">ICorThreadpool::CorSetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="44849-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="44849-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="44849-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44849-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44849-104">Syntax</span></span>  
  
```  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="44849-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44849-105">Requirements</span></span>  
 <span data-ttu-id="44849-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44849-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44849-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="44849-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44849-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44849-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44849-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44849-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44849-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44849-110">See also</span></span>
- [<span data-ttu-id="44849-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="44849-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
