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
ms.openlocfilehash: 738c98a0a37983faa71ea6e5eeaabb20639f604a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503145"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="f32cd-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="f32cd-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="f32cd-103">Ustawia mapę kodu dla określonej funkcji przy użyciu określonych wpisów mapy typowego języka pośredniego (CIL).</span><span class="sxs-lookup"><span data-stu-id="f32cd-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f32cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f32cd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f32cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f32cd-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="f32cd-106">podczas Liczba wpisów w mapie.</span><span class="sxs-lookup"><span data-stu-id="f32cd-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="f32cd-107">podczas Przypisana przez wywołujący tablica wpisów COR_IL_MAP.</span><span class="sxs-lookup"><span data-stu-id="f32cd-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="f32cd-108">Interpretacja tych wpisów jest taka sama jak w przypadku metody [ICorProfilerInfo:: SetILInstrumentedCodeMap —](icorprofilerinfo-setilinstrumentedcodemap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f32cd-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f32cd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f32cd-109">Remarks</span></span>  
 <span data-ttu-id="f32cd-110">Ustawienie mapowania przez wywołanie tej metody pozwala debugerowi pobrać mapowanie przez wywołanie [ICorDebugILCode2:: GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="f32cd-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="f32cd-111">Umożliwia również debugerowi używanie mapowania wewnętrznie podczas obliczania przesunięć IL dla śladów stosu i zmiennych okresów istnienia.</span><span class="sxs-lookup"><span data-stu-id="f32cd-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f32cd-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f32cd-112">Requirements</span></span>  
 <span data-ttu-id="f32cd-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f32cd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f32cd-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f32cd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f32cd-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f32cd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f32cd-116">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f32cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f32cd-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f32cd-117">See also</span></span>

- [<span data-ttu-id="f32cd-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="f32cd-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
