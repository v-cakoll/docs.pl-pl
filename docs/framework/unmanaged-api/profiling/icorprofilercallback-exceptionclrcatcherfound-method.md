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
ms.openlocfilehash: 59225677671388b4ed31f7fa440b6e502b604c63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597651"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="f1a39-102">ICorProfilerCallback::ExceptionCLRCatcherFound — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1a39-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="f1a39-103">Wywoływane, gdy `catch` blokowania, dla wyjątku znajduje się wewnątrz środowisko uruchomieniowe języka wspólnego (CLR), sam.</span><span class="sxs-lookup"><span data-stu-id="f1a39-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="f1a39-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="f1a39-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a39-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1a39-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f1a39-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1a39-106">Requirements</span></span>  
 <span data-ttu-id="f1a39-107">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1a39-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1a39-108">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f1a39-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1a39-109">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1a39-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1a39-110">**Wersja programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="f1a39-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a39-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1a39-111">See also</span></span>

- [<span data-ttu-id="f1a39-112">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f1a39-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f1a39-113">ExceptionCLRCatcherExecute, metoda</span><span class="sxs-lookup"><span data-stu-id="f1a39-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
