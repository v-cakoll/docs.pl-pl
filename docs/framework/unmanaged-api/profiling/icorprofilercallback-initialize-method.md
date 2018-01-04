---
title: "ICorProfilerCallback::Initialize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.Initialize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a54ed382724b99fb4b2ae3a21d2d212379f55fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="d3866-102">ICorProfilerCallback::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3866-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="d3866-103">Wywołuje się, by zainicjować profilera kodu przy każdym uruchomieniu typowych aplikacji środowiska uruchomieniowego (języka wspólnego CLR) języka.</span><span class="sxs-lookup"><span data-stu-id="d3866-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3866-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3866-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3866-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3866-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="d3866-106">[w](/cpp/atl/iunknown) interfejs, który należy wyszukać profilera [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d3866-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3866-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3866-107">Remarks</span></span>  
 <span data-ttu-id="d3866-108">`Initialize` Wywołanie jest tylko możliwość włączyć (lub wyłączyć) wywołań zwrotnych, które są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="d3866-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="d3866-109">Po włączeniu wywołanie zwrotne przez `Initialize` wywoływać, nie można wyłączyć później za pomocą [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="d3866-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="d3866-110">Wartość COR_PRF_MONITOR_IMMUTABLE [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenie wskazuje zdarzenia, które są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="d3866-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3866-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3866-111">Requirements</span></span>  
 <span data-ttu-id="d3866-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3866-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3866-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3866-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3866-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3866-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3866-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3866-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3866-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3866-116">See Also</span></span>  
 [<span data-ttu-id="d3866-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3866-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d3866-118">Shutdown, metoda</span><span class="sxs-lookup"><span data-stu-id="d3866-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
