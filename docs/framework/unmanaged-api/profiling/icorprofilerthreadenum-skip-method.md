---
title: ICorProfilerThreadEnum::Skip — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af6aab2483f0e92dc20936fe2b01e12590d99ca7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455373"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="ec452-102">ICorProfilerThreadEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec452-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="ec452-103">Przesuwa kursor modułu wyliczającego z bieżącej pozycji do pominięcia określonej liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="ec452-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec452-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec452-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec452-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec452-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ec452-106">[in] Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="ec452-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec452-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ec452-107">Return Value</span></span>  
 <span data-ttu-id="ec452-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="ec452-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ec452-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec452-109">HRESULT</span></span>|<span data-ttu-id="ec452-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ec452-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec452-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec452-111">S_OK</span></span>|<span data-ttu-id="ec452-112">`celt` elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="ec452-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="ec452-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ec452-113">S_FALSE</span></span>|<span data-ttu-id="ec452-114">Mniej niż `celt` elementy zostały pominięte, co oznacza, że nie ma żadnych więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="ec452-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec452-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec452-115">Remarks</span></span>  
 <span data-ttu-id="ec452-116">Nowa pozycja kursora ten moduł wyliczający jest (bieżące położenie) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="ec452-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec452-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec452-117">Requirements</span></span>  
 <span data-ttu-id="ec452-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec452-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec452-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec452-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec452-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec452-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec452-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec452-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec452-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec452-122">See Also</span></span>  
 [<span data-ttu-id="ec452-123">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec452-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="ec452-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="ec452-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
