---
title: ICorThreadpool::CorRegisterWaitForSingleObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorRegisterWaitForSingleObject
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegisterWaitForSingleObject
helpviewer_keywords:
- ICorThreadpool::CorRegisterWaitForSingleObject method [.NET Framework hosting]
- CorRegisterWaitForSingleObject method [.NET Framework hosting]
ms.assetid: cade1feb-71d2-43ed-85ca-7b2e9da12994
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8198bef4a479499724b07da245f40aa9d9f4c265
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437102"
---
# <a name="icorthreadpoolcorregisterwaitforsingleobject-method"></a><span data-ttu-id="365fb-102">ICorThreadpool::CorRegisterWaitForSingleObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="365fb-102">ICorThreadpool::CorRegisterWaitForSingleObject Method</span></span>
<span data-ttu-id="365fb-103">Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="365fb-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="365fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="365fb-104">Syntax</span></span>  
  
```  
HRESULT CorRegisterWaitForSingleObject (  
    [in]  HANDLE*             phNewWaitObject,  
    [in]  HANDLE              hWaitObject,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Context,  
    [in]  ULONG               timeout,  
    [in]  BOOL                executeOnlyOnce,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="365fb-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="365fb-105">Requirements</span></span>  
 <span data-ttu-id="365fb-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="365fb-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="365fb-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="365fb-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="365fb-108">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="365fb-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="365fb-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="365fb-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365fb-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="365fb-110">See Also</span></span>  
 [<span data-ttu-id="365fb-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="365fb-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
