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
ms.openlocfilehash: 7f1276e1adeece086ca7b6791eb6e870faf4d010
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502876"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="05e42-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs — Metoda</span><span class="sxs-lookup"><span data-stu-id="05e42-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="05e42-103">Pobiera `FunctionID` funkcję przy użyciu określonego tokenu metadanych, zawierającego klasę i `ClassID` wartości dowolnego argumentu typu.</span><span class="sxs-lookup"><span data-stu-id="05e42-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05e42-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05e42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05e42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05e42-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="05e42-106">podczas Identyfikator modułu, w którym znajduje się funkcja.</span><span class="sxs-lookup"><span data-stu-id="05e42-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="05e42-107">podczas `mdMethodDef`Token metadanych, który odwołuje się do funkcji.</span><span class="sxs-lookup"><span data-stu-id="05e42-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="05e42-108">podczas Identyfikator klasy zawierającej funkcję.</span><span class="sxs-lookup"><span data-stu-id="05e42-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="05e42-109">podczas Liczba parametrów typu dla danej funkcji.</span><span class="sxs-lookup"><span data-stu-id="05e42-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="05e42-110">Ta wartość musi być równa zero w przypadku funkcji innych niż ogólne.</span><span class="sxs-lookup"><span data-stu-id="05e42-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="05e42-111">podczas Tablica `ClassID` wartości, z których każdy jest argumentem funkcji.</span><span class="sxs-lookup"><span data-stu-id="05e42-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="05e42-112">Wartość `typeArgs` może być równa null, jeśli `cTypeArgs` jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="05e42-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="05e42-113">określoną Wskaźnik do `FunctionID` określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="05e42-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05e42-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05e42-114">Remarks</span></span>  
 <span data-ttu-id="05e42-115">Wywołanie `GetFunctionFromTokenAndTypeArgs` metody z `mdMethodRef` metadanymi zamiast `mdMethodDef` tokenu metadanych może mieć nieprzewidywalne wyniki.</span><span class="sxs-lookup"><span data-stu-id="05e42-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="05e42-116">Podczas przekazywania obiekty wywołujące powinny rozwiązać ten problem `mdMethodRef` `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="05e42-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="05e42-117">Jeśli funkcja nie jest już załadowana, wywołanie `GetFunctionFromTokenAndTypeArgs` spowoduje wystąpienie załadowania, które jest niebezpieczną operacją w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="05e42-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="05e42-118">Na przykład wywołanie tej metody podczas ładowania modułów lub typów może prowadzić do nieskończonej pętli, ponieważ środowisko uruchomieniowe próbuje cyklicznie ładować elementy.</span><span class="sxs-lookup"><span data-stu-id="05e42-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="05e42-119">Ogólnie rzecz biorąc, użycie `GetFunctionFromTokenAndTypeArgs` nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="05e42-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="05e42-120">Jeśli zainteresują Cię zdarzenia dotyczące konkretnej funkcji, powinny one przechowywać `ModuleID` i tej `mdMethodDef` funkcji, a następnie używać [ICorProfilerInfo2:: GetFunctionInfo2 —](icorprofilerinfo2-getfunctioninfo2-method.md) , aby sprawdzić, czy dana jest dana `FunctionID` żądana funkcja.</span><span class="sxs-lookup"><span data-stu-id="05e42-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05e42-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05e42-121">Requirements</span></span>  
 <span data-ttu-id="05e42-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05e42-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05e42-123">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="05e42-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05e42-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="05e42-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05e42-125">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05e42-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e42-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05e42-126">See also</span></span>

- [<span data-ttu-id="05e42-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="05e42-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="05e42-128">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="05e42-128">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
