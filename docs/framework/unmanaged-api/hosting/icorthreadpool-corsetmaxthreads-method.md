---
title: "ICorThreadpool::CorSetMaxThreads — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorSetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 384b214ac38eb99ce45bf3050f33f35702813c69
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="2e556-102">ICorThreadpool::CorSetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e556-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="2e556-103">Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2e556-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e556-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e556-104">Syntax</span></span>  
  
```  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2e556-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e556-105">Requirements</span></span>  
 <span data-ttu-id="2e556-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e556-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e556-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2e556-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e556-108">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e556-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e556-109">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e556-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e556-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e556-110">See Also</span></span>  
 [<span data-ttu-id="2e556-111">ICorThreadpool — interfejs</span><span class="sxs-lookup"><span data-stu-id="2e556-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
