---
title: ICorProfilerCallback::COMClassicVTableCreated — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4aa11b036c64ff6ffeec583c4cdd818d26067a74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162452"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="91cd8-102">ICorProfilerCallback::COMClassicVTableCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="91cd8-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="91cd8-103">Powiadamia program profilujący vtable międzyoperacyjnego modelu COM, dla określonego identyfikatora IID i klasa została utworzona.</span><span class="sxs-lookup"><span data-stu-id="91cd8-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91cd8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91cd8-104">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91cd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91cd8-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="91cd8-106">[in] Identyfikator klasy, dla którego została utworzona vtable.</span><span class="sxs-lookup"><span data-stu-id="91cd8-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="91cd8-107">[in] Identyfikator interfejsu zaimplementowany przez klasę.</span><span class="sxs-lookup"><span data-stu-id="91cd8-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="91cd8-108">Ta wartość może być NULL, jeśli interfejs jest tylko wewnętrzna.</span><span class="sxs-lookup"><span data-stu-id="91cd8-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="91cd8-109">[in] Wskaźnik do początku vtable.</span><span class="sxs-lookup"><span data-stu-id="91cd8-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="91cd8-110">[in] Liczba miejsc, które znajdują się w vtable.</span><span class="sxs-lookup"><span data-stu-id="91cd8-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91cd8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91cd8-111">Remarks</span></span>  
 <span data-ttu-id="91cd8-112">Program profilujący nie powinna blokować w jego implementacja tej metody, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="91cd8-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="91cd8-113">Jeśli program profilujący blokuje tutaj i wyrzucania elementów bezużytecznych jest podejmowana próba, środowisko uruchomieniowe spowoduje zablokowanie, dopóki nie zwróci to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="91cd8-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="91cd8-114">Implementacja tej metody program profilujący nie powinien wywoływać wywołanie kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="91cd8-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91cd8-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91cd8-115">Requirements</span></span>  
 <span data-ttu-id="91cd8-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91cd8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91cd8-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91cd8-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91cd8-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91cd8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91cd8-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91cd8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91cd8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91cd8-120">See also</span></span>

- [<span data-ttu-id="91cd8-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="91cd8-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="91cd8-122">COMClassicVTableDestroyed, metoda</span><span class="sxs-lookup"><span data-stu-id="91cd8-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
