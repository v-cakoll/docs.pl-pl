---
title: "ICorProfilerCallback::COMClassicVTableCreated — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableCreated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 39fa655065c2af10750b1285ef047678874723ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="6e19b-102">ICorProfilerCallback::COMClassicVTableCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="6e19b-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="6e19b-103">Powiadamia profilera utworzono vtable międzyoperacyjnego modelu COM, dla określonego identyfikatora IID i klasy.</span><span class="sxs-lookup"><span data-stu-id="6e19b-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e19b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e19b-104">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e19b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e19b-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="6e19b-106">[in] Identyfikator klasy, dla którego utworzono vtable.</span><span class="sxs-lookup"><span data-stu-id="6e19b-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="6e19b-107">[in] Identyfikator interfejsu zaimplementowany przez klasę.</span><span class="sxs-lookup"><span data-stu-id="6e19b-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="6e19b-108">Ta wartość może być NULL, jeśli interfejs jest tylko wewnętrzna.</span><span class="sxs-lookup"><span data-stu-id="6e19b-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="6e19b-109">[in] Wskaźnik do początku vtable.</span><span class="sxs-lookup"><span data-stu-id="6e19b-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="6e19b-110">[in] Liczba gniazd, które znajdują się w vtable.</span><span class="sxs-lookup"><span data-stu-id="6e19b-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e19b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e19b-111">Remarks</span></span>  
 <span data-ttu-id="6e19b-112">Profilera nie należy zablokować w jej implementacja tej metody, ponieważ stos nie może być w stanie, który umożliwia odzyskiwanie pamięci i dlatego nie można włączyć cenią sobie wcześniejsze wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6e19b-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="6e19b-113">Jeśli profilera blokuje tutaj i nastąpiła wyrzucanie elementów bezużytecznych, środowisko uruchomieniowe zablokuje dopóki zwraca tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6e19b-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="6e19b-114">Profiler implementacja tej metody nie powinny wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="6e19b-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e19b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e19b-115">Requirements</span></span>  
 <span data-ttu-id="6e19b-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e19b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e19b-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e19b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e19b-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e19b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e19b-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e19b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e19b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e19b-120">See Also</span></span>  
 [<span data-ttu-id="6e19b-121">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="6e19b-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="6e19b-122">COMClassicVTableDestroyed — metoda</span><span class="sxs-lookup"><span data-stu-id="6e19b-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
