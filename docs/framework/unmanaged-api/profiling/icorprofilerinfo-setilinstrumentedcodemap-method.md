---
title: ICorProfilerInfo::SetILInstrumentedCodeMap — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: 99e473268fd0d5bb8ce120b97576277949b86508
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869000"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="e30f9-102">ICorProfilerInfo::SetILInstrumentedCodeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="e30f9-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="e30f9-103">Ustawia mapę kodu dla określonej funkcji przy użyciu określonych wpisów mapy języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e30f9-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>

> [!NOTE]
> <span data-ttu-id="e30f9-104">W .NET Framework w wersji 2,0 wywoływanie `SetILInstrumentedCodeMap` na `FunctionID`, który reprezentuje funkcję generyczną w określonej domenie aplikacji, wpłynie na wszystkie wystąpienia tej funkcji w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e30f9-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>

## <a name="syntax"></a><span data-ttu-id="e30f9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e30f9-105">Syntax</span></span>

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a><span data-ttu-id="e30f9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e30f9-106">Parameters</span></span>

`functionId`\
<span data-ttu-id="e30f9-107">podczas Identyfikator funkcji, dla której ma zostać ustawiona Mapa kodu.</span><span class="sxs-lookup"><span data-stu-id="e30f9-107">[in] The ID of the function for which to set the code map.</span></span>

`fStartJit`\
<span data-ttu-id="e30f9-108">podczas Wartość logiczna wskazująca, czy wywołanie metody `SetILInstrumentedCodeMap` jest pierwszym elementem dla konkretnego `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="e30f9-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="e30f9-109">Ustaw `fStartJit` na `true` w pierwszym wywołaniu `SetILInstrumentedCodeMap` dla danego `FunctionID`i `false`.</span><span class="sxs-lookup"><span data-stu-id="e30f9-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>

`cILMapEntries`\
<span data-ttu-id="e30f9-110">podczas Liczba elementów w tablicy `cILMapEntries`.</span><span class="sxs-lookup"><span data-stu-id="e30f9-110">[in] The number of elements in the `cILMapEntries` array.</span></span>

`rgILMapEntries`\
<span data-ttu-id="e30f9-111">podczas Tablica struktur COR_IL_MAP, z których każdy Określa przesunięcie MSIL.</span><span class="sxs-lookup"><span data-stu-id="e30f9-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>

## <a name="remarks"></a><span data-ttu-id="e30f9-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e30f9-112">Remarks</span></span>

<span data-ttu-id="e30f9-113">Profiler często wstawia instrukcje w kodzie źródłowym metody w celu instrumentowania tej metody (na przykład w celu powiadomienia po osiągnięciu podanych linii źródłowej).</span><span class="sxs-lookup"><span data-stu-id="e30f9-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="e30f9-114">`SetILInstrumentedCodeMap` umożliwia programowi Profiler zamapowanie oryginalnych instrukcji MSIL na nowe lokalizacje.</span><span class="sxs-lookup"><span data-stu-id="e30f9-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="e30f9-115">Profiler może użyć metody [ICorProfilerInfo:: GetILToNativeMapping —](icorprofilerinfo-getiltonativemapping-method.md) , aby uzyskać początkowe przesunięcie MSIL dla danego przesunięcia natywnego.</span><span class="sxs-lookup"><span data-stu-id="e30f9-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>

<span data-ttu-id="e30f9-116">Debuger przyjmie, że każde Stare przesunięcie odwołuje się do przesunięcia MSIL w oryginalnym, niezmodyfikowanym kodzie MSIL i że każde nowe przesunięcie odwołuje się do przesunięcia MSIL w nowym, przyrządowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e30f9-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="e30f9-117">Mapa powinna być posortowana w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="e30f9-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="e30f9-118">Aby krok po kroku działał prawidłowo, postępuj zgodnie z następującymi wskazówkami:</span><span class="sxs-lookup"><span data-stu-id="e30f9-118">For stepping to work properly, follow these guidelines:</span></span>

- <span data-ttu-id="e30f9-119">Nie zmieniaj kolejności kodu MSIL z instrumentacją.</span><span class="sxs-lookup"><span data-stu-id="e30f9-119">Do not reorder instrumented MSIL code.</span></span>

- <span data-ttu-id="e30f9-120">Nie usuwaj oryginalnego kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="e30f9-120">Do not remove the original MSIL code.</span></span>

- <span data-ttu-id="e30f9-121">Dołącz wpisy dla wszystkich punktów sekwencji z pliku bazy danych programu (PDB) na mapie.</span><span class="sxs-lookup"><span data-stu-id="e30f9-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="e30f9-122">Mapa nie wykonuje interpolacji brakujących wpisów.</span><span class="sxs-lookup"><span data-stu-id="e30f9-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="e30f9-123">Dlatego, uwzględniając następujące mapowanie:</span><span class="sxs-lookup"><span data-stu-id="e30f9-123">So, given the following map:</span></span>

  <span data-ttu-id="e30f9-124">(0 stara, 0 New)</span><span class="sxs-lookup"><span data-stu-id="e30f9-124">(0 old, 0 new)</span></span>

  <span data-ttu-id="e30f9-125">(5 starych, 10 nowych)</span><span class="sxs-lookup"><span data-stu-id="e30f9-125">(5 old, 10 new)</span></span>

  <span data-ttu-id="e30f9-126">(9 starych, 20 nowych)</span><span class="sxs-lookup"><span data-stu-id="e30f9-126">(9 old, 20 new)</span></span>

  - <span data-ttu-id="e30f9-127">Stare przesunięcie 0, 1, 2, 3 lub 4 zostanie zmapowane na nowe przesunięcie 0.</span><span class="sxs-lookup"><span data-stu-id="e30f9-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>

  - <span data-ttu-id="e30f9-128">Stare przesunięcie o wartości 5, 6, 7 lub 8 zostanie zmapowane na nowe przesunięcie 10.</span><span class="sxs-lookup"><span data-stu-id="e30f9-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>

  - <span data-ttu-id="e30f9-129">Stare przesunięcie w wysokości 9 lub wyższej zostanie zmapowane do nowego przesunięcia 20.</span><span class="sxs-lookup"><span data-stu-id="e30f9-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>

  - <span data-ttu-id="e30f9-130">Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostanie zmapowane do starego przesunięcia 0.</span><span class="sxs-lookup"><span data-stu-id="e30f9-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>

  - <span data-ttu-id="e30f9-131">Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie zmapowane do starego przesunięcia 5.</span><span class="sxs-lookup"><span data-stu-id="e30f9-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>

  - <span data-ttu-id="e30f9-132">Nowe przesunięcie o wartości 20 lub wyższej zostanie zmapowane do starego przesunięcia 9.</span><span class="sxs-lookup"><span data-stu-id="e30f9-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>

<span data-ttu-id="e30f9-133">W .NET Framework 3,5 i poprzednich wersjach przypisujesz tablicę `rgILMapEntries`, wywołując metodę [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) .</span><span class="sxs-lookup"><span data-stu-id="e30f9-133">In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method.</span></span> <span data-ttu-id="e30f9-134">Ponieważ środowisko uruchomieniowe przejmuje własność tej pamięci, profiler nie powinien próbować go zwolnić.</span><span class="sxs-lookup"><span data-stu-id="e30f9-134">Because the runtime takes ownership of this memory, the profiler should not attempt to free it.</span></span>

## <a name="requirements"></a><span data-ttu-id="e30f9-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e30f9-135">Requirements</span></span>

<span data-ttu-id="e30f9-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e30f9-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e30f9-137">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e30f9-137">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e30f9-138">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e30f9-138">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e30f9-139">**Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e30f9-139">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e30f9-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e30f9-140">See also</span></span>

- [<span data-ttu-id="e30f9-141">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e30f9-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
