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
ms.openlocfilehash: d5b6cab555144c25c5984d74d19d5e81aa1a196d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="c7006-102">ICorProfilerFunctionControl::SetILFunctionBody — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7006-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="c7006-103">Zastępuje treść wspólnego języka pośredniego (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="c7006-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7006-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7006-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7006-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7006-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="c7006-106">[in] Całkowity rozmiar nowego CIL, łącznie z nagłówkiem i wszelkimi strukturami, które pochodzą z treści.</span><span class="sxs-lookup"><span data-stu-id="c7006-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="c7006-107">[in] Wskaźnik do nowego nagłówka CIL.</span><span class="sxs-lookup"><span data-stu-id="c7006-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7006-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c7006-108">Return Value</span></span>  
 <span data-ttu-id="c7006-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c7006-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="c7006-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7006-110">HRESULT</span></span>|<span data-ttu-id="c7006-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c7006-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7006-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7006-112">S_OK</span></span>|<span data-ttu-id="c7006-113">Zamiana powiodła się.</span><span class="sxs-lookup"><span data-stu-id="c7006-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7006-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7006-114">Remarks</span></span>  
 <span data-ttu-id="c7006-115">W odróżnieniu od [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody `SetILFunctionBody` metody zarządza ilość pamięci wymaganej dla nowych treści CIL.</span><span class="sxs-lookup"><span data-stu-id="c7006-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="c7006-116">To oznacza, że treść CIL udostępniane przez profiler nie mają do przydzielenia przy użyciu [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interfejsu lub przypisane do określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="c7006-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="c7006-117">Może być alokowana na dowolnej stercie.</span><span class="sxs-lookup"><span data-stu-id="c7006-117">It can be allocated on any heap.</span></span> <span data-ttu-id="c7006-118">Profiler można zwolnić pamięć używana na potrzeby jej treści CIL po `SetILFunctionBody` zwraca.</span><span class="sxs-lookup"><span data-stu-id="c7006-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7006-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7006-119">Requirements</span></span>  
 <span data-ttu-id="c7006-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7006-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7006-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7006-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7006-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7006-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7006-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7006-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7006-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7006-124">See Also</span></span>  
 [<span data-ttu-id="c7006-125">ICorProfilerFunctionControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7006-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
