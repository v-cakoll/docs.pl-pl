---
title: ICorProfilerModuleEnum::Skip — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 35256a25ed793ffee6ddc1b26088e0988fea5af2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454349"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="52cda-102">ICorProfilerModuleEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="52cda-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="52cda-103">Przesuwa kursor modułu wyliczającego z jego bieżącym położeniu tak, aby określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="52cda-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52cda-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52cda-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52cda-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52cda-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="52cda-106">[in] Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="52cda-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52cda-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="52cda-107">Return Value</span></span>  
 <span data-ttu-id="52cda-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="52cda-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="52cda-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52cda-109">HRESULT</span></span>|<span data-ttu-id="52cda-110">Opis</span><span class="sxs-lookup"><span data-stu-id="52cda-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52cda-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="52cda-111">S_OK</span></span>|<span data-ttu-id="52cda-112">`celt` elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="52cda-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="52cda-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="52cda-113">S_FALSE</span></span>|<span data-ttu-id="52cda-114">Mniej niż `celt` elementy zostały pominięte, co oznacza, że nie ma żadnych więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="52cda-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52cda-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52cda-115">Remarks</span></span>  
 <span data-ttu-id="52cda-116">Nowa pozycja kursora ten moduł wyliczający jest (bieżące położenie) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="52cda-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52cda-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52cda-117">Requirements</span></span>  
 <span data-ttu-id="52cda-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52cda-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52cda-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52cda-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52cda-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52cda-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52cda-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52cda-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cda-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52cda-122">See Also</span></span>  
 [<span data-ttu-id="52cda-123">ICorProfilerModuleEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="52cda-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="52cda-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="52cda-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
