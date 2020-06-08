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
ms.openlocfilehash: f5438ddc655f0f6a7c11d978a47b1bf9e2a13059
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497013"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="7d5de-102">ICorProfilerInfo2::GetFunctionInfo2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="7d5de-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="7d5de-103">Pobiera klasę nadrzędną, token metadanych i `ClassID` dla każdego argumentu typu, jeśli istnieje, funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d5de-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d5de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d5de-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7d5de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d5de-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="7d5de-106">podczas Identyfikator funkcji, dla której ma zostać pobrana Klasa nadrzędna i inne informacje.</span><span class="sxs-lookup"><span data-stu-id="7d5de-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="7d5de-107">podczas `COR_PRF_FRAME_INFO`Wartość, która wskazuje na informacje o klatce stosu.</span><span class="sxs-lookup"><span data-stu-id="7d5de-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="7d5de-108">określoną Wskaźnik do klasy nadrzędnej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d5de-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="7d5de-109">określoną Wskaźnik do modułu, w którym zdefiniowana jest Klasa nadrzędna funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d5de-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="7d5de-110">określoną Wskaźnik do tokenu metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d5de-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="7d5de-111">podczas Rozmiar `typeArgs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7d5de-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="7d5de-112">określoną Wskaźnik do łącznej liczby `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="7d5de-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="7d5de-113">określoną Tablica `ClassID` wartości, z których każdy jest identyfikatorem argumentu typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d5de-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="7d5de-114">Gdy metoda zwraca, `typeArgs` będzie zawierać niektóre lub wszystkie `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="7d5de-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d5de-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d5de-115">Remarks</span></span>  
 <span data-ttu-id="7d5de-116">Kod profilera może wywołać [ICorProfilerInfo:: GetModuleMetaData —](icorprofilerinfo-getmodulemetadata-method.md) w celu uzyskania interfejsu [metadanych](../metadata/index.md) dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="7d5de-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="7d5de-117">Token metadanych, który jest zwracany do lokalizacji, do której się odwołuje się, `pToken` może następnie zostać użyty w celu uzyskania dostępu do metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d5de-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="7d5de-118">Identyfikator klasy i argumenty typu, które są zwracane przez `pClassId` Parametry i są `typeArgs` zależne od wartości przekazanej w `frameInfo` parametrze, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="7d5de-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="7d5de-119">Wartość `frameInfo` parametru</span><span class="sxs-lookup"><span data-stu-id="7d5de-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="7d5de-120">Wynik</span><span class="sxs-lookup"><span data-stu-id="7d5de-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="7d5de-121">`COR_PRF_FRAME_INFO`Wartość uzyskana z `FunctionEnter2` wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="7d5de-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="7d5de-122">`ClassID`, Zwrócone w lokalizacji, do której odwołuje się `pClassId` , i wszystkie argumenty typu zwrócone w `typeArgs` tablicy, będą dokładne.</span><span class="sxs-lookup"><span data-stu-id="7d5de-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="7d5de-123">`COR_PRF_FRAME_INFO`Który został uzyskany ze źródła innego niż `FunctionEnter2` wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="7d5de-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="7d5de-124">Nie można `ClassID` określić argumentów dokładnie i typu.</span><span class="sxs-lookup"><span data-stu-id="7d5de-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="7d5de-125">Oznacza to, że `ClassID` może mieć wartość null, a niektóre argumenty typu mogą wrócić jako <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="7d5de-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="7d5de-126">Zero</span><span class="sxs-lookup"><span data-stu-id="7d5de-126">Zero</span></span>|<span data-ttu-id="7d5de-127">Nie można `ClassID` określić argumentów dokładnie i typu.</span><span class="sxs-lookup"><span data-stu-id="7d5de-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="7d5de-128">Oznacza to, że `ClassID` może mieć wartość null, a niektóre argumenty typu mogą wrócić jako <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="7d5de-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="7d5de-129">Po `GetFunctionInfo2` powrocie należy sprawdzić, czy `typeArgs` bufor jest wystarczająco duży, aby można było zawierać wszystkie `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="7d5de-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="7d5de-130">W tym celu należy porównać wartość wskazującą wartość `pcTypeArgs` `cTypeArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="7d5de-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="7d5de-131">Jeśli `pcTypeArgs` wskazuje wartość, która jest większa niż `cTypeArgs` podzielona przez rozmiar `ClassID` wartości, Przydziel większy `pcTypeArgs` bufor, Aktualizuj `cTypeArgs` o nowy, większy rozmiar i ponownie wywołaj `GetFunctionInfo2` .</span><span class="sxs-lookup"><span data-stu-id="7d5de-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="7d5de-132">Alternatywnie, można najpierw wywołać `GetFunctionInfo2` z buforem o zerowej długości, `pcTypeArgs` Aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="7d5de-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="7d5de-133">Następnie można ustawić rozmiar buforu na wartość zwracaną w `pcTypeArgs` podzieleniu przez rozmiar `ClassID` wartości i `GetFunctionInfo2` ponownie wywołać.</span><span class="sxs-lookup"><span data-stu-id="7d5de-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d5de-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d5de-134">Requirements</span></span>  
 <span data-ttu-id="7d5de-135">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d5de-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d5de-136">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7d5de-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7d5de-137">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d5de-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d5de-138">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d5de-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d5de-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d5de-139">See also</span></span>

- [<span data-ttu-id="7d5de-140">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d5de-140">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="7d5de-141">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d5de-141">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="7d5de-142">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="7d5de-142">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7d5de-143">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="7d5de-143">Profiling</span></span>](index.md)
