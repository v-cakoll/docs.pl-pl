---
title: ICorProfilerCallback4::GetReJITParameters — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca176be93b92e44228d9b4063e87a62263e83e04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184876"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="67edf-102">ICorProfilerCallback4::GetReJITParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="67edf-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="67edf-103">Umożliwia programowi profilującemu kodu Ustaw flagi generowania kodu alternatywnej dla nowej treści metody ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="67edf-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67edf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67edf-104">Syntax</span></span>  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67edf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="67edf-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="67edf-106">[in] Moduł, który zawiera metodę, która CLR musi mieć parametry ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="67edf-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="67edf-107">[in] `MethodDef` Metody, dla którego CLR wymaga parametrów ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="67edf-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="67edf-108">[in] Wskaźnik do [icorprofilerfunctioncontrol —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interfejsu używanego przez program profilujący do podawania kompilację JIT dla metody są ponownie kompilowane.</span><span class="sxs-lookup"><span data-stu-id="67edf-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67edf-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67edf-109">Remarks</span></span>  
 <span data-ttu-id="67edf-110">Problemy dotyczące środowiska CLR `GetReJITParameters` wywołania zwrotnego, aby program profilujący można określić parametry ponownej kompilacji danej metody.</span><span class="sxs-lookup"><span data-stu-id="67edf-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="67edf-111">`GetReJITParameters` Wywołania zwrotnego jest wydawane tylko raz dla każdej funkcji; parametry dostarczane przez program profilujący Zastosuj do wszystkich wystąpień tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="67edf-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67edf-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67edf-112">Requirements</span></span>  
 <span data-ttu-id="67edf-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67edf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67edf-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67edf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67edf-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67edf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67edf-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67edf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67edf-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67edf-117">See also</span></span>

- [<span data-ttu-id="67edf-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="67edf-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="67edf-119">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="67edf-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="67edf-120">JITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="67edf-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="67edf-121">ReJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="67edf-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
