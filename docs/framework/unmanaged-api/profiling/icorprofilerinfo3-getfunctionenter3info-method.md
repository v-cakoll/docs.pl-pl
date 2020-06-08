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
ms.openlocfilehash: 876ae07a432bfa36a7d9f43ae6c32ec03d7d3289
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496597"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="e5fd1-102">ICorProfilerInfo3::GetFunctionEnter3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5fd1-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="e5fd1-103">Dostarcza ramkę stosu i informacje o argumentach funkcji raportowanej do profilera przez funkcję [FunctionEnter3WithInfo](functionenter3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="e5fd1-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="e5fd1-104">Tę metodę można wywołać tylko w trakcie `FunctionEnter3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e5fd1-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5fd1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5fd1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5fd1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5fd1-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e5fd1-107">podczas `FunctionID`Funkcja, która jest wprowadzana.</span><span class="sxs-lookup"><span data-stu-id="e5fd1-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="e5fd1-108">podczas Nieprzezroczyste dojście, które reprezentuje informacje o danej klatce stosu.</span><span class="sxs-lookup"><span data-stu-id="e5fd1-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="e5fd1-109">Profiler powinien zapewnić taki sam `eltInfo` , który został podany przez funkcję [FunctionEnter3WithInfo](functionenter3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="e5fd1-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="e5fd1-110">określoną Nieprzezroczyste dojście reprezentujące ogólne informacje dotyczące danej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e5fd1-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="e5fd1-111">To dojście jest prawidłowe tylko `FunctionEnter3WithInfo` w przypadku wywołania zwrotnego, w którym Profiler nazywa `GetFunctionEnter3Info` metodę.</span><span class="sxs-lookup"><span data-stu-id="e5fd1-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="e5fd1-112">[in. out] Wskaźnik do łącznego rozmiaru (w bajtach) struktury [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) (oraz wszelkich dodatkowych struktur [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) dla zakresów argumentów wskazywanych przez `pArgumentInfo` ).</span><span class="sxs-lookup"><span data-stu-id="e5fd1-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="e5fd1-113">Jeśli określony rozmiar jest za mały, ERROR_INSUFFICIENT_BUFFER jest zwracany, a oczekiwany rozmiar jest przechowywany w `pcbArgumentInfo` .</span><span class="sxs-lookup"><span data-stu-id="e5fd1-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="e5fd1-114">Aby wywoływać `GetFunctionEnter3Info` tylko w celu pobrania oczekiwanej wartości parametru `*pcbArgumentInfo` , Set `*pcbArgumentInfo` = 0 i `pArgumentInfo` = null.</span><span class="sxs-lookup"><span data-stu-id="e5fd1-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="e5fd1-115">określoną Wskaźnik do struktury [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) , który opisuje lokalizacje argumentów funkcji w pamięci, w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="e5fd1-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5fd1-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5fd1-116">Remarks</span></span>  
 <span data-ttu-id="e5fd1-117">Profiler musi przydzielić wystarczającą ilość miejsca dla `COR_PRF_FUNCTION_ARGUMENT_INFO` struktury funkcji, która jest sprawdzana, i musi wskazywać rozmiar w `pcbArgumentInfo` parametrze.</span><span class="sxs-lookup"><span data-stu-id="e5fd1-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5fd1-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5fd1-118">Requirements</span></span>  
 <span data-ttu-id="e5fd1-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5fd1-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5fd1-120">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e5fd1-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5fd1-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e5fd1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5fd1-122">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5fd1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5fd1-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5fd1-123">See also</span></span>

- [<span data-ttu-id="e5fd1-124">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e5fd1-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="e5fd1-125">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e5fd1-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="e5fd1-126">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e5fd1-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="e5fd1-127">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5fd1-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="e5fd1-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="e5fd1-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e5fd1-129">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="e5fd1-129">Profiling</span></span>](index.md)
