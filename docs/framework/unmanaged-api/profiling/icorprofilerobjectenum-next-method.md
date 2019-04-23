---
title: ICorProfilerObjectEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 221752b537cd3a890ad646290a64a7022692f625
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173943"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="24b9f-102">ICorProfilerObjectEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="24b9f-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="24b9f-103">Pobiera określoną liczbę obiektów sąsiadujących z sekwencyjną kolekcją obiektów, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="24b9f-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24b9f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24b9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24b9f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="24b9f-106">[in] Liczba obiektów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="24b9f-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="24b9f-107">[out] Tablica `ObjectID` wartości, z których każdy reprezentuje pobrano obiekt.</span><span class="sxs-lookup"><span data-stu-id="24b9f-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="24b9f-108">[out] Wskaźnik do liczby elementów zwracanych w rzeczywistości w `objects` tablicy.</span><span class="sxs-lookup"><span data-stu-id="24b9f-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24b9f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24b9f-109">Requirements</span></span>  
 <span data-ttu-id="24b9f-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24b9f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24b9f-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24b9f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24b9f-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24b9f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24b9f-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24b9f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b9f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24b9f-114">See also</span></span>

- [<span data-ttu-id="24b9f-115">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="24b9f-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
