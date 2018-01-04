---
title: "ICorProfilerFunctionControl::SetILInstrumentedCodeMap — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 580d60fe0a6348a163fef9e215cddfc1bc4302b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="40ae4-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="40ae4-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="40ae4-103">Ustawia mapę kodu dla funkcji określonej przy użyciu określonego wpisów map wspólnego języka pośredniego (CIL).</span><span class="sxs-lookup"><span data-stu-id="40ae4-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40ae4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40ae4-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40ae4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40ae4-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="40ae4-106">[in] Liczba wpisów w planie.</span><span class="sxs-lookup"><span data-stu-id="40ae4-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="40ae4-107">[in] Tablica przydzielone przez obiekt wywołujący COR_IL_MAP wpisów.</span><span class="sxs-lookup"><span data-stu-id="40ae4-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="40ae4-108">Interpretacja te wpisy są takie same jak w przypadku [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="40ae4-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40ae4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40ae4-109">Remarks</span></span>  
 <span data-ttu-id="40ae4-110">Ustawienie mapowanie przez wywołanie tej metody umożliwia debugera tak, aby pobrać mapowanie przez wywołanie metody [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="40ae4-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="40ae4-111">Umożliwia także debugera używać mapowania wewnętrznie podczas obliczania IL przesunięciami śladów stosu i okresy istnienia zmiennej.</span><span class="sxs-lookup"><span data-stu-id="40ae4-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40ae4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40ae4-112">Requirements</span></span>  
 <span data-ttu-id="40ae4-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40ae4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40ae4-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="40ae4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40ae4-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40ae4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40ae4-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40ae4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ae4-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40ae4-117">See Also</span></span>  
 [<span data-ttu-id="40ae4-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="40ae4-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
