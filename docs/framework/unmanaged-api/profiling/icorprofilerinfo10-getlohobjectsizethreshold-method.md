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
ms.openlocfilehash: 7a0f6f6bea5bc919ebfe9c9acc3b02a31eaa7cd0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452217"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="45045-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold, Metoda</span><span class="sxs-lookup"><span data-stu-id="45045-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="45045-103">Pobiera wartość wartości progowej skonfigurowanej sterty dużych obiektów (LOH).</span><span class="sxs-lookup"><span data-stu-id="45045-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="45045-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45045-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="45045-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45045-105">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="45045-106">\[out] próg sterty dużego obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="45045-106">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="45045-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45045-107">Remarks</span></span>

<span data-ttu-id="45045-108">Obiekty większe niż próg sterty dużego obiektu zostaną przydzieloną na stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="45045-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="45045-109">Począwszy od platformy .NET Core 3,0, można skonfigurować próg sterty dużego obiektu, `pThreshold` będzie zawierać aktywny rozmiar progu sterty dużego obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="45045-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="45045-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45045-110">Requirements</span></span>

<span data-ttu-id="45045-111">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="45045-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="45045-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="45045-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="45045-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="45045-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="45045-114">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45045-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="45045-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45045-115">See also</span></span>

- [<span data-ttu-id="45045-116">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="45045-116">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
