---
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: a4c875f6aae996271dee9ac193768ef6981efc19
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863039"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="a395b-102">ICorProfilerInfo10:: SuspendRuntime, Metoda</span><span class="sxs-lookup"><span data-stu-id="a395b-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="a395b-103">Wstrzymuje środowisko uruchomieniowe bez wykonywania operacji GC.</span><span class="sxs-lookup"><span data-stu-id="a395b-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="a395b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a395b-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="a395b-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a395b-105">Requirements</span></span>

<span data-ttu-id="a395b-106">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="a395b-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="a395b-107">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a395b-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a395b-108">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a395b-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a395b-109">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a395b-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a395b-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a395b-110">See also</span></span>

- [<span data-ttu-id="a395b-111">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="a395b-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
