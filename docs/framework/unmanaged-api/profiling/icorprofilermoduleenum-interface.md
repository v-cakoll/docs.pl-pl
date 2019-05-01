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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040940"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="1e1fa-102">ICorProfilerModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1e1fa-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="1e1fa-103">Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji moduły załadowane przez program profilujący lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1e1fa-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e1fa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1e1fa-104">Methods</span></span>  
  
|<span data-ttu-id="1e1fa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1e1fa-105">Method</span></span>|<span data-ttu-id="1e1fa-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1e1fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e1fa-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="1e1fa-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="1e1fa-108">Pobiera wskaźnik interfejsu do kopii tego `ICorProfilerModuleEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1e1fa-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="1e1fa-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="1e1fa-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="1e1fa-110">Pobiera liczbę modułów zarządzanych, które zostały załadowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1e1fa-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="1e1fa-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="1e1fa-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="1e1fa-112">Pobiera określoną liczbę modułów sąsiadujących z sekwencyjną kolekcją obiektów, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1e1fa-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="1e1fa-113">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="1e1fa-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="1e1fa-114">Przenosi kursor modułu wyliczającego do pozycji początkowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1e1fa-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="1e1fa-115">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="1e1fa-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="1e1fa-116">Przesuwa do przodu pozycję kursora moduł wyliczający tak, aby określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="1e1fa-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e1fa-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e1fa-117">Remarks</span></span>  
 <span data-ttu-id="1e1fa-118">`ICorProfilerModuleEnum` Interfejs jest moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="1e1fa-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="1e1fa-119">Umożliwia odbiorcy tablicy do ściągnięcia elementów od nadawcy szybkością, która jest odpowiednia dla odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="1e1fa-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="1e1fa-120">Innymi słowy odbiornik jest w stanie jawnie sterowania przepływem elementów tablicy, tym samym unikając problemów związanych z przekazywania dużych tablic jako parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="1e1fa-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e1fa-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1e1fa-121">Requirements</span></span>  
 <span data-ttu-id="1e1fa-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e1fa-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e1fa-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1e1fa-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e1fa-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e1fa-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e1fa-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e1fa-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e1fa-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e1fa-126">See also</span></span>

- [<span data-ttu-id="1e1fa-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="1e1fa-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="1e1fa-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="1e1fa-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1e1fa-129">EnumModules, metoda</span><span class="sxs-lookup"><span data-stu-id="1e1fa-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
