---
title: ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: e4d0d9ed07c707e51e5833483b71079f2c330505
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496532"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="d39b5-102">ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="d39b5-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="d39b5-103">Udostępnia ramkę stosu funkcji, która jest raportowana do profilera przez funkcję [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="d39b5-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="d39b5-104">Tę metodę można wywołać tylko w trakcie `FunctionTailcall3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d39b5-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d39b5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d39b5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d39b5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d39b5-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d39b5-107">podczas `FunctionID`Funkcja, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="d39b5-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="d39b5-108">podczas Nieprzezroczyste dojście, które reprezentuje informacje o danej klatce stosu.</span><span class="sxs-lookup"><span data-stu-id="d39b5-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="d39b5-109">Profiler powinien zapewnić taki sam `eltInfo` , który został przekazany do profilera przez `FunctionTailcall3WithInfo` funkcję.</span><span class="sxs-lookup"><span data-stu-id="d39b5-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="d39b5-110">określoną Nieprzezroczyste dojście reprezentujące ogólne informacje dotyczące danej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="d39b5-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="d39b5-111">To dojście jest prawidłowe tylko `FunctionTailcall3WithInfo` w przypadku wywołania zwrotnego, w którym Profiler nazywa `GetFunctionTailcall3Info` metodę.</span><span class="sxs-lookup"><span data-stu-id="d39b5-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d39b5-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d39b5-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d39b5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d39b5-113">Requirements</span></span>  
 <span data-ttu-id="d39b5-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d39b5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d39b5-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d39b5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d39b5-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d39b5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d39b5-117">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d39b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39b5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d39b5-118">See also</span></span>

- [<span data-ttu-id="d39b5-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d39b5-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="d39b5-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d39b5-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="d39b5-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d39b5-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="d39b5-122">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="d39b5-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d39b5-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="d39b5-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d39b5-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="d39b5-124">Profiling</span></span>](index.md)
