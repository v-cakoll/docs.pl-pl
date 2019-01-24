---
title: IGCHostControl::RequestVirtualMemLimit — Metoda
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db1572c035242a4a143ee435957409e5d16fca1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607176"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="168b1-102">IGCHostControl::RequestVirtualMemLimit — Metoda</span><span class="sxs-lookup"><span data-stu-id="168b1-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="168b1-103">Żąda hosta, aby zmienić limity pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="168b1-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="168b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="168b1-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="168b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="168b1-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="168b1-106">[in] Żądany rozmiar pamięci do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="168b1-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="168b1-107">[out w] Wskaźnik do rzeczywistego rozmiaru pamięci przydzielonej.</span><span class="sxs-lookup"><span data-stu-id="168b1-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="168b1-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="168b1-108">Requirements</span></span>  
 <span data-ttu-id="168b1-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="168b1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="168b1-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="168b1-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="168b1-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="168b1-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="168b1-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="168b1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="168b1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="168b1-113">See also</span></span>
- [<span data-ttu-id="168b1-114">IGCHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="168b1-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
