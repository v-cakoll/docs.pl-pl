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
ms.openlocfilehash: 6cc1cfadd809b7406845596ace78e308ccbf529a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="2a4f0-102">Metoda ICorProfilerInfo5::SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="2a4f0-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="2a4f0-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="2a4f0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2a4f0-104">Ustawia wartość, która określa typy zdarzeń, dla których chce otrzymywać powiadomienia o zdarzeniach środowisko uruchomieniowe języka wspólnego (CLR) profilera.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="2a4f0-105">Zapewnia więcej funkcji niż [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a4f0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a4f0-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a4f0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a4f0-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="2a4f0-108">[in] Wartość 4-bajtowych, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="2a4f0-109">Każdy bit określa różne możliwości, zachowanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="2a4f0-110">Bity zostały opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="2a4f0-111">[in] Wartość 4-bajtowych, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="2a4f0-112">Każdy bit określa różne możliwości, zachowanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="2a4f0-113">Bity zostały opisane w [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a4f0-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a4f0-114">Remarks</span></span>  
 <span data-ttu-id="2a4f0-115">`SetEventMask2` Metoda jest używana do ustawiania wywołań zwrotnych, do których subskrybuje profilera.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="2a4f0-116">Zazwyczaj wywołanie [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metodę, aby określić, które są skonfigurowane, wykonaj logicznych lub jego `pdwEventsLow` i `pdwEventsHigh` wartości i wszelkie nowe bity chcesz ustawić, a następnie wywołać `SetEventMask2` — metoda.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="2a4f0-117">Ta metoda jest zalecanym sposobem [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2a4f0-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a4f0-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a4f0-118">Requirements</span></span>  
 <span data-ttu-id="2a4f0-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a4f0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a4f0-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a4f0-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a4f0-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a4f0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a4f0-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a4f0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4f0-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a4f0-123">See Also</span></span>  
 [<span data-ttu-id="2a4f0-124">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="2a4f0-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [<span data-ttu-id="2a4f0-125">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="2a4f0-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
