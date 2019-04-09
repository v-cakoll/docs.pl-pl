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
ms.openlocfilehash: b5b4210bda7d41b190f1025b62132c5df896a2a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088395"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="8fa89-102">IGCHost::SetVirtualMemLimit — Metoda</span><span class="sxs-lookup"><span data-stu-id="8fa89-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="8fa89-103">Ustawia maksymalny rozmiar pamięci wirtualnej w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="8fa89-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fa89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fa89-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fa89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fa89-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="8fa89-106">[in] Maksymalny rozmiar w megabajtach pamięci wirtualnej w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="8fa89-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fa89-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8fa89-107">Remarks</span></span>  
 <span data-ttu-id="8fa89-108">Maksymalny rozmiar pamięci wirtualnej w środowisku uruchomieniowym można dynamicznie zmieniać.</span><span class="sxs-lookup"><span data-stu-id="8fa89-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fa89-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fa89-109">Requirements</span></span>  
 <span data-ttu-id="8fa89-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fa89-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fa89-111">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="8fa89-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="8fa89-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fa89-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8fa89-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8fa89-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8fa89-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fa89-114">See also</span></span>

- [<span data-ttu-id="8fa89-115">IGCHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8fa89-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
