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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700764"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="d3d33-102">ICorThreadpool::CorBindIoCompletionCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3d33-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="d3d33-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d3d33-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3d33-104">Syntax</span></span>  
  
```  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d3d33-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3d33-105">Requirements</span></span>  
 <span data-ttu-id="d3d33-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d33-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d33-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3d33-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3d33-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3d33-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3d33-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d33-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d33-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3d33-110">See also</span></span>

- [<span data-ttu-id="d3d33-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3d33-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
