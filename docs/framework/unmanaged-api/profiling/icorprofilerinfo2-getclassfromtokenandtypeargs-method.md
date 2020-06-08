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
ms.openlocfilehash: 702c5f9f2bc08c824bdc0607741a6afd65a3e89b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497260"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="02282-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs — Metoda</span><span class="sxs-lookup"><span data-stu-id="02282-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="02282-103">Pobiera `ClassID` Typ przy użyciu określonego tokenu metadanych i `ClassID` wartości dowolnego argumentu typu.</span><span class="sxs-lookup"><span data-stu-id="02282-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02282-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="02282-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02282-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02282-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="02282-106">podczas Identyfikator modułu, w którym znajduje się typ.</span><span class="sxs-lookup"><span data-stu-id="02282-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="02282-107">podczas `mdTypeDef`Token metadanych, który odwołuje się do typu.</span><span class="sxs-lookup"><span data-stu-id="02282-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="02282-108">podczas Liczba parametrów typu dla danego typu.</span><span class="sxs-lookup"><span data-stu-id="02282-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="02282-109">Ta wartość musi być równa zero dla typów innych niż ogólne.</span><span class="sxs-lookup"><span data-stu-id="02282-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="02282-110">podczas Tablica `ClassID` wartości, z których każdy jest argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="02282-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="02282-111">Wartość `typeArgs` może być równa null, jeśli `cTypeArgs` jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="02282-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="02282-112">określoną Wskaźnik do `ClassID` określonego typu.</span><span class="sxs-lookup"><span data-stu-id="02282-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02282-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02282-113">Remarks</span></span>  
 <span data-ttu-id="02282-114">Wywołanie `GetClassFromTokenAndTypeArgs` metody z `mdTypeRef` `mdTypeDef` tokenem instead of metadanych może mieć nieprzewidywalne wyniki; obiekty wywołujące powinny rozpoznać `mdTypeRef` element do `mdTypeDef` podczas jego przekazywania.</span><span class="sxs-lookup"><span data-stu-id="02282-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="02282-115">Jeśli typ nie jest już załadowany, wywołanie `GetClassFromTokenAndTypeArgs` wywoła ładowanie, które jest niebezpieczną operacją w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="02282-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="02282-116">Na przykład wywołanie tej metody podczas ładowania modułów lub innych typów może prowadzić do nieskończonej pętli, ponieważ środowisko uruchomieniowe próbuje cyklicznie ładować elementy.</span><span class="sxs-lookup"><span data-stu-id="02282-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="02282-117">Ogólnie rzecz biorąc, użycie `GetClassFromTokenAndTypeArgs` nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="02282-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="02282-118">Jeśli zainteresują Cię zdarzenia dotyczące określonego typu, powinny one przechowywać `ModuleID` i tego `mdTypeDef` typu, a następnie używać [ICorProfilerInfo2:: GetClassIDInfo2 —](icorprofilerinfo2-getclassidinfo2-method.md) , aby sprawdzić, czy dana `ClassID` jest określona dla żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="02282-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02282-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02282-119">Requirements</span></span>  
 <span data-ttu-id="02282-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02282-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02282-121">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="02282-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02282-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="02282-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02282-123">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02282-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02282-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02282-124">See also</span></span>

- [<span data-ttu-id="02282-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="02282-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="02282-126">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="02282-126">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
