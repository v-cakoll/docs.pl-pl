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
ms.openlocfilehash: 6c9ec6af90cc47c3c01621563a9813789c25aa1d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500341"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="b0adb-102">ICorProfilerCallback::COMClassicVTableCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0adb-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="b0adb-103">Powiadamia program profilujący, że utworzono tablicę jednoelementową dla określonego identyfikatora IID i klasy.</span><span class="sxs-lookup"><span data-stu-id="b0adb-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0adb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0adb-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0adb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0adb-105">Parameters</span></span>

- `wrappedClasId`

  <span data-ttu-id="b0adb-106">\[in] Identyfikator klasy, dla której utworzono tablicę.</span><span class="sxs-lookup"><span data-stu-id="b0adb-106">\[in] The ID of the class for which the vtable has been created.</span></span>

- `implementedIID`

  <span data-ttu-id="b0adb-107">\[in) identyfikator interfejsu zaimplementowanego przez klasę.</span><span class="sxs-lookup"><span data-stu-id="b0adb-107">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="b0adb-108">Ta wartość może być RÓWNa NULL, jeśli interfejs jest tylko wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="b0adb-108">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="b0adb-109">\[w] wskaźnik do początku tabeli tablicowej.</span><span class="sxs-lookup"><span data-stu-id="b0adb-109">\[in] A pointer to the start of the vtable.</span></span>

- `cSlots`

  <span data-ttu-id="b0adb-110">\[w] Liczba gniazd, które znajdują się w tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="b0adb-110">\[in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0adb-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0adb-111">Remarks</span></span>  
 <span data-ttu-id="b0adb-112">Profiler nie powinien blokować swojej implementacji tej metody, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych i dlatego nie można włączyć zastępujący elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b0adb-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b0adb-113">Jeśli profiler blokuje tutaj i zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b0adb-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b0adb-114">Implementacja profilera nie powinna być wywoływana w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="b0adb-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0adb-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0adb-115">Requirements</span></span>  
 <span data-ttu-id="b0adb-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0adb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0adb-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b0adb-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0adb-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b0adb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0adb-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0adb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0adb-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0adb-120">See also</span></span>

- [<span data-ttu-id="b0adb-121">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b0adb-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b0adb-122">COMClassicVTableDestroyed, metoda</span><span class="sxs-lookup"><span data-stu-id="b0adb-122">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
