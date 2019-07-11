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
ms.openlocfilehash: 7bd983a41307a4244b5426b8f6b997569cd631e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770507"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="39640-102">IApartmentCallback::DoCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="39640-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="39640-103">Wykonuje określoną funkcję w ramach typu apartment.</span><span class="sxs-lookup"><span data-stu-id="39640-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39640-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39640-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39640-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39640-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="39640-106">[in] Wskaźnik do funkcji, które mają być wykonane w ramach typu apartment.</span><span class="sxs-lookup"><span data-stu-id="39640-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="39640-107">[in] Wskaźnik do argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="39640-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39640-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39640-108">Requirements</span></span>  
 <span data-ttu-id="39640-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39640-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39640-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="39640-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39640-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39640-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39640-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39640-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39640-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39640-113">See also</span></span>

- [<span data-ttu-id="39640-114">IApartmentCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="39640-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
