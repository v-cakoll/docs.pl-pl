---
title: IApartmentCallback::DoCallback — Metoda
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77a2ccaf6f972fadd8396378dc7777ec4c85120d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110230"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="e08e6-102">IApartmentCallback::DoCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="e08e6-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="e08e6-103">Wykonuje określoną funkcję w ramach typu apartment.</span><span class="sxs-lookup"><span data-stu-id="e08e6-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e08e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e08e6-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e08e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e08e6-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="e08e6-106">[in] Wskaźnik do funkcji, które mają być wykonane w ramach typu apartment.</span><span class="sxs-lookup"><span data-stu-id="e08e6-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="e08e6-107">[in] Wskaźnik do argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="e08e6-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e08e6-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e08e6-108">Requirements</span></span>  
 <span data-ttu-id="e08e6-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e08e6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e08e6-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e08e6-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e08e6-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e08e6-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e08e6-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e08e6-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e08e6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e08e6-113">See also</span></span>

- [<span data-ttu-id="e08e6-114">IApartmentCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e08e6-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
