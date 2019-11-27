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
ms.openlocfilehash: c33a868b643cb3e3fd5dfaf436e3078bc590705c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449816"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="c4b1f-102">ICorProfilerInfo10:: RequestReJITWithInliners, Metoda</span><span class="sxs-lookup"><span data-stu-id="c4b1f-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="c4b1f-103">ReJITs wymagane metody, a także wszystkie wbudowane metody.</span><span class="sxs-lookup"><span data-stu-id="c4b1f-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4b1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4b1f-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

#### <a name="parameters"></a><span data-ttu-id="c4b1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4b1f-105">Parameters</span></span>

`dwRejitFlags` \
<span data-ttu-id="c4b1f-106">podczas Maska bitów [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="c4b1f-106">[in] A bitmask of [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span></span>

`cFunctions` \
<span data-ttu-id="c4b1f-107">podczas Liczba funkcji, które mają zostać ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="c4b1f-107">[in] The number of functions to recompile.</span></span>

`moduleIds` \
<span data-ttu-id="c4b1f-108">podczas Określa `moduleId` część par (`module`, `methodDef`), które identyfikują funkcje, które mają być ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="c4b1f-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

`methodIds` \
<span data-ttu-id="c4b1f-109">podczas Określa `methodId` część par (`module`, `methodDef`), które identyfikują funkcje, które mają być ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="c4b1f-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4b1f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4b1f-110">Remarks</span></span>

<span data-ttu-id="c4b1f-111">[RequestReJIT —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) nie wykonuje żadnych śledzonych metod.</span><span class="sxs-lookup"><span data-stu-id="c4b1f-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="c4b1f-112">Profiler powinien zablokować tworzenie i śledzenie i wywoływać `RequestReJIT` dla wszystkich elementów, aby upewnić się, że każde wystąpienie metody wbudowanej zostało ReJITted.</span><span class="sxs-lookup"><span data-stu-id="c4b1f-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="c4b1f-113">Stanowi to problem z ReJIT po dołączeniu, ponieważ Profiler nie jest obecny do monitorowania tworzenia konspektu.</span><span class="sxs-lookup"><span data-stu-id="c4b1f-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="c4b1f-114">Ta metoda może być wywoływana w celu zagwarantowania, że pełny zestaw elementów ReJITted również będzie się znajdować.</span><span class="sxs-lookup"><span data-stu-id="c4b1f-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4b1f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4b1f-115">Requirements</span></span>

<span data-ttu-id="c4b1f-116">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c4b1f-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="c4b1f-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c4b1f-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c4b1f-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c4b1f-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c4b1f-119">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b1f-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c4b1f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4b1f-120">See also</span></span>

- [<span data-ttu-id="c4b1f-121">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="c4b1f-121">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
