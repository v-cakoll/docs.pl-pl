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
ms.openlocfilehash: d59de04e6af6cfec473899e0a3edadcb3257d385
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665682"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="a5afb-102">ICorProfilerInfo8:: GetDynamicFunctionInfo, Metoda</span><span class="sxs-lookup"><span data-stu-id="a5afb-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="a5afb-103">Pobiera informacje o metodach dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="a5afb-103">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="a5afb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5afb-104">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

#### <a name="parameters"></a><span data-ttu-id="a5afb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5afb-105">Parameters</span></span>

`functionId` \
<span data-ttu-id="a5afb-106">podczas Identyfikator funkcji, dla której mają zostać pobrane informacje.</span><span class="sxs-lookup"><span data-stu-id="a5afb-106">[in] The ID of the function for which to retrieve information.</span></span>

`moduleId` \
<span data-ttu-id="a5afb-107">podczas Wskaźnik do modułu, w którym zdefiniowana jest Klasa nadrzędna funkcji.</span><span class="sxs-lookup"><span data-stu-id="a5afb-107">[in] A pointer to the module in which the function's parent class is defined.</span></span>

`ppvSig` \
<span data-ttu-id="a5afb-108">określoną Wskaźnik do podpisu dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="a5afb-108">[out] A pointer to the signature for the function.</span></span>

`pbSig` \
<span data-ttu-id="a5afb-109">określoną Wskaźnik do liczby bajtów dla sygnatury funkcji.</span><span class="sxs-lookup"><span data-stu-id="a5afb-109">[out] A pointer to the count of bytes for the function signature.</span></span>

`cchName` \
<span data-ttu-id="a5afb-110">podczas Maksymalny rozmiar `wszName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a5afb-110">[in] The maximum size of the `wszName` array.</span></span>

`pcchName` \
<span data-ttu-id="a5afb-111">określoną Liczba znaków w `wszName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a5afb-111">[out] The number of characters in the `wszName` array.</span></span>

`wszName` \
<span data-ttu-id="a5afb-112">określoną Tablica `WCHAR` , która jest nazwą funkcji (jeśli taka istnieje).</span><span class="sxs-lookup"><span data-stu-id="a5afb-112">[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5afb-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5afb-113">Remarks</span></span>

<span data-ttu-id="a5afb-114">Niektóre metody, takie jak IL repliks lub LCG, nie mają skojarzonych metadanych, które można pobrać za pomocą interfejsów API [IMetaDataImport](../metadata/imetadataimport-interface.md) i [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a5afb-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="a5afb-115">Takie metody mogą być napotkane przez program do zaprogramowania za pomocą wskaźników instrukcji lub przez nasłuchiwanie [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="a5afb-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="a5afb-116">Ten interfejs API może służyć do pobierania informacji o metodach dynamicznych, łącznie z przyjazną nazwą, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="a5afb-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="a5afb-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5afb-117">Requirements</span></span>

<span data-ttu-id="a5afb-118">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5afb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a5afb-119">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a5afb-119">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a5afb-120">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5afb-120">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a5afb-121">**.NET Framework wersje:** [! UWZGLĘDNIj[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="a5afb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="a5afb-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5afb-122">See also</span></span>

- [<span data-ttu-id="a5afb-123">ICorProfilerInfo8, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5afb-123">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
