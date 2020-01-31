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
ms.openlocfilehash: 2713fa90240cb0bf41f455b6ed65d76c568a2cf8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868268"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="48067-102">ICorProfilerModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="48067-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="48067-103">Dostarcza metody sekwencyjnie iteracji przez kolekcję modułów ładowanych przez aplikację lub profiler.</span><span class="sxs-lookup"><span data-stu-id="48067-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48067-104">Metody</span><span class="sxs-lookup"><span data-stu-id="48067-104">Methods</span></span>  
  
|<span data-ttu-id="48067-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="48067-105">Method</span></span>|<span data-ttu-id="48067-106">Opis</span><span class="sxs-lookup"><span data-stu-id="48067-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48067-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="48067-107">Clone Method</span></span>](icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="48067-108">Pobiera wskaźnik interfejsu do kopii tego interfejsu `ICorProfilerModuleEnum`.</span><span class="sxs-lookup"><span data-stu-id="48067-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="48067-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="48067-109">GetCount Method</span></span>](icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="48067-110">Pobiera liczbę modułów zarządzanych, które zostały załadowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48067-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="48067-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="48067-111">Next Method</span></span>](icorprofilermoduleenum-next-method.md)|<span data-ttu-id="48067-112">Pobiera określoną liczbę modułów ciągłego z kolekcji sekwencyjnej obiektów, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="48067-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="48067-113">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="48067-113">Reset Method</span></span>](icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="48067-114">Przenosi kursor modułu wyliczającego do początkowego położenia sekwencji.</span><span class="sxs-lookup"><span data-stu-id="48067-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="48067-115">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="48067-115">Skip Method</span></span>](icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="48067-116">Przesuwa pozycję kursora modułu wyliczającego tak, aby określona liczba elementów została pominięta.</span><span class="sxs-lookup"><span data-stu-id="48067-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48067-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48067-117">Remarks</span></span>  
 <span data-ttu-id="48067-118">Interfejs `ICorProfilerModuleEnum` jest modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="48067-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="48067-119">Umożliwia odbiorcom tablicy ściąganie elementów od nadawcy według stawki, która jest odpowiednia dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="48067-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="48067-120">Innymi słowy, odbiorca może jawnie kontrolować przepływ elementów tablicy, co pozwala uniknąć problemów związanych z przekazywaniem dużych tablic jako parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="48067-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48067-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48067-121">Requirements</span></span>  
 <span data-ttu-id="48067-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48067-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48067-123">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="48067-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48067-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="48067-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48067-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48067-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48067-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48067-126">See also</span></span>

- [<span data-ttu-id="48067-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="48067-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="48067-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="48067-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="48067-129">EnumModules, metoda</span><span class="sxs-lookup"><span data-stu-id="48067-129">EnumModules Method</span></span>](icorprofilerinfo3-enummodules-method.md)
