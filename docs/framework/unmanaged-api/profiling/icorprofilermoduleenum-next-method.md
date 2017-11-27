---
title: "ICorProfilerModuleEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Next Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c20b6970c0df30b75bacf76f52c7610bd4a3a5e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="83724-102">ICorProfilerModuleEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="83724-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="83724-103">Pobiera określoną liczbę modułów ciągłe z sekwencyjną kolekcją modułów, zaczynając od modułu wyliczającego bieżącej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="83724-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83724-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83724-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83724-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83724-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="83724-106">[in] Liczba modułów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="83724-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="83724-107">[out] Tablica `ModuleID` wartości, z których każdy reprezentuje pobrane modułu.</span><span class="sxs-lookup"><span data-stu-id="83724-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="83724-108">[out] Wskaźnik do liczby elementów faktycznie zwracane w `ids` tablicy.</span><span class="sxs-lookup"><span data-stu-id="83724-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83724-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="83724-109">Return Value</span></span>  
 <span data-ttu-id="83724-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="83724-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="83724-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83724-111">HRESULT</span></span>|<span data-ttu-id="83724-112">Opis</span><span class="sxs-lookup"><span data-stu-id="83724-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83724-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="83724-113">S_OK</span></span>|<span data-ttu-id="83724-114">`celt`elementy zostały zwrócone.</span><span class="sxs-lookup"><span data-stu-id="83724-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="83724-115">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="83724-115">S_FALSE</span></span>|<span data-ttu-id="83724-116">Mniej niż `celt` elementy zostały zwrócone, co oznacza, że wyliczenia została zakończona.</span><span class="sxs-lookup"><span data-stu-id="83724-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83724-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83724-117">Requirements</span></span>  
 <span data-ttu-id="83724-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83724-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83724-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83724-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83724-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83724-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83724-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83724-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83724-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83724-122">See Also</span></span>  
 [<span data-ttu-id="83724-123">ICorProfilerModuleEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="83724-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="83724-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="83724-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
