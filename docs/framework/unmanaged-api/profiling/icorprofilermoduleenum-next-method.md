---
title: ICorProfilerModuleEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
ms.openlocfilehash: 7a3ad94a4149d6ebb70e077926771e28d7f82779
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494842"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="01f23-102">ICorProfilerModuleEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="01f23-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="01f23-103">Pobiera określoną liczbę modułów ciągłych z sekwencyjnego zbioru modułów, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="01f23-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01f23-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01f23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01f23-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="01f23-106">podczas Liczba modułów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="01f23-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="01f23-107">określoną Tablica `ModuleID` wartości, z których każdy reprezentuje pobrany moduł.</span><span class="sxs-lookup"><span data-stu-id="01f23-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="01f23-108">określoną Wskaźnik do liczby elementów faktycznie zwracanych w `ids` tablicy.</span><span class="sxs-lookup"><span data-stu-id="01f23-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01f23-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="01f23-109">Return Value</span></span>  
 <span data-ttu-id="01f23-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="01f23-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="01f23-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01f23-111">HRESULT</span></span>|<span data-ttu-id="01f23-112">Opis</span><span class="sxs-lookup"><span data-stu-id="01f23-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01f23-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="01f23-113">S_OK</span></span>|<span data-ttu-id="01f23-114">`celt`elementy zostały zwrócone.</span><span class="sxs-lookup"><span data-stu-id="01f23-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="01f23-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="01f23-115">S_FALSE</span></span>|<span data-ttu-id="01f23-116">`celt`Zwrócono mniej niż elementy, co oznacza, że Wyliczenie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="01f23-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01f23-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01f23-117">Requirements</span></span>  
 <span data-ttu-id="01f23-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01f23-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01f23-119">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="01f23-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01f23-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="01f23-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01f23-121">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f23-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f23-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01f23-122">See also</span></span>

- [<span data-ttu-id="01f23-123">ICorProfilerModuleEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="01f23-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="01f23-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="01f23-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
