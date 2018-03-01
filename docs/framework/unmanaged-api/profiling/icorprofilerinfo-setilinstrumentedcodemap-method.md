---
title: "ICorProfilerInfo::SetILInstrumentedCodeMap — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 127f6d76e85ed30f1407d16f8d81c93dd2941960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="8303e-102">ICorProfilerInfo::SetILInstrumentedCodeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="8303e-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="8303e-103">Ustawia mapę kodu dla funkcji określonej przy użyciu określonego wpisów map język pośredni (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8303e-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8303e-104">W programie .NET Framework w wersji 2.0, wywoływania `SetILInstrumentedCodeMap` na `FunctionID` czy reprezentuje ogólnego działać w domenie określonej aplikacji będzie miało wpływ na wszystkie wystąpienia tej funkcji w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8303e-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8303e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8303e-105">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8303e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8303e-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8303e-107">[in] Identyfikator funkcji, dla którego mają zostać ustawione mapy kodu.</span><span class="sxs-lookup"><span data-stu-id="8303e-107">[in] The ID of the function for which to set the code map.</span></span>  
  
 `fStartJit`  
 <span data-ttu-id="8303e-108">[in] Wartość logiczna, która wskazuje, czy wywołanie `SetILInstrumentedCodeMap` metoda jest pierwszy dla konkretnej `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="8303e-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="8303e-109">Ustaw `fStartJit` do `true` w pierwszym wywołaniu `SetILInstrumentedCodeMap` dla danego `FunctionID`, a w `false` później.</span><span class="sxs-lookup"><span data-stu-id="8303e-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>  
  
 `cILMapEntries`  
 <span data-ttu-id="8303e-110">[in] Liczba elementów w `cILMapEntries` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8303e-110">[in] The number of elements in the `cILMapEntries` array.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="8303e-111">[in] Tablica struktur COR_IL_MAP, z których każdy określa przesunięcie MSIL.</span><span class="sxs-lookup"><span data-stu-id="8303e-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8303e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8303e-112">Remarks</span></span>  
 <span data-ttu-id="8303e-113">Profiler często wstawia instrukcje w kodzie źródłowym metody w celu agregowania tej metody (na przykład do wysyłania powiadomień o osiągnięciu wiersza danego źródła).</span><span class="sxs-lookup"><span data-stu-id="8303e-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="8303e-114">`SetILInstrumentedCodeMap`Umożliwia profiler do mapowania oryginalnego instrukcje MSIL do nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="8303e-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="8303e-115">Można użyć profiler [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metodę, aby pobrać oryginalnego przesunięcie MSIL dla danego przesunięcia macierzystego.</span><span class="sxs-lookup"><span data-stu-id="8303e-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>  
  
 <span data-ttu-id="8303e-116">Debuger przyjmie założenie, że każdy starego przesunięcie odwołuje się do MSIL w oryginalnym niezmodyfikowanego kodu MSIL, i że każdego nowego przesunięcie odwołuje się do przesunięcia MSIL kodem nowy, instrumentowanych.</span><span class="sxs-lookup"><span data-stu-id="8303e-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="8303e-117">Mapy mają być sortowane w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="8303e-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="8303e-118">Wykonywanie krok po kroku, aby działała poprawnie, wykonaj następujące wytyczne:</span><span class="sxs-lookup"><span data-stu-id="8303e-118">For stepping to work properly, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="8303e-119">Zmień kolejność nie instrumentowanych kod MSIL.</span><span class="sxs-lookup"><span data-stu-id="8303e-119">Do not reorder instrumented MSIL code.</span></span>  
  
-   <span data-ttu-id="8303e-120">Nie usuwaj oryginalnego kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="8303e-120">Do not remove the original MSIL code.</span></span>  
  
-   <span data-ttu-id="8303e-121">Zawierać wpisy dla wszystkich punktów sekwencji z pliku programu (PDB) bazy danych na mapie.</span><span class="sxs-lookup"><span data-stu-id="8303e-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="8303e-122">Mapa nie interpolować Brak wpisów.</span><span class="sxs-lookup"><span data-stu-id="8303e-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="8303e-123">Tak podane mapy następujące:</span><span class="sxs-lookup"><span data-stu-id="8303e-123">So, given the following map:</span></span>  
  
     <span data-ttu-id="8303e-124">(0 stare, 0 nowy)</span><span class="sxs-lookup"><span data-stu-id="8303e-124">(0 old, 0 new)</span></span>  
  
     <span data-ttu-id="8303e-125">(5 stare, 10 nowych)</span><span class="sxs-lookup"><span data-stu-id="8303e-125">(5 old, 10 new)</span></span>  
  
     <span data-ttu-id="8303e-126">(9 stare, 20 nowy)</span><span class="sxs-lookup"><span data-stu-id="8303e-126">(9 old, 20 new)</span></span>  
  
    -   <span data-ttu-id="8303e-127">Stary przesunięciem równym 0, 1, 2, 3 lub 4 zostaną zmapowane do nowego przesunięciu 0.</span><span class="sxs-lookup"><span data-stu-id="8303e-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>  
  
    -   <span data-ttu-id="8303e-128">Stary przesunięcie 5, 6, 7 lub 8 zostaną zmapowane do nowego przesunięcie 10.</span><span class="sxs-lookup"><span data-stu-id="8303e-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
    -   <span data-ttu-id="8303e-129">Przesunięcie starego 9 lub nowszą zostaną zmapowane do nowego przesunięcie 20.</span><span class="sxs-lookup"><span data-stu-id="8303e-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
    -   <span data-ttu-id="8303e-130">Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostaną zmapowane do starego przesunięciu 0.</span><span class="sxs-lookup"><span data-stu-id="8303e-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
    -   <span data-ttu-id="8303e-131">Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostaną zmapowane do starego przesunięcie 5.</span><span class="sxs-lookup"><span data-stu-id="8303e-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
    -   <span data-ttu-id="8303e-132">Nowe przesunięcie 20 lub wyższe zostaną zmapowane do starego przesunięcie 9.</span><span class="sxs-lookup"><span data-stu-id="8303e-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8303e-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8303e-133">Requirements</span></span>  
 <span data-ttu-id="8303e-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8303e-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8303e-135">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8303e-135">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8303e-136">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8303e-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8303e-137">**Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8303e-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8303e-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8303e-138">See Also</span></span>  
 [<span data-ttu-id="8303e-139">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="8303e-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
