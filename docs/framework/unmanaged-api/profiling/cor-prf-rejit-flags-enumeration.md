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
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177102"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="9f11b-102">COR_PRF_REJIT_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9f11b-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="9f11b-103">Zawiera wartości, które wskazują, jak [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) api powinien zachowywać.</span><span class="sxs-lookup"><span data-stu-id="9f11b-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f11b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f11b-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="9f11b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9f11b-105">Members</span></span>  
  
|<span data-ttu-id="9f11b-106">Członek</span><span class="sxs-lookup"><span data-stu-id="9f11b-106">Member</span></span>|<span data-ttu-id="9f11b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9f11b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="9f11b-108">Metody ReJITted zostaną zablokowane przed inlined w innych metodach.</span><span class="sxs-lookup"><span data-stu-id="9f11b-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="9f11b-109">Odbieranie `GetFunctionParameters` wywołań zwrotnych dla wszelkich metod, które wbudowane metody wymagane do ReJITted.</span><span class="sxs-lookup"><span data-stu-id="9f11b-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="9f11b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f11b-110">Requirements</span></span>  
 <span data-ttu-id="9f11b-111">**Platformy:** Zobacz [.NET Core obsługiwane systemy operacyjne](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="9f11b-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="9f11b-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9f11b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9f11b-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f11b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f11b-114">**Wersje programu .NET Framework:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f11b-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9f11b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f11b-115">See also</span></span>

- [<span data-ttu-id="9f11b-116">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9f11b-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
