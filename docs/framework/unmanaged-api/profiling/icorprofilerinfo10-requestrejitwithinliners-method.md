---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 99b6893854c358720259095bf3c0270cb3676483
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452178"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="59331-102">ICorProfilerInfo10:: RequestReJITWithInliners, Metoda</span><span class="sxs-lookup"><span data-stu-id="59331-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="59331-103">ReJITs wymagane metody, a także wszystkie wbudowane metody.</span><span class="sxs-lookup"><span data-stu-id="59331-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="59331-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59331-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="59331-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="59331-105">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="59331-106">\[w) — Maska bitów [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="59331-106">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="59331-107">\[] liczba funkcji, które mają zostać ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="59331-107">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="59331-108">\[in] określa `moduleId` część par (`module`, `methodDef`), które identyfikują funkcje, które mają być ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="59331-108">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="59331-109">\[in] określa `methodId` część par (`module`, `methodDef`), które identyfikują funkcje, które mają być ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="59331-109">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="59331-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59331-110">Remarks</span></span>

<span data-ttu-id="59331-111">[RequestReJIT —](icorprofilerinfo4-requestrejit-method.md) nie wykonuje żadnych śledzonych metod.</span><span class="sxs-lookup"><span data-stu-id="59331-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="59331-112">Profiler powinien zablokować tworzenie i śledzenie i wywoływać `RequestReJIT` dla wszystkich elementów, aby upewnić się, że każde wystąpienie metody wbudowanej zostało ReJITted.</span><span class="sxs-lookup"><span data-stu-id="59331-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="59331-113">Stanowi to problem z ReJIT po dołączeniu, ponieważ Profiler nie jest obecny do monitorowania tworzenia konspektu.</span><span class="sxs-lookup"><span data-stu-id="59331-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="59331-114">Ta metoda może być wywoływana w celu zagwarantowania, że pełny zestaw elementów ReJITted również będzie się znajdować.</span><span class="sxs-lookup"><span data-stu-id="59331-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="59331-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59331-115">Requirements</span></span>

<span data-ttu-id="59331-116">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="59331-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="59331-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="59331-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="59331-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="59331-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="59331-119">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59331-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="59331-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59331-120">See also</span></span>

- [<span data-ttu-id="59331-121">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="59331-121">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
