---
title: ICorProfilerCallback::ExceptionSearchFunctionEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3633665a3fcac0ca1d90ac562056b8b380ab2ca9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072535"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="921c4-102">ICorProfilerCallback::ExceptionSearchFunctionEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="921c4-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="921c4-103">Powiadamia program profilujący, że faza wyszukiwania dla obsługi wyjątków rozpoczął wyszukiwanie funkcji można znaleźć programu obsługi dla bieżącego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="921c4-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="921c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="921c4-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="921c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="921c4-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="921c4-106">[in] Identyfikator funkcji, która została wprowadzona.</span><span class="sxs-lookup"><span data-stu-id="921c4-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="921c4-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="921c4-107">Requirements</span></span>  
 <span data-ttu-id="921c4-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="921c4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="921c4-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="921c4-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="921c4-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="921c4-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="921c4-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="921c4-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="921c4-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="921c4-112">See also</span></span>

- [<span data-ttu-id="921c4-113">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="921c4-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="921c4-114">ExceptionSearchFunctionLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="921c4-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
