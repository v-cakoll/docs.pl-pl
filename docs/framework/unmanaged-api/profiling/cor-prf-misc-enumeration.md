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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b40ac5f49288f7b30018e0c8c727e3ce6b73ae8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199495"
---
# <a name="corprfmisc-enumeration"></a><span data-ttu-id="af2f9-102">COR_PRF_MISC — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="af2f9-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="af2f9-103">Zawiera wartości stałych, które określają specjalne identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="af2f9-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af2f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af2f9-104">Syntax</span></span>  
  
```  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="af2f9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="af2f9-105">Members</span></span>  
  
|<span data-ttu-id="af2f9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="af2f9-106">Member</span></span>|<span data-ttu-id="af2f9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="af2f9-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="af2f9-108">Domyślny identyfikator używany przez [icorprofilerinfo::getmoduleinfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) dla modułu, który jeszcze nie został dołączony do zestawu.</span><span class="sxs-lookup"><span data-stu-id="af2f9-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="af2f9-109">Identyfikator klasy domyślne stałe globalne, które nie należą do klasy.</span><span class="sxs-lookup"><span data-stu-id="af2f9-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="af2f9-110">Domyślny identyfikator modułu dla obiektów globalnych, które nie należą do modułu.</span><span class="sxs-lookup"><span data-stu-id="af2f9-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af2f9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af2f9-111">Requirements</span></span>  
 <span data-ttu-id="af2f9-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af2f9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af2f9-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af2f9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af2f9-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af2f9-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="af2f9-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="af2f9-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af2f9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af2f9-116">See also</span></span>

- [<span data-ttu-id="af2f9-117">Profilowanie — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="af2f9-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
