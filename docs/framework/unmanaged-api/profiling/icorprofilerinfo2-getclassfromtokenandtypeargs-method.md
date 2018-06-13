---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04be252092732296354cfec102cf8fe648ed2dd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456641"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="cb439-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb439-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="cb439-103">Pobiera `ClassID` typu przy użyciu tokenu określonych metadanych i `ClassID` wartości dowolnego argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="cb439-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb439-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb439-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb439-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb439-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="cb439-106">[in] Identyfikator modułu, w której znajduje się typu.</span><span class="sxs-lookup"><span data-stu-id="cb439-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="cb439-107">[in] `mdTypeDef` Token metadanych, który odwołuje się do typu.</span><span class="sxs-lookup"><span data-stu-id="cb439-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="cb439-108">[in] Liczba parametrów typu dla danego typu.</span><span class="sxs-lookup"><span data-stu-id="cb439-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="cb439-109">Ta wartość musi być zero dla typu nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="cb439-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="cb439-110">[in] Tablica `ClassID` wartości, z których każdy jest argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="cb439-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="cb439-111">Wartość `typeArgs` może mieć wartości NULL, jeśli `cTypeArgs` jest ustawiony na zero.</span><span class="sxs-lookup"><span data-stu-id="cb439-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="cb439-112">[out] Wskaźnik do `ClassID` określonego typu.</span><span class="sxs-lookup"><span data-stu-id="cb439-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb439-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb439-113">Remarks</span></span>  
 <span data-ttu-id="cb439-114">Wywoływanie `GetClassFromTokenAndTypeArgs` metody z `mdTypeRef` zamiast `mdTypeDef` token metadanych może mieć nieprzewidziane skutki; powinna być rozpoznawana przez obiekty wywołujące `mdTypeRef` do `mdTypeDef` podczas przekazywania go.</span><span class="sxs-lookup"><span data-stu-id="cb439-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="cb439-115">Jeśli typ nie jest już załadowany, wywoływania `GetClassFromTokenAndTypeArgs` wyzwoli ładowania, który jest niebezpieczne operacji w wielu sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="cb439-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="cb439-116">Na przykład wywołaniem tej metody w czasie ładowania modułów lub innych typów może spowodować nieskończoną pętlę jako środowisko uruchomieniowe próbuje załadować rekurencyjnie rzeczy.</span><span class="sxs-lookup"><span data-stu-id="cb439-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="cb439-117">Ogólnie rzecz biorąc, użycie `GetClassFromTokenAndTypeArgs` jest niezalecane.</span><span class="sxs-lookup"><span data-stu-id="cb439-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="cb439-118">Zainteresowani profilery zdarzenia dla określonego typu, należy przechowywać `ModuleID` i `mdTypeDef` typu i użyj [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) Aby sprawdzić, czy danego `ClassID` jest odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="cb439-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb439-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb439-119">Requirements</span></span>  
 <span data-ttu-id="cb439-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb439-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb439-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb439-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb439-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb439-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb439-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb439-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb439-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb439-124">See Also</span></span>  
 [<span data-ttu-id="cb439-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb439-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="cb439-126">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb439-126">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
