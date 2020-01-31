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
ms.openlocfilehash: 948628f469eecabfbbe792dcc3edf2e1204ffc36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865964"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="74ffe-102">ICorProfilerCallback::RootReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="74ffe-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="74ffe-103">Powiadamia profiler o informacji o odwołaniach głównych po wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="74ffe-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ffe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="74ffe-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="74ffe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74ffe-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="74ffe-106">podczas Liczba odwołań w tablicy `rootRefIds`.</span><span class="sxs-lookup"><span data-stu-id="74ffe-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="74ffe-107">podczas Tablica identyfikatorów obiektów odwołujących się do obiektu statycznego lub obiektu na stosie.</span><span class="sxs-lookup"><span data-stu-id="74ffe-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74ffe-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74ffe-108">Remarks</span></span>  
 <span data-ttu-id="74ffe-109">Elementy `RootReferences` i [ICorProfilerCallback2:: RootReferences2 —](icorprofilercallback2-rootreferences2-method.md) są wywoływane w celu powiadomienia profilera.</span><span class="sxs-lookup"><span data-stu-id="74ffe-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="74ffe-110">Obiekty profilowające zwykle implementują jeden lub drugi, ale nie obie, ponieważ informacje przesyłane `RootReferences2` są nadzbiorem, który przeszedł `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="74ffe-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="74ffe-111">Istnieje możliwość, aby tablica `rootRefIds` zawierała obiekt o wartości null.</span><span class="sxs-lookup"><span data-stu-id="74ffe-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="74ffe-112">Na przykład wszystkie odwołania do obiektów zadeklarowane na stosie są traktowane jako elementy główne przez moduł wyrzucania elementów bezużytecznych i zawsze będą raportowane.</span><span class="sxs-lookup"><span data-stu-id="74ffe-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="74ffe-113">Identyfikatory obiektów zwrócone przez `RootReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może być w trakcie przeniesienia obiektów ze starych adresów na nowe adresy.</span><span class="sxs-lookup"><span data-stu-id="74ffe-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="74ffe-114">W związku z tym, nie mogą próbować zbadać obiektów podczas wywołania `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="74ffe-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="74ffe-115">Gdy wywoływana jest [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) , wszystkie obiekty zostały przeniesione do nowych lokalizacji i można je bezpiecznie sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="74ffe-115">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74ffe-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74ffe-116">Requirements</span></span>  
 <span data-ttu-id="74ffe-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74ffe-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74ffe-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="74ffe-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74ffe-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="74ffe-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74ffe-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74ffe-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ffe-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74ffe-121">See also</span></span>

- [<span data-ttu-id="74ffe-122">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="74ffe-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
