---
title: ICorProfilerInfo2::GetFunctionInfo2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
ms.openlocfilehash: 11f9a186f5ec5e3b9e718a3ccd43b35b66d28078
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433180"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="d2ca3-102">ICorProfilerInfo2::GetFunctionInfo2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2ca3-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="d2ca3-103">Pobiera klasę nadrzędną, token metadanych i `ClassID` każdego argumentu typu, jeśli istnieje, funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2ca3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2ca3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2ca3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2ca3-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="d2ca3-106">podczas Identyfikator funkcji, dla której ma zostać pobrana Klasa nadrzędna i inne informacje.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="d2ca3-107">podczas Wartość `COR_PRF_FRAME_INFO`, która wskazuje na informacje o ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="d2ca3-108">określoną Wskaźnik do klasy nadrzędnej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="d2ca3-109">określoną Wskaźnik do modułu, w którym zdefiniowana jest Klasa nadrzędna funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="d2ca3-110">określoną Wskaźnik do tokenu metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="d2ca3-111">podczas Rozmiar tablicy `typeArgs`.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="d2ca3-112">określoną Wskaźnik do łącznej liczby wartości `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="d2ca3-113">określoną Tablica wartości `ClassID`, z których każdy jest IDENTYFIKATORem argumentu typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="d2ca3-114">Gdy metoda zwraca, `typeArgs` będzie zawierać niektóre lub wszystkie wartości `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2ca3-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2ca3-115">Remarks</span></span>  
 <span data-ttu-id="d2ca3-116">Kod profilera może wywołać [ICorProfilerInfo:: GetModuleMetaData —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) w celu uzyskania interfejsu [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="d2ca3-117">Token metadanych, który jest zwracany do lokalizacji, do której odwołuje się `pToken`, może następnie zostać użyty w celu uzyskania dostępu do metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="d2ca3-118">Identyfikatory klasy i argumenty typu, które są zwracane przez parametry `pClassId` i `typeArgs`, zależą od wartości przekazanej w parametrze `frameInfo`, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="d2ca3-119">Wartość parametru `frameInfo`</span><span class="sxs-lookup"><span data-stu-id="d2ca3-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="d2ca3-120">Wynik</span><span class="sxs-lookup"><span data-stu-id="d2ca3-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="d2ca3-121">Wartość `COR_PRF_FRAME_INFO` uzyskana z wywołania zwrotnego `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="d2ca3-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="d2ca3-122">`ClassID`, zwrócona w lokalizacji, do której odwołuje się `pClassId`, a wszystkie argumenty typu zwrócone w tablicy `typeArgs`, będą dokładne.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="d2ca3-123">`COR_PRF_FRAME_INFO` uzyskany ze źródła innego niż `FunctionEnter2` wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="d2ca3-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="d2ca3-124">Nie można określić dokładnej `ClassID` i argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="d2ca3-125">Oznacza to, że `ClassID` może mieć wartość null, a niektóre argumenty typu mogą wrócić jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="d2ca3-126">Zero</span><span class="sxs-lookup"><span data-stu-id="d2ca3-126">Zero</span></span>|<span data-ttu-id="d2ca3-127">Nie można określić dokładnej `ClassID` i argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="d2ca3-128">Oznacza to, że `ClassID` może mieć wartość null, a niektóre argumenty typu mogą wrócić jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="d2ca3-129">Po powrocie `GetFunctionInfo2` należy sprawdzić, czy bufor `typeArgs` był wystarczająco duży, aby zawierał wszystkie wartości `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="d2ca3-130">W tym celu należy porównać wartość, która `pcTypeArgs` wskazuje na wartość parametru `cTypeArgs`.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="d2ca3-131">Jeśli `pcTypeArgs` wskazuje wartość, która jest większa niż `cTypeArgs` podzielona przez rozmiar `ClassID` wartości, Przydziel większy bufor `pcTypeArgs`, zaktualizuj `cTypeArgs` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetFunctionInfo2`.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="d2ca3-132">Alternatywnie można najpierw wywołać `GetFunctionInfo2` z buforem `pcTypeArgs` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d2ca3-133">Następnie można ustawić rozmiar buforu na wartość zwróconą przez `pcTypeArgs` podzieloną przez rozmiar `ClassID` wartości i ponownie wywołać `GetFunctionInfo2`.</span><span class="sxs-lookup"><span data-stu-id="d2ca3-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2ca3-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2ca3-134">Requirements</span></span>  
 <span data-ttu-id="d2ca3-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2ca3-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2ca3-136">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d2ca3-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2ca3-137">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d2ca3-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2ca3-138">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2ca3-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ca3-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2ca3-139">See also</span></span>

- [<span data-ttu-id="d2ca3-140">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2ca3-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="d2ca3-141">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2ca3-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="d2ca3-142">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="d2ca3-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d2ca3-143">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="d2ca3-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
