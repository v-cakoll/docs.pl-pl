---
title: ICorProfilerFunctionEnum::Skip — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: d2a0bff0d3d93ab8542699cffd3d0ecc032246ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448200"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="c405a-102">ICorProfilerFunctionEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="c405a-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="c405a-103">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, tak aby określona liczba elementów została pominięta.</span><span class="sxs-lookup"><span data-stu-id="c405a-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c405a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c405a-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c405a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c405a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c405a-106">podczas Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="c405a-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c405a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c405a-107">Return Value</span></span>  
 <span data-ttu-id="c405a-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="c405a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c405a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c405a-109">HRESULT</span></span>|<span data-ttu-id="c405a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c405a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c405a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c405a-111">S_OK</span></span>|<span data-ttu-id="c405a-112">elementy `celt` zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="c405a-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="c405a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c405a-113">S_FALSE</span></span>|<span data-ttu-id="c405a-114">Pominięto mniej niż `celt` elementów, co oznacza, że nie ma więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="c405a-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c405a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c405a-115">Remarks</span></span>  
 <span data-ttu-id="c405a-116">Nowa pozycja kursora tego modułu wyliczającego to (bieżące położenie) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="c405a-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c405a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c405a-117">Requirements</span></span>  
 <span data-ttu-id="c405a-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c405a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c405a-119">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c405a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c405a-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c405a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c405a-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c405a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c405a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c405a-122">See also</span></span>

- [<span data-ttu-id="c405a-123">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="c405a-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="c405a-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c405a-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
