---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 9b5059d9e4bf9b79dc67664c7a7971041d1cf35b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861687"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="541fa-102">ICorProfilerInfo8:: GetDynamicFunctionInfo, Metoda</span><span class="sxs-lookup"><span data-stu-id="541fa-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="541fa-103">Pobiera informacje o metodach dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="541fa-103">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="541fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="541fa-104">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a><span data-ttu-id="541fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="541fa-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="541fa-106">\[in) identyfikator funkcji, dla której mają zostać pobrane informacje.</span><span class="sxs-lookup"><span data-stu-id="541fa-106">\[in] The ID of the function for which to retrieve information.</span></span>

- `moduleId`

  <span data-ttu-id="541fa-107">\[w] wskaźnik do modułu, w którym zdefiniowana jest Klasa nadrzędna funkcji.</span><span class="sxs-lookup"><span data-stu-id="541fa-107">\[in] A pointer to the module in which the function's parent class is defined.</span></span>

- `ppvSig`

  <span data-ttu-id="541fa-108">\[out] wskaźnik do podpisu dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="541fa-108">\[out] A pointer to the signature for the function.</span></span>

- `pbSig`

  <span data-ttu-id="541fa-109">\[out] wskaźnik do liczby bajtów dla sygnatury funkcji.</span><span class="sxs-lookup"><span data-stu-id="541fa-109">\[out] A pointer to the count of bytes for the function signature.</span></span>

- `cchName`

  <span data-ttu-id="541fa-110">\[] maksymalny rozmiar tablicy `wszName`.</span><span class="sxs-lookup"><span data-stu-id="541fa-110">\[in] The maximum size of the `wszName` array.</span></span>

- `pcchName`

  <span data-ttu-id="541fa-111">\[out] liczba znaków w tablicy `wszName`.</span><span class="sxs-lookup"><span data-stu-id="541fa-111">\[out] The number of characters in the `wszName` array.</span></span>

- `wszName`

  <span data-ttu-id="541fa-112">\[out] tablica `WCHAR`, która jest nazwą funkcji (jeśli taka istnieje).</span><span class="sxs-lookup"><span data-stu-id="541fa-112">\[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="541fa-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="541fa-113">Remarks</span></span>

<span data-ttu-id="541fa-114">Niektóre metody, takie jak IL repliks lub LCG, nie mają skojarzonych metadanych, które można pobrać za pomocą interfejsów API [IMetaDataImport](../metadata/imetadataimport-interface.md) i [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="541fa-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="541fa-115">Takie metody mogą być napotkane przez program do zaprogramowania za pomocą wskaźników instrukcji lub przez nasłuchiwanie [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="541fa-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="541fa-116">Ten interfejs API może służyć do pobierania informacji o metodach dynamicznych, łącznie z przyjazną nazwą, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="541fa-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="541fa-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="541fa-117">Requirements</span></span>

<span data-ttu-id="541fa-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="541fa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="541fa-119">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="541fa-119">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="541fa-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="541fa-120">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="541fa-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="541fa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="541fa-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="541fa-122">See also</span></span>

- [<span data-ttu-id="541fa-123">ICorProfilerInfo8, interfejs</span><span class="sxs-lookup"><span data-stu-id="541fa-123">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
