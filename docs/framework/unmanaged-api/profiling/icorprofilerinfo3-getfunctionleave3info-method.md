---
title: ICorProfilerInfo3::GetFunctionLeave3Info — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: bab52d9179d7454cab4a47e1a2bfe80a49b00c2a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502837"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="c2c8f-102">ICorProfilerInfo3::GetFunctionLeave3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2c8f-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="c2c8f-103">Udostępnia ramkę stosu i zwracaną wartość funkcji raportowanej do profilera przez funkcję [funkcji FunctionLeave3WithInfo](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="c2c8f-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="c2c8f-104">Tę metodę można wywołać tylko w trakcie `FunctionLeave3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c8f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2c8f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2c8f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2c8f-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c2c8f-107">podczas `FunctionID`Funkcja, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="c2c8f-108">podczas Nieprzezroczyste dojście, które reprezentuje informacje o danej klatce stosu.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="c2c8f-109">Profiler powinien zapewnić taki sam `eltInfo` , który został przekazany do profilera przez funkcję [FunctionLeave3WithInfo](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="c2c8f-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="c2c8f-110">określoną Nieprzezroczyste dojście reprezentujące ogólne informacje dotyczące danej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="c2c8f-111">To dojście jest prawidłowe tylko `FunctionLeave3WithInfo` w przypadku wywołania zwrotnego, w którym Profiler nazywa `GetFunctionLeave3Info` metodę.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="c2c8f-112">określoną Wskaźnik do struktury [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , która zawiera wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="c2c8f-113">Aby można było uzyskać dostęp do informacji o wartości zwracanej, `COR_PRF_ENABLE_FUNCTION_RETVAL` należy ustawić flagę.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="c2c8f-114">Profiler może użyć [metody ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2c8f-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2c8f-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c8f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2c8f-116">Requirements</span></span>  
 <span data-ttu-id="c2c8f-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2c8f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2c8f-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c2c8f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2c8f-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2c8f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2c8f-120">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2c8f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c8f-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2c8f-121">See also</span></span>

- [<span data-ttu-id="c2c8f-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c2c8f-122">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="c2c8f-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c2c8f-123">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="c2c8f-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c2c8f-124">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="c2c8f-125">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2c8f-125">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c2c8f-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c2c8f-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c2c8f-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="c2c8f-127">Profiling</span></span>](index.md)
