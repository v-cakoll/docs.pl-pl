---
title: "ICorProfilerFunctionEnum::Skip — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Skip Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c5142b091ec32c162daaca9c53cb65763bb5ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="a5b86-102">ICorProfilerFunctionEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="a5b86-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="a5b86-103">Przesuwa kursor modułu wyliczającego z jego bieżącym położeniu tak, aby określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="a5b86-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5b86-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5b86-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5b86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5b86-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a5b86-106">[in] Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="a5b86-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5b86-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a5b86-107">Return Value</span></span>  
 <span data-ttu-id="a5b86-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="a5b86-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a5b86-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5b86-109">HRESULT</span></span>|<span data-ttu-id="a5b86-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a5b86-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5b86-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5b86-111">S_OK</span></span>|<span data-ttu-id="a5b86-112">`celt`elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="a5b86-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="a5b86-113">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a5b86-113">S_FALSE</span></span>|<span data-ttu-id="a5b86-114">Mniej niż `celt` elementy zostały pominięte, co oznacza, że nie ma żadnych więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="a5b86-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5b86-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5b86-115">Remarks</span></span>  
 <span data-ttu-id="a5b86-116">Nowa pozycja kursora ten moduł wyliczający jest (bieżące położenie) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="a5b86-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5b86-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5b86-117">Requirements</span></span>  
 <span data-ttu-id="a5b86-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5b86-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5b86-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5b86-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5b86-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5b86-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5b86-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5b86-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b86-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5b86-122">See Also</span></span>  
 [<span data-ttu-id="a5b86-123">ICorProfilerFunctionEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="a5b86-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="a5b86-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a5b86-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
