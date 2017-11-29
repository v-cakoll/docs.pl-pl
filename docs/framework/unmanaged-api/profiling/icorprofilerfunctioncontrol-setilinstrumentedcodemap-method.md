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
ms.openlocfilehash: f7f97a383cf6769d4449e7a5f6be8d31fe6e3b51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="348cf-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="348cf-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="348cf-103">Ustawia mapę kodu dla funkcji określonej przy użyciu określonego wpisów map wspólnego języka pośredniego (CIL).</span><span class="sxs-lookup"><span data-stu-id="348cf-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="348cf-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="348cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="348cf-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="348cf-106">[in] Liczba wpisów w planie.</span><span class="sxs-lookup"><span data-stu-id="348cf-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="348cf-107">[in] Tablica przydzielone przez obiekt wywołujący COR_IL_MAP wpisów.</span><span class="sxs-lookup"><span data-stu-id="348cf-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="348cf-108">Interpretacja te wpisy są takie same jak w przypadku [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="348cf-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="348cf-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="348cf-109">Remarks</span></span>  
 <span data-ttu-id="348cf-110">Ustawienie mapowanie przez wywołanie tej metody umożliwia debugera tak, aby pobrać mapowanie przez wywołanie metody [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="348cf-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="348cf-111">Umożliwia także debugera używać mapowania wewnętrznie podczas obliczania IL przesunięciami śladów stosu i okresy istnienia zmiennej.</span><span class="sxs-lookup"><span data-stu-id="348cf-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="348cf-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="348cf-112">Requirements</span></span>  
 <span data-ttu-id="348cf-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="348cf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="348cf-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="348cf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="348cf-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="348cf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="348cf-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="348cf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348cf-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="348cf-117">See Also</span></span>  
 [<span data-ttu-id="348cf-118">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="348cf-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
