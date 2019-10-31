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
ms.openlocfilehash: c060e4883335a8318970b5fbd74bf72c9e13f5bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134862"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="2ee43-102">IGCHost::SetVirtualMemLimit — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ee43-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="2ee43-103">Ustawia maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2ee43-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee43-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ee43-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ee43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ee43-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="2ee43-106">podczas Maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego (w megabajtach).</span><span class="sxs-lookup"><span data-stu-id="2ee43-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ee43-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ee43-107">Remarks</span></span>  
 <span data-ttu-id="2ee43-108">Maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego można zmienić dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="2ee43-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ee43-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ee43-109">Requirements</span></span>  
 <span data-ttu-id="2ee43-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ee43-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ee43-111">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="2ee43-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="2ee43-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2ee43-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ee43-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ee43-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee43-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ee43-114">See also</span></span>

- [<span data-ttu-id="2ee43-115">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ee43-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
