---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 95473a8ce8d5fd7540228ecd9767448e51b5b326
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868987"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="3e716-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold, Metoda</span><span class="sxs-lookup"><span data-stu-id="3e716-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="3e716-103">Pobiera wartość wartości progowej skonfigurowanej sterty dużych obiektów (LOH).</span><span class="sxs-lookup"><span data-stu-id="3e716-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e716-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e716-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="3e716-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e716-105">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="3e716-106">\[out] próg sterty dużego obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="3e716-106">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e716-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e716-107">Remarks</span></span>

<span data-ttu-id="3e716-108">Obiekty większe niż próg sterty dużego obiektu zostaną przydzieloną na stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3e716-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="3e716-109">Począwszy od platformy .NET Core 3,0, można skonfigurować próg sterty dużego obiektu, `pThreshold` będzie zawierać aktywny rozmiar progu sterty dużego obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="3e716-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e716-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e716-110">Requirements</span></span>

<span data-ttu-id="3e716-111">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="3e716-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="3e716-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3e716-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="3e716-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3e716-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3e716-114">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e716-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3e716-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e716-115">See also</span></span>

- [<span data-ttu-id="3e716-116">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="3e716-116">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
