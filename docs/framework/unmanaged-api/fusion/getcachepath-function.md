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
ms.openlocfilehash: 13e1468ef5a48f18910c1f8082cdd7c4849da14a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132696"
---
# <a name="getcachepath-function"></a><span data-ttu-id="c27f2-102">GetCachePath — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c27f2-102">GetCachePath Function</span></span>
<span data-ttu-id="c27f2-103">Pobiera ścieżkę do buforowanego zestawu przy użyciu określonych flag.</span><span class="sxs-lookup"><span data-stu-id="c27f2-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c27f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c27f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c27f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c27f2-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="c27f2-106">podczas Wartość [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) , która wskazuje Źródło buforowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c27f2-106">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="c27f2-107">określoną Zwrócony wskaźnik do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c27f2-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="c27f2-108">[in. out] Żądana Maksymalna długość `pwzCachePath`i po powrocie, rzeczywista długość `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="c27f2-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c27f2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c27f2-109">Requirements</span></span>  
 <span data-ttu-id="c27f2-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c27f2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c27f2-111">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c27f2-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c27f2-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c27f2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c27f2-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c27f2-113">See also</span></span>

- [<span data-ttu-id="c27f2-114">ASM_CACHE_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c27f2-114">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="c27f2-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="c27f2-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
