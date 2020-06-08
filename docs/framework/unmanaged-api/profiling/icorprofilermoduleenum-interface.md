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
ms.openlocfilehash: fe11c0bbe273ae07cdae43f681a558e07a291ffb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494894"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="082c0-102">ICorProfilerModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="082c0-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="082c0-103">Dostarcza metody sekwencyjnie iteracji przez kolekcję modułów ładowanych przez aplikację lub profiler.</span><span class="sxs-lookup"><span data-stu-id="082c0-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="082c0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="082c0-104">Methods</span></span>  
  
|<span data-ttu-id="082c0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="082c0-105">Method</span></span>|<span data-ttu-id="082c0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="082c0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="082c0-107">Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="082c0-107">Clone Method</span></span>](icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="082c0-108">Pobiera wskaźnik interfejsu do kopii tego `ICorProfilerModuleEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="082c0-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="082c0-109">GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="082c0-109">GetCount Method</span></span>](icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="082c0-110">Pobiera liczbę modułów zarządzanych, które zostały załadowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="082c0-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="082c0-111">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="082c0-111">Next Method</span></span>](icorprofilermoduleenum-next-method.md)|<span data-ttu-id="082c0-112">Pobiera określoną liczbę modułów ciągłego z kolekcji sekwencyjnej obiektów, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="082c0-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="082c0-113">Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="082c0-113">Reset Method</span></span>](icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="082c0-114">Przenosi kursor modułu wyliczającego do początkowego położenia sekwencji.</span><span class="sxs-lookup"><span data-stu-id="082c0-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="082c0-115">Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="082c0-115">Skip Method</span></span>](icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="082c0-116">Przesuwa pozycję kursora modułu wyliczającego tak, aby określona liczba elementów została pominięta.</span><span class="sxs-lookup"><span data-stu-id="082c0-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="082c0-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="082c0-117">Remarks</span></span>  
 <span data-ttu-id="082c0-118">`ICorProfilerModuleEnum`Interfejs jest modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="082c0-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="082c0-119">Umożliwia odbiorcom tablicy ściąganie elementów od nadawcy według stawki, która jest odpowiednia dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="082c0-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="082c0-120">Innymi słowy, odbiorca może jawnie kontrolować przepływ elementów tablicy, co pozwala uniknąć problemów związanych z przekazywaniem dużych tablic jako parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="082c0-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="082c0-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="082c0-121">Requirements</span></span>  
 <span data-ttu-id="082c0-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="082c0-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="082c0-123">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="082c0-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="082c0-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="082c0-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="082c0-125">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="082c0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="082c0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="082c0-126">See also</span></span>

- [<span data-ttu-id="082c0-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="082c0-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="082c0-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="082c0-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="082c0-129">EnumModules, metoda</span><span class="sxs-lookup"><span data-stu-id="082c0-129">EnumModules Method</span></span>](icorprofilerinfo3-enummodules-method.md)
