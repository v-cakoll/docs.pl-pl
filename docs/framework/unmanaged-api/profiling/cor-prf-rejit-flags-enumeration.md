---
title: COR_PRF_REJIT_FLAGS — Wyliczenie
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: 3b4f85072b9dcf87d696b979fa6cbf4e59393f82
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453042"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="73cc0-102">COR_PRF_REJIT_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="73cc0-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="73cc0-103">Zawiera wartości wskazujące, jak działa interfejs API [ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) .</span><span class="sxs-lookup"><span data-stu-id="73cc0-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73cc0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73cc0-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="73cc0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="73cc0-105">Members</span></span>  
  
|<span data-ttu-id="73cc0-106">Członek</span><span class="sxs-lookup"><span data-stu-id="73cc0-106">Member</span></span>|<span data-ttu-id="73cc0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="73cc0-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="73cc0-108">Metody ReJITted będą blokowane przed zapisaniem ich w innych metodach.</span><span class="sxs-lookup"><span data-stu-id="73cc0-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="73cc0-109">Odbieraj `GetFunctionParameters` wywołania zwrotne dla każdej metody, która w sposób zażądała metody ReJITted.</span><span class="sxs-lookup"><span data-stu-id="73cc0-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="73cc0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73cc0-110">Requirements</span></span>  
 <span data-ttu-id="73cc0-111">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="73cc0-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="73cc0-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="73cc0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73cc0-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73cc0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73cc0-114">**Wersje .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73cc0-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="73cc0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73cc0-115">See also</span></span>

- [<span data-ttu-id="73cc0-116">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="73cc0-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
