---
title: ICorProfilerModuleEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2275eb37d0e62c3f0ee8bbc8ea6db66901a3f1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="ee33d-102">ICorProfilerModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ee33d-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="ee33d-103">Udostępnia metody sekwencyjnie iterowania po kolekcji moduły załadowane przez profiler lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee33d-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee33d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ee33d-104">Methods</span></span>  
  
|<span data-ttu-id="ee33d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee33d-105">Method</span></span>|<span data-ttu-id="ee33d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ee33d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee33d-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="ee33d-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="ee33d-108">Pobiera wskaźnika interfejsu kopię `ICorProfilerModuleEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ee33d-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="ee33d-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="ee33d-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="ee33d-110">Pobiera liczbę modułów zarządzanych, które zostały załadowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee33d-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="ee33d-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="ee33d-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="ee33d-112">Pobiera określoną liczbę modułów ciągłe z sekwencyjną kolekcją obiektów, zaczynając od modułu wyliczającego bieżącej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="ee33d-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="ee33d-113">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="ee33d-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="ee33d-114">Przesuwa kursor modułu wyliczającego pozycji początkowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="ee33d-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="ee33d-115">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="ee33d-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="ee33d-116">Zmienia pozycję kursora modułu wyliczającego, dzięki czemu określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="ee33d-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee33d-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee33d-117">Remarks</span></span>  
 <span data-ttu-id="ee33d-118">`ICorProfilerModuleEnum` Interfejs jest moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="ee33d-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="ee33d-119">Umożliwia odbiorcy tablicy do ściągania elementów od nadawcy szybkością, który jest odpowiedni dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="ee33d-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="ee33d-120">Innymi słowy odbiorca jest w stanie jawnie sterowanie przepływem elementów tablicy, zapobiegając problemów związanych z przekazywanie dużych tablic jako parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="ee33d-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee33d-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee33d-121">Requirements</span></span>  
 <span data-ttu-id="ee33d-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee33d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee33d-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee33d-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee33d-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee33d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee33d-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee33d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee33d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee33d-126">See Also</span></span>  
 [<span data-ttu-id="ee33d-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee33d-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="ee33d-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="ee33d-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="ee33d-129">EnumModules, metoda</span><span class="sxs-lookup"><span data-stu-id="ee33d-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
