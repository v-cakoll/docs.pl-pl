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
ms.openlocfilehash: 11ce2fdccbf24fd688376cc3256f6db79a7cc352
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447852"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="e1655-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1655-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="e1655-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span><span class="sxs-lookup"><span data-stu-id="e1655-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1655-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1655-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1655-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1655-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="e1655-106">[in] The number of entries in the map.</span><span class="sxs-lookup"><span data-stu-id="e1655-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="e1655-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span><span class="sxs-lookup"><span data-stu-id="e1655-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="e1655-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="e1655-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1655-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1655-109">Remarks</span></span>  
 <span data-ttu-id="e1655-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="e1655-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="e1655-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span><span class="sxs-lookup"><span data-stu-id="e1655-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1655-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1655-112">Requirements</span></span>  
 <span data-ttu-id="e1655-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1655-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1655-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1655-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1655-115">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1655-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1655-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1655-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1655-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1655-117">See also</span></span>

- [<span data-ttu-id="e1655-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1655-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
