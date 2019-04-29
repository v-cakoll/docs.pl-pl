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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b640a6dee9ae50278d6a844d20d21eae156e9dd7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598549"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="09d10-102">ICorProfilerCallback::ExceptionCLRCatcherExecute — Metoda</span><span class="sxs-lookup"><span data-stu-id="09d10-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="09d10-103">Wywoływane, gdy `catch` blokowania, dla wyjątku jest wykonywany wewnątrz środowisko uruchomieniowe języka wspólnego (CLR), sam.</span><span class="sxs-lookup"><span data-stu-id="09d10-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="09d10-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="09d10-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09d10-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="09d10-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="09d10-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09d10-106">Requirements</span></span>  
 <span data-ttu-id="09d10-107">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09d10-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09d10-108">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="09d10-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09d10-109">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09d10-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09d10-110">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="09d10-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09d10-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09d10-111">See also</span></span>

- [<span data-ttu-id="09d10-112">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="09d10-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="09d10-113">ExceptionCLRCatcherFound, metoda</span><span class="sxs-lookup"><span data-stu-id="09d10-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
