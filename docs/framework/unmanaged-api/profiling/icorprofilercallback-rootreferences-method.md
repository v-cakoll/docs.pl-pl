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
ms.openlocfilehash: 467d065ab4d47e698c7043697ebe2ccf5f98a3cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452588"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="848b0-102">ICorProfilerCallback::RootReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="848b0-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="848b0-103">Powiadamia profilera z informacji o odwołaniach głównego po wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="848b0-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="848b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="848b0-104">Syntax</span></span>  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="848b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="848b0-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="848b0-106">[in] Liczba odwołań w `rootRefIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="848b0-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="848b0-107">[in] Tablica identyfikatory obiektów, które odwołują się do statycznego obiektu albo obiekt na stosie.</span><span class="sxs-lookup"><span data-stu-id="848b0-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="848b0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="848b0-108">Remarks</span></span>  
 <span data-ttu-id="848b0-109">Zarówno `RootReferences` i [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) są wywoływane w celu powiadomienia profilera.</span><span class="sxs-lookup"><span data-stu-id="848b0-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="848b0-110">Profilery będzie zwykle implementowany jednej lub drugiej, ale nie obu, ponieważ informacje przekazano `RootReferences2` jest nadzbiorem tego przekazano `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="848b0-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="848b0-111">Istnieje możliwość `rootRefIds` tablica zawiera obiekt zerowy.</span><span class="sxs-lookup"><span data-stu-id="848b0-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="848b0-112">Na przykład wszystkie odwołania do obiektów zadeklarowane na stosie są traktowane jako katalogów głównych przez moduł garbage collector i zawsze będą zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="848b0-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="848b0-113">Identyfikatory obiektów zwrócona przez `RootReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w środku przenoszenie obiektów z stare adresy do nowych adresów.</span><span class="sxs-lookup"><span data-stu-id="848b0-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="848b0-114">W związku z tym profilowania nie wolno próbować sprawdzić obiekty podczas `RootReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="848b0-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="848b0-115">Gdy [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wszystkie obiekty zostały przeniesione do nowej lokalizacji i może być bezpiecznie kontrolowane.</span><span class="sxs-lookup"><span data-stu-id="848b0-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="848b0-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="848b0-116">Requirements</span></span>  
 <span data-ttu-id="848b0-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="848b0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="848b0-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="848b0-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="848b0-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="848b0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="848b0-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="848b0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="848b0-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="848b0-121">See Also</span></span>  
 [<span data-ttu-id="848b0-122">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="848b0-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
