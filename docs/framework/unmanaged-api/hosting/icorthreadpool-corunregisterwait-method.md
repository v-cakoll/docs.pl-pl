---
title: ICorThreadpool::CorUnregisterWait — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af41a20bcdcbfc44a5a4b0b30947ab9093948291
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122840"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="c1c5f-102">ICorThreadpool::CorUnregisterWait — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1c5f-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="c1c5f-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c1c5f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1c5f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1c5f-104">Syntax</span></span>  
  
```  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c1c5f-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1c5f-105">Requirements</span></span>  
 <span data-ttu-id="c1c5f-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1c5f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1c5f-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1c5f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1c5f-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1c5f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c1c5f-109">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c1c5f-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c1c5f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1c5f-110">See also</span></span>

- [<span data-ttu-id="c1c5f-111">ICorThreadpool — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c1c5f-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
