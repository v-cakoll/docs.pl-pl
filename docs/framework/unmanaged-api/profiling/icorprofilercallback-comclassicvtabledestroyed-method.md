---
title: ICorProfilerCallback::COMClassicVTableDestroyed — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
ms.openlocfilehash: 98d5dcf3b691f16f63390851e207f518bf26ab11
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866523"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="1eaef-102">ICorProfilerCallback::COMClassicVTableDestroyed — Metoda</span><span class="sxs-lookup"><span data-stu-id="1eaef-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="1eaef-103">Powiadamia profiler o zniszczeniu międzyoperacyjności modelu COM Interop.</span><span class="sxs-lookup"><span data-stu-id="1eaef-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1eaef-104">To wywołanie zwrotne prawdopodobnie nigdy nie wystąpi, ponieważ zniszczenie tablic wirtualnych występuje bardzo blisko zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="1eaef-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eaef-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1eaef-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1eaef-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1eaef-106">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="1eaef-107">\[in) identyfikator klasy, dla której utworzono tę tablicę.</span><span class="sxs-lookup"><span data-stu-id="1eaef-107">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="1eaef-108">\[in) identyfikator interfejsu zaimplementowanego przez klasę.</span><span class="sxs-lookup"><span data-stu-id="1eaef-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="1eaef-109">Ta wartość może być RÓWNa NULL, jeśli interfejs jest tylko wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="1eaef-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="1eaef-110">\[w] wskaźnik do początku elementu tablicowego.</span><span class="sxs-lookup"><span data-stu-id="1eaef-110">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="1eaef-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1eaef-111">Remarks</span></span>  
 <span data-ttu-id="1eaef-112">Profiler nie powinien blokować swojej implementacji tej metody, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych i dlatego nie można włączyć zastępujący elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1eaef-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="1eaef-113">Jeśli profiler blokuje tutaj i zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1eaef-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="1eaef-114">Implementacja profilera nie powinna być wywoływana w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="1eaef-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eaef-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1eaef-115">Requirements</span></span>  
 <span data-ttu-id="1eaef-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eaef-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eaef-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1eaef-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1eaef-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1eaef-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1eaef-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eaef-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eaef-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1eaef-120">See also</span></span>

- [<span data-ttu-id="1eaef-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="1eaef-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1eaef-122">COMClassicVTableCreated, metoda</span><span class="sxs-lookup"><span data-stu-id="1eaef-122">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
