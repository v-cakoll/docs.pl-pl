---
title: ICorProfilerCallback::Initialize — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16001c4af2bcd8aa8d5fff6b06fa8c275bc24cb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191006"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="79d68-102">ICorProfilerCallback::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="79d68-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="79d68-103">Wywoływane w celu zainicjowania programu profilującego kodu, przy każdym uruchomieniu typowych aplikacji środowiska uruchomieniowego (języka wspólnego CLR) języka.</span><span class="sxs-lookup"><span data-stu-id="79d68-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79d68-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="79d68-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79d68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79d68-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="79d68-106">[w](/cpp/atl/iunknown) interfejs, który program profilujący musi szukać [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="79d68-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79d68-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79d68-107">Remarks</span></span>  
 <span data-ttu-id="79d68-108">`Initialize` Wywołanie jest tylko szansy sprzedaży, aby włączyć (lub wyłączyć) wywołania zwrotne, które są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="79d68-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="79d68-109">Po włączeniu wywołanie zwrotne przez `Initialize` wywoływać, nie można wyłączyć, używając [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="79d68-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="79d68-110">Wartość COR_PRF_MONITOR_IMMUTABLE [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia wskazuje, jakie zdarzenia są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="79d68-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79d68-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="79d68-111">Requirements</span></span>  
 <span data-ttu-id="79d68-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79d68-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79d68-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79d68-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79d68-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79d68-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="79d68-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="79d68-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="79d68-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79d68-116">See also</span></span>

- [<span data-ttu-id="79d68-117">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="79d68-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="79d68-118">Shutdown, metoda</span><span class="sxs-lookup"><span data-stu-id="79d68-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
