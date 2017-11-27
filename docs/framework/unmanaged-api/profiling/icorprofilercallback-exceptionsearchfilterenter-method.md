---
title: "ICorProfilerCallback::ExceptionSearchFilterEnter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionSearchFilterEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 129bc39fc9edd8f3101e7d03272bcab35c746d73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="6ca9e-102">ICorProfilerCallback::ExceptionSearchFilterEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ca9e-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="6ca9e-103">Powiadamia profilera fazy wyszukiwania obsługi wyjątków zostało uruchomione, wykonywanie filtru wyjątków zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6ca9e-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ca9e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ca9e-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ca9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ca9e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6ca9e-106">[in] Identyfikator funkcji, która zawiera filtr.</span><span class="sxs-lookup"><span data-stu-id="6ca9e-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ca9e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ca9e-107">Requirements</span></span>  
 <span data-ttu-id="6ca9e-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ca9e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ca9e-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6ca9e-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6ca9e-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ca9e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ca9e-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ca9e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca9e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ca9e-112">See Also</span></span>  
 [<span data-ttu-id="6ca9e-113">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="6ca9e-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="6ca9e-114">ExceptionSearchFilterLeave — metoda</span><span class="sxs-lookup"><span data-stu-id="6ca9e-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
