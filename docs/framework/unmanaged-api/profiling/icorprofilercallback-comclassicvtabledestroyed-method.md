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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30d1e80d05344448c19c9f8f2d261442e4041487
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="9ba67-102">ICorProfilerCallback::COMClassicVTableDestroyed — Metoda</span><span class="sxs-lookup"><span data-stu-id="9ba67-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="9ba67-103">Powiadamia profilera vtable międzyoperacyjnego modelu COM jest niszczone.</span><span class="sxs-lookup"><span data-stu-id="9ba67-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ba67-104">Tego wywołania zwrotnego prawdopodobnie nigdy nie występuje, ponieważ zniszczenie tablic metod wirtualnych odbywa się bardzo bliski zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="9ba67-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ba67-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ba67-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ba67-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ba67-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="9ba67-107">[in] Identyfikator klasy, dla którego utworzono ten vtable.</span><span class="sxs-lookup"><span data-stu-id="9ba67-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="9ba67-108">[in] Identyfikator interfejsu zaimplementowany przez klasę.</span><span class="sxs-lookup"><span data-stu-id="9ba67-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="9ba67-109">Ta wartość może być NULL, jeśli interfejs jest tylko wewnętrzna.</span><span class="sxs-lookup"><span data-stu-id="9ba67-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="9ba67-110">[in] Wskaźnik do początku vtable.</span><span class="sxs-lookup"><span data-stu-id="9ba67-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ba67-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ba67-111">Remarks</span></span>  
 <span data-ttu-id="9ba67-112">Profilera nie należy zablokować w jej implementacja tej metody, ponieważ stos nie może być w stanie, który umożliwia odzyskiwanie pamięci i dlatego nie można włączyć cenią sobie wcześniejsze wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9ba67-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9ba67-113">Jeśli profilera blokuje tutaj i nastąpiła wyrzucanie elementów bezużytecznych, środowisko uruchomieniowe zablokuje dopóki zwraca tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9ba67-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9ba67-114">Profiler implementacja tej metody nie powinny wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="9ba67-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ba67-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ba67-115">Requirements</span></span>  
 <span data-ttu-id="9ba67-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ba67-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ba67-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ba67-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ba67-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ba67-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ba67-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ba67-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba67-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ba67-120">See Also</span></span>  
 [<span data-ttu-id="9ba67-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ba67-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9ba67-122">COMClassicVTableCreated, metoda</span><span class="sxs-lookup"><span data-stu-id="9ba67-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
