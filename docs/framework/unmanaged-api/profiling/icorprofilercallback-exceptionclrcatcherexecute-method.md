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
ms.openlocfilehash: 6057593362e75044a9b2db32ad5dafe439a551d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451145"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="0a024-102">ICorProfilerCallback::ExceptionCLRCatcherExecute — Metoda</span><span class="sxs-lookup"><span data-stu-id="0a024-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="0a024-103">Wywoływane, gdy `catch` zablokować dla wyjątku jest wykonywana wewnątrz środowisko uruchomieniowe języka wspólnego (CLR) samej siebie.</span><span class="sxs-lookup"><span data-stu-id="0a024-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="0a024-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="0a024-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a024-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a024-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="0a024-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a024-106">Requirements</span></span>  
 <span data-ttu-id="0a024-107">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a024-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a024-108">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0a024-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a024-109">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a024-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a024-110">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="0a024-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a024-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a024-111">See Also</span></span>  
 [<span data-ttu-id="0a024-112">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a024-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="0a024-113">ExceptionCLRCatcherFound, metoda</span><span class="sxs-lookup"><span data-stu-id="0a024-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
