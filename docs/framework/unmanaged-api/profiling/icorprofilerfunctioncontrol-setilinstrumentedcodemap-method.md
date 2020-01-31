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
ms.openlocfilehash: b2fca16b3b859df8bd7409149eb5a3cf7b011c5c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864586"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="a1bf1-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1bf1-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="a1bf1-103">Ustawia mapę kodu dla określonej funkcji przy użyciu określonych wpisów mapy typowego języka pośredniego (CIL).</span><span class="sxs-lookup"><span data-stu-id="a1bf1-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1bf1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1bf1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1bf1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1bf1-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="a1bf1-106">podczas Liczba wpisów w mapie.</span><span class="sxs-lookup"><span data-stu-id="a1bf1-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="a1bf1-107">podczas Przypisana przez wywołujący tablica wpisów COR_IL_MAP.</span><span class="sxs-lookup"><span data-stu-id="a1bf1-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="a1bf1-108">Interpretacja tych wpisów jest taka sama jak w przypadku metody [ICorProfilerInfo:: SetILInstrumentedCodeMap —](icorprofilerinfo-setilinstrumentedcodemap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a1bf1-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1bf1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1bf1-109">Remarks</span></span>  
 <span data-ttu-id="a1bf1-110">Ustawienie mapowania przez wywołanie tej metody pozwala debugerowi pobrać mapowanie przez wywołanie [ICorDebugILCode2:: GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="a1bf1-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="a1bf1-111">Umożliwia również debugerowi używanie mapowania wewnętrznie podczas obliczania przesunięć IL dla śladów stosu i zmiennych okresów istnienia.</span><span class="sxs-lookup"><span data-stu-id="a1bf1-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1bf1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1bf1-112">Requirements</span></span>  
 <span data-ttu-id="a1bf1-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1bf1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1bf1-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a1bf1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1bf1-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a1bf1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1bf1-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1bf1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1bf1-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1bf1-117">See also</span></span>

- [<span data-ttu-id="a1bf1-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1bf1-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
