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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e374c03ca90c904cd4ef8a4585cb35ccf43cb43
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766526"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="67a5b-102">IGCHost::GetStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="67a5b-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="67a5b-103">Pobiera statystyki dla bieżącego stanu systemu czyszczenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="67a5b-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67a5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67a5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67a5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="67a5b-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="67a5b-106">[out w] Wskaźnik do [cor_gc_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) strukturę, która zawiera dane statystyczne dla bieżącego stanu systemu kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="67a5b-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67a5b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67a5b-107">Remarks</span></span>  
 <span data-ttu-id="67a5b-108">Statystyki można przez system inteligentne alokacji systemu kolekcji wyrzucania elementów działania pomocy.</span><span class="sxs-lookup"><span data-stu-id="67a5b-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="67a5b-109">Na przykład system alokacji może określić, po zapoznaniu się z statystyki, którą chce dodać większej ilości pamięci lub wymusić kolekcji.</span><span class="sxs-lookup"><span data-stu-id="67a5b-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67a5b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67a5b-110">Requirements</span></span>  
 <span data-ttu-id="67a5b-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67a5b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67a5b-112">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="67a5b-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="67a5b-113">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="67a5b-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67a5b-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67a5b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a5b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67a5b-115">See also</span></span>

- [<span data-ttu-id="67a5b-116">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="67a5b-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
