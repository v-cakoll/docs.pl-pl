---
title: "ICorProfilerCallback4::GetReJITParameters — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.GetReJITParameters
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: acecbe10fd79394b27e6264c337d584d9fb259b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="d3b49-102">ICorProfilerCallback4::GetReJITParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3b49-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="d3b49-103">Umożliwia profilującego można ustawić flagi generowania inny kod dla nowych treści metody ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d3b49-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3b49-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3b49-104">Syntax</span></span>  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3b49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3b49-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="d3b49-106">[in] Moduł, który zawiera metodę, dla którego CLR wymaga ustawienia parametrów ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="d3b49-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="d3b49-107">[in] `MethodDef` Metody, dla którego CLR wymaga ustawienia parametrów ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="d3b49-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="d3b49-108">[in] Wskaźnik do [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interfejs, który profilera mogą wykorzystywać do dostarczania informacji ponownej kompilacji JIT dla metody jest ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="d3b49-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3b49-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3b49-109">Remarks</span></span>  
 <span data-ttu-id="d3b49-110">Problemy CLR `GetReJITParameters` wywołania zwrotnego, aby profilera można określić parametry ponowną kompilację danej metody.</span><span class="sxs-lookup"><span data-stu-id="d3b49-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="d3b49-111">`GetReJITParameters` Wywołania zwrotnego jest wystawiony tylko raz dla każdej funkcji; parametry dostarczane przez profiler dotyczą wszystkich wystąpień tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d3b49-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3b49-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3b49-112">Requirements</span></span>  
 <span data-ttu-id="d3b49-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3b49-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3b49-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3b49-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3b49-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3b49-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3b49-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3b49-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b49-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3b49-117">See Also</span></span>  
 [<span data-ttu-id="d3b49-118">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="d3b49-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d3b49-119">ICorProfilerCallback4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d3b49-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="d3b49-120">JITCompilationStarted — metoda</span><span class="sxs-lookup"><span data-stu-id="d3b49-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [<span data-ttu-id="d3b49-121">ReJITCompilationStarted — metoda</span><span class="sxs-lookup"><span data-stu-id="d3b49-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
