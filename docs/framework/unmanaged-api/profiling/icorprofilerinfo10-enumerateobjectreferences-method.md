---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 9aadf9701444d215291b6fc19cc8cd61ca832837
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452243"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="ad3c2-102">ICorProfilerInfo10:: EnumerateObjectReferences, Metoda</span><span class="sxs-lookup"><span data-stu-id="ad3c2-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="ad3c2-103">Podanym identyfikatorem ObjectID, wywołaniem zwrotnym i clientData, wylicza każde odwołanie do obiektu (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="ad3c2-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="ad3c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad3c2-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="ad3c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad3c2-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="ad3c2-106">\[w] obiekt, na którym mają zostać wyliczone odwołania.</span><span class="sxs-lookup"><span data-stu-id="ad3c2-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="ad3c2-107">\[w] funkcja, która zostanie wywołana z odwołaniami dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="ad3c2-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="ad3c2-108">\[in] dane dostarczone przez profiler do przekazania do funkcji `callback`.</span><span class="sxs-lookup"><span data-stu-id="ad3c2-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad3c2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad3c2-109">Remarks</span></span>

<span data-ttu-id="ad3c2-110">Metoda `EnumerateObjectReferences` jest podobna do [ObjectReferences —](icorprofilercallback-objectreferences-method.md), z tą różnicą, że wyszukuje odwołania na żądanie profilera, zamiast wstępnie przydzielić tablicę do przechowywania odwołań.</span><span class="sxs-lookup"><span data-stu-id="ad3c2-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="ad3c2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad3c2-111">Requirements</span></span>

<span data-ttu-id="ad3c2-112">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="ad3c2-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="ad3c2-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ad3c2-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="ad3c2-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ad3c2-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ad3c2-115">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad3c2-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ad3c2-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad3c2-116">See also</span></span>

- [<span data-ttu-id="ad3c2-117">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad3c2-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
