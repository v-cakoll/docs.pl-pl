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
ms.openlocfilehash: 3f3351c13530b636cb6715c815b81ab4d9306f53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115781"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="c139e-102">ICorProfilerFunctionControl::SetILFunctionBody — Metoda</span><span class="sxs-lookup"><span data-stu-id="c139e-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="c139e-103">Zastępuje treść wspólnego języka pośredniego (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="c139e-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c139e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c139e-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c139e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c139e-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="c139e-106">[in] Całkowity rozmiar nowego CIL, łącznie z nagłówkiem i wszelkimi strukturami, które pochodzą z treści.</span><span class="sxs-lookup"><span data-stu-id="c139e-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="c139e-107">[in] Wskaźnik do nowego nagłówka CIL.</span><span class="sxs-lookup"><span data-stu-id="c139e-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c139e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c139e-108">Return Value</span></span>  
 <span data-ttu-id="c139e-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c139e-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="c139e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c139e-110">HRESULT</span></span>|<span data-ttu-id="c139e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c139e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c139e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c139e-112">S_OK</span></span>|<span data-ttu-id="c139e-113">Zamiana powiodła się.</span><span class="sxs-lookup"><span data-stu-id="c139e-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c139e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c139e-114">Remarks</span></span>  
 <span data-ttu-id="c139e-115">W odróżnieniu od [icorprofilerinfo::setilfunctionbody —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody `SetILFunctionBody` zarządza pamięcią wymaganą dla nowej treści CIL.</span><span class="sxs-lookup"><span data-stu-id="c139e-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="c139e-116">Oznacza to, że treść CIL dostarczona przez profiler musi być alokowana za pomocą [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interfejs lub w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="c139e-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="c139e-117">Może być alokowana na dowolnej stercie.</span><span class="sxs-lookup"><span data-stu-id="c139e-117">It can be allocated on any heap.</span></span> <span data-ttu-id="c139e-118">Profiler można zwolnić pamięć użytą dla tej treści CIL po `SetILFunctionBody` zwraca.</span><span class="sxs-lookup"><span data-stu-id="c139e-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c139e-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c139e-119">Requirements</span></span>  
 <span data-ttu-id="c139e-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c139e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c139e-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c139e-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c139e-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c139e-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c139e-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c139e-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c139e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c139e-124">See also</span></span>

- [<span data-ttu-id="c139e-125">ICorProfilerFunctionControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c139e-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
