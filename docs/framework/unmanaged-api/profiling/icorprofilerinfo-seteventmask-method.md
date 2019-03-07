---
title: ICorProfilerInfo::SetEventMask — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66a59fd338b9cbaadb2c19d0957c38ffe1af25e9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471293"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="0876c-102">ICorProfilerInfo::SetEventMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="0876c-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="0876c-103">Ustawia wartość, która określa typy zdarzeń, dla których program profilujący chce otrzymywać powiadomienia z środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="0876c-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0876c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0876c-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0876c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0876c-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="0876c-106">[in] Wartość 4-bajtowych, który określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0876c-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="0876c-107">Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0876c-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="0876c-108">Bity są opisane w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0876c-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0876c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0876c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0876c-110">Należy wywołać [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody zamiast tej metody.</span><span class="sxs-lookup"><span data-stu-id="0876c-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="0876c-111">Mimo że `SetEventMask` metoda może być obsługiwany, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) udostępnia dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="0876c-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0876c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0876c-112">Requirements</span></span>  
 <span data-ttu-id="0876c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0876c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0876c-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0876c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0876c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0876c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0876c-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0876c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0876c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0876c-117">See also</span></span>
- [<span data-ttu-id="0876c-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="0876c-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="0876c-119">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="0876c-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
