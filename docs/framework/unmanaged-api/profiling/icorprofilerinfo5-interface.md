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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b249605833e8fbd219495ab92bebc2eff6177eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094258"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="aacf1-102">Interfejs ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="aacf1-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="aacf1-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="aacf1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="aacf1-104">Podklasa klasy [icorprofilerinfo4 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) , udostępnia metody do użycia przez profilery kodu do komunikowania się z środowisko uruchomieniowe języka wspólnego (CLR) do kontrolowania, monitorowanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aacf1-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aacf1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="aacf1-105">Methods</span></span>  
  
|<span data-ttu-id="aacf1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="aacf1-106">Method</span></span>|<span data-ttu-id="aacf1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="aacf1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aacf1-108">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="aacf1-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="aacf1-109">Pobiera bieżący kategorie zdarzeń, dla których program profilujący chce otrzymywać powiadomienia, ze środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="aacf1-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="aacf1-110">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="aacf1-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="aacf1-111">Ustawia wartość, która określa typy zdarzeń, dla których program profilujący chce otrzymywać powiadomienia o zdarzeniach, ze środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="aacf1-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aacf1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aacf1-112">Remarks</span></span>  
 <span data-ttu-id="aacf1-113">Metody dostępne dla tego interfejsu są przeznaczone do zastąpienia [icorprofilerinfo::geteventmask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="aacf1-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aacf1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aacf1-114">Requirements</span></span>  
 <span data-ttu-id="aacf1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aacf1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aacf1-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aacf1-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aacf1-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aacf1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aacf1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aacf1-118">See also</span></span>

- [<span data-ttu-id="aacf1-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="aacf1-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
