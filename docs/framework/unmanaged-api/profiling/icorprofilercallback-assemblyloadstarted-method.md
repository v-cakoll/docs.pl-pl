---
title: ICorProfilerCallback::AssemblyLoadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
ms.openlocfilehash: df172edb97a82ae3bf2d46c8be6ea05d5445a09a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500432"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="40621-102">ICorProfilerCallback::AssemblyLoadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="40621-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="40621-103">Powiadamia program profilujący, że zestaw jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="40621-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40621-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40621-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40621-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40621-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="40621-106">\[w] identyfikuje zestaw, który jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="40621-106">\[in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="40621-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40621-107">Remarks</span></span>  
 <span data-ttu-id="40621-108">Wartość `assemblyId` nie jest prawidłowa dla żądania informacji, dopóki nie zostanie wywołana metoda [ICorProfilerCallback:: AssemblyLoadFinished —](icorprofilercallback-assemblyloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="40621-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40621-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40621-109">Requirements</span></span>  
 <span data-ttu-id="40621-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40621-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40621-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="40621-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40621-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="40621-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40621-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40621-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40621-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40621-114">See also</span></span>

- [<span data-ttu-id="40621-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="40621-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
