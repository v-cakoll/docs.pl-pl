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
ms.openlocfilehash: 850f05520e4146b5016bb574f02aa800dfcaaf32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494582"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="ac25f-102">ICorProfilerObjectEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac25f-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="ac25f-103">Pobiera określoną liczbę obiektów ciągłego z kolekcji sekwencyjnej obiektów, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="ac25f-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac25f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac25f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac25f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac25f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ac25f-106">podczas Liczba obiektów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="ac25f-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="ac25f-107">określoną Tablica `ObjectID` wartości, z których każdy reprezentuje pobrany obiekt.</span><span class="sxs-lookup"><span data-stu-id="ac25f-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ac25f-108">określoną Wskaźnik do liczby elementów faktycznie zwracanych w `objects` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ac25f-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac25f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac25f-109">Requirements</span></span>  
 <span data-ttu-id="ac25f-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac25f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac25f-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ac25f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac25f-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ac25f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac25f-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac25f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac25f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac25f-114">See also</span></span>

- [<span data-ttu-id="ac25f-115">ICorProfilerObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ac25f-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
