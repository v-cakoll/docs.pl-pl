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
ms.openlocfilehash: c2c9ed848984d36ddf10d32d120deda76a4d47cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500289"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="5fee0-102">ICorProfilerCallback::ExceptionOSHandlerEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="5fee0-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="5fee0-103">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="5fee0-103">Not implemented.</span></span> <span data-ttu-id="5fee0-104">Profiler wymagający niezarządzanych informacji o wyjątku musi uzyskać te informacje w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="5fee0-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fee0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fee0-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5fee0-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5fee0-106">Requirements</span></span>  
 <span data-ttu-id="5fee0-107">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fee0-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fee0-108">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5fee0-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5fee0-109">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5fee0-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fee0-110">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fee0-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fee0-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fee0-111">See also</span></span>

- [<span data-ttu-id="5fee0-112">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5fee0-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
