---
title: IGCHost2::SetGCStartupLimitsEx — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f92667191cad163998d233e1110365de65c0340c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437693"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="6266d-102">IGCHost2::SetGCStartupLimitsEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="6266d-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="6266d-103">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="6266d-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6266d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6266d-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6266d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6266d-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="6266d-106">[in] Rozmiar segmentu używaną przez system kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="6266d-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="6266d-107">[in] Maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="6266d-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6266d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6266d-108">Remarks</span></span>  
 <span data-ttu-id="6266d-109">Wartości który `SetGCStartupLimitsEx` zestawy można określić jedynie, aby uruchomić hosta.</span><span class="sxs-lookup"><span data-stu-id="6266d-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="6266d-110">Nie można później zmienić tych wartości.</span><span class="sxs-lookup"><span data-stu-id="6266d-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6266d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6266d-111">Requirements</span></span>  
 <span data-ttu-id="6266d-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6266d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6266d-113">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="6266d-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="6266d-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6266d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6266d-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6266d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6266d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6266d-116">See Also</span></span>  
 [<span data-ttu-id="6266d-117">IGCHost2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6266d-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
