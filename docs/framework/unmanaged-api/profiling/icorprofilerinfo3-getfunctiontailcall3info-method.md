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
ms.openlocfilehash: 5346792cb2a1309268cb4ba48625aa559777fbaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176997"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="9b862-102">ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="9b862-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="9b862-103">Udostępnia ramkę stosu funkcji, która jest zgłaszana do profilera przez [functiontailcall3WithInfo](functiontailcall3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="9b862-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="9b862-104">Tę metodę można wywołać `FunctionTailcall3WithInfo` tylko podczas wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9b862-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b862-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b862-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b862-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b862-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9b862-107">[w] Funkcja, `FunctionID` która powraca.</span><span class="sxs-lookup"><span data-stu-id="9b862-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="9b862-108">[w] Nieprzezroczysty uchwyt, który reprezentuje informacje o danej ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="9b862-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="9b862-109">Profiler powinien zapewnić `eltInfo` taki sam, który został `FunctionTailcall3WithInfo` podany do profilera przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="9b862-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="9b862-110">[na zewnątrz] Nieprzezroczysty dojście reprezentujące ogólne informacje o danej ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="9b862-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="9b862-111">Ten dojście jest `FunctionTailcall3WithInfo` prawidłowy tylko podczas wywołania zwrotnego, w którym profiler o nazwie `GetFunctionTailcall3Info` metody.</span><span class="sxs-lookup"><span data-stu-id="9b862-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b862-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9b862-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b862-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b862-113">Requirements</span></span>  
 <span data-ttu-id="9b862-114">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b862-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b862-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b862-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b862-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b862-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b862-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b862-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b862-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b862-118">See also</span></span>

- [<span data-ttu-id="9b862-119">Functionenter3withinfo</span><span class="sxs-lookup"><span data-stu-id="9b862-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="9b862-120">Functionleave3withinfo</span><span class="sxs-lookup"><span data-stu-id="9b862-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="9b862-121">FunkcjaTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9b862-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="9b862-122">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="9b862-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="9b862-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="9b862-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9b862-124">Profilowania</span><span class="sxs-lookup"><span data-stu-id="9b862-124">Profiling</span></span>](index.md)
