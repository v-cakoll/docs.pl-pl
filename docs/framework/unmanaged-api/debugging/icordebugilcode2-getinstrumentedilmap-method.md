---
title: Metoda ICorDebugILCode2::GetInstrumentedILMap
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4197b018ea85402762a8591b40f3503c02af3974
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222877"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="57793-102">Metoda ICorDebugILCode2::GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="57793-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="57793-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="57793-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="57793-104">Zwraca mapę z Instrumentacji profilera języka pośredniego (IL) przesunięcia do oryginalnego przesunięcia IL metody dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="57793-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57793-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="57793-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57793-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="57793-106">Parameters</span></span>  
 <span data-ttu-id="57793-107">CMap</span><span class="sxs-lookup"><span data-stu-id="57793-107">cMap</span></span>  
 <span data-ttu-id="57793-108">[in] Pojemność magazynu `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="57793-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="57793-109">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="57793-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="57793-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="57793-110">pcMap</span></span>  
 <span data-ttu-id="57793-111">[out] Liczba wartości cor_il_map — zapisywane do tablicy mapy.</span><span class="sxs-lookup"><span data-stu-id="57793-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="57793-112">map</span><span class="sxs-lookup"><span data-stu-id="57793-112">map</span></span>  
 <span data-ttu-id="57793-113">[out] Tablica wartości cor_il_map —, które zawierają informacje dotyczące mapowania z Instrumentacji profilera IL do IL oryginalną metodę.</span><span class="sxs-lookup"><span data-stu-id="57793-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57793-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57793-114">Remarks</span></span>  
 <span data-ttu-id="57793-115">Jeśli profiler ustawia mapowanie przez wywołanie metody [icorprofilerinfo::setilinstrumentedcodemap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metody, debuger tę metodę można wywołać można pobrać mapowania i mapowanie wewnętrznie do obliczania IL rekompensaty w przypadku stosu ślady i okresy istnienia zmiennych.</span><span class="sxs-lookup"><span data-stu-id="57793-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="57793-116">Jeśli `cMap` wynosi 0 i `pcMap` ma wartość inną niż**null**, `pcMap` wynosi liczba dostępnych wartości cor_il_map —.</span><span class="sxs-lookup"><span data-stu-id="57793-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="57793-117">Jeśli `cMap` jest różna od zera, reprezentuje pojemność magazynu `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="57793-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="57793-118">Po powrocie z metody `map` może zawierać maksymalnie `cMap` elementów, a `pcMap` jest równa wartości cor_il_map — rzeczywiście zapisanych na `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="57793-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="57793-119">Jeśli nie zostały zinstrumentowane IL lub mapowanie nie podano przez program profilujący, Metoda ta zwraca `S_OK` i ustawia `pcMap` na 0.</span><span class="sxs-lookup"><span data-stu-id="57793-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57793-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57793-120">Requirements</span></span>  
 <span data-ttu-id="57793-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57793-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57793-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57793-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57793-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57793-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57793-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57793-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57793-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57793-125">See also</span></span>

- [<span data-ttu-id="57793-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="57793-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="57793-127">ICorDebugILCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="57793-127">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="57793-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="57793-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
