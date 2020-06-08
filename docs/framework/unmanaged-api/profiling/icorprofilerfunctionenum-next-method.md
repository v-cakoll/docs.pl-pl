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
ms.openlocfilehash: df62ad1af0ea91783cb62bb0590b6e36d812de3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503071"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="743ca-102">ICorProfilerFunctionEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="743ca-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="743ca-103">Pobiera określoną liczbę funkcji ciągłych z sekwencyjnego zbioru funkcji, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="743ca-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="743ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="743ca-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="743ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="743ca-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="743ca-106">podczas Liczba funkcji do pobrania.</span><span class="sxs-lookup"><span data-stu-id="743ca-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="743ca-107">określoną Tablica `COR_PRF_FUNCTION` wartości, z których każdy reprezentuje pobraną funkcję.</span><span class="sxs-lookup"><span data-stu-id="743ca-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="743ca-108">określoną Wskaźnik do liczby funkcji faktycznie zwracanych w `ids` tablicy.</span><span class="sxs-lookup"><span data-stu-id="743ca-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="743ca-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="743ca-109">Return Value</span></span>  
 <span data-ttu-id="743ca-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="743ca-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="743ca-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="743ca-111">HRESULT</span></span>|<span data-ttu-id="743ca-112">Opis</span><span class="sxs-lookup"><span data-stu-id="743ca-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="743ca-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="743ca-113">S_OK</span></span>|<span data-ttu-id="743ca-114">`celt`elementy zostały zwrócone.</span><span class="sxs-lookup"><span data-stu-id="743ca-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="743ca-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="743ca-115">S_FALSE</span></span>|<span data-ttu-id="743ca-116">`celt`Zwrócono mniej niż elementy, co oznacza, że Wyliczenie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="743ca-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="743ca-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="743ca-117">Requirements</span></span>  
 <span data-ttu-id="743ca-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="743ca-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="743ca-119">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="743ca-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="743ca-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="743ca-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="743ca-121">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="743ca-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="743ca-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="743ca-122">See also</span></span>

- [<span data-ttu-id="743ca-123">ICorProfilerFunctionEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="743ca-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="743ca-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="743ca-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
