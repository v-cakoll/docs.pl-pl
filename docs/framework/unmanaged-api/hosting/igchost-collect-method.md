---
title: IGCHost::Collect — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f911d99470b9870f5c42d4170a4024123c10e7f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511124"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="57cad-102">IGCHost::Collect — Metoda</span><span class="sxs-lookup"><span data-stu-id="57cad-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="57cad-103">Wymusza kolekcji wystąpi dla danej generacji, bez względu na stan bieżącej operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="57cad-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57cad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57cad-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57cad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57cad-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="57cad-106">[in] Generowanie, na którym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="57cad-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="57cad-107">Wartość -1 wskazuje, że wszystkie generacje zostaną poddane wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="57cad-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57cad-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57cad-108">Requirements</span></span>  
 <span data-ttu-id="57cad-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57cad-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57cad-110">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="57cad-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="57cad-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57cad-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57cad-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57cad-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57cad-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57cad-113">See also</span></span>
- [<span data-ttu-id="57cad-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="57cad-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
