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
ms.openlocfilehash: 7fd62e0d3d9173f3b75882131e57126075c0677f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863312"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="2ed60-102">ICorProfilerInfo10:: EnumerateObjectReferences, Metoda</span><span class="sxs-lookup"><span data-stu-id="2ed60-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="2ed60-103">Podanym identyfikatorem ObjectID, wywołaniem zwrotnym i clientData, wylicza każde odwołanie do obiektu (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="2ed60-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="2ed60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ed60-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="2ed60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ed60-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="2ed60-106">\[w] obiekt, na którym mają zostać wyliczone odwołania.</span><span class="sxs-lookup"><span data-stu-id="2ed60-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="2ed60-107">\[w] funkcja, która zostanie wywołana z odwołaniami dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="2ed60-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="2ed60-108">\[in] dane dostarczone przez profiler do przekazania do funkcji `callback`.</span><span class="sxs-lookup"><span data-stu-id="2ed60-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ed60-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ed60-109">Remarks</span></span>

<span data-ttu-id="2ed60-110">Metoda `EnumerateObjectReferences` jest podobna do [ObjectReferences —](icorprofilercallback-objectreferences-method.md), z tą różnicą, że wyszukuje odwołania na żądanie profilera, zamiast wstępnie przydzielić tablicę do przechowywania odwołań.</span><span class="sxs-lookup"><span data-stu-id="2ed60-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ed60-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ed60-111">Requirements</span></span>

<span data-ttu-id="2ed60-112">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="2ed60-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="2ed60-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2ed60-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="2ed60-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2ed60-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2ed60-115">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ed60-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2ed60-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ed60-116">See also</span></span>

- [<span data-ttu-id="2ed60-117">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ed60-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
