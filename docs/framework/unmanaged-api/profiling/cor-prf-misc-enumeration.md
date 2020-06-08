---
title: COR_PRF_MISC — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: 7b8f2845589a8372f62c95ef1a82eae3ed602c1f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500835"
---
# <a name="cor_prf_misc-enumeration"></a><span data-ttu-id="04dff-102">COR_PRF_MISC — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="04dff-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="04dff-103">Zawiera wartości stałe, które określają identyfikatory specjalne.</span><span class="sxs-lookup"><span data-stu-id="04dff-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04dff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04dff-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="04dff-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="04dff-105">Members</span></span>  
  
|<span data-ttu-id="04dff-106">Członek</span><span class="sxs-lookup"><span data-stu-id="04dff-106">Member</span></span>|<span data-ttu-id="04dff-107">Opis</span><span class="sxs-lookup"><span data-stu-id="04dff-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="04dff-108">Domyślny identyfikator używany przez [ICorProfilerInfo:: GetModuleInfo —](icorprofilerinfo-getmoduleinfo-method.md) dla modułu, który nie został jeszcze dołączony do zestawu.</span><span class="sxs-lookup"><span data-stu-id="04dff-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="04dff-109">Domyślny identyfikator klasy dla stałych globalnych, które nie należą do klasy.</span><span class="sxs-lookup"><span data-stu-id="04dff-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="04dff-110">Domyślny identyfikator modułu dla obiektów globalnych, które nie należą do modułu.</span><span class="sxs-lookup"><span data-stu-id="04dff-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04dff-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04dff-111">Requirements</span></span>  
 <span data-ttu-id="04dff-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04dff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04dff-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="04dff-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04dff-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="04dff-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04dff-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04dff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04dff-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04dff-116">See also</span></span>

- [<span data-ttu-id="04dff-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="04dff-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
