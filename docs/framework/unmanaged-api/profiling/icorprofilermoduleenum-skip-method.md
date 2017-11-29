---
title: "ICorProfilerModuleEnum::Skip — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Skip Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7331c5221de1dc1bfdbbce77f8c40f4fbc95aea2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="7e163-102">ICorProfilerModuleEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e163-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="7e163-103">Przesuwa kursor modułu wyliczającego z jego bieżącym położeniu tak, aby określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="7e163-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e163-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e163-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e163-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e163-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7e163-106">[in] Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="7e163-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e163-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7e163-107">Return Value</span></span>  
 <span data-ttu-id="7e163-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="7e163-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7e163-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e163-109">HRESULT</span></span>|<span data-ttu-id="7e163-110">Opis</span><span class="sxs-lookup"><span data-stu-id="7e163-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e163-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e163-111">S_OK</span></span>|<span data-ttu-id="7e163-112">`celt`elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="7e163-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="7e163-113">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7e163-113">S_FALSE</span></span>|<span data-ttu-id="7e163-114">Mniej niż `celt` elementy zostały pominięte, co oznacza, że nie ma żadnych więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="7e163-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e163-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e163-115">Remarks</span></span>  
 <span data-ttu-id="7e163-116">Nowa pozycja kursora ten moduł wyliczający jest (bieżące położenie) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="7e163-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e163-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e163-117">Requirements</span></span>  
 <span data-ttu-id="7e163-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e163-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e163-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e163-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e163-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e163-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e163-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e163-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e163-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e163-122">See Also</span></span>  
 [<span data-ttu-id="7e163-123">ICorProfilerModuleEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="7e163-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="7e163-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="7e163-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
