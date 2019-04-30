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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699584"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="f1d29-102">ICorThreadpool::CorUnregisterWait — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1d29-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="f1d29-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f1d29-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1d29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1d29-104">Syntax</span></span>  
  
```  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f1d29-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1d29-105">Requirements</span></span>  
 <span data-ttu-id="f1d29-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1d29-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1d29-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f1d29-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1d29-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1d29-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1d29-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1d29-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d29-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1d29-110">See also</span></span>

- [<span data-ttu-id="f1d29-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="f1d29-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
