---
title: ICorProfilerFunctionEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
ms.openlocfilehash: 2ad4494cf3a429020099b4bd9d961341437fcd1e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447787"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="b5a25-102">ICorProfilerFunctionEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="b5a25-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="b5a25-103">Pobiera określoną liczbę funkcji ciągłych z sekwencyjnego zbioru funkcji, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="b5a25-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5a25-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5a25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5a25-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b5a25-106">podczas Liczba funkcji do pobrania.</span><span class="sxs-lookup"><span data-stu-id="b5a25-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="b5a25-107">określoną Tablica wartości `COR_PRF_FUNCTION`, z których każdy reprezentuje pobraną funkcję.</span><span class="sxs-lookup"><span data-stu-id="b5a25-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b5a25-108">określoną Wskaźnik do liczby funkcji faktycznie zwracanych w tablicy `ids`.</span><span class="sxs-lookup"><span data-stu-id="b5a25-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5a25-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b5a25-109">Return Value</span></span>  
 <span data-ttu-id="b5a25-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="b5a25-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b5a25-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5a25-111">HRESULT</span></span>|<span data-ttu-id="b5a25-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b5a25-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5a25-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5a25-113">S_OK</span></span>|<span data-ttu-id="b5a25-114">zwrócono `celt` elementów.</span><span class="sxs-lookup"><span data-stu-id="b5a25-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="b5a25-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b5a25-115">S_FALSE</span></span>|<span data-ttu-id="b5a25-116">Zwrócono mniej niż `celt` elementów, co oznacza, że Wyliczenie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="b5a25-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5a25-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5a25-117">Requirements</span></span>  
 <span data-ttu-id="b5a25-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5a25-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5a25-119">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b5a25-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5a25-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b5a25-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5a25-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5a25-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a25-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5a25-122">See also</span></span>

- [<span data-ttu-id="b5a25-123">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b5a25-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="b5a25-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="b5a25-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
