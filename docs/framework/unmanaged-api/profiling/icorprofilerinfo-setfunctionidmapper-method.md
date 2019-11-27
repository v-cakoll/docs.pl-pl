---
title: ICorProfilerInfo::SetFunctionIDMapper — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: 4ba3c378b93e3ae1ef288c0edabfacfcfd7070d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438672"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="27fbe-102">ICorProfilerInfo::SetFunctionIDMapper — Metoda</span><span class="sxs-lookup"><span data-stu-id="27fbe-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="27fbe-103">Określa funkcję zaimplementowaną przez profiler, która zostanie wywołana w celu mapowania wartości `FunctionID` na wartości alternatywne, które są przesyłane do punktów zaczepienia wejścia/wyjścia profilera.</span><span class="sxs-lookup"><span data-stu-id="27fbe-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27fbe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27fbe-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27fbe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27fbe-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="27fbe-106">podczas Wskaźnik do implementacji [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) , który zostanie wywołany w celu mapowania wartości `FunctionID` na ich wartości alternatywne.</span><span class="sxs-lookup"><span data-stu-id="27fbe-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27fbe-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27fbe-107">Remarks</span></span>  
 <span data-ttu-id="27fbe-108">Alternatywy dla wartości `FunctionID` zostaną przesłane do punktów zaczepienia wejścia/wyjścia funkcji profilera ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)), które są określone przez metodę [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="27fbe-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="27fbe-109">`FunctionIDMapper` można ustawić tylko raz i zaleca się jej ustawienie w [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="27fbe-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27fbe-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27fbe-110">Requirements</span></span>  
 <span data-ttu-id="27fbe-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27fbe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27fbe-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="27fbe-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27fbe-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="27fbe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27fbe-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27fbe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27fbe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27fbe-115">See also</span></span>

- [<span data-ttu-id="27fbe-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="27fbe-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
