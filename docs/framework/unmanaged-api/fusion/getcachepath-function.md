---
title: "GetCachePath — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 371dab83d7441681b9d6bd5723bcd8c3caadb50e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getcachepath-function"></a><span data-ttu-id="b03a1-102">GetCachePath — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b03a1-102">GetCachePath Function</span></span>
<span data-ttu-id="b03a1-103">Pobiera ścieżkę do zestawu pamięci podręcznej, przy użyciu określonych flag.</span><span class="sxs-lookup"><span data-stu-id="b03a1-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b03a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b03a1-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b03a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b03a1-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="b03a1-106">[in] [Asm_cache_flags —](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) wartość, która wskazuje źródło pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b03a1-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="b03a1-107">[out] Zwrócony wskaźnik do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b03a1-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="b03a1-108">[w, out] Żądana długość maksymalna `pwzCachePath`, a po powrocie, z rzeczywistą długością `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="b03a1-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b03a1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b03a1-109">Requirements</span></span>  
 <span data-ttu-id="b03a1-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b03a1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b03a1-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b03a1-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b03a1-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b03a1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b03a1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b03a1-113">See Also</span></span>  
 [<span data-ttu-id="b03a1-114">ASM_CACHE_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b03a1-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 [<span data-ttu-id="b03a1-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="b03a1-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
