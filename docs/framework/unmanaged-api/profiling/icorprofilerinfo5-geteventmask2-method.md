---
title: Metoda ICorProfilerInfo5::GetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8ebddf9a16b2eddbbc58342f68b517064e8d794
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214640"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="d2480-102">Metoda ICorProfilerInfo5::GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="d2480-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="d2480-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="d2480-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d2480-104">Pobiera bieżący kategorie zdarzeń, dla których program profilujący chce otrzymywać powiadomienia z środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d2480-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="d2480-105">Oferuje funkcje, które nie został dostarczony przez [icorprofilerinfo::geteventmask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d2480-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2480-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2480-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2480-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2480-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="d2480-108">[out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d2480-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="d2480-109">Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d2480-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="d2480-110">Bity są opisane w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d2480-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="d2480-111">[out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d2480-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="d2480-112">Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d2480-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="d2480-113">Bity są opisane w [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d2480-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2480-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2480-114">Remarks</span></span>  
 <span data-ttu-id="d2480-115">`GetEventMask2` Metoda jest używana do określenia wywołania zwrotne, które zostały zasubskrybowane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="d2480-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="d2480-116">Zwykle wykonać logiczne OR `pdwEventsLow` i `pdwEventsHigh` wartości i żadnych nowych elementów, które chcesz ustawić, a następnie wywołaj [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d2480-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="d2480-117">Ta metoda jest zalecaną alternatywą [geteventmask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d2480-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2480-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2480-118">Requirements</span></span>  
 <span data-ttu-id="d2480-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2480-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2480-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d2480-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2480-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2480-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d2480-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d2480-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d2480-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2480-123">See also</span></span>

- [<span data-ttu-id="d2480-124">Interfejs ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="d2480-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="d2480-125">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="d2480-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
