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
ms.openlocfilehash: d6b6575cf04635b40b504b11bc415f61f05b4205
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973754"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="1123a-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold, Metoda</span><span class="sxs-lookup"><span data-stu-id="1123a-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>
  
 <span data-ttu-id="1123a-103">Pobiera wartość wartości progowej skonfigurowanej sterty dużych obiektów (LOH).</span><span class="sxs-lookup"><span data-stu-id="1123a-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="1123a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1123a-104">Syntax</span></span>  
  
```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```  
  
#### <a name="parameters"></a><span data-ttu-id="1123a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1123a-105">Parameters</span></span>  
 `pThreshold` \
 <span data-ttu-id="1123a-106">określoną Próg sterty dużego obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="1123a-106">[out] The large object heap threshold in bytes.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="1123a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1123a-107">Remarks</span></span>  
 <span data-ttu-id="1123a-108">Obiekty większe niż próg sterty dużego obiektu zostaną przydzieloną na stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1123a-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="1123a-109">Począwszy od platformy .NET Core 3,0 próg sterty dużego obiektu jest konfigurowalny, `pThreshold` będzie zawierać aktywny rozmiar progu sterty dużego obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="1123a-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="1123a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1123a-110">Requirements</span></span>  
 <span data-ttu-id="1123a-111">**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="1123a-111">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="1123a-112">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1123a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1123a-113">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1123a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1123a-114">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1123a-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1123a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1123a-115">See also</span></span>
- [<span data-ttu-id="1123a-116">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="1123a-116">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

