---
title: "IApartmentCallback::DoCallback — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IApartmentCallback.DoCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03c72af5fba0871433e46c2b8045c55bbf0a5ff6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="7f47a-102">IApartmentCallback::DoCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f47a-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="7f47a-103">Wykonuje określoną funkcję w apartamencie.</span><span class="sxs-lookup"><span data-stu-id="7f47a-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f47a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f47a-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f47a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f47a-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="7f47a-106">[in] Wskaźnik do funkcję, która ma zostać wykonana w obrębie apartamencie.</span><span class="sxs-lookup"><span data-stu-id="7f47a-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="7f47a-107">[in] Wskaźnik do argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f47a-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f47a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f47a-108">Requirements</span></span>  
 <span data-ttu-id="7f47a-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f47a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f47a-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7f47a-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f47a-111">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f47a-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f47a-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f47a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f47a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f47a-113">See Also</span></span>  
 [<span data-ttu-id="7f47a-114">IApartmentCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="7f47a-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
