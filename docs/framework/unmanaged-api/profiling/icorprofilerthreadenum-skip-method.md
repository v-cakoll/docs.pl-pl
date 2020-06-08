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
ms.openlocfilehash: 4218faf1c324175424ab20305224f7f2fa51bb7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494218"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="9e0bd-102">ICorProfilerThreadEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e0bd-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="9e0bd-103">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, aby pominąć określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="9e0bd-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e0bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e0bd-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e0bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e0bd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9e0bd-106">podczas Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="9e0bd-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e0bd-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9e0bd-107">Return Value</span></span>  
 <span data-ttu-id="9e0bd-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="9e0bd-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9e0bd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e0bd-109">HRESULT</span></span>|<span data-ttu-id="9e0bd-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9e0bd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e0bd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e0bd-111">S_OK</span></span>|<span data-ttu-id="9e0bd-112">`celt`elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="9e0bd-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="9e0bd-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9e0bd-113">S_FALSE</span></span>|<span data-ttu-id="9e0bd-114">`celt`Pominięto mniej niż elementy, co oznacza, że nie ma więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="9e0bd-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e0bd-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e0bd-115">Remarks</span></span>  
 <span data-ttu-id="9e0bd-116">Nowa pozycja kursora tego modułu wyliczającego to (bieżąca pozycja) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="9e0bd-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e0bd-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e0bd-117">Requirements</span></span>  
 <span data-ttu-id="9e0bd-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e0bd-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e0bd-119">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9e0bd-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e0bd-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9e0bd-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e0bd-121">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e0bd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0bd-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e0bd-122">See also</span></span>

- [<span data-ttu-id="9e0bd-123">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e0bd-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="9e0bd-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="9e0bd-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
