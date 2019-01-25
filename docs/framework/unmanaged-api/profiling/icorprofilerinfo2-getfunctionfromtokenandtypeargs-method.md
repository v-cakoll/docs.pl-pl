---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60a9ba78211cd02300cccc7d150bb08fa68b0604
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556184"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="e9c5d-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9c5d-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="e9c5d-103">Pobiera `FunctionID` funkcji przy użyciu tokenu określonych metadanych, klasą, i `ClassID` wartości wszelkich argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9c5d-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9c5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9c5d-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="e9c5d-106">[in] Identyfikator modułu, w której znajduje się funkcja.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="e9c5d-107">[in] `mdMethodDef` Token metadanych, który odwołuje się do funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="e9c5d-108">[in] Identyfikator klasy funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="e9c5d-109">[in] Liczba parametrów typu dla danej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="e9c5d-110">Ta wartość musi mieć wartość zero dla funkcji nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="e9c5d-111">[in] Tablica `ClassID` wartości, z których każdy jest argumentem funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="e9c5d-112">Wartość `typeArgs` może mieć wartości NULL, jeśli `cTypeArgs` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="e9c5d-113">[out] Wskaźnik do `FunctionID` określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9c5d-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9c5d-114">Remarks</span></span>  
 <span data-ttu-id="e9c5d-115">Wywoływanie `GetFunctionFromTokenAndTypeArgs` metody z `mdMethodRef` metadanych zamiast `mdMethodDef` token metadanych może przynieść nieprzewidywalne rezultaty.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="e9c5d-116">Obiekty wywołujące powinna być rozpoznawana `mdMethodRef` do `mdMethodDef` podczas przekazywania go.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="e9c5d-117">Jeśli funkcja nie jest już załadowany, wywołanie `GetFunctionFromTokenAndTypeArgs` spowoduje, że podczas ładowania wystąpią, który jest niebezpieczne operacji w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="e9c5d-118">Na przykład wywołanie tej metody podczas ładowania modułów i typów może prowadzić do wejścia w nieskończoną pętlę jako środowisko wykonawcze próby rekurencyjnie załadować rzeczy.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="e9c5d-119">Ogólnie rzecz biorąc, użytkowania `GetFunctionFromTokenAndTypeArgs` jest niezalecane.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="e9c5d-120">Zainteresowani profilery zdarzeń związanych z konkretną funkcję, należy przechowywać `ModuleID` i `mdMethodDef` tej funkcji oraz [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) Aby sprawdzić, czy dany `FunctionID` jest w przypadku odpowiednią funkcję.</span><span class="sxs-lookup"><span data-stu-id="e9c5d-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9c5d-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9c5d-121">Requirements</span></span>  
 <span data-ttu-id="e9c5d-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9c5d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9c5d-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9c5d-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9c5d-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9c5d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9c5d-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9c5d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c5d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9c5d-126">See also</span></span>
- [<span data-ttu-id="e9c5d-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9c5d-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="e9c5d-128">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9c5d-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
