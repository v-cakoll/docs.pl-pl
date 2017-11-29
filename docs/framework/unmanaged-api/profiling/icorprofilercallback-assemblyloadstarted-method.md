---
title: "ICorProfilerCallback::AssemblyLoadStarted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 654cc5fb445184bd07d145701898239bee3e9c8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="143f1-102">ICorProfilerCallback::AssemblyLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="143f1-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="143f1-103">Powiadamia profilera, że zestaw jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="143f1-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="143f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="143f1-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="143f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="143f1-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="143f1-106">[in] Określa zestaw, który jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="143f1-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="143f1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="143f1-107">Remarks</span></span>  
 <span data-ttu-id="143f1-108">Wartość `assemblyId` jest nieprawidłowa dla żądania informacji do [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="143f1-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="143f1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="143f1-109">Requirements</span></span>  
 <span data-ttu-id="143f1-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="143f1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="143f1-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="143f1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="143f1-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="143f1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="143f1-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="143f1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="143f1-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="143f1-114">See Also</span></span>  
 [<span data-ttu-id="143f1-115">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="143f1-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
