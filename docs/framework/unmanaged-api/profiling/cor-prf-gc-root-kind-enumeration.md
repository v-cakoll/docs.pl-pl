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
ms.openlocfilehash: 0ea584bfff4340e5e9635d6c31e177e88765b582
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500874"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="8d7e9-102">COR_PRF_GC_ROOT_KIND — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8d7e9-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="8d7e9-103">Wskazuje rodzaj katalogu głównego wyrzucania elementów bezużytecznych, który jest udostępniany przez wywołanie zwrotne [ICorProfilerCallback2:: RootReferences2 —](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8d7e9-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d7e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d7e9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="8d7e9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8d7e9-105">Members</span></span>  
  
|<span data-ttu-id="8d7e9-106">Członek</span><span class="sxs-lookup"><span data-stu-id="8d7e9-106">Member</span></span>|<span data-ttu-id="8d7e9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8d7e9-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="8d7e9-108">Element główny jest zmienną na stosie.</span><span class="sxs-lookup"><span data-stu-id="8d7e9-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="8d7e9-109">Katalog główny jest wpisem w kolejce finalizatora.</span><span class="sxs-lookup"><span data-stu-id="8d7e9-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="8d7e9-110">Katalog główny jest dojściem do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="8d7e9-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="8d7e9-111">Rodzaj elementu głównego jest nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="8d7e9-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d7e9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d7e9-112">Requirements</span></span>  
 <span data-ttu-id="8d7e9-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d7e9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d7e9-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8d7e9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d7e9-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8d7e9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d7e9-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d7e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d7e9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d7e9-117">See also</span></span>

- [<span data-ttu-id="8d7e9-118">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8d7e9-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
