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
ms.openlocfilehash: a88a6c19a5c8b45576dd6f632adf70f7ec2eed55
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751873"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="04002-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs — Metoda</span><span class="sxs-lookup"><span data-stu-id="04002-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="04002-103">Pobiera `ClassID` typu przy użyciu tokenu określonych metadanych i `ClassID` wartości wszelkich argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="04002-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04002-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04002-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04002-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04002-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="04002-106">[in] Identyfikator modułu, w której znajduje się typu.</span><span class="sxs-lookup"><span data-stu-id="04002-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="04002-107">[in] `mdTypeDef` Token metadanych, który odwołuje się do typu.</span><span class="sxs-lookup"><span data-stu-id="04002-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="04002-108">[in] Liczba parametrów typu dla danego typu.</span><span class="sxs-lookup"><span data-stu-id="04002-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="04002-109">Ta wartość musi mieć wartość zero dla typu nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="04002-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="04002-110">[in] Tablica `ClassID` wartości, z których każdy jest argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="04002-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="04002-111">Wartość `typeArgs` może mieć wartości NULL, jeśli `cTypeArgs` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="04002-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="04002-112">[out] Wskaźnik do `ClassID` określonego typu.</span><span class="sxs-lookup"><span data-stu-id="04002-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04002-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04002-113">Remarks</span></span>  
 <span data-ttu-id="04002-114">Wywoływanie `GetClassFromTokenAndTypeArgs` metody z `mdTypeRef` zamiast `mdTypeDef` token metadanych może przynieść nieprzewidywalne rezultaty; obiekty wywołujące powinna być rozpoznawana `mdTypeRef` do `mdTypeDef` podczas przekazywania go.</span><span class="sxs-lookup"><span data-stu-id="04002-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="04002-115">Jeśli typ nie jest już załadowany, wywołanie `GetClassFromTokenAndTypeArgs` wyzwoli załadunku, które jest operacją niebezpiecznych w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="04002-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="04002-116">Na przykład wywołanie tej metody w czasie ładowania modułów lub innych typów może prowadzić do wejścia w nieskończoną pętlę jako środowisko wykonawcze próby rekurencyjnie załadować rzeczy.</span><span class="sxs-lookup"><span data-stu-id="04002-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="04002-117">Ogólnie rzecz biorąc, użytkowania `GetClassFromTokenAndTypeArgs` jest niezalecane.</span><span class="sxs-lookup"><span data-stu-id="04002-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="04002-118">Zainteresowani profilery zdarzeń dla określonego typu, należy przechowywać `ModuleID` i `mdTypeDef` tego typu i użyj [icorprofilerinfo2::getclassidinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) Aby sprawdzić, czy dany `ClassID` jest żądany typ.</span><span class="sxs-lookup"><span data-stu-id="04002-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04002-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04002-119">Requirements</span></span>  
 <span data-ttu-id="04002-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04002-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04002-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04002-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04002-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04002-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04002-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04002-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04002-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04002-124">See also</span></span>

- [<span data-ttu-id="04002-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="04002-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="04002-126">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="04002-126">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
