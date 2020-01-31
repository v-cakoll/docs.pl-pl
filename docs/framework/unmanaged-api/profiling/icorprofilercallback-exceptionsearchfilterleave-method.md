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
ms.openlocfilehash: 607143d7848534329a55a9caebdb6b9175b2749c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866419"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="d210f-102">ICorProfilerCallback::ExceptionSearchFilterLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="d210f-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="d210f-103">Powiadamia profiler o zakończeniu wykonywania przez filtr użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d210f-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d210f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d210f-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d210f-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d210f-105">Requirements</span></span>  
 <span data-ttu-id="d210f-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d210f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d210f-107">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d210f-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d210f-108">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d210f-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d210f-109">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d210f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d210f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d210f-110">See also</span></span>

- [<span data-ttu-id="d210f-111">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d210f-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d210f-112">ExceptionSearchFilterEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="d210f-112">ExceptionSearchFilterEnter Method</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)
