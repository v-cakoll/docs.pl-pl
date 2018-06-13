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
ms.openlocfilehash: c25f39cf64f462ac319803354e6a2a54ea482b9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436939"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="99c6c-102">ICorThreadpool::CorGetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="99c6c-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="99c6c-103">Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="99c6c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99c6c-104">Syntax</span></span>  
  
```  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="99c6c-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99c6c-105">Requirements</span></span>  
 <span data-ttu-id="99c6c-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99c6c-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99c6c-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99c6c-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99c6c-108">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99c6c-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99c6c-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99c6c-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c6c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99c6c-110">See Also</span></span>  
 [<span data-ttu-id="99c6c-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="99c6c-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
