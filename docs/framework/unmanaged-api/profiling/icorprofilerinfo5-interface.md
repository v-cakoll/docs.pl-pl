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
ms.openlocfilehash: e6df5dcb26d61d30407d1efeeed7d207744276fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124187"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="5b6c1-102">Interfejs ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="5b6c1-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="5b6c1-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="5b6c1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5b6c1-104">Podklasa elementu [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) , która dostarcza metody do użycia przez program Code profilowas do komunikowania się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania monitorowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5b6c1-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b6c1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5b6c1-105">Methods</span></span>  
  
|<span data-ttu-id="5b6c1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5b6c1-106">Method</span></span>|<span data-ttu-id="5b6c1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5b6c1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b6c1-108">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="5b6c1-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="5b6c1-109">Pobiera bieżące kategorie zdarzeń, dla których profiler chce otrzymywać powiadomienia z aparatu CLR.</span><span class="sxs-lookup"><span data-stu-id="5b6c1-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="5b6c1-110">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="5b6c1-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="5b6c1-111">Ustawia wartość określającą typy zdarzeń, dla których profiler chce odbierać powiadomienia o zdarzeniach z środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5b6c1-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b6c1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b6c1-112">Remarks</span></span>  
 <span data-ttu-id="5b6c1-113">Metody dostępne w tym interfejsie zastępują metody [ICorProfilerInfo:: GetEventMask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5b6c1-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b6c1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b6c1-114">Requirements</span></span>  
 <span data-ttu-id="5b6c1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b6c1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b6c1-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5b6c1-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b6c1-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b6c1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b6c1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b6c1-118">See also</span></span>

- [<span data-ttu-id="5b6c1-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="5b6c1-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
