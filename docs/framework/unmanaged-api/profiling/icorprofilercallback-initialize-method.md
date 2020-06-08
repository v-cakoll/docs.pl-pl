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
ms.openlocfilehash: ea4fc8ab39d616415106150f56f4b7afd5f68237
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500107"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="eb919-102">ICorProfilerCallback::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb919-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="eb919-103">Wywołuje się, by zainicjować profiler kodu za każdym razem, gdy jest uruchomiona nowa aplikacja środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="eb919-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb919-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb919-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb919-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb919-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="eb919-106">\[in) wskaźnik do interfejsu [IUnknown](/cpp/atl/iunknown) , który profiler musi wykonać zapytanie o wskaźnik interfejsu [ICorProfilerInfo](icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="eb919-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="eb919-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb919-107">Remarks</span></span>  
 <span data-ttu-id="eb919-108">`Initialize`Wywołanie jest jedyną możliwością, aby włączyć (lub wyłączyć) wywołania zwrotne, które są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="eb919-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="eb919-109">Po włączeniu wywołania zwrotnego przez `Initialize` wywołanie nie można go wyłączyć później za pomocą [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="eb919-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="eb919-110">COR_PRF_MONITOR_IMMUTABLE wartość wyliczenia [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) wskazuje, które zdarzenia są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="eb919-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb919-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb919-111">Requirements</span></span>  
 <span data-ttu-id="eb919-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb919-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb919-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eb919-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb919-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eb919-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb919-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb919-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb919-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb919-116">See also</span></span>

- [<span data-ttu-id="eb919-117">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="eb919-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="eb919-118">Shutdown, metoda</span><span class="sxs-lookup"><span data-stu-id="eb919-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
