---
title: "ICorProfilerInfo2::GetFunctionInfo2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b0c288b88c868bc6e324ec57b3956344f03f34e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="2ec9a-102">ICorProfilerInfo2::GetFunctionInfo2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ec9a-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="2ec9a-103">Pobiera klasy nadrzędnej, token metadanych i `ClassID` argumentu typu, jeśli jest obecny, funkcji.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ec9a-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="2ec9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ec9a-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="2ec9a-106">[in] Identyfikator funkcji, dla którego można pobrać obiektu nadrzędnego, klasy i inne informacje.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="2ec9a-107">[in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="2ec9a-108">[out] Wskaźnik do funkcji klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="2ec9a-109">[out] Wskaźnik do modułu, w którym zdefiniowana jest klasa nadrzędna funkcji.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="2ec9a-110">[out] Wskaźnik do tokenu metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="2ec9a-111">[in] Rozmiar `typeArgs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="2ec9a-112">[out] Wskaźnik do łączna liczba `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="2ec9a-113">[out] Tablica `ClassID` wartości, z których każdy jest Identyfikatorem typem argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="2ec9a-114">Gdy metoda zwróci wartość, `typeArgs` będzie zawierał niektórych lub wszystkich `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ec9a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ec9a-115">Remarks</span></span>  
 <span data-ttu-id="2ec9a-116">Kod profiler może wywołać [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskanie [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) interfejs dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="2ec9a-117">Token metadanych, która jest zwracana do lokalizacji odwołuje się `pToken` mogą następnie służyć do uzyskania dostępu do funkcji metadanych.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="2ec9a-118">Klasa identyfikator i typ argumenty, które są zwracane przez `pClassId` i `typeArgs` parametry są zależne od wartości, który jest przekazywany w `frameInfo` parametru, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="2ec9a-119">Wartość `frameInfo` parametru</span><span class="sxs-lookup"><span data-stu-id="2ec9a-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="2ec9a-120">Wynik</span><span class="sxs-lookup"><span data-stu-id="2ec9a-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="2ec9a-121">A `COR_PRF_FRAME_INFO` wartości, który został uzyskany z `FunctionEnter2` wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="2ec9a-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="2ec9a-122">`ClassID`, Zwracane w lokalizacji odwołuje się `pClassId`, i wpisz wszystkich argumentów i zwracane w `typeArgs` tablicy, będą dokładne.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="2ec9a-123">A `COR_PRF_FRAME_INFO` uzyskany od źródła innego niż `FunctionEnter2` wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="2ec9a-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="2ec9a-124">Dokładnie `ClassID` i nie można określić argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="2ec9a-125">Oznacza to `ClassID` może mieć wartości null i niektórych argumentów typu może występować jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="2ec9a-126">Zero</span><span class="sxs-lookup"><span data-stu-id="2ec9a-126">Zero</span></span>|<span data-ttu-id="2ec9a-127">Dokładnie `ClassID` i nie można określić argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="2ec9a-128">Oznacza to `ClassID` może mieć wartości null i niektórych argumentów typu może występować jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="2ec9a-129">Po `GetFunctionInfo2` zwróci wartość, należy sprawdzić, czy `typeArgs` bufor był wystarczająco duży, aby pomieścić wszystkie `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="2ec9a-130">W tym celu należy porównać wartości który `pcTypeArgs` wskazuje wartość `cTypeArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="2ec9a-131">Jeśli `pcTypeArgs` wskazuje wartość, która jest większa niż `cTypeArgs` podzielonej przez rozmiar `ClassID` wartość, Przydziel większy `pcTypeArgs` buforu, zaktualizuj `cTypeArgs` z nowej, większy rozmiar i wywołanie `GetFunctionInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="2ec9a-132">Alternatywnie można wywołać `GetFunctionInfo2` o zerowej długości `pcTypeArgs` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="2ec9a-133">Rozmiar buforu można następnie ustawić wartość zwracana w `pcTypeArgs` podzielonej przez rozmiar `ClassID` wartość i wywołanie `GetFunctionInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="2ec9a-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ec9a-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ec9a-134">Requirements</span></span>  
 <span data-ttu-id="2ec9a-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ec9a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ec9a-136">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2ec9a-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2ec9a-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ec9a-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ec9a-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ec9a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec9a-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ec9a-139">See Also</span></span>  
 [<span data-ttu-id="2ec9a-140">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="2ec9a-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="2ec9a-141">ICorProfilerInfo2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="2ec9a-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="2ec9a-142">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="2ec9a-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="2ec9a-143">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="2ec9a-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
