---
title: "ICorProfilerCallback::JITFunctionPitched — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITFunctionPitched
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5b14bc5735c83897e818ca2038455e0c6510e27
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="c7d11-102">ICorProfilerCallback::JITFunctionPitched — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7d11-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="c7d11-103">Powiadamia profilera który funkcja, która została just-in-time (JIT)-skompilowany został usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="c7d11-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7d11-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7d11-104">Syntax</span></span>  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7d11-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7d11-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c7d11-106">[in] Identyfikator funkcji, która została usunięta.</span><span class="sxs-lookup"><span data-stu-id="c7d11-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7d11-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7d11-107">Remarks</span></span>  
 <span data-ttu-id="c7d11-108">Jeśli usunięto funkcja jest wywoływana, profilera otrzymają nowe zdarzenia kompilacji JIT, gdy funkcja jest ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="c7d11-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="c7d11-109">Obecnie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) przy użyciu kompilatora JIT nie powoduje usunięcia funkcji z pamięci, dzięki czemu to wywołanie zwrotne nie jest obecnie używana i nie zostanie odebrana przez profiler.</span><span class="sxs-lookup"><span data-stu-id="c7d11-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="c7d11-110">Wartość `functionId` jest nieprawidłowa, dopóki funkcja jest ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="c7d11-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="c7d11-111">Gdy funkcja jest ponownie kompilowana, takie same `functionId` zostanie użyta wartość.</span><span class="sxs-lookup"><span data-stu-id="c7d11-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d11-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7d11-112">Requirements</span></span>  
 <span data-ttu-id="c7d11-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7d11-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7d11-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7d11-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7d11-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7d11-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7d11-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7d11-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d11-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7d11-117">See Also</span></span>  
 [<span data-ttu-id="c7d11-118">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="c7d11-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
