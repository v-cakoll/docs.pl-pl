---
title: "ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc89ca6213008192c0af8e519ae255c13e9763c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="f7a22-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs — Metoda</span><span class="sxs-lookup"><span data-stu-id="f7a22-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="f7a22-103">Pobiera `FunctionID` funkcji przy użyciu tokenu określonych metadanych, klasą, i `ClassID` wartości dowolnego argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="f7a22-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a22-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7a22-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7a22-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7a22-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="f7a22-106">[in] Identyfikator modułu, w której znajduje się funkcja.</span><span class="sxs-lookup"><span data-stu-id="f7a22-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="f7a22-107">[in] `mdMethodDef` Token metadanych, który odwołuje się do funkcji.</span><span class="sxs-lookup"><span data-stu-id="f7a22-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="f7a22-108">[in] Identyfikator klasy zawierające funkcji.</span><span class="sxs-lookup"><span data-stu-id="f7a22-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="f7a22-109">[in] Liczba parametrów typu dla danej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f7a22-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="f7a22-110">Ta wartość musi wynosić zero dla funkcji nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="f7a22-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="f7a22-111">[in] Tablica `ClassID` wartości, z których każdy jest argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="f7a22-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="f7a22-112">Wartość `typeArgs` może mieć wartości NULL, jeśli `cTypeArgs` jest ustawiony na zero.</span><span class="sxs-lookup"><span data-stu-id="f7a22-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="f7a22-113">[out] Wskaźnik do `FunctionID` określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="f7a22-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7a22-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7a22-114">Remarks</span></span>  
 <span data-ttu-id="f7a22-115">Wywoływanie `GetFunctionFromTokenAndTypeArgs` metody z `mdMethodRef` metadanych zamiast `mdMethodDef` token metadanych może mieć nieprzewidywalne skutki.</span><span class="sxs-lookup"><span data-stu-id="f7a22-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="f7a22-116">Powinna być rozpoznawana przez obiekty wywołujące `mdMethodRef` do `mdMethodDef` podczas przekazywania go.</span><span class="sxs-lookup"><span data-stu-id="f7a22-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="f7a22-117">Jeśli funkcja nie jest już załadowany, wywoływania `GetFunctionFromTokenAndTypeArgs` spowoduje, że ładowanie było, który jest niebezpieczne operacji w wielu sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="f7a22-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="f7a22-118">Na przykład wywołaniem tej metody w czasie ładowania modułów lub typów może spowodować nieskończoną pętlę jako środowisko uruchomieniowe próbuje załadować rekurencyjnie rzeczy.</span><span class="sxs-lookup"><span data-stu-id="f7a22-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="f7a22-119">Ogólnie rzecz biorąc, użycie `GetFunctionFromTokenAndTypeArgs` jest niezalecane.</span><span class="sxs-lookup"><span data-stu-id="f7a22-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="f7a22-120">Zainteresowani profilery zdarzeń dla danej funkcji, należy przechowywać `ModuleID` i `mdMethodDef` tej funkcji i użyj [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) Aby sprawdzić, czy danego `FunctionID` jest z odpowiednią funkcję.</span><span class="sxs-lookup"><span data-stu-id="f7a22-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7a22-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7a22-121">Requirements</span></span>  
 <span data-ttu-id="f7a22-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7a22-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7a22-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7a22-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7a22-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7a22-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7a22-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7a22-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a22-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7a22-126">See Also</span></span>  
 [<span data-ttu-id="f7a22-127">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="f7a22-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="f7a22-128">ICorProfilerInfo2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="f7a22-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
