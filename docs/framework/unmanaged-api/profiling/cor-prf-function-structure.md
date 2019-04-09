---
title: COR_PRF_FUNCTION — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14d42a4032c3e2b1c231414678912e1658e759d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101728"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="ae982-102">COR_PRF_FUNCTION — Struktura</span><span class="sxs-lookup"><span data-stu-id="ae982-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="ae982-103">Udostępnia reprezentację unikatową funkcję, łącząc się jego Identyfikatorem jego ponownej kompilacji wersji.</span><span class="sxs-lookup"><span data-stu-id="ae982-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae982-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae982-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="ae982-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ae982-105">Members</span></span>  
  
|<span data-ttu-id="ae982-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ae982-106">Member</span></span>|<span data-ttu-id="ae982-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ae982-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="ae982-108">Identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="ae982-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="ae982-109">Identyfikator funkcji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ae982-109">The ID of the recompiled function.</span></span> <span data-ttu-id="ae982-110">Wartość 0 (zero) reprezentuje oryginalną wersję funkcji.</span><span class="sxs-lookup"><span data-stu-id="ae982-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae982-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae982-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae982-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae982-112">Requirements</span></span>  
 <span data-ttu-id="ae982-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae982-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae982-114">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ae982-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ae982-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae982-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ae982-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ae982-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ae982-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae982-117">See also</span></span>

- [<span data-ttu-id="ae982-118">Profiling — Struktury</span><span class="sxs-lookup"><span data-stu-id="ae982-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
