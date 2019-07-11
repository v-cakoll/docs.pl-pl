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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d831dd7a63c06327bb0f373b3be254401c6e2ee9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780352"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="badc2-102">ICorProfilerFunctionControl::SetILFunctionBody — Metoda</span><span class="sxs-lookup"><span data-stu-id="badc2-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="badc2-103">Zastępuje treść wspólnego języka pośredniego (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="badc2-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="badc2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="badc2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="badc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="badc2-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="badc2-106">[in] Całkowity rozmiar nowego CIL, łącznie z nagłówkiem i wszelkimi strukturami, które pochodzą z treści.</span><span class="sxs-lookup"><span data-stu-id="badc2-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="badc2-107">[in] Wskaźnik do nowego nagłówka CIL.</span><span class="sxs-lookup"><span data-stu-id="badc2-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="badc2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="badc2-108">Return Value</span></span>  
 <span data-ttu-id="badc2-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="badc2-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="badc2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="badc2-110">HRESULT</span></span>|<span data-ttu-id="badc2-111">Opis</span><span class="sxs-lookup"><span data-stu-id="badc2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="badc2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="badc2-112">S_OK</span></span>|<span data-ttu-id="badc2-113">Zamiana powiodła się.</span><span class="sxs-lookup"><span data-stu-id="badc2-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="badc2-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="badc2-114">Remarks</span></span>  
 <span data-ttu-id="badc2-115">W odróżnieniu od [icorprofilerinfo::setilfunctionbody —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody `SetILFunctionBody` zarządza pamięcią wymaganą dla nowej treści CIL.</span><span class="sxs-lookup"><span data-stu-id="badc2-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="badc2-116">Oznacza to, że treść CIL dostarczona przez profiler musi być alokowana za pomocą [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interfejs lub w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="badc2-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="badc2-117">Może być alokowana na dowolnej stercie.</span><span class="sxs-lookup"><span data-stu-id="badc2-117">It can be allocated on any heap.</span></span> <span data-ttu-id="badc2-118">Profiler można zwolnić pamięć użytą dla tej treści CIL po `SetILFunctionBody` zwraca.</span><span class="sxs-lookup"><span data-stu-id="badc2-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="badc2-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="badc2-119">Requirements</span></span>  
 <span data-ttu-id="badc2-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="badc2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="badc2-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="badc2-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="badc2-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="badc2-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="badc2-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="badc2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="badc2-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="badc2-124">See also</span></span>

- [<span data-ttu-id="badc2-125">ICorProfilerFunctionControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="badc2-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
