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
ms.openlocfilehash: 683cec06cd4c2fdef310126adc2921c858ca5687
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776031"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="ff9e8-102">ICorProfilerCallback::ExceptionCLRCatcherFound — Metoda</span><span class="sxs-lookup"><span data-stu-id="ff9e8-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="ff9e8-103">Wywoływane, gdy `catch` blokowania, dla wyjątku znajduje się wewnątrz środowisko uruchomieniowe języka wspólnego (CLR), sam.</span><span class="sxs-lookup"><span data-stu-id="ff9e8-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="ff9e8-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="ff9e8-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff9e8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff9e8-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="ff9e8-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff9e8-106">Requirements</span></span>  
 <span data-ttu-id="ff9e8-107">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff9e8-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff9e8-108">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ff9e8-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff9e8-109">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff9e8-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff9e8-110">**Wersja programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="ff9e8-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff9e8-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff9e8-111">See also</span></span>

- [<span data-ttu-id="ff9e8-112">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ff9e8-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ff9e8-113">ExceptionCLRCatcherExecute, metoda</span><span class="sxs-lookup"><span data-stu-id="ff9e8-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
