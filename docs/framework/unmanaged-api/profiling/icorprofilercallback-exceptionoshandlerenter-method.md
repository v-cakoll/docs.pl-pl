---
title: ICorProfilerCallback::ExceptionOSHandlerEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2dc7c22ee075f347604864d8bee1a4e871da616
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451769"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="4dd15-102">ICorProfilerCallback::ExceptionOSHandlerEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="4dd15-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="4dd15-103">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="4dd15-103">Not implemented.</span></span> <span data-ttu-id="4dd15-104">Profiler wymagające niezarządzany wyjątek informacji należy uzyskać te informacje w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="4dd15-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dd15-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dd15-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4dd15-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4dd15-106">Requirements</span></span>  
 <span data-ttu-id="4dd15-107">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dd15-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dd15-108">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4dd15-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4dd15-109">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dd15-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dd15-110">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dd15-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd15-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4dd15-111">See Also</span></span>  
 [<span data-ttu-id="4dd15-112">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="4dd15-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
