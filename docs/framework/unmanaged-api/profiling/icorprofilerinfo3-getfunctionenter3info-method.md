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
ms.openlocfilehash: 8df3700c6002e7a181d4882c4afd8542c6b6c93a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164830"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="194bf-102">ICorProfilerInfo3::GetFunctionEnter3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="194bf-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="194bf-103">Zawiera informacje stosu ramki i argument funkcji, która jest zgłaszany do profilera za [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="194bf-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="194bf-104">Ta metoda może być wywoływana tylko podczas `FunctionEnter3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="194bf-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="194bf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="194bf-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="194bf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="194bf-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="194bf-107">[in] `FunctionID` Funkcji, która jest wprowadzanych.</span><span class="sxs-lookup"><span data-stu-id="194bf-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="194bf-108">[in] Dojście nieprzezroczyste reprezentujący informacji na temat ramkę stosu w danym.</span><span class="sxs-lookup"><span data-stu-id="194bf-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="194bf-109">Program profilujący powinien udostępniać takie same `eltInfo` , zostało przekazane przez [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="194bf-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="194bf-110">[out] Dojście nieprzezroczyste reprezentujący typów ogólnych informacji na temat ramkę stosu w danym.</span><span class="sxs-lookup"><span data-stu-id="194bf-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="194bf-111">Tego dojścia jest prawidłowy tylko podczas `FunctionEnter3WithInfo` wywołania zwrotnego, w którym profiler wywołał metodę `GetFunctionEnter3Info` metody.</span><span class="sxs-lookup"><span data-stu-id="194bf-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="194bf-112">[out w] Wskaźnik do łączny rozmiar w bajtach, z [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktury (oraz wszelkie dodatkowe [cor_prf_function_argument_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktur dla zakresów argument wskazywany przez `pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="194bf-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="194bf-113">Jeśli wybrany rozmiar nie jest wystarczająco dużo, zwracany jest ERROR_INSUFFICIENT_BUFFER i oczekiwany rozmiar jest przechowywany w `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="194bf-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="194bf-114">Aby wywołać `GetFunctionEnter3Info` tylko w celu pobrania z oczekiwaną wartością `*pcbArgumentInfo`ustaw `*pcbArgumentInfo`= 0 i `pArgumentInfo`= NULL.</span><span class="sxs-lookup"><span data-stu-id="194bf-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="194bf-115">[out] Wskaźnik do [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) strukturę, która opisuje lokalizacje argumentów funkcji w pamięci, w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="194bf-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="194bf-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="194bf-116">Remarks</span></span>  
 <span data-ttu-id="194bf-117">Program profilujący musi przydzielić wystarczającej ilości miejsca dla `COR_PRF_FUNCTION_ARGUMENT_INFO` struktury funkcja, która jest poddawana i musi wskazywać wielkość w `pcbArgumentInfo` parametru.</span><span class="sxs-lookup"><span data-stu-id="194bf-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="194bf-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="194bf-118">Requirements</span></span>  
 <span data-ttu-id="194bf-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="194bf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="194bf-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="194bf-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="194bf-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="194bf-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="194bf-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="194bf-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="194bf-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="194bf-123">See also</span></span>

- [<span data-ttu-id="194bf-124">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="194bf-124">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="194bf-125">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="194bf-125">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="194bf-126">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="194bf-126">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="194bf-127">ICorProfilerInfo3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="194bf-127">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="194bf-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="194bf-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="194bf-129">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="194bf-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
