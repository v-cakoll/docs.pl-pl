---
title: "ICorProfilerInfo::SetEventMask — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetEventMask
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bb42be7f8e5722ec9924284c257e814a186564d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="ebdcf-102">ICorProfilerInfo::SetEventMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="ebdcf-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="ebdcf-103">Ustawia wartość, która określa typy zdarzeń, dla których chce otrzymywać powiadomienia środowisko uruchomieniowe języka wspólnego (CLR) profilera.</span><span class="sxs-lookup"><span data-stu-id="ebdcf-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebdcf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebdcf-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebdcf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebdcf-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="ebdcf-106">[in] Wartość 4-bajtowych, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ebdcf-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="ebdcf-107">Każdy bit określa różne możliwości, zachowanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ebdcf-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="ebdcf-108">Bity zostały opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ebdcf-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebdcf-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebdcf-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebdcf-110">Należy wywołać [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody zamiast tej metody.</span><span class="sxs-lookup"><span data-stu-id="ebdcf-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="ebdcf-111">Mimo że `SetEventMask` metoda może być obsługiwany, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) udostępnia dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="ebdcf-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebdcf-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebdcf-112">Requirements</span></span>  
 <span data-ttu-id="ebdcf-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebdcf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebdcf-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ebdcf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ebdcf-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebdcf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebdcf-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebdcf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebdcf-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebdcf-117">See Also</span></span>  
 [<span data-ttu-id="ebdcf-118">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="ebdcf-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="ebdcf-119">Metoda SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="ebdcf-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
