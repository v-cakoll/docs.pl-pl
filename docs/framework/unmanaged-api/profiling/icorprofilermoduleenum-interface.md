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
ms.openlocfilehash: 99db173aa7c6064d9f635412d539cc2d4509b24a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124660"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="5dac0-102">ICorProfilerModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5dac0-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="5dac0-103">Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji moduły załadowane przez program profilujący lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5dac0-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5dac0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5dac0-104">Methods</span></span>  
  
|<span data-ttu-id="5dac0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5dac0-105">Method</span></span>|<span data-ttu-id="5dac0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5dac0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5dac0-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="5dac0-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="5dac0-108">Pobiera wskaźnik interfejsu do kopii tego `ICorProfilerModuleEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5dac0-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="5dac0-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="5dac0-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="5dac0-110">Pobiera liczbę modułów zarządzanych, które zostały załadowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5dac0-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="5dac0-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="5dac0-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="5dac0-112">Pobiera określoną liczbę modułów sąsiadujących z sekwencyjną kolekcją obiektów, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5dac0-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="5dac0-113">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="5dac0-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="5dac0-114">Przenosi kursor modułu wyliczającego do pozycji początkowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5dac0-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="5dac0-115">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="5dac0-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="5dac0-116">Przesuwa do przodu pozycję kursora moduł wyliczający tak, aby określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="5dac0-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dac0-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5dac0-117">Remarks</span></span>  
 <span data-ttu-id="5dac0-118">`ICorProfilerModuleEnum` Interfejs jest moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="5dac0-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="5dac0-119">Umożliwia odbiorcy tablicy do ściągnięcia elementów od nadawcy szybkością, która jest odpowiednia dla odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="5dac0-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="5dac0-120">Innymi słowy odbiornik jest w stanie jawnie sterowania przepływem elementów tablicy, tym samym unikając problemów związanych z przekazywania dużych tablic jako parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="5dac0-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dac0-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5dac0-121">Requirements</span></span>  
 <span data-ttu-id="5dac0-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dac0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dac0-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5dac0-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5dac0-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dac0-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dac0-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dac0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dac0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5dac0-126">See also</span></span>

- [<span data-ttu-id="5dac0-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="5dac0-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="5dac0-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="5dac0-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5dac0-129">EnumModules, metoda</span><span class="sxs-lookup"><span data-stu-id="5dac0-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
