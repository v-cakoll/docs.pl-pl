---
title: "ICorProfilerCallback::ExceptionCLRCatcherExecute — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b63f428cd75ed98d30e4b6ecca69dbe3b5b5656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="fdc32-102">ICorProfilerCallback::ExceptionCLRCatcherExecute — Metoda</span><span class="sxs-lookup"><span data-stu-id="fdc32-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="fdc32-103">Wywoływane, gdy `catch` zablokować dla wyjątku jest wykonywana wewnątrz środowisko uruchomieniowe języka wspólnego (CLR) samej siebie.</span><span class="sxs-lookup"><span data-stu-id="fdc32-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="fdc32-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="fdc32-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdc32-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdc32-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="fdc32-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdc32-106">Requirements</span></span>  
 <span data-ttu-id="fdc32-107">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdc32-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdc32-108">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fdc32-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fdc32-109">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdc32-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdc32-110">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="fdc32-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc32-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdc32-111">See Also</span></span>  
 [<span data-ttu-id="fdc32-112">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="fdc32-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="fdc32-113">ExceptionCLRCatcherFound — metoda</span><span class="sxs-lookup"><span data-stu-id="fdc32-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
