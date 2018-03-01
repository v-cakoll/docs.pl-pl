---
title: "ICorProfilerFunctionEnum::Skip — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ddde6069072092cfc0441686ce4d53aa0a4bd534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="c2d2b-102">ICorProfilerFunctionEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2d2b-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="c2d2b-103">Przesuwa kursor modułu wyliczającego z jego bieżącym położeniu tak, aby określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d2b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2d2b-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2d2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2d2b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c2d2b-106">[in] Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2d2b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c2d2b-107">Return Value</span></span>  
 <span data-ttu-id="c2d2b-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c2d2b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2d2b-109">HRESULT</span></span>|<span data-ttu-id="c2d2b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c2d2b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2d2b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2d2b-111">S_OK</span></span>|<span data-ttu-id="c2d2b-112">`celt`elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="c2d2b-113">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c2d2b-113">S_FALSE</span></span>|<span data-ttu-id="c2d2b-114">Mniej niż `celt` elementy zostały pominięte, co oznacza, że nie ma żadnych więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2d2b-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2d2b-115">Remarks</span></span>  
 <span data-ttu-id="c2d2b-116">Nowa pozycja kursora ten moduł wyliczający jest (bieżące położenie) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d2b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2d2b-117">Requirements</span></span>  
 <span data-ttu-id="c2d2b-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d2b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d2b-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2d2b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2d2b-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2d2b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2d2b-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d2b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d2b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2d2b-122">See Also</span></span>  
 [<span data-ttu-id="c2d2b-123">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2d2b-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="c2d2b-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c2d2b-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
