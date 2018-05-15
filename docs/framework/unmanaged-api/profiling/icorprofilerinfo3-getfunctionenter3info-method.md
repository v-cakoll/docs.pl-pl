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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5d06988330b9ec83463165661ea5425d8563c60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="16861-102">ICorProfilerInfo3::GetFunctionEnter3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="16861-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="16861-103">Zawiera informacje ramki i argument stosu funkcji, która jest raportowany przez profiler [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="16861-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="16861-104">Tę metodę można wywołać tylko podczas `FunctionEnter3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="16861-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16861-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="16861-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16861-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="16861-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="16861-107">[in] `FunctionID` Funkcji, która jest wprowadzane.</span><span class="sxs-lookup"><span data-stu-id="16861-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="16861-108">[in] Nieprzezroczystego uchwyt reprezentujący informacji na temat ramka stosu danego.</span><span class="sxs-lookup"><span data-stu-id="16861-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="16861-109">Profiler powinien zawierać takie same `eltInfo` który został udzielony przez [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="16861-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="16861-110">[out] Nieprzezroczystego uchwyt reprezentujący informacje ogólne o ramka stosu danego.</span><span class="sxs-lookup"><span data-stu-id="16861-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="16861-111">Ta dojścia jest prawidłowy tylko w trakcie `FunctionEnter3WithInfo` wywołania zwrotnego o nazwie profilera `GetFunctionEnter3Info` metody.</span><span class="sxs-lookup"><span data-stu-id="16861-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="16861-112">[w, out] Wskaźnik całkowity rozmiar w bajtach z [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktury (oraz wszelkie dodatkowe [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktur zakresów argument wskazywana przez `pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="16861-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="16861-113">Jeśli określony rozmiar jest niewystarczający, zwracany jest ERROR_INSUFFICIENT_BUFFER i oczekiwanym rozmiarem są przechowywane w `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="16861-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="16861-114">Aby wywołać `GetFunctionEnter3Info` tylko w celu oczekiwanej wartości dla pobrania `*pcbArgumentInfo`ustaw `*pcbArgumentInfo`= 0 i `pArgumentInfo`= NULL.</span><span class="sxs-lookup"><span data-stu-id="16861-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="16861-115">[out] Wskaźnik do [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktury, która opisuje lokalizacje argumentów funkcji w pamięci w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="16861-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16861-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16861-116">Remarks</span></span>  
 <span data-ttu-id="16861-117">Profiler musi przydzielić wystarczającą ilość miejsca na `COR_PRF_FUNCTION_ARGUMENT_INFO` struktury funkcji, która jest kontrolowanym i musi wskazywać rozmiar w `pcbArgumentInfo` parametru.</span><span class="sxs-lookup"><span data-stu-id="16861-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16861-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16861-118">Requirements</span></span>  
 <span data-ttu-id="16861-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16861-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16861-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="16861-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="16861-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16861-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16861-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16861-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16861-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16861-123">See Also</span></span>  
 [<span data-ttu-id="16861-124">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="16861-124">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="16861-125">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="16861-125">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="16861-126">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="16861-126">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="16861-127">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="16861-127">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="16861-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="16861-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="16861-129">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="16861-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
