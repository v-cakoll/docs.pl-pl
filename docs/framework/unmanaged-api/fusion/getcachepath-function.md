---
title: GetCachePath — Funkcja
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92366190c769344b41923cbb25ed4b04afceaae9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778671"
---
# <a name="getcachepath-function"></a><span data-ttu-id="7876b-102">GetCachePath — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7876b-102">GetCachePath Function</span></span>
<span data-ttu-id="7876b-103">Pobiera ścieżkę do zestawu pamięci podręcznej, przy użyciu określonych flag.</span><span class="sxs-lookup"><span data-stu-id="7876b-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7876b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7876b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7876b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7876b-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="7876b-106">[in] [Asm_cache_flags —](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) wartość, która wskazuje źródło pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="7876b-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="7876b-107">[out] Zwrócony wskaźnik do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="7876b-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="7876b-108">[out w] Żądana długość maksymalna `pwzCachePath`, a po powrocie, rzeczywista długość `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="7876b-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7876b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7876b-109">Requirements</span></span>  
 <span data-ttu-id="7876b-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7876b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7876b-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7876b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7876b-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7876b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7876b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7876b-113">See also</span></span>

- [<span data-ttu-id="7876b-114">ASM_CACHE_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7876b-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)
- [<span data-ttu-id="7876b-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="7876b-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
