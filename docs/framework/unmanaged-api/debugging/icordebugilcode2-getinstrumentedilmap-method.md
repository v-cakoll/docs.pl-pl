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
ms.openlocfilehash: 6a712ed9e3534ca6bb2962989f1ab3750a25d539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417905"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="ab415-102">Metoda ICorDebugILCode2::GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="ab415-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="ab415-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="ab415-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ab415-104">Zwraca mapę z Instrumentacji profilera języku pośrednim (IL) przesunięcia do oryginalnego przesunięcia metody IL dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ab415-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab415-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab415-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab415-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab415-106">Parameters</span></span>  
 <span data-ttu-id="ab415-107">cMap</span><span class="sxs-lookup"><span data-stu-id="ab415-107">cMap</span></span>  
 <span data-ttu-id="ab415-108">[in] Pojemność `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ab415-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="ab415-109">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="ab415-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="ab415-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="ab415-110">pcMap</span></span>  
 <span data-ttu-id="ab415-111">[out] Liczba wartości COR_IL_MAP zapisywane do tablicy mapy.</span><span class="sxs-lookup"><span data-stu-id="ab415-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="ab415-112">map</span><span class="sxs-lookup"><span data-stu-id="ab415-112">map</span></span>  
 <span data-ttu-id="ab415-113">[out] Tablica wartości COR_IL_MAP, które udostępniają informacje dotyczące mapowania z Instrumentacji profilera IL do IL oryginalnej metody.</span><span class="sxs-lookup"><span data-stu-id="ab415-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab415-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab415-114">Remarks</span></span>  
 <span data-ttu-id="ab415-115">Jeśli profilera ustawia mapowanie przez wywołanie metody [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metody debuger tę metodę można wywołać można pobrać mapowania i mapowanie wewnętrznie do obliczania IL przesunięciami stosu Śledzenie i okresy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ab415-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="ab415-116">Jeśli `cMap` 0 i `pcMap` ma wartość inną niż**null**, `pcMap` wynosi liczba dostępnych wartości COR_IL_MAP.</span><span class="sxs-lookup"><span data-stu-id="ab415-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="ab415-117">Jeśli `cMap` jest różna od zera, reprezentuje pojemność `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ab415-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="ab415-118">Gdy metoda zwróci wartość, `map` może zawierać maksymalnie `cMap` elementów, i `pcMap` jest równa wartości COR_IL_MAP faktycznie zapisane `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ab415-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="ab415-119">Jeśli nie zostały zinstrumentowane IL lub mapowanie nie zostało dostarczone przez profiler, ta metoda zwraca `S_OK` i ustawia `pcMap` na 0.</span><span class="sxs-lookup"><span data-stu-id="ab415-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab415-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab415-120">Requirements</span></span>  
 <span data-ttu-id="ab415-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab415-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab415-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab415-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab415-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab415-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab415-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab415-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab415-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab415-125">See Also</span></span>  
 [<span data-ttu-id="ab415-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="ab415-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)  
 [<span data-ttu-id="ab415-127">ICorDebugILCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab415-127">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [<span data-ttu-id="ab415-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ab415-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
