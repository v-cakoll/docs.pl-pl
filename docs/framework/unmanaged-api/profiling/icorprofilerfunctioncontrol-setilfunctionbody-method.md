---
title: ICorProfilerFunctionControl::SetILFunctionBody — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: f6e2cfe47bdd212e39549544b06bf5b11033a956
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429886"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="5e182-102">ICorProfilerFunctionControl::SetILFunctionBody — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e182-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="5e182-103">Zastępuje treść wspólnego języka pośredniego (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="5e182-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e182-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e182-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e182-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e182-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="5e182-106">[in] Całkowity rozmiar nowego CIL, łącznie z nagłówkiem i wszelkimi strukturami, które pochodzą z treści.</span><span class="sxs-lookup"><span data-stu-id="5e182-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="5e182-107">[in] Wskaźnik do nowego nagłówka CIL.</span><span class="sxs-lookup"><span data-stu-id="5e182-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e182-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5e182-108">Return Value</span></span>  
 <span data-ttu-id="5e182-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5e182-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="5e182-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e182-110">HRESULT</span></span>|<span data-ttu-id="5e182-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5e182-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e182-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e182-112">S_OK</span></span>|<span data-ttu-id="5e182-113">Zamiana powiodła się.</span><span class="sxs-lookup"><span data-stu-id="5e182-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e182-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e182-114">Remarks</span></span>  
 <span data-ttu-id="5e182-115">W przeciwieństwie do metody [ICorProfilerInfo:: SetILFunctionBody —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) Metoda `SetILFunctionBody` zarządza pamięcią wymaganą dla nowej treści CIL.</span><span class="sxs-lookup"><span data-stu-id="5e182-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="5e182-116">Oznacza to, że treści CIL dostarczone przez profiler nie muszą być przydzielone za pomocą interfejsu [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) ani przydzielone w ramach określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="5e182-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="5e182-117">Może być alokowana na dowolnej stercie.</span><span class="sxs-lookup"><span data-stu-id="5e182-117">It can be allocated on any heap.</span></span> <span data-ttu-id="5e182-118">Profiler może zwolnić pamięć używaną dla swojej treści CIL po powrocie `SetILFunctionBody`.</span><span class="sxs-lookup"><span data-stu-id="5e182-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e182-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e182-119">Requirements</span></span>  
 <span data-ttu-id="5e182-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e182-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e182-121">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5e182-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e182-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5e182-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e182-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e182-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e182-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e182-124">See also</span></span>

- [<span data-ttu-id="5e182-125">ICorProfilerFunctionControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e182-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
