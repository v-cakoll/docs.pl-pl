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
ms.openlocfilehash: 4ba082182ec7e2f639ef94baeb29203ee792fba0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="3f564-102">Interfejs ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="3f564-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="3f564-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="3f564-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3f564-104">Podklasa [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) zapewnia metody do użycia przez profilery kodu do komunikowania się z środowisko uruchomieniowe języka wspólnego (CLR), aby kontrolować monitorowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3f564-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f564-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3f564-105">Methods</span></span>  
  
|<span data-ttu-id="3f564-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3f564-106">Method</span></span>|<span data-ttu-id="3f564-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3f564-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f564-108">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="3f564-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="3f564-109">Pobiera bieżący kategorii zdarzeń, dla których chce otrzymywać powiadomień według CLR profilera.</span><span class="sxs-lookup"><span data-stu-id="3f564-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="3f564-110">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="3f564-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="3f564-111">Ustawia wartość, która określa typy zdarzeń, dla których chce otrzymywać powiadomienia o zdarzeniach środowiska CLR profilera.</span><span class="sxs-lookup"><span data-stu-id="3f564-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f564-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f564-112">Remarks</span></span>  
 <span data-ttu-id="3f564-113">Dostępne metody w tym interfejsie mają na celu Zastąp [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3f564-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f564-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f564-114">Requirements</span></span>  
 <span data-ttu-id="3f564-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f564-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f564-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3f564-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f564-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f564-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f564-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f564-118">See Also</span></span>  
 [<span data-ttu-id="3f564-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3f564-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
