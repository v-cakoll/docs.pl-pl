---
title: ICorProfilerCallback::ExceptionCLRCatcherFound — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
ms.openlocfilehash: a543e5119a3ad5580fb67c31dc0e59ab62eab571
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866495"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="52bee-102">ICorProfilerCallback::ExceptionCLRCatcherFound — Metoda</span><span class="sxs-lookup"><span data-stu-id="52bee-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="52bee-103">Wywołuje się, gdy w samym środowisku uruchomieniowym języka wspólnego (CLR) zostanie znaleziony blok `catch` dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="52bee-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="52bee-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="52bee-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52bee-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="52bee-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="52bee-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52bee-106">Requirements</span></span>  
 <span data-ttu-id="52bee-107">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52bee-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52bee-108">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="52bee-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52bee-109">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="52bee-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52bee-110">**Wersja .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="52bee-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52bee-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52bee-111">See also</span></span>

- [<span data-ttu-id="52bee-112">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="52bee-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="52bee-113">ExceptionCLRCatcherExecute, metoda</span><span class="sxs-lookup"><span data-stu-id="52bee-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
