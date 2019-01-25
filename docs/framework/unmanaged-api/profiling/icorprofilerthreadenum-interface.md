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
ms.openlocfilehash: dd7d5f66ef7c8f2b36b8dcb725b1931993c118dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526395"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="594f3-102">ICorProfilerThreadEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="594f3-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="594f3-103">Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji wątków we wspólnym środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="594f3-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="594f3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="594f3-104">Methods</span></span>  
  
|<span data-ttu-id="594f3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="594f3-105">Method</span></span>|<span data-ttu-id="594f3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="594f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="594f3-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="594f3-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="594f3-108">Pobiera wskaźnik interfejsu do kopii tego `ICorProfilerThreadEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="594f3-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="594f3-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="594f3-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="594f3-110">Pobiera liczbę wątków, które są używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="594f3-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="594f3-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="594f3-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="594f3-112">Pobiera określoną liczbę wątków sąsiadujących z sekwencyjną kolekcją wątków, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="594f3-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="594f3-113">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="594f3-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="594f3-114">Przenosi kursor modułu wyliczającego do pozycji początkowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="594f3-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="594f3-115">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="594f3-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="594f3-116">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, aby pominąć określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="594f3-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="594f3-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="594f3-117">Remarks</span></span>  
 <span data-ttu-id="594f3-118">`ICorProfilerThreadEnum` Interfejs jest moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="594f3-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="594f3-119">Umożliwia odbiorcy tablicy do ściągnięcia elementów od nadawcy szybkością, która jest odpowiednia dla odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="594f3-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="594f3-120">Innymi słowy odbiornik jest w stanie jawnie sterowania przepływem elementów tablicy, tym samym unikając problemów związanych z przekazywania dużych tablic jako parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="594f3-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="594f3-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="594f3-121">Requirements</span></span>  
 <span data-ttu-id="594f3-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="594f3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="594f3-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="594f3-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="594f3-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="594f3-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="594f3-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="594f3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="594f3-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="594f3-126">See also</span></span>
- [<span data-ttu-id="594f3-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="594f3-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="594f3-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="594f3-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
