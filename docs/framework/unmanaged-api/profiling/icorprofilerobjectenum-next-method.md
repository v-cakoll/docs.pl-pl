---
title: "ICorProfilerObjectEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Next
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfeec7c3ee2038b77549e53b10534d817b667687
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="973d0-102">ICorProfilerObjectEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="973d0-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="973d0-103">Pobiera określoną liczbę obiektów ciągłe z sekwencyjną kolekcją obiektów, zaczynając od modułu wyliczającego bieżącej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="973d0-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="973d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="973d0-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="973d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="973d0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="973d0-106">[in] Liczba obiektów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="973d0-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="973d0-107">[out] Tablica `ObjectID` wartości, z których każdy reprezentuje obiekt pobrane.</span><span class="sxs-lookup"><span data-stu-id="973d0-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="973d0-108">[out] Wskaźnik do liczby elementów faktycznie zwracane w `objects` tablicy.</span><span class="sxs-lookup"><span data-stu-id="973d0-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="973d0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="973d0-109">Requirements</span></span>  
 <span data-ttu-id="973d0-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="973d0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="973d0-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="973d0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="973d0-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="973d0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="973d0-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="973d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="973d0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="973d0-114">See Also</span></span>  
 [<span data-ttu-id="973d0-115">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="973d0-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
