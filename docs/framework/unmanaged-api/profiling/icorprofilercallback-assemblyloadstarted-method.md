---
title: ICorProfilerCallback::AssemblyLoadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
ms.openlocfilehash: 34744132442440ef160841db5a50bf75355f2410
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445159"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="71036-102">ICorProfilerCallback::AssemblyLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="71036-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="71036-103">Notifies the profiler that an assembly is being loaded.</span><span class="sxs-lookup"><span data-stu-id="71036-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71036-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71036-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71036-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71036-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="71036-106">[in] Identifies the assembly that is being loaded.</span><span class="sxs-lookup"><span data-stu-id="71036-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71036-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71036-107">Remarks</span></span>  
 <span data-ttu-id="71036-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span><span class="sxs-lookup"><span data-stu-id="71036-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71036-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71036-109">Requirements</span></span>  
 <span data-ttu-id="71036-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71036-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71036-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71036-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71036-112">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71036-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71036-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71036-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71036-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71036-114">See also</span></span>

- [<span data-ttu-id="71036-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="71036-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
