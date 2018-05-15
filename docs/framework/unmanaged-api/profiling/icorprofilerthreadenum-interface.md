---
title: ICorProfilerThreadEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b9662ccb854345d41bb73a5cf01a94b9949891d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="3d9c6-102">ICorProfilerThreadEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3d9c6-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="3d9c6-103">Udostępnia metody sekwencyjnie iterowania po kolekcji wątki środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="3d9c6-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3d9c6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3d9c6-104">Methods</span></span>  
  
|<span data-ttu-id="3d9c6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3d9c6-105">Method</span></span>|<span data-ttu-id="3d9c6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3d9c6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3d9c6-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="3d9c6-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="3d9c6-108">Pobiera wskaźnika interfejsu kopię `ICorProfilerThreadEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3d9c6-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="3d9c6-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="3d9c6-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="3d9c6-110">Pobiera liczbę wątków, które są używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="3d9c6-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="3d9c6-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="3d9c6-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="3d9c6-112">Pobiera określoną liczbę wątków ciągłe z sekwencyjną kolekcją wątków, zaczynając od modułu wyliczającego bieżącej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="3d9c6-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="3d9c6-113">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="3d9c6-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="3d9c6-114">Przesuwa kursor modułu wyliczającego pozycji początkowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="3d9c6-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="3d9c6-115">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="3d9c6-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="3d9c6-116">Przesuwa kursor modułu wyliczającego z bieżącej pozycji do pominięcia określonej liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="3d9c6-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d9c6-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d9c6-117">Remarks</span></span>  
 <span data-ttu-id="3d9c6-118">`ICorProfilerThreadEnum` Interfejs jest moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="3d9c6-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="3d9c6-119">Umożliwia odbiorcy tablicy do ściągania elementów od nadawcy szybkością, który jest odpowiedni dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="3d9c6-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="3d9c6-120">Innymi słowy odbiorca jest w stanie jawnie sterowanie przepływem elementów tablicy, zapobiegając problemów związanych z przekazywanie dużych tablic jako parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="3d9c6-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d9c6-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d9c6-121">Requirements</span></span>  
 <span data-ttu-id="3d9c6-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d9c6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d9c6-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d9c6-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d9c6-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d9c6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d9c6-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d9c6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9c6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d9c6-126">See Also</span></span>  
 [<span data-ttu-id="3d9c6-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="3d9c6-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="3d9c6-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3d9c6-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
