---
title: ICorProfilerCallback::JITFunctionPitched — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91bc626e2c75cd7eb2eafad0fc26d343e5b278e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530735"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="f1138-102">ICorProfilerCallback::JITFunctionPitched — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1138-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="f1138-103">Powiadamia program profilujący, że funkcja, która została just-in-time (JIT) — skompilowany został usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="f1138-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1138-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1138-104">Syntax</span></span>  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1138-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1138-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f1138-106">[in] Identyfikator funkcji, która została usunięta.</span><span class="sxs-lookup"><span data-stu-id="f1138-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1138-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1138-107">Remarks</span></span>  
 <span data-ttu-id="f1138-108">Jeśli usunięto funkcja jest wywoływana, program profilujący otrzyma nowe zdarzenia kompilacji JIT, gdy funkcja jest ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="f1138-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="f1138-109">Obecnie kompilator JIT języka wspólnego środowiska uruchomieniowego (języka wspólnego CLR) nie powoduje usunięcia funkcji z pamięci, dzięki czemu to wywołanie zwrotne nie jest obecnie używana i nie będą odbierane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="f1138-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="f1138-110">Wartość `functionId` jest nieprawidłowa, dopóki funkcja jest ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="f1138-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="f1138-111">Gdy funkcja jest ponownie kompilowany, taka sama `functionId` zostanie użyta wartość.</span><span class="sxs-lookup"><span data-stu-id="f1138-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1138-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1138-112">Requirements</span></span>  
 <span data-ttu-id="f1138-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1138-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1138-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f1138-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1138-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1138-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1138-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1138-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1138-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1138-117">See also</span></span>
- [<span data-ttu-id="f1138-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f1138-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
