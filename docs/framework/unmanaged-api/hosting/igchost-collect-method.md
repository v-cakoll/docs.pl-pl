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
ms.openlocfilehash: 9c4fa79f4918412720592bce449a001a349ae657
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766566"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="675a4-102">IGCHost::Collect — Metoda</span><span class="sxs-lookup"><span data-stu-id="675a4-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="675a4-103">Wymusza kolekcji wystąpi dla danej generacji, bez względu na stan bieżącej operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="675a4-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="675a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="675a4-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="675a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="675a4-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="675a4-106">[in] Generowanie, na którym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="675a4-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="675a4-107">Wartość -1 wskazuje, że wszystkie generacje zostaną poddane wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="675a4-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="675a4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="675a4-108">Requirements</span></span>  
 <span data-ttu-id="675a4-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="675a4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="675a4-110">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="675a4-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="675a4-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="675a4-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="675a4-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="675a4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="675a4-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="675a4-113">See also</span></span>

- [<span data-ttu-id="675a4-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="675a4-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
