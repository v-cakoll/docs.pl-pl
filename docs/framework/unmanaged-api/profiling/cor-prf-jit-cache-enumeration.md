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
ms.openlocfilehash: d19d7ed2262db6d3c6e7f15db0e96da52f86db4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500861"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="2f4a3-102">COR_PRF_JIT_CACHE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2f4a3-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="2f4a3-103">Wskazuje wynik funkcji wyszukiwania w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2f4a3-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f4a3-104">`COR_PRF_CACHED_FUNCTION_FOUND`ma wartość zero, więc `COR_PRF_JIT_CACHE` nie może być używana jako surogat wartości logicznej.</span><span class="sxs-lookup"><span data-stu-id="2f4a3-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f4a3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f4a3-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="2f4a3-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2f4a3-106">Members</span></span>  
  
|<span data-ttu-id="2f4a3-107">Członek</span><span class="sxs-lookup"><span data-stu-id="2f4a3-107">Member</span></span>|<span data-ttu-id="2f4a3-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2f4a3-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="2f4a3-109">Wyszukiwanie odnalazło funkcję.</span><span class="sxs-lookup"><span data-stu-id="2f4a3-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="2f4a3-110">Wyszukiwanie nie znalazło funkcji.</span><span class="sxs-lookup"><span data-stu-id="2f4a3-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f4a3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f4a3-111">Requirements</span></span>  
 <span data-ttu-id="2f4a3-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f4a3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f4a3-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2f4a3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f4a3-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2f4a3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f4a3-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f4a3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4a3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f4a3-116">See also</span></span>

- [<span data-ttu-id="2f4a3-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2f4a3-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
