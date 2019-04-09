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
ms.openlocfilehash: 397e8afcc176bcd9733e83dc6425fe49f385931e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078205"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="20880-102">ICorProfilerModuleEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="20880-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="20880-103">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, tak, aby określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="20880-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20880-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20880-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20880-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20880-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="20880-106">[in] Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="20880-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20880-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="20880-107">Return Value</span></span>  
 <span data-ttu-id="20880-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="20880-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="20880-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20880-109">HRESULT</span></span>|<span data-ttu-id="20880-110">Opis</span><span class="sxs-lookup"><span data-stu-id="20880-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20880-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="20880-111">S_OK</span></span>|`celt` <span data-ttu-id="20880-112">elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="20880-112">elements were skipped.</span></span>|  
|<span data-ttu-id="20880-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="20880-113">S_FALSE</span></span>|<span data-ttu-id="20880-114">Mniej niż `celt` elementy zostały pominięte, co oznacza, że nie istnieją żadne więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="20880-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20880-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20880-115">Remarks</span></span>  
 <span data-ttu-id="20880-116">Nowe położenie kursora ten moduł wyliczający jest (bieżącej pozycji) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="20880-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20880-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20880-117">Requirements</span></span>  
 <span data-ttu-id="20880-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20880-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20880-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20880-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20880-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20880-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="20880-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="20880-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="20880-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20880-122">See also</span></span>

- [<span data-ttu-id="20880-123">ICorProfilerModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="20880-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="20880-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="20880-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
