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
ms.openlocfilehash: 79be2572f52ec509d9551261074204bf62ad5388
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445060"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="77e54-102">ICorProfilerCallback::COMClassicVTableCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="77e54-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="77e54-103">Powiadamia program profilujący, że utworzono tablicę jednoelementową dla określonego identyfikatora IID i klasy.</span><span class="sxs-lookup"><span data-stu-id="77e54-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77e54-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77e54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77e54-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="77e54-106">podczas Identyfikator klasy, dla której utworzono tablicę.</span><span class="sxs-lookup"><span data-stu-id="77e54-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="77e54-107">podczas Identyfikator interfejsu zaimplementowanego przez klasę.</span><span class="sxs-lookup"><span data-stu-id="77e54-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="77e54-108">Ta wartość może być RÓWNa NULL, jeśli interfejs jest tylko wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="77e54-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="77e54-109">podczas Wskaźnik do początku elementu tablicowego.</span><span class="sxs-lookup"><span data-stu-id="77e54-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="77e54-110">podczas Liczba gniazd, które znajdują się w tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="77e54-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77e54-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77e54-111">Remarks</span></span>  
 <span data-ttu-id="77e54-112">Profiler nie powinien blokować swojej implementacji tej metody, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych i dlatego nie można włączyć zastępujący elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="77e54-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="77e54-113">Jeśli profiler blokuje tutaj i zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="77e54-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="77e54-114">Implementacja profilera nie powinna być wywoływana w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="77e54-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77e54-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77e54-115">Requirements</span></span>  
 <span data-ttu-id="77e54-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77e54-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77e54-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="77e54-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77e54-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="77e54-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77e54-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77e54-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e54-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77e54-120">See also</span></span>

- [<span data-ttu-id="77e54-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="77e54-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="77e54-122">COMClassicVTableDestroyed, metoda</span><span class="sxs-lookup"><span data-stu-id="77e54-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
