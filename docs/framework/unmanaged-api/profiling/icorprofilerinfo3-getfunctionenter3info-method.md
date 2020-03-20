---
title: ICorProfilerInfo3::GetFunctionEnter3Info — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
ms.openlocfilehash: 50d16b8036144d6ede349149fa4ae37344064d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177023"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="3eb31-102">ICorProfilerInfo3::GetFunctionEnter3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="3eb31-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="3eb31-103">Zawiera ramki stosu i argument informacji funkcji, która jest zgłaszana do profilera przez [FunctionEnter3WithInfo](functionenter3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="3eb31-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="3eb31-104">Tę metodę można wywołać `FunctionEnter3WithInfo` tylko podczas wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3eb31-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb31-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3eb31-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eb31-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3eb31-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3eb31-107">[w] Funkcja, `FunctionID` która jest wprowadzana.</span><span class="sxs-lookup"><span data-stu-id="3eb31-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="3eb31-108">[w] Nieprzezroczysty uchwyt, który reprezentuje informacje o danej ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="3eb31-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="3eb31-109">Profiler powinien zapewnić `eltInfo` taki sam, że został podany przez [FunctionEnter3WithInfo](functionenter3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="3eb31-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="3eb31-110">[na zewnątrz] Nieprzezroczysty dojście reprezentujące ogólne informacje o danej ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="3eb31-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="3eb31-111">Ten dojście jest `FunctionEnter3WithInfo` prawidłowy tylko podczas wywołania zwrotnego, w którym profiler o nazwie `GetFunctionEnter3Info` metody.</span><span class="sxs-lookup"><span data-stu-id="3eb31-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="3eb31-112">[w, na zewnątrz] Wskaźnik do całkowitego rozmiaru , w bajtach, [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) struktury (plus wszelkie dodatkowe [struktury COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) dla zakresów argumentów wskazanych przez `pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="3eb31-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="3eb31-113">Jeśli określony rozmiar nie wystarczy, ERROR_INSUFFICIENT_BUFFER jest zwracany, a `pcbArgumentInfo`oczekiwany rozmiar jest przechowywany w pliku .</span><span class="sxs-lookup"><span data-stu-id="3eb31-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="3eb31-114">Aby `GetFunctionEnter3Info` wywołać tylko pobrać oczekiwaną wartość dla `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 i `pArgumentInfo`=NULL.</span><span class="sxs-lookup"><span data-stu-id="3eb31-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="3eb31-115">[na zewnątrz] Wskaźnik do [struktury COR_PRF_FUNCTION_ARGUMENT_INFO,](cor-prf-function-argument-info-structure.md) który opisuje lokalizacje argumentów funkcji w pamięci, w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="3eb31-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eb31-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3eb31-116">Remarks</span></span>  
 <span data-ttu-id="3eb31-117">Profiler musi przydzielić wystarczającą `COR_PRF_FUNCTION_ARGUMENT_INFO` ilość miejsca dla struktury funkcji, która jest `pcbArgumentInfo` kontrolowana i musi wskazywać rozmiar w parametrze.</span><span class="sxs-lookup"><span data-stu-id="3eb31-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eb31-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3eb31-118">Requirements</span></span>  
 <span data-ttu-id="3eb31-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eb31-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eb31-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3eb31-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3eb31-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3eb31-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3eb31-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eb31-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb31-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3eb31-123">See also</span></span>

- [<span data-ttu-id="3eb31-124">Functionenter3withinfo</span><span class="sxs-lookup"><span data-stu-id="3eb31-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="3eb31-125">Functionleave3withinfo</span><span class="sxs-lookup"><span data-stu-id="3eb31-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="3eb31-126">FunkcjaTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="3eb31-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="3eb31-127">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="3eb31-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="3eb31-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3eb31-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3eb31-129">Profilowania</span><span class="sxs-lookup"><span data-stu-id="3eb31-129">Profiling</span></span>](index.md)
