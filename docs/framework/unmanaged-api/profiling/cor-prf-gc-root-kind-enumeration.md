---
title: COR_PRF_GC_ROOT_KIND — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: 2fe4735b7f218e89577702cde04d8d4f4de2a971
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447355"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="cc3f1-102">COR_PRF_GC_ROOT_KIND — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cc3f1-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="cc3f1-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc3f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc3f1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="cc3f1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="cc3f1-105">Members</span></span>  
  
|<span data-ttu-id="cc3f1-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="cc3f1-106">Member</span></span>|<span data-ttu-id="cc3f1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cc3f1-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="cc3f1-108">The root is a variable on the stack.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="cc3f1-109">The root is an entry in the finalizer queue.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="cc3f1-110">The root is a garbage collection handle.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="cc3f1-111">The kind of root is unspecified.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc3f1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc3f1-112">Requirements</span></span>  
 <span data-ttu-id="cc3f1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc3f1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc3f1-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc3f1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc3f1-115">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc3f1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc3f1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc3f1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc3f1-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc3f1-117">See also</span></span>

- [<span data-ttu-id="cc3f1-118">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="cc3f1-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
