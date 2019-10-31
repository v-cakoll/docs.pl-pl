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
ms.openlocfilehash: 7dede4e5af702f1b86b430450db4a669c326c062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131064"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="97a05-102">Metoda ICorDebugILCode2::GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="97a05-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="97a05-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="97a05-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="97a05-104">Zwraca mapę z przesunięcia języka pośredniego (IL) instrumentacji do metody oryginalnej dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="97a05-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97a05-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="97a05-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97a05-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97a05-106">Parameters</span></span>  
 <span data-ttu-id="97a05-107">cMap</span><span class="sxs-lookup"><span data-stu-id="97a05-107">cMap</span></span>  
 <span data-ttu-id="97a05-108">podczas Pojemność magazynu tablicy `map`.</span><span class="sxs-lookup"><span data-stu-id="97a05-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="97a05-109">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="97a05-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="97a05-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="97a05-110">pcMap</span></span>  
 <span data-ttu-id="97a05-111">określoną Liczba wartości COR_IL_MAP zapisywana w tablicy map.</span><span class="sxs-lookup"><span data-stu-id="97a05-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="97a05-112">map</span><span class="sxs-lookup"><span data-stu-id="97a05-112">map</span></span>  
 <span data-ttu-id="97a05-113">określoną Tablica wartości COR_IL_MAP, które dostarczają informacji o mapowaniach z Instrumentacji IL do języka IL, do metodyki, którą można wykonać przy użyciu narzędzia.</span><span class="sxs-lookup"><span data-stu-id="97a05-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97a05-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97a05-114">Remarks</span></span>  
 <span data-ttu-id="97a05-115">Jeśli profiler ustawi mapowanie przez wywołanie metody [ICorProfilerInfo:: SetILInstrumentedCodeMap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , debuger może wywołać tę metodę, aby pobrać mapowanie i używać mapowania wewnętrznie podczas obliczania przesunięć Il dla śladów stosu i zmiennej okresy istnienia.</span><span class="sxs-lookup"><span data-stu-id="97a05-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="97a05-116">Jeśli `cMap` ma wartość 0, a `pcMap` ma**wartość**różną od null, `pcMap` jest ustawiona na liczbę dostępnych wartości COR_IL_MAP.</span><span class="sxs-lookup"><span data-stu-id="97a05-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="97a05-117">Jeśli `cMap` jest różna od zera, reprezentuje pojemność magazynu `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="97a05-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="97a05-118">Gdy metoda zwraca, `map` zawiera maksymalnie `cMap` elementów, a `pcMap` jest ustawiona na liczbę COR_IL_MAP wartości rzeczywiście zapisywana w tablicy `map`.</span><span class="sxs-lookup"><span data-stu-id="97a05-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="97a05-119">Jeśli obiekt IL nie został Instrumentacją lub mapowanie nie zostało dostarczone przez profiler, Metoda ta zwraca `S_OK` i ustawia `pcMap` na 0.</span><span class="sxs-lookup"><span data-stu-id="97a05-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97a05-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97a05-120">Requirements</span></span>  
 <span data-ttu-id="97a05-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97a05-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97a05-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97a05-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97a05-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="97a05-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97a05-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97a05-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a05-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97a05-125">See also</span></span>

- [<span data-ttu-id="97a05-126">ICorProfilerInfo:: SetILInstrumentedCodeMap —</span><span class="sxs-lookup"><span data-stu-id="97a05-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="97a05-127">ICorDebugILCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="97a05-127">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="97a05-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="97a05-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
