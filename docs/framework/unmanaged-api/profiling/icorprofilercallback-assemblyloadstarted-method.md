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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af40d8b603d3bd13abbc5a1c06464583bfa7842d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450222"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="67d4e-102">ICorProfilerCallback::AssemblyLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="67d4e-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="67d4e-103">Powiadamia profilera, że zestaw jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="67d4e-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67d4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67d4e-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67d4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="67d4e-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="67d4e-106">[in] Określa zestaw, który jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="67d4e-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67d4e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67d4e-107">Remarks</span></span>  
 <span data-ttu-id="67d4e-108">Wartość `assemblyId` jest nieprawidłowa dla żądania informacji do [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="67d4e-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67d4e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67d4e-109">Requirements</span></span>  
 <span data-ttu-id="67d4e-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67d4e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67d4e-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67d4e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67d4e-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67d4e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67d4e-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67d4e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67d4e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67d4e-114">See Also</span></span>  
 [<span data-ttu-id="67d4e-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="67d4e-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
