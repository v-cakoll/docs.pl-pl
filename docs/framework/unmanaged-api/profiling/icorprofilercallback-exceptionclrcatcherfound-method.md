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
ms.openlocfilehash: ef5122d49c428af4faa27f3827a5c60721ef0f74
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435826"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="5e9df-102">ICorProfilerCallback::ExceptionCLRCatcherFound — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e9df-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="5e9df-103">Wywołuje się, gdy w samym środowisku uruchomieniowym języka wspólnego (CLR) zostanie znaleziony blok `catch` dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5e9df-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="5e9df-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="5e9df-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e9df-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e9df-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="5e9df-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e9df-106">Requirements</span></span>  
 <span data-ttu-id="5e9df-107">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e9df-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e9df-108">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5e9df-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e9df-109">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5e9df-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e9df-110">**Wersja .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="5e9df-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e9df-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e9df-111">See also</span></span>

- [<span data-ttu-id="5e9df-112">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e9df-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="5e9df-113">ExceptionCLRCatcherExecute, metoda</span><span class="sxs-lookup"><span data-stu-id="5e9df-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
