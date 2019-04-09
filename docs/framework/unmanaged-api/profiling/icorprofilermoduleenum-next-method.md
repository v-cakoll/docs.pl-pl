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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57d8279ba9733e6a381d445d50df56b415353a16
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077150"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="b45ae-102">ICorProfilerModuleEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="b45ae-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="b45ae-103">Pobiera określoną liczbę modułów sąsiadujących z sekwencyjną kolekcją modułów, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="b45ae-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b45ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b45ae-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b45ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b45ae-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b45ae-106">[in] Liczba modułów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="b45ae-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="b45ae-107">[out] Tablica `ModuleID` wartości, z których każdy reprezentuje pobrane modułu.</span><span class="sxs-lookup"><span data-stu-id="b45ae-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b45ae-108">[out] Wskaźnik do liczby elementów zwracanych w rzeczywistości w `ids` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b45ae-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b45ae-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b45ae-109">Return Value</span></span>  
 <span data-ttu-id="b45ae-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="b45ae-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b45ae-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b45ae-111">HRESULT</span></span>|<span data-ttu-id="b45ae-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b45ae-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b45ae-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b45ae-113">S_OK</span></span>|`celt` <span data-ttu-id="b45ae-114">elementy zostały zwrócone.</span><span class="sxs-lookup"><span data-stu-id="b45ae-114">elements were returned.</span></span>|  
|<span data-ttu-id="b45ae-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b45ae-115">S_FALSE</span></span>|<span data-ttu-id="b45ae-116">Mniej niż `celt` zwróconych elementów, co oznacza, że wyliczanie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="b45ae-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b45ae-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b45ae-117">Requirements</span></span>  
 <span data-ttu-id="b45ae-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b45ae-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b45ae-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b45ae-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b45ae-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b45ae-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b45ae-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b45ae-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b45ae-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b45ae-122">See also</span></span>

- [<span data-ttu-id="b45ae-123">ICorProfilerModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b45ae-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="b45ae-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="b45ae-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
