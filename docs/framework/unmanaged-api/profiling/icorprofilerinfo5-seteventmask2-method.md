---
title: Metoda ICorProfilerInfo5::SetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 266219894ffefa0d4066c6ca68c7cadf6265e098
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175815"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="74768-102">Metoda ICorProfilerInfo5::SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="74768-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="74768-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="74768-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="74768-104">Ustawia wartość, która określa typy zdarzeń, dla których program profilujący chce otrzymywać powiadomienia o zdarzeniach środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="74768-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="74768-105">Zapewnia więcej funkcji niż [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="74768-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74768-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="74768-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74768-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="74768-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="74768-108">[in] Wartość 4-bajtowych, który określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="74768-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="74768-109">Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="74768-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="74768-110">Bity są opisane w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="74768-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="74768-111">[in] Wartość 4-bajtowych, który określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="74768-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="74768-112">Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="74768-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="74768-113">Bity są opisane w [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="74768-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74768-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74768-114">Remarks</span></span>  
 <span data-ttu-id="74768-115">`SetEventMask2` Metoda jest używana do ustawiania wywołań zwrotnych, do których subskrybuje profilera.</span><span class="sxs-lookup"><span data-stu-id="74768-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="74768-116">Zazwyczaj należy wywołać [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metodę pozwala ustalić, które bity są ustawione, wykonać logiczne OR z jego `pdwEventsLow` i `pdwEventsHigh` wartości i żadnych nowych elementów, które chcesz ustawić, a następnie wywołaj `SetEventMask2` metody.</span><span class="sxs-lookup"><span data-stu-id="74768-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="74768-117">Ta metoda jest zalecaną alternatywą [seteventmask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="74768-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74768-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74768-118">Requirements</span></span>  
 <span data-ttu-id="74768-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74768-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74768-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74768-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74768-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74768-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74768-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74768-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74768-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74768-123">See also</span></span>

- [<span data-ttu-id="74768-124">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="74768-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="74768-125">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="74768-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
