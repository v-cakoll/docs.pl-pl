---
title: ICorProfilerCallback::ExceptionSearchCatcherFound — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: 080777b656e1c3df1cc4170fe1dff6de6ddb41fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445395"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="61ae8-102">ICorProfilerCallback::ExceptionSearchCatcherFound — Metoda</span><span class="sxs-lookup"><span data-stu-id="61ae8-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="61ae8-103">Powiadamia profiler, że faza wyszukiwania obsługi wyjątków znalazła procedurę obsługi dla zgłoszonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="61ae8-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ae8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61ae8-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61ae8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61ae8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="61ae8-106">podczas Identyfikator funkcji, która zawiera procedurę obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="61ae8-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61ae8-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61ae8-107">Requirements</span></span>  
 <span data-ttu-id="61ae8-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61ae8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ae8-109">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="61ae8-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61ae8-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="61ae8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61ae8-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ae8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ae8-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61ae8-112">See also</span></span>

- [<span data-ttu-id="61ae8-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="61ae8-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
