---
title: ICorThreadpool::CorBindIoCompletionCallback — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorBindIoCompletionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorBindIoCompletionCallback
helpviewer_keywords:
- CorBindIoCompletionCallback method [.NET Framework hosting]
- ICorThreadpool::CorBindIoCompletionCallback method [.NET Framework hosting]
ms.assetid: 2b159225-f09c-42f1-aa7c-44087e121249
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3faffbf9dc85c563dac84fc2e4e4d849db5d42d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148528"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="beafd-102">ICorThreadpool::CorBindIoCompletionCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="beafd-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="beafd-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="beafd-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beafd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="beafd-104">Syntax</span></span>  
  
```  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="beafd-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="beafd-105">Requirements</span></span>  
 <span data-ttu-id="beafd-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beafd-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beafd-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="beafd-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="beafd-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="beafd-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="beafd-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beafd-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beafd-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="beafd-110">See also</span></span>

- [<span data-ttu-id="beafd-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="beafd-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
