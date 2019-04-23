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
ms.openlocfilehash: 0cdbe36403f830926d611ffdc655d82ea25ddeef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144797"
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="b76a6-102">COR_PRF_JIT_CACHE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b76a6-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="b76a6-103">Wskazuje wynik wyszukiwania funkcję pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b76a6-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b76a6-104">`COR_PRF_CACHED_FUNCTION_FOUND` ma wartość zero, więc `COR_PRF_JIT_CACHE` nie można użyć jako logiczna zastępczy.</span><span class="sxs-lookup"><span data-stu-id="b76a6-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b76a6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b76a6-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="b76a6-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b76a6-106">Members</span></span>  
  
|<span data-ttu-id="b76a6-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b76a6-107">Member</span></span>|<span data-ttu-id="b76a6-108">Opis</span><span class="sxs-lookup"><span data-stu-id="b76a6-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="b76a6-109">Nie można odnaleźć funkcji.</span><span class="sxs-lookup"><span data-stu-id="b76a6-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="b76a6-110">Nie znaleziono funkcji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="b76a6-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b76a6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b76a6-111">Requirements</span></span>  
 <span data-ttu-id="b76a6-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b76a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b76a6-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b76a6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b76a6-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b76a6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b76a6-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b76a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b76a6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b76a6-116">See also</span></span>

- [<span data-ttu-id="b76a6-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b76a6-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
