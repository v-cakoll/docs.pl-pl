---
title: IGCHost::GetStats — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
ms.openlocfilehash: c86786a34ff236fb57a1ea6bc4d00b9cd5c4a717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134893"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="a83a2-102">IGCHost::GetStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="a83a2-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="a83a2-103">Pobiera statystyki bieżącego stanu systemu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="a83a2-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a83a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a83a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a83a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a83a2-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="a83a2-106">[in. out] Wskaźnik do struktury [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) , który zawiera statystyki dotyczące bieżącego stanu systemu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="a83a2-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a83a2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a83a2-107">Remarks</span></span>  
 <span data-ttu-id="a83a2-108">Dane statystyczne mogą być używane przez system alokacji inteligentnej, aby ułatwić działanie systemu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a83a2-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="a83a2-109">Na przykład system alokacji może określić, po przejrzeniu statystyk, że należy dodać więcej pamięci lub wymusić zbieranie danych.</span><span class="sxs-lookup"><span data-stu-id="a83a2-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a83a2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a83a2-110">Requirements</span></span>  
 <span data-ttu-id="a83a2-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a83a2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a83a2-112">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="a83a2-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="a83a2-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a83a2-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a83a2-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a83a2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a83a2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a83a2-115">See also</span></span>

- [<span data-ttu-id="a83a2-116">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="a83a2-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
