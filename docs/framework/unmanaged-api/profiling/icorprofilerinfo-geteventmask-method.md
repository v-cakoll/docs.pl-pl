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
ms.openlocfilehash: a1051f42788b3c2a63780f43f5784b063ef23027
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483994"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="9057d-102">ICorProfilerInfo::GetEventMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="9057d-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="9057d-103">Pobiera bieżący kategorie zdarzeń, dla których program profilujący chce otrzymywać powiadomienia o zdarzeniach środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="9057d-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9057d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9057d-104">Syntax</span></span>  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9057d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9057d-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="9057d-106">[out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9057d-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="9057d-107">Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9057d-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="9057d-108">Bity są opisane w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9057d-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9057d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9057d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9057d-110">Należy wywołać [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metody zamiast tej metody.</span><span class="sxs-lookup"><span data-stu-id="9057d-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="9057d-111">Mimo że `SetEventMask` metoda może być obsługiwany, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) udostępnia dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="9057d-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9057d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9057d-112">Requirements</span></span>  
 <span data-ttu-id="9057d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9057d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9057d-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9057d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9057d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9057d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9057d-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9057d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9057d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9057d-117">See also</span></span>
- [<span data-ttu-id="9057d-118">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="9057d-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="9057d-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="9057d-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
