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
ms.openlocfilehash: cce96e8c6d046beba9e45c7121bf68444fd51c95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173345"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="b62f0-102">ICorProfilerThreadEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="b62f0-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="b62f0-103">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, aby pominąć określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="b62f0-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b62f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b62f0-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b62f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b62f0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b62f0-106">[in] Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="b62f0-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b62f0-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b62f0-107">Return Value</span></span>  
 <span data-ttu-id="b62f0-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="b62f0-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b62f0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b62f0-109">HRESULT</span></span>|<span data-ttu-id="b62f0-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b62f0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b62f0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b62f0-111">S_OK</span></span>|`celt` <span data-ttu-id="b62f0-112">elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="b62f0-112">elements were skipped.</span></span>|  
|<span data-ttu-id="b62f0-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b62f0-113">S_FALSE</span></span>|<span data-ttu-id="b62f0-114">Mniej niż `celt` elementy zostały pominięte, co oznacza, że nie istnieją żadne więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="b62f0-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b62f0-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b62f0-115">Remarks</span></span>  
 <span data-ttu-id="b62f0-116">Nowe położenie kursora ten moduł wyliczający jest (bieżącej pozycji) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="b62f0-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b62f0-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b62f0-117">Requirements</span></span>  
 <span data-ttu-id="b62f0-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b62f0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b62f0-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b62f0-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b62f0-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b62f0-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b62f0-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b62f0-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b62f0-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b62f0-122">See also</span></span>

- [<span data-ttu-id="b62f0-123">ICorProfilerThreadEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b62f0-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="b62f0-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="b62f0-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
