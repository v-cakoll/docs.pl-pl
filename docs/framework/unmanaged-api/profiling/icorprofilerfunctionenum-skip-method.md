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
ms.openlocfilehash: 0f096f76ec47cfe3399e9184eb82bf20040efbbb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503045"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="f94d5-102">ICorProfilerFunctionEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="f94d5-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="f94d5-103">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, tak aby określona liczba elementów została pominięta.</span><span class="sxs-lookup"><span data-stu-id="f94d5-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f94d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f94d5-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f94d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f94d5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f94d5-106">podczas Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="f94d5-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f94d5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f94d5-107">Return Value</span></span>  
 <span data-ttu-id="f94d5-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="f94d5-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f94d5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f94d5-109">HRESULT</span></span>|<span data-ttu-id="f94d5-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f94d5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f94d5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f94d5-111">S_OK</span></span>|<span data-ttu-id="f94d5-112">`celt`elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="f94d5-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="f94d5-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f94d5-113">S_FALSE</span></span>|<span data-ttu-id="f94d5-114">`celt`Pominięto mniej niż elementy, co oznacza, że nie ma więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="f94d5-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f94d5-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f94d5-115">Remarks</span></span>  
 <span data-ttu-id="f94d5-116">Nowa pozycja kursora tego modułu wyliczającego to (bieżąca pozycja) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="f94d5-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f94d5-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f94d5-117">Requirements</span></span>  
 <span data-ttu-id="f94d5-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f94d5-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f94d5-119">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f94d5-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f94d5-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f94d5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f94d5-121">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f94d5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94d5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f94d5-122">See also</span></span>

- [<span data-ttu-id="f94d5-123">ICorProfilerFunctionEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f94d5-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="f94d5-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f94d5-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
