---
title: ICorProfilerFunctionEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: add30952588ace0cbc80191617c37d7222cffee7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864495"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="5e906-102">ICorProfilerFunctionEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5e906-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="5e906-103">Zapewnia metody sekwencyjnej iteracji przez kolekcję funkcji w środowisku uruchomieniowym języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="5e906-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e906-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5e906-104">Methods</span></span>  
  
|<span data-ttu-id="5e906-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5e906-105">Method</span></span>|<span data-ttu-id="5e906-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5e906-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e906-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="5e906-107">Clone Method</span></span>](icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="5e906-108">Pobiera wskaźnik interfejsu do kopii tego interfejsu `ICorProfilerFunctionEnum`.</span><span class="sxs-lookup"><span data-stu-id="5e906-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="5e906-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="5e906-109">GetCount Method</span></span>](icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="5e906-110">Pobiera liczbę funkcji, które zostały załadowane przez aplikację lub wymuszanie załadowane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="5e906-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="5e906-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="5e906-111">Next Method</span></span>](icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="5e906-112">Pobiera określoną liczbę funkcji ciągłych z sekwencyjnego zbioru funkcji, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5e906-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="5e906-113">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="5e906-113">Reset Method</span></span>](icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="5e906-114">Przenosi kursor modułu wyliczającego do początkowego położenia sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5e906-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="5e906-115">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="5e906-115">Skip Method</span></span>](icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="5e906-116">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, tak aby określona liczba elementów została pominięta.</span><span class="sxs-lookup"><span data-stu-id="5e906-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e906-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e906-117">Remarks</span></span>  
 <span data-ttu-id="5e906-118">Interfejs `ICorProfilerFunctionEnum` jest modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="5e906-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="5e906-119">Umożliwia odbiorcom tablicy ściąganie elementów od nadawcy według stawki, która jest odpowiednia dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="5e906-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="5e906-120">Innymi słowy, odbiorca może jawnie kontrolować przepływ elementów tablicy, co pozwala uniknąć problemów związanych z przekazywaniem dużych tablic jako parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="5e906-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="5e906-121">`ICorProfilerFunctionEnum` wylicza funkcje, które zostały już skompilowane JIT, ale nie zawierają funkcji ładowanych z obrazów natywnych generowanych za pomocą programu Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="5e906-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e906-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e906-122">Requirements</span></span>  
 <span data-ttu-id="5e906-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e906-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e906-124">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5e906-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e906-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5e906-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e906-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e906-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e906-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e906-127">See also</span></span>

- [<span data-ttu-id="5e906-128">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e906-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="5e906-129">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="5e906-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5e906-130">EnumJITedFunctions, metoda</span><span class="sxs-lookup"><span data-stu-id="5e906-130">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
