---
title: "COR_PRF_GC_ROOT_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e00f695edb94acbd54d6bd009ccd629aeec1b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprfgcrootflags-enumeration"></a><span data-ttu-id="8c287-102">COR_PRF_GC_ROOT_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8c287-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="8c287-103">Wskazuje właściwość głównego kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c287-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c287-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c287-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="8c287-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8c287-105">Members</span></span>  
  
|<span data-ttu-id="8c287-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8c287-106">Member</span></span>|<span data-ttu-id="8c287-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8c287-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="8c287-108">Katalog główny zapobiega wyrzucania elementów bezużytecznych przenoszenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8c287-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="8c287-109">Katalog główny nie zapobiega wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="8c287-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="8c287-110">Katalog główny odwołuje się do pola obiektu, a nie samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="8c287-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="8c287-111">Głównego zapobiega wyrzucanie elementów bezużytecznych, jeśli liczba odwołanie do obiektu jest określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="8c287-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c287-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c287-112">Remarks</span></span>  
 <span data-ttu-id="8c287-113">`COR_PRF_GC_ROOT_FLAGS`jest maską bitów udostępnia dodatkowe informacje o specjalne katalogów głównych.</span><span class="sxs-lookup"><span data-stu-id="8c287-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="8c287-114">Niemniej jednak nie wszystkie certyfikaty główne są specjalne.</span><span class="sxs-lookup"><span data-stu-id="8c287-114">However, not all roots are special.</span></span> <span data-ttu-id="8c287-115">Na przykład niektóre katalogów głównych nie są słabe odwołania, wewnętrznych wskaźników przypiętych lub zliczane odwołania.</span><span class="sxs-lookup"><span data-stu-id="8c287-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="8c287-116">Dla tych certyfikatów głównych nie ma żadnych flag w celu przedstawienia.</span><span class="sxs-lookup"><span data-stu-id="8c287-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="8c287-117">W związku z tym te metody, które używają tego wyliczenia, takich jak [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) metody send 0 flagi maski bitów, wskazujące, że wszystkie flagi są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8c287-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c287-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c287-118">Requirements</span></span>  
 <span data-ttu-id="8c287-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c287-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c287-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8c287-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c287-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c287-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c287-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c287-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c287-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c287-123">See Also</span></span>  
 [<span data-ttu-id="8c287-124">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8c287-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
