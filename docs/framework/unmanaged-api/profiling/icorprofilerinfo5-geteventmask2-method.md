---
title: Metoda ICorProfilerInfo5::GetEventMask2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerInfo5.GetEventMask2
api_location: mscorwks.dll
api_type: COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72adbbdc3495f4171f555d119cb61d5dbc5ef0e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="aff36-102">Metoda ICorProfilerInfo5::GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="aff36-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="aff36-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="aff36-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="aff36-104">Pobiera bieżący kategorii zdarzeń, dla których chce otrzymywać powiadomień według środowisko uruchomieniowe języka wspólnego (CLR) profilera.</span><span class="sxs-lookup"><span data-stu-id="aff36-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="aff36-105">Zapewnia funkcje nie są udostępniane przez [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="aff36-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aff36-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="aff36-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aff36-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="aff36-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="aff36-108">[out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aff36-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="aff36-109">Każdy bit określa różne możliwości, zachowanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aff36-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="aff36-110">Bity zostały opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="aff36-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="aff36-111">[out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aff36-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="aff36-112">Każdy bit określa różne możliwości, zachowanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aff36-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="aff36-113">Bity zostały opisane w [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="aff36-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aff36-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aff36-114">Remarks</span></span>  
 <span data-ttu-id="aff36-115">`GetEventMask2` Metoda jest używana do określenia wywołania zwrotne, które subskrybuje profilera.</span><span class="sxs-lookup"><span data-stu-id="aff36-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="aff36-116">Zwykle wykonać logicznych lub `pdwEventsLow` i `pdwEventsHigh` wartości i wszelkie nowe bity chcesz ustawić, a następnie wywołać [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="aff36-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="aff36-117">Ta metoda jest zalecanym sposobem [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="aff36-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aff36-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aff36-118">Requirements</span></span>  
 <span data-ttu-id="aff36-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aff36-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aff36-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aff36-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aff36-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aff36-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aff36-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aff36-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff36-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aff36-123">See Also</span></span>  
 [<span data-ttu-id="aff36-124">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="aff36-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [<span data-ttu-id="aff36-125">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="aff36-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
