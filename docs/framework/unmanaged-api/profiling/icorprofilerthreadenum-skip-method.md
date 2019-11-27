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
ms.openlocfilehash: aaa8eaa2c4eb927a817425611f71e51c9f3d37af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447575"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="a2612-102">ICorProfilerThreadEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2612-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="a2612-103">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, aby pominąć określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="a2612-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2612-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2612-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2612-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2612-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a2612-106">podczas Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="a2612-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2612-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="a2612-107">Return Value</span></span>  
 <span data-ttu-id="a2612-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="a2612-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a2612-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2612-109">HRESULT</span></span>|<span data-ttu-id="a2612-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a2612-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2612-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2612-111">S_OK</span></span>|<span data-ttu-id="a2612-112">elementy `celt` zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="a2612-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="a2612-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a2612-113">S_FALSE</span></span>|<span data-ttu-id="a2612-114">Pominięto mniej niż `celt` elementów, co oznacza, że nie ma więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="a2612-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2612-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2612-115">Remarks</span></span>  
 <span data-ttu-id="a2612-116">Nowa pozycja kursora tego modułu wyliczającego to (bieżące położenie) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="a2612-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2612-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2612-117">Requirements</span></span>  
 <span data-ttu-id="a2612-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2612-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2612-119">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a2612-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a2612-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a2612-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2612-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2612-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2612-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2612-122">See also</span></span>

- [<span data-ttu-id="a2612-123">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2612-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="a2612-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a2612-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
