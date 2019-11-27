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
ms.openlocfilehash: 174486a88192bd5ff11074930d5ad3375603f8a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449460"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a><span data-ttu-id="182b9-102">COR_PRF_GC_ROOT_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="182b9-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="182b9-103">Wskazuje Właściwość katalogu głównego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="182b9-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="182b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="182b9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="182b9-105">Members</span><span class="sxs-lookup"><span data-stu-id="182b9-105">Members</span></span>  
  
|<span data-ttu-id="182b9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="182b9-106">Member</span></span>|<span data-ttu-id="182b9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="182b9-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="182b9-108">Katalog główny uniemożliwia przechodzenie obiektu przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="182b9-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="182b9-109">Element główny nie zapobiega wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="182b9-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="182b9-110">Element główny odwołuje się do pola obiektu, a nie samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="182b9-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="182b9-111">Katalog główny uniemożliwia wyrzucanie elementów bezużytecznych, jeśli liczba odwołań obiektu jest określona.</span><span class="sxs-lookup"><span data-stu-id="182b9-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="182b9-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="182b9-112">Remarks</span></span>  
 <span data-ttu-id="182b9-113">`COR_PRF_GC_ROOT_FLAGS` jest maską bitów, która zawiera dodatkowe informacje na temat specjalnych katalogów głównych.</span><span class="sxs-lookup"><span data-stu-id="182b9-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="182b9-114">Nie wszystkie elementy główne są jednak specjalne.</span><span class="sxs-lookup"><span data-stu-id="182b9-114">However, not all roots are special.</span></span> <span data-ttu-id="182b9-115">Na przykład niektóre elementy główne nie są słabymi odwołaniami, wewnętrznymi wskaźnikami, przypiętymi lub zliczanymi odwołaniami.</span><span class="sxs-lookup"><span data-stu-id="182b9-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="182b9-116">W przypadku takich elementów głównych nie ma flag do przekazania.</span><span class="sxs-lookup"><span data-stu-id="182b9-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="182b9-117">W związku z tym metody używające tego wyliczenia, takie jak [ICorProfilerCallback2:: RootReferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) , wysyłają 0 dla flag maska bitów, wskazując, że wszystkie flagi są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="182b9-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="182b9-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="182b9-118">Requirements</span></span>  
 <span data-ttu-id="182b9-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="182b9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="182b9-120">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="182b9-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="182b9-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="182b9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="182b9-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="182b9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182b9-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="182b9-123">See also</span></span>

- [<span data-ttu-id="182b9-124">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="182b9-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
