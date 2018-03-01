---
title: "ICorProfilerInfo2::GetFunctionInfo2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e7a48f109c22ae768e636a7f6b57e4e10ac76012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="50e32-102">ICorProfilerInfo2::GetFunctionInfo2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="50e32-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="50e32-103">Pobiera klasy nadrzędnej, token metadanych i `ClassID` argumentu typu, jeśli jest obecny, funkcji.</span><span class="sxs-lookup"><span data-stu-id="50e32-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e32-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50e32-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="50e32-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50e32-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="50e32-106">[in] Identyfikator funkcji, dla którego można pobrać obiektu nadrzędnego, klasy i inne informacje.</span><span class="sxs-lookup"><span data-stu-id="50e32-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="50e32-107">[in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="50e32-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="50e32-108">[out] Wskaźnik do funkcji klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="50e32-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="50e32-109">[out] Wskaźnik do modułu, w którym zdefiniowana jest klasa nadrzędna funkcji.</span><span class="sxs-lookup"><span data-stu-id="50e32-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="50e32-110">[out] Wskaźnik do tokenu metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="50e32-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="50e32-111">[in] Rozmiar `typeArgs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="50e32-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="50e32-112">[out] Wskaźnik do łączna liczba `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="50e32-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="50e32-113">[out] Tablica `ClassID` wartości, z których każdy jest Identyfikatorem typem argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="50e32-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="50e32-114">Gdy metoda zwróci wartość, `typeArgs` będzie zawierał niektórych lub wszystkich `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="50e32-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50e32-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50e32-115">Remarks</span></span>  
 <span data-ttu-id="50e32-116">Kod profiler może wywołać [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskanie [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) interfejs dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="50e32-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="50e32-117">Token metadanych, która jest zwracana do lokalizacji odwołuje się `pToken` mogą następnie służyć do uzyskania dostępu do funkcji metadanych.</span><span class="sxs-lookup"><span data-stu-id="50e32-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="50e32-118">Klasa identyfikator i typ argumenty, które są zwracane przez `pClassId` i `typeArgs` parametry są zależne od wartości, który jest przekazywany w `frameInfo` parametru, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="50e32-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="50e32-119">Wartość `frameInfo` parametru</span><span class="sxs-lookup"><span data-stu-id="50e32-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="50e32-120">Wynik</span><span class="sxs-lookup"><span data-stu-id="50e32-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="50e32-121">A `COR_PRF_FRAME_INFO` wartości, który został uzyskany z `FunctionEnter2` wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="50e32-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="50e32-122">`ClassID`, Zwracane w lokalizacji odwołuje się `pClassId`, i wpisz wszystkich argumentów i zwracane w `typeArgs` tablicy, będą dokładne.</span><span class="sxs-lookup"><span data-stu-id="50e32-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="50e32-123">A `COR_PRF_FRAME_INFO` uzyskany od źródła innego niż `FunctionEnter2` wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="50e32-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="50e32-124">Dokładnie `ClassID` i nie można określić argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="50e32-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="50e32-125">Oznacza to `ClassID` może mieć wartości null i niektórych argumentów typu może występować jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="50e32-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="50e32-126">Zero</span><span class="sxs-lookup"><span data-stu-id="50e32-126">Zero</span></span>|<span data-ttu-id="50e32-127">Dokładnie `ClassID` i nie można określić argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="50e32-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="50e32-128">Oznacza to `ClassID` może mieć wartości null i niektórych argumentów typu może występować jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="50e32-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="50e32-129">Po `GetFunctionInfo2` zwróci wartość, należy sprawdzić, czy `typeArgs` bufor był wystarczająco duży, aby pomieścić wszystkie `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="50e32-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="50e32-130">W tym celu należy porównać wartości który `pcTypeArgs` wskazuje wartość `cTypeArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="50e32-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="50e32-131">Jeśli `pcTypeArgs` wskazuje wartość, która jest większa niż `cTypeArgs` podzielonej przez rozmiar `ClassID` wartość, Przydziel większy `pcTypeArgs` buforu, zaktualizuj `cTypeArgs` z nowej, większy rozmiar i wywołanie `GetFunctionInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="50e32-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="50e32-132">Alternatywnie można wywołać `GetFunctionInfo2` o zerowej długości `pcTypeArgs` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="50e32-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="50e32-133">Rozmiar buforu można następnie ustawić wartość zwracana w `pcTypeArgs` podzielonej przez rozmiar `ClassID` wartość i wywołanie `GetFunctionInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="50e32-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e32-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50e32-134">Requirements</span></span>  
 <span data-ttu-id="50e32-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e32-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e32-136">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50e32-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50e32-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50e32-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50e32-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e32-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e32-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50e32-139">See Also</span></span>  
 [<span data-ttu-id="50e32-140">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="50e32-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="50e32-141">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="50e32-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="50e32-142">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="50e32-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="50e32-143">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="50e32-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
