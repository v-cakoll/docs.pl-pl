---
title: COR_PRF_GC_ROOT_FLAGS — Wyliczenie
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263c22a07f363c2752afb50779515de043976e93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207711"
---
# <a name="corprfgcrootflags-enumeration"></a><span data-ttu-id="941c7-102">COR_PRF_GC_ROOT_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="941c7-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="941c7-103">Wskazuje właściwość kolekcji wyrzucania elementów katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="941c7-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="941c7-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="941c7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="941c7-105">Members</span></span>  
  
|<span data-ttu-id="941c7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="941c7-106">Member</span></span>|<span data-ttu-id="941c7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="941c7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="941c7-108">Katalog główny zapobiega wyrzucania elementów bezużytecznych z przeniesienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="941c7-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="941c7-109">Katalog główny nie uniemożliwia wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="941c7-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="941c7-110">Katalog główny odwołuje się do pola obiektu, a nie samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="941c7-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="941c7-111">Katalog główny zapobiega wyrzucania elementów bezużytecznych, jeśli licznik odwołań obiektu jest określoną wartością.</span><span class="sxs-lookup"><span data-stu-id="941c7-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="941c7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="941c7-112">Remarks</span></span>  
 <span data-ttu-id="941c7-113">`COR_PRF_GC_ROOT_FLAGS` jest maską bitów, który zawiera dodatkowe informacje na temat specjalne katalogów głównych.</span><span class="sxs-lookup"><span data-stu-id="941c7-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="941c7-114">Jednak nie wszystkie elementy główne są specjalne.</span><span class="sxs-lookup"><span data-stu-id="941c7-114">However, not all roots are special.</span></span> <span data-ttu-id="941c7-115">Na przykład niektóre elementy główne nie są słabe odwołania, wskaźniki posługiwanie się nimi, przypiętych lub zliczonych odwołań.</span><span class="sxs-lookup"><span data-stu-id="941c7-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="941c7-116">Takie elementy główne są nie flagi do przekazania.</span><span class="sxs-lookup"><span data-stu-id="941c7-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="941c7-117">W związku z tym, w przypadku metod, które używają tego wyliczenia, takich jak [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) metody wysyłania 0 maski bitów flag, wskazujący, że wszystkie flagi są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="941c7-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="941c7-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="941c7-118">Requirements</span></span>  
 <span data-ttu-id="941c7-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="941c7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="941c7-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="941c7-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="941c7-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="941c7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="941c7-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="941c7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="941c7-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="941c7-123">See also</span></span>

- [<span data-ttu-id="941c7-124">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="941c7-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
