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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4780242dc34f31ecd0ff0dc2c339cdaa30278a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721165"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="e06e7-102">ICorProfilerInfo::SetILInstrumentedCodeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="e06e7-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="e06e7-103">Ustawia mapę kodu dla określonej funkcji przy użyciu określonego wpisy mapy intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e06e7-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e06e7-104">W .NET Framework w wersji 2.0, wywołanie `SetILInstrumentedCodeMap` na `FunctionID` czy reprezentuje ogólnej funkcji w domenie określonej aplikacji będzie miało wpływ na wszystkie wystąpienia tej funkcji w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e06e7-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06e7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e06e7-105">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e06e7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e06e7-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e06e7-107">[in] Identyfikator funkcji, dla którego ma zostać ustawiony na mapie kodu.</span><span class="sxs-lookup"><span data-stu-id="e06e7-107">[in] The ID of the function for which to set the code map.</span></span>  
  
 `fStartJit`  
 <span data-ttu-id="e06e7-108">[in] Wartość logiczna, która wskazuje, czy wywołanie `SetILInstrumentedCodeMap` metody jest to pierwszy określonego `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="e06e7-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="e06e7-109">Ustaw `fStartJit` do `true` w pierwszym wywołaniu `SetILInstrumentedCodeMap` dla danego `FunctionID`, a `false` po tej dacie.</span><span class="sxs-lookup"><span data-stu-id="e06e7-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>  
  
 `cILMapEntries`  
 <span data-ttu-id="e06e7-110">[in] Liczba elementów w `cILMapEntries` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e06e7-110">[in] The number of elements in the `cILMapEntries` array.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="e06e7-111">[in] Tablica cor_il_map — struktur, z których każdy określa przesunięcie MSIL.</span><span class="sxs-lookup"><span data-stu-id="e06e7-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e06e7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e06e7-112">Remarks</span></span>  
 <span data-ttu-id="e06e7-113">Program profilujący często wstawia instrukcji w kodzie źródłowym metodę w celu Instrumentacja tej metody (na przykład do wysyłania powiadomień o osiągnięciu linię danego źródła).</span><span class="sxs-lookup"><span data-stu-id="e06e7-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="e06e7-114">`SetILInstrumentedCodeMap` Umożliwia programowi profilującemu mapowania oryginalny instrukcji MSIL ich nowych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e06e7-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="e06e7-115">Program profilujący może używać [icorprofilerinfo::getiltonativemapping —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metodę, aby uzyskać oryginalnego przesunięcie MSIL po danym przesunięciu macierzystym.</span><span class="sxs-lookup"><span data-stu-id="e06e7-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>  
  
 <span data-ttu-id="e06e7-116">Debuger założy, że każdy stare przesunięcie odwołuje się do MSIL w kodzie MSIL oryginalne, niezmodyfikowanego i że każdy nowy przesunięcie odwołuje się do przesunięcia MSIL kodem nowe, instrumentowanych.</span><span class="sxs-lookup"><span data-stu-id="e06e7-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="e06e7-117">Mapa powinny być sortowane w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="e06e7-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="e06e7-118">Do przechodzenia, aby zapewnić prawidłowe działanie, należy przestrzegać następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="e06e7-118">For stepping to work properly, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="e06e7-119">Nie zmieniają kolejności instrumentowanych kod MSIL.</span><span class="sxs-lookup"><span data-stu-id="e06e7-119">Do not reorder instrumented MSIL code.</span></span>  
  
-   <span data-ttu-id="e06e7-120">Nie usuwaj oryginalnego kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="e06e7-120">Do not remove the original MSIL code.</span></span>  
  
-   <span data-ttu-id="e06e7-121">Zawierać wpisy dla wszystkich punktów sekwencji z plik bazy danych (PDB) programu w mapie.</span><span class="sxs-lookup"><span data-stu-id="e06e7-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="e06e7-122">Mapa nie interpolacji Brak wpisów.</span><span class="sxs-lookup"><span data-stu-id="e06e7-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="e06e7-123">Tak biorąc pod uwagę poniższe mapy:</span><span class="sxs-lookup"><span data-stu-id="e06e7-123">So, given the following map:</span></span>  
  
     <span data-ttu-id="e06e7-124">(0 stare, 0 nowe)</span><span class="sxs-lookup"><span data-stu-id="e06e7-124">(0 old, 0 new)</span></span>  
  
     <span data-ttu-id="e06e7-125">(5 stare, 10 nowych)</span><span class="sxs-lookup"><span data-stu-id="e06e7-125">(5 old, 10 new)</span></span>  
  
     <span data-ttu-id="e06e7-126">(9 stare, 20 nowych)</span><span class="sxs-lookup"><span data-stu-id="e06e7-126">(9 old, 20 new)</span></span>  
  
    -   <span data-ttu-id="e06e7-127">Stary przesunięcia 0, 1, 2, 3 lub 4 zostanie zamapowane do nowego przesunięciu 0.</span><span class="sxs-lookup"><span data-stu-id="e06e7-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>  
  
    -   <span data-ttu-id="e06e7-128">Przesunięcie stare 5, 6, 7 lub 8 zostaną odwzorowane na nowe przesunięcie 10.</span><span class="sxs-lookup"><span data-stu-id="e06e7-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
    -   <span data-ttu-id="e06e7-129">Stary przesunięcie 9 lub nowszą zostaną odwzorowane na nowe przesunięcie 20.</span><span class="sxs-lookup"><span data-stu-id="e06e7-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
    -   <span data-ttu-id="e06e7-130">Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostaną zmapowane do starego przesunięciu 0.</span><span class="sxs-lookup"><span data-stu-id="e06e7-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
    -   <span data-ttu-id="e06e7-131">Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie zamapowane do starego przesunięcia 5.</span><span class="sxs-lookup"><span data-stu-id="e06e7-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
    -   <span data-ttu-id="e06e7-132">Nowe przesunięcie 20 lub nowszej zostanie zamapowane do starego przesunięcia 9.</span><span class="sxs-lookup"><span data-stu-id="e06e7-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e06e7-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e06e7-133">Requirements</span></span>  
 <span data-ttu-id="e06e7-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e06e7-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e06e7-135">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e06e7-135">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e06e7-136">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e06e7-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e06e7-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e06e7-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06e7-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e06e7-138">See also</span></span>
- [<span data-ttu-id="e06e7-139">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e06e7-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
