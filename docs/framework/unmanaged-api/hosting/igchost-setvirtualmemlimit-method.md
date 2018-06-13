---
title: IGCHost::SetVirtualMemLimit — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1d61c8aeaf458d8cbbd2976fa83aaa0eeb0f834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437742"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="8d22e-102">IGCHost::SetVirtualMemLimit — Metoda</span><span class="sxs-lookup"><span data-stu-id="8d22e-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="8d22e-103">Ustawia maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8d22e-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d22e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d22e-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d22e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d22e-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="8d22e-106">[in] Rozmiar maksymalny wyrażony w megabajtach ilość pamięci wirtualnej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8d22e-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d22e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d22e-107">Remarks</span></span>  
 <span data-ttu-id="8d22e-108">Maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego można zmienić dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="8d22e-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d22e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d22e-109">Requirements</span></span>  
 <span data-ttu-id="8d22e-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d22e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d22e-111">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="8d22e-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="8d22e-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d22e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d22e-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d22e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d22e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d22e-114">See Also</span></span>  
 [<span data-ttu-id="8d22e-115">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="8d22e-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
