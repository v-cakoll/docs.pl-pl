---
title: "ICorProfilerInfo3::SetFunctionIDMapper2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: adc23b8774737f9884ded7ec1e3a891ed8b63b2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="4c036-102">ICorProfilerInfo3::SetFunctionIDMapper2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c036-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="4c036-103">Określa zaimplementowana profilera funkcję, która będzie wywoływana w celu mapowania `FunctionID` wartości alternatywne wartości, które są przekazywane do profilera działać punkty zaczepienia wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="4c036-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="4c036-104">Ta metoda jest rozszerzeniem [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metody z parametrem dodatkowych danych, którego może używać profilowania, aby usunąć Niejednoznaczność między środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="4c036-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c036-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c036-105">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c036-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c036-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="4c036-107">[in] Wskaźnik do [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementację, która będzie wywoływana w celu mapowania `FunctionID` wartości alternatywne wartości.</span><span class="sxs-lookup"><span data-stu-id="4c036-107">[in] A pointer to a [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="4c036-108">[in] Wskaźnik, który jest przekazywany do każdego [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) wywołania funkcji wprowadzone przez bieżącego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4c036-108">[in] A pointer that is passed to every [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="4c036-109">Profiler można użyć tych informacji do odróżniania między środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="4c036-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c036-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4c036-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c036-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c036-111">Remarks</span></span>  
 <span data-ttu-id="4c036-112">Alternatywy dla wartości FunctionID zostaną przekazane do punkty zaczepienia wejścia/wyjścia funkcji profilera ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) ; lub [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) określono przez [ SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) lub [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4c036-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md); or [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="4c036-113">`FunctionIDMapper2` Metody można ustawić tylko raz; zalecane ustawienie [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4c036-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c036-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c036-114">Requirements</span></span>  
 <span data-ttu-id="4c036-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c036-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c036-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c036-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c036-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c036-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c036-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c036-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c036-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c036-119">See Also</span></span>  
 [<span data-ttu-id="4c036-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="4c036-120">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="4c036-121">ICorProfilerInfo3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="4c036-121">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="4c036-122">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="4c036-122">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="4c036-123">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="4c036-123">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
