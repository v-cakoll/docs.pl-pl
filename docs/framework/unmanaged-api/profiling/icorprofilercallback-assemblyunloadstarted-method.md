---
title: ICorProfilerCallback::AssemblyUnloadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10475831be02bd4a958da84b7b75409cf3ad4097
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="e21f4-102">ICorProfilerCallback::AssemblyUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="e21f4-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="e21f4-103">Powiadamia profiler jest zwalniany zestawu.</span><span class="sxs-lookup"><span data-stu-id="e21f4-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e21f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e21f4-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e21f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e21f4-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="e21f4-106">[in] Określa zestaw, który jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="e21f4-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e21f4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e21f4-107">Remarks</span></span>  
 <span data-ttu-id="e21f4-108">Wartość `assemblyId` jest nieprawidłowa dla żądania informacji po `AssemblyUnloadStarted` metoda zwraca — jest to profilera ostatnia możliwość uzyskania informacji na temat tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e21f4-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e21f4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e21f4-109">Requirements</span></span>  
 <span data-ttu-id="e21f4-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e21f4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e21f4-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e21f4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e21f4-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e21f4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e21f4-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e21f4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e21f4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e21f4-114">See Also</span></span>  
 [<span data-ttu-id="e21f4-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e21f4-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="e21f4-116">AssemblyUnloadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="e21f4-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
