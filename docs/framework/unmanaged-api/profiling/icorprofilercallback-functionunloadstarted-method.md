---
title: ICorProfilerCallback::FunctionUnloadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: f57a3ed70267de65daed85305ad7d623b4ca0337
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448018"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="ddcc0-102">ICorProfilerCallback::FunctionUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="ddcc0-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="ddcc0-103">Powiadamia profiler o rozpoczęciu pracy przez środowisko uruchomieniowe w celu zwolnienia funkcji.</span><span class="sxs-lookup"><span data-stu-id="ddcc0-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcc0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddcc0-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="ddcc0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddcc0-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ddcc0-106">podczas Identyfikator funkcji, która jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="ddcc0-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddcc0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddcc0-107">Remarks</span></span>  
 <span data-ttu-id="ddcc0-108">Wartość parametru `functionId` nie jest już prawidłowa po powrocie tej metody do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ddcc0-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddcc0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddcc0-109">Requirements</span></span>  
 <span data-ttu-id="ddcc0-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddcc0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddcc0-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ddcc0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ddcc0-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ddcc0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddcc0-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddcc0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcc0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddcc0-114">See also</span></span>

- [<span data-ttu-id="ddcc0-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ddcc0-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
