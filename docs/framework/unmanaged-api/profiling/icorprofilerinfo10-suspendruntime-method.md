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
ms.openlocfilehash: 74300a12d000565a63cd7ea862c759d47b87bbe1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665695"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="85585-102">ICorProfilerInfo10:: SuspendRuntime, Metoda</span><span class="sxs-lookup"><span data-stu-id="85585-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="85585-103">Wstrzymuje środowisko uruchomieniowe bez wykonywania operacji GC.</span><span class="sxs-lookup"><span data-stu-id="85585-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="85585-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85585-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="85585-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85585-105">Requirements</span></span>

<span data-ttu-id="85585-106">**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="85585-106">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="85585-107">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="85585-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="85585-108">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85585-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="85585-109">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85585-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="85585-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85585-110">See also</span></span>

- [<span data-ttu-id="85585-111">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="85585-111">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
