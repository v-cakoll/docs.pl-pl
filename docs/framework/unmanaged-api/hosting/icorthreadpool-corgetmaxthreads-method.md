---
title: ICorThreadpool::CorGetMaxThreads — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbf5c02972a8331b3dd5e35ffcc4213e094e532d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175737"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="fdeb2-102">ICorThreadpool::CorGetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="fdeb2-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="fdeb2-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="fdeb2-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdeb2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdeb2-104">Syntax</span></span>  
  
```  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fdeb2-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdeb2-105">Requirements</span></span>  
 <span data-ttu-id="fdeb2-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdeb2-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdeb2-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fdeb2-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fdeb2-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fdeb2-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdeb2-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdeb2-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdeb2-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdeb2-110">See also</span></span>

- [<span data-ttu-id="fdeb2-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="fdeb2-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
