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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b7a4c8dfc9e082b29d462b835886d6bf252bb39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753670"
---
# <a name="corprfgcrootkind-enumeration"></a><span data-ttu-id="20c0a-102">COR_PRF_GC_ROOT_KIND — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="20c0a-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="20c0a-103">Wskazuje rodzaj głównego kolekcji wyrzucania elementów, który jest udostępniany przez [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="20c0a-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20c0a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="20c0a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="20c0a-105">Members</span></span>  
  
|<span data-ttu-id="20c0a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="20c0a-106">Member</span></span>|<span data-ttu-id="20c0a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="20c0a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="20c0a-108">Katalog główny jest zmienną na stosie.</span><span class="sxs-lookup"><span data-stu-id="20c0a-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="20c0a-109">Katalog główny jest wpis w kolejce finalizatora.</span><span class="sxs-lookup"><span data-stu-id="20c0a-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="20c0a-110">Katalog główny jest uchwytem kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="20c0a-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="20c0a-111">Rodzaj elementu głównego jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="20c0a-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20c0a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20c0a-112">Requirements</span></span>  
 <span data-ttu-id="20c0a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20c0a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20c0a-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20c0a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20c0a-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20c0a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20c0a-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20c0a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c0a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20c0a-117">See also</span></span>

- [<span data-ttu-id="20c0a-118">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="20c0a-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
