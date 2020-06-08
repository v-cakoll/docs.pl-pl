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
- ConditionalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
ms.openlocfilehash: 17fbc99b30921f795c1f7ff882ec73432aade8c6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499249"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="cc2de-102">Metoda ICorProfilerCallback5::ConditionalWeakTableElementReferences</span><span class="sxs-lookup"><span data-stu-id="cc2de-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="cc2de-103">Identyfikuje przechodnie zamknięcie obiektów, do których odwołują się te elementy główne za pośrednictwem bezpośrednich odwołań do pól składowych i za pośrednictwem `ConditionalWeakTable` zależności.</span><span class="sxs-lookup"><span data-stu-id="cc2de-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="cc2de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc2de-104">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="cc2de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc2de-105">Parameters</span></span>

`cRootRefs`\
<span data-ttu-id="cc2de-106">podczas Liczba elementów w `keyRefIds` `valueRefIds` `rootIds` tablicach, i.</span><span class="sxs-lookup"><span data-stu-id="cc2de-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

`keyRefIds`\
<span data-ttu-id="cc2de-107">podczas Tablica identyfikatorów obiektów, z których każdy zawiera `ObjectID` element dla elementu podstawowego w parze uchwytów zależnych.</span><span class="sxs-lookup"><span data-stu-id="cc2de-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

`valueRefIds`\
<span data-ttu-id="cc2de-108">podczas Tablica identyfikatorów obiektów, z których każdy zawiera `ObjectID` element dla elementu pomocniczego w parze zależnych uchwytów.</span><span class="sxs-lookup"><span data-stu-id="cc2de-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="cc2de-109">( `keyRefIds[i]` utrzymuje `valueRefIds[i]` aktywność).</span><span class="sxs-lookup"><span data-stu-id="cc2de-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

`rootIds`\
<span data-ttu-id="cc2de-110">podczas Tablica `GCHandleID` wartości, która wskazuje liczbę całkowitą, która zawiera dodatkowe informacje o katalogu głównym wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cc2de-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="cc2de-111">Żadna z `ObjectID` wartości zwracanych przez `ConditionalWeakTableElementReferences` metodę nie jest prawidłowa podczas wywołania zwrotnego, ponieważ moduł wyrzucania elementów bezużytecznych może być w trakcie przechodzenia obiektów ze starych do nowych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="cc2de-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="cc2de-112">W związku z tym nie należy próbować kontrolować obiektów podczas `ConditionalWeakTableElementReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="cc2de-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="cc2de-113">W programie `GarbageCollectionFinished` wszystkie obiekty zostały przeniesione do nowych lokalizacji i można przeprowadzić inspekcję.</span><span class="sxs-lookup"><span data-stu-id="cc2de-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="cc2de-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc2de-114">Example</span></span>

<span data-ttu-id="cc2de-115">Poniższy przykład kodu demonstruje sposób implementacji [ICorProfilerCallback5](icorprofilercallback5-interface.md) i używania tej metody.</span><span class="sxs-lookup"><span data-stu-id="cc2de-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

```cpp
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

## <a name="remarks"></a><span data-ttu-id="cc2de-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc2de-116">Remarks</span></span>

<span data-ttu-id="cc2de-117">Profiler dla .NET Framework 4,5 lub nowszych wersji implementuje interfejs [ICorProfilerCallback5](icorprofilercallback5-interface.md) i rejestruje zależności określone przez `ConditionalWeakTableElementReferences` metodę.</span><span class="sxs-lookup"><span data-stu-id="cc2de-117">A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="cc2de-118">`ICorProfilerCallback5`zapewnia pełen zestaw zależności między obiektami na żywo reprezentowane przez `ConditionalWeakTable` wpisy.</span><span class="sxs-lookup"><span data-stu-id="cc2de-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="cc2de-119">Te zależności i odwołania do pól elementu członkowskiego określone przez metodę [ICorProfilerCallback:: ObjectReferences —](icorprofilercallback-objectreferences-method.md) umożliwiają zarządzanemu profilerowi generowanie grafu pełnego obiektu na żywo obiektów.</span><span class="sxs-lookup"><span data-stu-id="cc2de-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc2de-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc2de-120">Requirements</span></span>

<span data-ttu-id="cc2de-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc2de-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="cc2de-122">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cc2de-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="cc2de-123">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc2de-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cc2de-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc2de-124">See also</span></span>

- [<span data-ttu-id="cc2de-125">ICorProfilerCallback5, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc2de-125">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)
