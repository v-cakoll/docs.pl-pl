---
title: ICorProfilerThreadEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a014a4e06464f461af25103037b349b2f18a2a5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488711"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="76f36-102">ICorProfilerThreadEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="76f36-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="76f36-103">Pobiera określoną liczbę wątków sąsiadujących z sekwencyjną kolekcją wątków, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="76f36-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f36-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76f36-104">Syntax</span></span>  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76f36-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76f36-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="76f36-106">[in] Liczba wątków do pobierania.</span><span class="sxs-lookup"><span data-stu-id="76f36-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="76f36-107">[out] Tablica `ThreadID` wartości, z których każdy reprezentuje pobrane wątku.</span><span class="sxs-lookup"><span data-stu-id="76f36-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="76f36-108">[out] Wskaźnik do liczby wątków rzeczywistego zwrotu w `ids` tablicy.</span><span class="sxs-lookup"><span data-stu-id="76f36-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76f36-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="76f36-109">Return Value</span></span>  
 <span data-ttu-id="76f36-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="76f36-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="76f36-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76f36-111">HRESULT</span></span>|<span data-ttu-id="76f36-112">Opis</span><span class="sxs-lookup"><span data-stu-id="76f36-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76f36-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="76f36-113">S_OK</span></span>|<span data-ttu-id="76f36-114">`celt` elementy zostały zwrócone.</span><span class="sxs-lookup"><span data-stu-id="76f36-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="76f36-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="76f36-115">S_FALSE</span></span>|<span data-ttu-id="76f36-116">Mniej niż `celt` zwróconych elementów, co oznacza, że wyliczanie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="76f36-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76f36-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76f36-117">Requirements</span></span>  
 <span data-ttu-id="76f36-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76f36-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76f36-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="76f36-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76f36-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76f36-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76f36-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76f36-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f36-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76f36-122">See also</span></span>
- [<span data-ttu-id="76f36-123">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="76f36-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="76f36-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="76f36-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
