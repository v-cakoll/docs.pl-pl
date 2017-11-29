---
title: "ICorProfilerCallback::COMClassicVTableDestroyed — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableDestroyed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebff8297a708b130a0d3983fd75b76c3aeaeceaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="5a12d-102">ICorProfilerCallback::COMClassicVTableDestroyed — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a12d-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="5a12d-103">Powiadamia profilera vtable międzyoperacyjnego modelu COM jest niszczone.</span><span class="sxs-lookup"><span data-stu-id="5a12d-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a12d-104">Tego wywołania zwrotnego prawdopodobnie nigdy nie występuje, ponieważ zniszczenie tablic metod wirtualnych odbywa się bardzo bliski zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="5a12d-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a12d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a12d-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a12d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a12d-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="5a12d-107">[in] Identyfikator klasy, dla którego utworzono ten vtable.</span><span class="sxs-lookup"><span data-stu-id="5a12d-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="5a12d-108">[in] Identyfikator interfejsu zaimplementowany przez klasę.</span><span class="sxs-lookup"><span data-stu-id="5a12d-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="5a12d-109">Ta wartość może być NULL, jeśli interfejs jest tylko wewnętrzna.</span><span class="sxs-lookup"><span data-stu-id="5a12d-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="5a12d-110">[in] Wskaźnik do początku vtable.</span><span class="sxs-lookup"><span data-stu-id="5a12d-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a12d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a12d-111">Remarks</span></span>  
 <span data-ttu-id="5a12d-112">Profilera nie należy zablokować w jej implementacja tej metody, ponieważ stos nie może być w stanie, który umożliwia odzyskiwanie pamięci i dlatego nie można włączyć cenią sobie wcześniejsze wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5a12d-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="5a12d-113">Jeśli profilera blokuje tutaj i nastąpiła wyrzucanie elementów bezużytecznych, środowisko uruchomieniowe zablokuje dopóki zwraca tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5a12d-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="5a12d-114">Profiler implementacja tej metody nie powinny wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="5a12d-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a12d-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a12d-115">Requirements</span></span>  
 <span data-ttu-id="5a12d-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a12d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a12d-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a12d-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a12d-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a12d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a12d-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a12d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a12d-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a12d-120">See Also</span></span>  
 [<span data-ttu-id="5a12d-121">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="5a12d-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="5a12d-122">COMClassicVTableCreated — metoda</span><span class="sxs-lookup"><span data-stu-id="5a12d-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
