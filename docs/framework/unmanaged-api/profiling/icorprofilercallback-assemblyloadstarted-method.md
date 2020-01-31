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
ms.openlocfilehash: b83be5e79c533e7e5a2468a12a0793d300700428
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866643"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="dea2d-102">ICorProfilerCallback::AssemblyLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="dea2d-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="dea2d-103">Powiadamia program profilujący, że zestaw jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="dea2d-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea2d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dea2d-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dea2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dea2d-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="dea2d-106">\[in] określa ładowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="dea2d-106">\[in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="dea2d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dea2d-107">Remarks</span></span>  
 <span data-ttu-id="dea2d-108">Wartość `assemblyId` nie jest prawidłowa dla żądania informacji, dopóki nie zostanie wywołana metoda [ICorProfilerCallback:: AssemblyLoadFinished —](icorprofilercallback-assemblyloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dea2d-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dea2d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dea2d-109">Requirements</span></span>  
 <span data-ttu-id="dea2d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dea2d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dea2d-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dea2d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dea2d-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dea2d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dea2d-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dea2d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea2d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dea2d-114">See also</span></span>

- [<span data-ttu-id="dea2d-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="dea2d-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
