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
ms.openlocfilehash: d6518612c213d21c2dc7d80878121ccd3b7e2abb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449852"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="69ebe-102">ICorProfilerInfo10:: EnumerateObjectReferences, Metoda</span><span class="sxs-lookup"><span data-stu-id="69ebe-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="69ebe-103">Podanym identyfikatorem ObjectID, wywołaniem zwrotnym i clientData, wylicza każde odwołanie do obiektu (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="69ebe-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="69ebe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69ebe-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

#### <a name="parameters"></a><span data-ttu-id="69ebe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69ebe-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="69ebe-106">podczas Obiekt, na którym mają zostać wyliczone odwołania.</span><span class="sxs-lookup"><span data-stu-id="69ebe-106">[in] The object to enumerate references on.</span></span>

`callback` \
<span data-ttu-id="69ebe-107">podczas Funkcja, która będzie wywoływana z odwołaniami dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="69ebe-107">[in] The function that will be called with the references for the object.</span></span>

`clientData` \
<span data-ttu-id="69ebe-108">podczas Dane dostarczone przez profiler do przekazania do funkcji `callback`.</span><span class="sxs-lookup"><span data-stu-id="69ebe-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="69ebe-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69ebe-109">Remarks</span></span>

<span data-ttu-id="69ebe-110">Metoda `EnumerateObjectReferences` jest podobna do [ObjectReferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), z tą różnicą, że wyszukuje odwołania na żądanie profilera, zamiast wstępnie przydzielić tablicę do przechowywania odwołań.</span><span class="sxs-lookup"><span data-stu-id="69ebe-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="69ebe-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69ebe-111">Requirements</span></span>

<span data-ttu-id="69ebe-112">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="69ebe-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="69ebe-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="69ebe-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="69ebe-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="69ebe-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="69ebe-115">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69ebe-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="69ebe-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69ebe-116">See also</span></span>

- [<span data-ttu-id="69ebe-117">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="69ebe-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
