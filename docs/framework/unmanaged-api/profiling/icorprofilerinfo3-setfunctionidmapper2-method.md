---
title: ICorProfilerInfo3::SetFunctionIDMapper2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 107f596801832809e64088c85540c441e66189cf
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868476"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="bae2b-102">ICorProfilerInfo3::SetFunctionIDMapper2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="bae2b-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="bae2b-103">Określa funkcję zaimplementowaną przez profiler, która zostanie wywołana w celu mapowania wartości `FunctionID` na wartości alternatywne, które są przesyłane do punktów zaczepienia wejścia/wyjścia profilera.</span><span class="sxs-lookup"><span data-stu-id="bae2b-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="bae2b-104">Ta metoda rozszerza metodę [ICorProfilerInfo:: SetFunctionIDMapper —](icorprofilerinfo-setfunctionidmapper-method.md) z dodatkowym parametrem danych, którego mogą używać pliki do rozróżniania między środowiskami uruchomieniowymi.</span><span class="sxs-lookup"><span data-stu-id="bae2b-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bae2b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bae2b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bae2b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bae2b-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="bae2b-107">podczas Wskaźnik do implementacji [FunctionIDMapper2 —](functionidmapper2-function.md) , który zostanie wywołany w celu mapowania wartości `FunctionID` na ich wartości alternatywne.</span><span class="sxs-lookup"><span data-stu-id="bae2b-107">[in] A pointer to a [FunctionIDMapper2](functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="bae2b-108">podczas Wskaźnik, który jest przesyłany do każdego wywołania funkcji [FunctionIDMapper2 —](functionidmapper2-function.md) wykonanego przez bieżące środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="bae2b-108">[in] A pointer that is passed to every [FunctionIDMapper2](functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="bae2b-109">Profiler może używać tych informacji do rozróżnienia między środowiskami uruchomieniowymi.</span><span class="sxs-lookup"><span data-stu-id="bae2b-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bae2b-110">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="bae2b-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bae2b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bae2b-111">Remarks</span></span>  
 <span data-ttu-id="bae2b-112">Alternatywy dla wartości FunctionID zostaną przesłane do punktów zaczepienia wejścia/wyjścia profilera ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md);, [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)i [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)), które są określone przez metodę [SetEnterLeaveFunctionHooks3 —](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) lub [SetEnterLeaveFunctionHooks3WithInfo —](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bae2b-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md); or [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="bae2b-113">Metodę `FunctionIDMapper2` można ustawić tylko raz; zalecamy ustawienie go w [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="bae2b-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bae2b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bae2b-114">Requirements</span></span>  
 <span data-ttu-id="bae2b-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bae2b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bae2b-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bae2b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bae2b-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bae2b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bae2b-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bae2b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bae2b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bae2b-119">See also</span></span>

- [<span data-ttu-id="bae2b-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="bae2b-120">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="bae2b-121">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="bae2b-121">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="bae2b-122">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="bae2b-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="bae2b-123">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="bae2b-123">Profiling</span></span>](index.md)
