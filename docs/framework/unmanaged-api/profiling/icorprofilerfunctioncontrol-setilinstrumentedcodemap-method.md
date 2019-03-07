---
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 328702b48de8f3c471783743fb84a271f608a97a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477130"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="bb982-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb982-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="bb982-103">Ustawia mapę kodu dla określonej funkcji przy użyciu określonego wpisy mapy wspólny język pośredni (CIL).</span><span class="sxs-lookup"><span data-stu-id="bb982-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb982-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb982-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb982-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb982-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="bb982-106">[in] Liczba wpisów w mapie.</span><span class="sxs-lookup"><span data-stu-id="bb982-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="bb982-107">[in] Tablica przydzielana przez obiekt wywołujący cor_il_map — wpisy.</span><span class="sxs-lookup"><span data-stu-id="bb982-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="bb982-108">Interpretacja te wpisy są takie same jak w przypadku [icorprofilerinfo::setilinstrumentedcodemap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="bb982-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb982-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb982-109">Remarks</span></span>  
 <span data-ttu-id="bb982-110">Ustawienie mapowanie przez wywołanie tej metody umożliwia debugerowi, aby pobrać mapowanie przez wywołanie metody [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="bb982-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="bb982-111">Umożliwia także debugera do użycia mapowanie wewnętrznie, podczas obliczania IL rekompensaty w przypadku ślady stosu i okresy istnienia zmiennych.</span><span class="sxs-lookup"><span data-stu-id="bb982-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb982-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb982-112">Requirements</span></span>  
 <span data-ttu-id="bb982-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb982-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb982-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb982-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb982-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb982-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb982-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb982-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb982-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb982-117">See also</span></span>
- [<span data-ttu-id="bb982-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb982-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
