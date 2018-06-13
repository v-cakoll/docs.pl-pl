---
title: Metoda ICorProfilerCallback5::ConditionalWeakTableElementReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- CondiitonalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ee3c3302d77bcc7b807c01ccb5bab172153ddda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459954"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="555d9-102">Metoda ICorProfilerCallback5::ConditionalWeakTableElementReferences</span><span class="sxs-lookup"><span data-stu-id="555d9-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>
<span data-ttu-id="555d9-103">Identyfikuje przechodnie zamknięcia odwołuje się katalogami za pomocą obu odwołania do pól bezpośrednimi elementami członkowskimi i za pomocą obiektów `ConditionalWeakTable` zależności.</span><span class="sxs-lookup"><span data-stu-id="555d9-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="555d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="555d9-104">Syntax</span></span>  
  
```  
HRESULT ConditionalWeakTableElementReferences(     [in]                     ULONG    cRootRefs,     [in, size_is(cRootRefs)] ObjectID keyRefIds[],     [in, size_is(cRootRefs)] ObjectID valueRefIds[],     [in, size_is(cRootRefs)] GCHandleID rootIds[]);};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="555d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="555d9-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="555d9-106">[in] Liczba elementów w `keyRefIds`, `valueRefIds`, i `rootIds` tablic.</span><span class="sxs-lookup"><span data-stu-id="555d9-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>  
  
 `keyRefIds`  
 <span data-ttu-id="555d9-107">[in] Tablica wartości identyfikatorów obiektów, z których każdy zawiera `ObjectID` podstawowego elementu w parze dojścia zależnych.</span><span class="sxs-lookup"><span data-stu-id="555d9-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>  
  
 `valueRefIds`  
 <span data-ttu-id="555d9-108">[in] Tablica wartości identyfikatorów obiektów, z których każdy zawiera `ObjectID` dla elementu pomocniczego w parze dojścia zależnych.</span><span class="sxs-lookup"><span data-stu-id="555d9-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="555d9-109">(`keyRefIds[i]` przechowuje `valueRefIds[i]` aktywności.)</span><span class="sxs-lookup"><span data-stu-id="555d9-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>  
  
 `rootIds`  
 <span data-ttu-id="555d9-110">[in] Tablica `GCHandleID` wartości, które wskazują liczba całkowita, która zawiera dodatkowe informacje dotyczące głównego kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="555d9-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>  
  
 <span data-ttu-id="555d9-111">Żadna z `ObjectID` wartości zwracanych przez `ConditionalWeakTableElementReferences` — metoda są prawidłowe podczas wywołania zwrotnego, ponieważ moduł garbage collector może znajdować się w trakcie przenoszenia obiektów ze starej do nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="555d9-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="555d9-112">W związku z tym profilery nie powinny podejmować próby sprawdź obiekty podczas `ConditionalWeakTableElementReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="555d9-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="555d9-113">W `GarbageCollectionFinished`, wszystkie obiekty zostały przeniesione do nowej lokalizacji i można przeprowadzić inspekcji.</span><span class="sxs-lookup"><span data-stu-id="555d9-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>  
  
## <a name="example"></a><span data-ttu-id="555d9-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="555d9-114">Example</span></span>  
 <span data-ttu-id="555d9-115">Poniższy przykład kodu pokazuje, jak wdrożyć [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) i użyć tej metody.</span><span class="sxs-lookup"><span data-stu-id="555d9-115">The following code example demonstrates how to implement [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) and use this method.</span></span>  
  
```  
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(  
    ULONG      cRootRefs,  
    ObjectID   keyRefIds[],  
    ObjectID   valueRefIds[],  
    GCHandleID rootIds[])  
{  
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");  
    for (unsigned int i = 0; i < cRootRefs; ++i)  
    {  
        // Save dependency to XML for later retrieval  
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);  
        // or store dependency to an internal map  
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);  
        // or add arc to object graph  
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);  
    }  
    return S_OK;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="555d9-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="555d9-116">Remarks</span></span>  
 <span data-ttu-id="555d9-117">Profilera dla [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] lub nowsze wersje implementuje [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) interfejsu i rejestruje zależności określony przez `ConditionalWeakTableElementReferences` metody.</span><span class="sxs-lookup"><span data-stu-id="555d9-117">A profiler for the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] or later versions implements the [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="555d9-118">`ICorProfilerCallback5` zapewnia pełny zestaw zależności między obiektami na żywo reprezentowany przez `ConditionalWeakTable` wpisów.</span><span class="sxs-lookup"><span data-stu-id="555d9-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="555d9-119">Te zależności i element członkowski odwołania określony przez pole [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) metoda włączyć zarządzany profiler do generowania wykresu obiektu pełne obiektów na żywo.</span><span class="sxs-lookup"><span data-stu-id="555d9-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="555d9-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="555d9-120">Requirements</span></span>  
 <span data-ttu-id="555d9-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="555d9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="555d9-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="555d9-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="555d9-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="555d9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="555d9-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="555d9-124">See Also</span></span>  
 [<span data-ttu-id="555d9-125">ICorProfilerCallback5, interfejs</span><span class="sxs-lookup"><span data-stu-id="555d9-125">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)
