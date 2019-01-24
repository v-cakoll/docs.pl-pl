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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df3baf21de7a1e6ec0590d85719eaa40d5da489f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511908"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="5858e-102">ICorProfilerFunctionEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5858e-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="5858e-103">Udostępnia metody do sekwencyjnie iteracji przez kolekcję funkcji środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="5858e-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5858e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5858e-104">Methods</span></span>  
  
|<span data-ttu-id="5858e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5858e-105">Method</span></span>|<span data-ttu-id="5858e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5858e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5858e-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="5858e-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="5858e-108">Pobiera wskaźnik interfejsu do kopii tego `ICorProfilerFunctionEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5858e-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="5858e-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="5858e-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="5858e-110">Pobiera liczbę funkcji, które zostały załadowane do aplikacji lub Wymuś ładowany przez program profilujący.</span><span class="sxs-lookup"><span data-stu-id="5858e-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="5858e-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="5858e-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="5858e-112">Pobiera określoną liczbę funkcji ciągłego z sekwencyjną kolekcją funkcji, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5858e-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="5858e-113">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="5858e-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="5858e-114">Przenosi kursor modułu wyliczającego do pozycji początkowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5858e-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="5858e-115">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="5858e-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="5858e-116">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, tak, aby określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="5858e-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5858e-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5858e-117">Remarks</span></span>  
 <span data-ttu-id="5858e-118">`ICorProfilerFunctionEnum` Interfejs jest moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="5858e-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="5858e-119">Umożliwia odbiorcy tablicy do ściągnięcia elementów od nadawcy szybkością, która jest odpowiednia dla odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="5858e-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="5858e-120">Innymi słowy odbiornik jest w stanie jawnie sterowania przepływem elementów tablicy, tym samym unikając problemów związanych z przekazywania dużych tablic jako parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="5858e-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="5858e-121">`ICorProfilerFunctionEnum` Wylicza za pośrednictwem funkcji, które zostały już skompilowane JIT, ale nie obejmuje funkcje, które są ładowane z obrazy natywne generowane przez program Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="5858e-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5858e-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5858e-122">Requirements</span></span>  
 <span data-ttu-id="5858e-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5858e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5858e-124">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5858e-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5858e-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5858e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5858e-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5858e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5858e-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5858e-127">See also</span></span>
- [<span data-ttu-id="5858e-128">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="5858e-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="5858e-129">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="5858e-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5858e-130">EnumJITedFunctions, metoda</span><span class="sxs-lookup"><span data-stu-id="5858e-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
