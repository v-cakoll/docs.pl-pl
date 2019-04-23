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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110230"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="1984e-102">IApartmentCallback::DoCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="1984e-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="1984e-103">Wykonuje określoną funkcję w ramach typu apartment.</span><span class="sxs-lookup"><span data-stu-id="1984e-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1984e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1984e-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1984e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1984e-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="1984e-106">[in] Wskaźnik do funkcji, które mają być wykonane w ramach typu apartment.</span><span class="sxs-lookup"><span data-stu-id="1984e-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="1984e-107">[in] Wskaźnik do argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="1984e-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1984e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1984e-108">Requirements</span></span>  
 <span data-ttu-id="1984e-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1984e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1984e-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1984e-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1984e-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1984e-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1984e-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1984e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1984e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1984e-113">See also</span></span>

- [<span data-ttu-id="1984e-114">IApartmentCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="1984e-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
