---
title: ICorThreadpool::CorDeleteTimer — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6870af271f7169d9f0ad1bff99dffe4ea4cf3a62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437225"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="65ae3-102">ICorThreadpool::CorDeleteTimer — Metoda</span><span class="sxs-lookup"><span data-stu-id="65ae3-102">ICorThreadpool::CorDeleteTimer Method</span></span>
<span data-ttu-id="65ae3-103">Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="65ae3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ae3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65ae3-104">Syntax</span></span>  
  
```  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="65ae3-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65ae3-105">Requirements</span></span>  
 <span data-ttu-id="65ae3-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ae3-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ae3-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65ae3-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65ae3-108">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65ae3-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65ae3-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ae3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ae3-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65ae3-110">See Also</span></span>  
 [<span data-ttu-id="65ae3-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="65ae3-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
