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
ms.openlocfilehash: 2715a5b6b03a5ad33a6f18fb736fce3911bfbef0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500029"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="90c81-102">ICorProfilerCallback::JITFunctionPitched — Metoda</span><span class="sxs-lookup"><span data-stu-id="90c81-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="90c81-103">Powiadamia program profilujący, że funkcja, która została skompilowana just-in-Time (JIT), została usunięta z pamięci.</span><span class="sxs-lookup"><span data-stu-id="90c81-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="90c81-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90c81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90c81-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="90c81-106">podczas Identyfikator funkcji, która została usunięta.</span><span class="sxs-lookup"><span data-stu-id="90c81-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90c81-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90c81-107">Remarks</span></span>  
 <span data-ttu-id="90c81-108">Jeśli usunięta funkcja zostanie wywołana, profiler otrzyma nowe zdarzenia JIT-kompilacja po ponownym skompilowaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="90c81-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="90c81-109">Obecnie kompilator JIT środowiska uruchomieniowego języka wspólnego (CLR) nie usuwa funkcji z pamięci, więc to wywołanie zwrotne nie jest obecnie używane i nie zostanie odebrane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="90c81-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="90c81-110">Wartość `functionId` jest nieprawidłowa, dopóki funkcja nie zostanie ponownie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="90c81-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="90c81-111">Po ponownym skompilowaniu funkcji `functionId` zostanie użyta ta sama wartość.</span><span class="sxs-lookup"><span data-stu-id="90c81-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90c81-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90c81-112">Requirements</span></span>  
 <span data-ttu-id="90c81-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90c81-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90c81-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="90c81-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90c81-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="90c81-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90c81-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90c81-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c81-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90c81-117">See also</span></span>

- [<span data-ttu-id="90c81-118">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="90c81-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
