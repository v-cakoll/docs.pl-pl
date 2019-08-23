---
title: ICorProfilerInfo::GetEventMask — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fea50b9d42511540197c80d4ba402834b216830
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957946"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="e578c-102">ICorProfilerInfo::GetEventMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="e578c-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="e578c-103">Pobiera bieżące kategorie zdarzeń, dla których profiler chce otrzymywać powiadomienia o zdarzeniach z aparatu plików wykonywalnych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e578c-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e578c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e578c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e578c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e578c-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="e578c-106">określoną Wskaźnik do 4-bajtowej wartości, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e578c-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="e578c-107">Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e578c-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="e578c-108">Bity są opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="e578c-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e578c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e578c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e578c-110">Zamiast tej metody należy wywołać metodę [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e578c-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="e578c-111">Mimo że metoda nadal jest obsługiwana, GetEventMask2 oferuje dodatkowe funkcje. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) `SetEventMask`</span><span class="sxs-lookup"><span data-stu-id="e578c-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e578c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e578c-112">Requirements</span></span>  
 <span data-ttu-id="e578c-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e578c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e578c-114">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e578c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e578c-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e578c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e578c-116">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e578c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e578c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e578c-117">See also</span></span>

- [<span data-ttu-id="e578c-118">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="e578c-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="e578c-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e578c-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
