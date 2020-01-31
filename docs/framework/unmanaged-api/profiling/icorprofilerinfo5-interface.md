---
title: Interfejs ICorProfilerInfo5
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: 655cdd5db0894a4e44d43b071caf1ee0829ffe50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861726"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="c0d4e-102">Interfejs ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="c0d4e-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="c0d4e-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="c0d4e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c0d4e-104">Podklasa elementu [ICorProfilerInfo4](icorprofilerinfo4-interface.md) , która dostarcza metody do użycia przez program Code profilowas do komunikowania się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania monitorowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c0d4e-104">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0d4e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c0d4e-105">Methods</span></span>  
  
|<span data-ttu-id="c0d4e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c0d4e-106">Method</span></span>|<span data-ttu-id="c0d4e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c0d4e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0d4e-108">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="c0d4e-108">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="c0d4e-109">Pobiera bieżące kategorie zdarzeń, dla których profiler chce otrzymywać powiadomienia z aparatu CLR.</span><span class="sxs-lookup"><span data-stu-id="c0d4e-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="c0d4e-110">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="c0d4e-110">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="c0d4e-111">Ustawia wartość określającą typy zdarzeń, dla których profiler chce odbierać powiadomienia o zdarzeniach z środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="c0d4e-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0d4e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0d4e-112">Remarks</span></span>  
 <span data-ttu-id="c0d4e-113">Metody dostępne w tym interfejsie zastępują metody [ICorProfilerInfo:: GetEventMask —](icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c0d4e-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0d4e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0d4e-114">Requirements</span></span>  
 <span data-ttu-id="c0d4e-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0d4e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0d4e-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c0d4e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0d4e-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0d4e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d4e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0d4e-118">See also</span></span>

- [<span data-ttu-id="c0d4e-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c0d4e-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
