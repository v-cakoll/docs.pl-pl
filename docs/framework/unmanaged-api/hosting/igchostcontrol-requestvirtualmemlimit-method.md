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
ms.openlocfilehash: d4814e44b1a5311cf6800c804df7a7e11000cbab
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805133"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="c4101-102">IGCHostControl::RequestVirtualMemLimit — Metoda</span><span class="sxs-lookup"><span data-stu-id="c4101-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="c4101-103">Żąda od hosta zmiany limitów pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c4101-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4101-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4101-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4101-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4101-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="c4101-106">podczas Żądany rozmiar pamięci do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="c4101-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="c4101-107">[in. out] Wskaźnik do rzeczywistego rozmiaru przydzieloną pamięci.</span><span class="sxs-lookup"><span data-stu-id="c4101-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4101-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4101-108">Requirements</span></span>  
 <span data-ttu-id="c4101-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4101-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4101-110">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c4101-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4101-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c4101-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4101-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4101-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4101-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4101-113">See also</span></span>

- [<span data-ttu-id="c4101-114">IGCHostControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c4101-114">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)
