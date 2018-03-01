---
title: "ICorProfilerCallback::ExceptionSearchFilterLeave — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e0bbde11a2b9c346cbda73ee29da20140524b51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="68f3d-102">ICorProfilerCallback::ExceptionSearchFilterLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="68f3d-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="68f3d-103">Powiadamia profilera, że filtr użytkownika właśnie zakończono wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="68f3d-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f3d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68f3d-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="68f3d-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68f3d-105">Requirements</span></span>  
 <span data-ttu-id="68f3d-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f3d-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f3d-107">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="68f3d-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="68f3d-108">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68f3d-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68f3d-109">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f3d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f3d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68f3d-110">See Also</span></span>  
 [<span data-ttu-id="68f3d-111">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="68f3d-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="68f3d-112">ExceptionSearchFilterEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="68f3d-112">ExceptionSearchFilterEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)
