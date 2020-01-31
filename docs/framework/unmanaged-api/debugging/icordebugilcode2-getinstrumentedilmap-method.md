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
ms.openlocfilehash: 728a6c83dc321fa28dc4ff84c4e874d886524b36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788569"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="c8ef7-102">Metoda ICorDebugILCode2::GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="c8ef7-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="c8ef7-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="c8ef7-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c8ef7-104">Zwraca mapę z przesunięcia języka pośredniego (IL) instrumentacji do metody oryginalnej dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8ef7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8ef7-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8ef7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8ef7-106">Parameters</span></span>  
 <span data-ttu-id="c8ef7-107">cMap</span><span class="sxs-lookup"><span data-stu-id="c8ef7-107">cMap</span></span>  
 <span data-ttu-id="c8ef7-108">podczas Pojemność magazynu tablicy `map`.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="c8ef7-109">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="c8ef7-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="c8ef7-110">pcMap</span></span>  
 <span data-ttu-id="c8ef7-111">określoną Liczba wartości COR_IL_MAP zapisywana w tablicy map.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="c8ef7-112">map</span><span class="sxs-lookup"><span data-stu-id="c8ef7-112">map</span></span>  
 <span data-ttu-id="c8ef7-113">określoną Tablica wartości COR_IL_MAP, które dostarczają informacji o mapowaniach z Instrumentacji Il do języka IL, w przypadku metody języka, która została oryginalną metodą.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8ef7-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8ef7-114">Remarks</span></span>  
 <span data-ttu-id="c8ef7-115">Jeśli profiler ustawi mapowanie, wywołując metodę [ICorProfilerInfo:: SetILInstrumentedCodeMap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , debuger może wywołać tę metodę, aby pobrać mapowanie i używać mapowania wewnętrznie podczas obliczania przesunięć Il dla śladów stosu i zmiennych okresów istnienia.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="c8ef7-116">Jeśli `cMap` ma wartość 0, a `pcMap` ma**wartość**różną od null, `pcMap` jest ustawiona na liczbę dostępnych wartości COR_IL_MAP.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="c8ef7-117">Jeśli `cMap` jest różna od zera, reprezentuje pojemność magazynu `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="c8ef7-118">Gdy metoda zwraca, `map` zawiera maksymalnie `cMap` elementów, a `pcMap` jest ustawiona na liczbę wartości COR_IL_MAP rzeczywiście zapisywana w tablicy `map`.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="c8ef7-119">Jeśli obiekt IL nie został Instrumentacją lub mapowanie nie zostało dostarczone przez profiler, Metoda ta zwraca `S_OK` i ustawia `pcMap` na 0.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8ef7-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8ef7-120">Requirements</span></span>  
 <span data-ttu-id="c8ef7-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8ef7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8ef7-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c8ef7-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8ef7-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c8ef7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8ef7-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8ef7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ef7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8ef7-125">See also</span></span>

- [<span data-ttu-id="c8ef7-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="c8ef7-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="c8ef7-127">ICorDebugILCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c8ef7-127">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="c8ef7-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c8ef7-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
