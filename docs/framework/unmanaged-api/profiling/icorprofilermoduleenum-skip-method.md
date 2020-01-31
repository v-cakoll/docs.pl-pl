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
ms.openlocfilehash: fb7a2a6d8bac7e9a67a5275694fc07e0f1d469e1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861336"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="43722-102">ICorProfilerModuleEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="43722-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="43722-103">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, tak aby określona liczba elementów została pominięta.</span><span class="sxs-lookup"><span data-stu-id="43722-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43722-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43722-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43722-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43722-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="43722-106">podczas Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="43722-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43722-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="43722-107">Return Value</span></span>  
 <span data-ttu-id="43722-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="43722-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="43722-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43722-109">HRESULT</span></span>|<span data-ttu-id="43722-110">Opis</span><span class="sxs-lookup"><span data-stu-id="43722-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43722-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="43722-111">S_OK</span></span>|<span data-ttu-id="43722-112">elementy `celt` zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="43722-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="43722-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="43722-113">S_FALSE</span></span>|<span data-ttu-id="43722-114">Pominięto mniej niż `celt` elementów, co oznacza, że nie ma więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="43722-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43722-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43722-115">Remarks</span></span>  
 <span data-ttu-id="43722-116">Nowa pozycja kursora tego modułu wyliczającego to (bieżące położenie) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="43722-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43722-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43722-117">Requirements</span></span>  
 <span data-ttu-id="43722-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43722-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43722-119">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="43722-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43722-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="43722-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43722-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43722-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43722-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43722-122">See also</span></span>

- [<span data-ttu-id="43722-123">ICorProfilerModuleEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="43722-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="43722-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="43722-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
