---
title: "ICorProfilerInfo::GetEventMask — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetEventMask
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f8bfc0dc5686aa560bfa8282256b5e476976136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="fe086-102">ICorProfilerInfo::GetEventMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe086-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="fe086-103">Pobiera bieżący kategorii zdarzeń, dla których chce otrzymywać powiadomienia o zdarzeniach środowisko uruchomieniowe języka wspólnego (CLR) profilera.</span><span class="sxs-lookup"><span data-stu-id="fe086-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe086-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe086-104">Syntax</span></span>  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe086-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe086-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="fe086-106">[out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fe086-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="fe086-107">Każdy bit określa różne możliwości, zachowanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fe086-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="fe086-108">Bity zostały opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="fe086-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe086-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe086-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe086-110">Należy wywołać [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metody zamiast tej metody.</span><span class="sxs-lookup"><span data-stu-id="fe086-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="fe086-111">Mimo że `SetEventMask` metoda może być obsługiwany, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) udostępnia dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="fe086-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe086-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe086-112">Requirements</span></span>  
 <span data-ttu-id="fe086-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe086-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe086-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe086-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe086-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe086-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe086-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe086-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe086-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe086-117">See Also</span></span>  
 [<span data-ttu-id="fe086-118">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="fe086-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)  
 [<span data-ttu-id="fe086-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="fe086-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
