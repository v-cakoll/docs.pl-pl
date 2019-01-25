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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: edbd48c910c89c9dd5feea33d9598933fd63befa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729788"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="58c85-102">ICorProfilerCallback::ExceptionCLRCatcherFound — Metoda</span><span class="sxs-lookup"><span data-stu-id="58c85-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="58c85-103">Wywoływane, gdy `catch` blokowania, dla wyjątku znajduje się wewnątrz środowisko uruchomieniowe języka wspólnego (CLR), sam.</span><span class="sxs-lookup"><span data-stu-id="58c85-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="58c85-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="58c85-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c85-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="58c85-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="58c85-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58c85-106">Requirements</span></span>  
 <span data-ttu-id="58c85-107">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58c85-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58c85-108">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58c85-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58c85-109">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58c85-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58c85-110">**Wersja programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="58c85-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58c85-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58c85-111">See also</span></span>
- [<span data-ttu-id="58c85-112">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="58c85-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="58c85-113">ExceptionCLRCatcherExecute, metoda</span><span class="sxs-lookup"><span data-stu-id="58c85-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
