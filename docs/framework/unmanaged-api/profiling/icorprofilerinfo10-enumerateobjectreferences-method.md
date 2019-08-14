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
ms.openlocfilehash: 4b13659f7c9909e9795caee1eace8da8092c5b9a
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973757"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="b5584-102">ICorProfilerInfo10:: EnumerateObjectReferences, Metoda</span><span class="sxs-lookup"><span data-stu-id="b5584-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>
  
 <span data-ttu-id="b5584-103">Podanym identyfikatorem ObjectID, wywołaniem zwrotnym i clientData, wylicza każde odwołanie do obiektu (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="b5584-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="b5584-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5584-104">Syntax</span></span>  
  
```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5584-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5584-105">Parameters</span></span>  

 `objectId` \
 <span data-ttu-id="b5584-106">podczas Obiekt, na którym mają zostać wyliczone odwołania.</span><span class="sxs-lookup"><span data-stu-id="b5584-106">[in] The object to enumerate references on.</span></span>

 `callback` \
 <span data-ttu-id="b5584-107">podczas Funkcja, która będzie wywoływana z odwołaniami dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="b5584-107">[in] The function that will be called with the references for the object.</span></span>

 `clientData` \
 <span data-ttu-id="b5584-108">podczas Dane dostarczone przez `callback` Profiler do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="b5584-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="b5584-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5584-109">Remarks</span></span>  
 <span data-ttu-id="b5584-110">Metoda jest podobna do ObjectReferences —, z tą różnicą, że przeprowadza odwołania na żądanie dla profilera zamiast wstępnie przydzielić tablicę do przechowywania odwołań. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) `EnumerateObjectReferences`</span><span class="sxs-lookup"><span data-stu-id="b5584-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>  

## <a name="requirements"></a><span data-ttu-id="b5584-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5584-111">Requirements</span></span>  
 <span data-ttu-id="b5584-112">**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="b5584-112">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="b5584-113">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b5584-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5584-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5584-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5584-115">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5584-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b5584-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5584-116">See also</span></span>
- [<span data-ttu-id="b5584-117">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="b5584-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

