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
ms.openlocfilehash: b6e26d1538cab30db66e887aee89b8fbae501bdb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177010"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="fd79e-102">ICorProfilerObjectEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="fd79e-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="fd79e-103">Pobiera określoną liczbę obiektów ciągłych z sekwencyjnej kolekcji obiektów, począwszy od bieżącej pozycji wyliczacza w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="fd79e-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd79e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd79e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd79e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd79e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="fd79e-106">[w] Liczba obiektów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="fd79e-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="fd79e-107">[na zewnątrz] Tablica `ObjectID` wartości, z których każda reprezentuje pobrany obiekt.</span><span class="sxs-lookup"><span data-stu-id="fd79e-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="fd79e-108">[na zewnątrz] Wskaźnik do liczby elementów faktycznie `objects` zwróconych w tablicy.</span><span class="sxs-lookup"><span data-stu-id="fd79e-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd79e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd79e-109">Requirements</span></span>  
 <span data-ttu-id="fd79e-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd79e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd79e-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fd79e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd79e-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd79e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd79e-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd79e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd79e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd79e-114">See also</span></span>

- [<span data-ttu-id="fd79e-115">ICorProfilerObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fd79e-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
