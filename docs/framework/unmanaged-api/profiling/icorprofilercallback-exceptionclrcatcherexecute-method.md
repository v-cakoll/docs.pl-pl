---
title: ICorProfilerCallback::ExceptionCLRCatcherExecute — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
ms.openlocfilehash: f14dff33217656c35379a214f007ccb3642ef4b1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866458"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="d8125-102">ICorProfilerCallback::ExceptionCLRCatcherExecute — Metoda</span><span class="sxs-lookup"><span data-stu-id="d8125-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="d8125-103">Wywołuje się, gdy blok `catch` dla wyjątku jest wykonywany wewnątrz samego środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d8125-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="d8125-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="d8125-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8125-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8125-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d8125-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d8125-106">Requirements</span></span>  
 <span data-ttu-id="d8125-107">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8125-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8125-108">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d8125-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8125-109">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d8125-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8125-110">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="d8125-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8125-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8125-111">See also</span></span>

- [<span data-ttu-id="d8125-112">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d8125-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d8125-113">ExceptionCLRCatcherFound, metoda</span><span class="sxs-lookup"><span data-stu-id="d8125-113">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
