---
title: COR_PRF_JIT_CACHE — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_JIT_CACHE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_JIT_CACHE
helpviewer_keywords:
- COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30500e8ea55f8298b9a980e34dc611b58a51bdcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916400"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="6373e-102">COR_PRF_JIT_CACHE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6373e-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="6373e-103">Wskazuje wynik funkcji wyszukiwania w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6373e-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6373e-104">`COR_PRF_CACHED_FUNCTION_FOUND`ma wartość zero, więc `COR_PRF_JIT_CACHE` nie może być używana jako surogat wartości logicznej.</span><span class="sxs-lookup"><span data-stu-id="6373e-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6373e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6373e-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="6373e-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6373e-106">Members</span></span>  
  
|<span data-ttu-id="6373e-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6373e-107">Member</span></span>|<span data-ttu-id="6373e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6373e-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="6373e-109">Wyszukiwanie odnalazło funkcję.</span><span class="sxs-lookup"><span data-stu-id="6373e-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="6373e-110">Wyszukiwanie nie znalazło funkcji.</span><span class="sxs-lookup"><span data-stu-id="6373e-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6373e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6373e-111">Requirements</span></span>  
 <span data-ttu-id="6373e-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6373e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6373e-113">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6373e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6373e-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6373e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6373e-115">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6373e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6373e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6373e-116">See also</span></span>

- [<span data-ttu-id="6373e-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6373e-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
