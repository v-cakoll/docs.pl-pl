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
ms.openlocfilehash: ed01b2f59c46d1dcedd62846ea663c9aa7213b37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="88121-102">ICorProfilerThreadEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="88121-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="88121-103">Pobiera określoną liczbę wątków ciągłe z sekwencyjną kolekcją wątków, zaczynając od modułu wyliczającego bieżącej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="88121-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88121-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88121-104">Syntax</span></span>  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88121-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88121-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="88121-106">[in] Liczba wątków do pobierania.</span><span class="sxs-lookup"><span data-stu-id="88121-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="88121-107">[out] Tablica `ThreadID` wartości, z których każdy reprezentuje pobrane wątku.</span><span class="sxs-lookup"><span data-stu-id="88121-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="88121-108">[out] Wskaźnik do liczby wątków faktycznie zwracane w `ids` tablicy.</span><span class="sxs-lookup"><span data-stu-id="88121-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88121-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="88121-109">Return Value</span></span>  
 <span data-ttu-id="88121-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="88121-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="88121-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88121-111">HRESULT</span></span>|<span data-ttu-id="88121-112">Opis</span><span class="sxs-lookup"><span data-stu-id="88121-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88121-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="88121-113">S_OK</span></span>|<span data-ttu-id="88121-114">`celt` elementy zostały zwrócone.</span><span class="sxs-lookup"><span data-stu-id="88121-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="88121-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="88121-115">S_FALSE</span></span>|<span data-ttu-id="88121-116">Mniej niż `celt` elementy zostały zwrócone, co oznacza, że wyliczenia została zakończona.</span><span class="sxs-lookup"><span data-stu-id="88121-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88121-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88121-117">Requirements</span></span>  
 <span data-ttu-id="88121-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88121-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88121-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="88121-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="88121-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88121-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88121-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88121-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88121-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88121-122">See Also</span></span>  
 [<span data-ttu-id="88121-123">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="88121-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="88121-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="88121-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
