---
title: ICorProfilerCallback::ExceptionSearchFilterLeave — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13de3470e70635243aed78ac603cebc841c8fa59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="f4ca9-102">ICorProfilerCallback::ExceptionSearchFilterLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="f4ca9-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="f4ca9-103">Powiadamia profilera, że filtr użytkownika właśnie zakończono wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="f4ca9-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4ca9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4ca9-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f4ca9-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4ca9-105">Requirements</span></span>  
 <span data-ttu-id="f4ca9-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4ca9-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4ca9-107">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f4ca9-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f4ca9-108">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4ca9-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4ca9-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4ca9-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ca9-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4ca9-110">See Also</span></span>  
 [<span data-ttu-id="f4ca9-111">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f4ca9-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f4ca9-112">ExceptionSearchFilterEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="f4ca9-112">ExceptionSearchFilterEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)
