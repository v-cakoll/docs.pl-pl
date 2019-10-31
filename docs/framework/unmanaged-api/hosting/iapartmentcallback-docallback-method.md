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
ms.openlocfilehash: 9bb257a3d84d5022b9ae13c89a34572485d3033b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126942"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="18b89-102">IApartmentCallback::DoCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="18b89-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="18b89-103">Wykonuje określoną funkcję w obrębie apartamentu.</span><span class="sxs-lookup"><span data-stu-id="18b89-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18b89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="18b89-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18b89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18b89-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="18b89-106">podczas Wskaźnik do funkcji, która ma zostać wykonana w obrębie apartamentu.</span><span class="sxs-lookup"><span data-stu-id="18b89-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="18b89-107">podczas Wskaźnik do argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="18b89-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18b89-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18b89-108">Requirements</span></span>  
 <span data-ttu-id="18b89-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18b89-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18b89-110">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="18b89-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18b89-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="18b89-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18b89-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18b89-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b89-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18b89-113">See also</span></span>

- [<span data-ttu-id="18b89-114">IApartmentCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="18b89-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
