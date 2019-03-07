---
title: ICorProfilerCallback::RootReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfab1d716b5a8b530561e2dc72442591eb0d8e42
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499033"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="e5ea3-102">ICorProfilerCallback::RootReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5ea3-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="e5ea3-103">Powiadamia program profilujący informacje na temat odwołań do katalogu głównego po wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e5ea3-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ea3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5ea3-104">Syntax</span></span>  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5ea3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5ea3-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="e5ea3-106">[in] Liczba odwołań w `rootRefIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e5ea3-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="e5ea3-107">[in] Tablica identyfikatory obiektów, odwołujące się do obiektu statycznego lub obiekt na stosie.</span><span class="sxs-lookup"><span data-stu-id="e5ea3-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5ea3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5ea3-108">Remarks</span></span>  
 <span data-ttu-id="e5ea3-109">Zarówno `RootReferences` i [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) są wywoływane w celu powiadomić profiler.</span><span class="sxs-lookup"><span data-stu-id="e5ea3-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="e5ea3-110">Profilery wdroży zwykle jednej lub drugiej, ale nie oba, ponieważ informacje są przekazywane w `RootReferences2` jest nadzbiorem, przekazanej `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="e5ea3-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="e5ea3-111">Możliwe jest `rootRefIds` tablicy zawiera obiekt z wartością null.</span><span class="sxs-lookup"><span data-stu-id="e5ea3-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="e5ea3-112">Na przykład wszystkie odwołania do obiektu zadeklarowany na stosie są traktowane jako elementy główne przez moduł odśmiecania pamięci i zawsze będą raportowane.</span><span class="sxs-lookup"><span data-stu-id="e5ea3-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="e5ea3-113">Identyfikatory obiektów są zwracane przez `RootReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucania elementów bezużytecznych może być w trakcie przenoszenia obiektów z stare adresy do nowych adresów.</span><span class="sxs-lookup"><span data-stu-id="e5ea3-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="e5ea3-114">W związku z tym, profilowania nie wolno próbować Zbadaj obiekty podczas `RootReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="e5ea3-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="e5ea3-115">Gdy [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wszystkie obiekty zostały przeniesione do ich nowych lokalizacji i może być bezpiecznie kontrolowane.</span><span class="sxs-lookup"><span data-stu-id="e5ea3-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5ea3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5ea3-116">Requirements</span></span>  
 <span data-ttu-id="e5ea3-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ea3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ea3-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5ea3-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5ea3-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5ea3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5ea3-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ea3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ea3-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5ea3-121">See also</span></span>
- [<span data-ttu-id="e5ea3-122">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5ea3-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
