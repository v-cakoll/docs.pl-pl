---
title: ICorProfilerInfo::ForceGC — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5672d1b89b4260d1ebfbf444deb2702f215a0e95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078086"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="1f308-102">ICorProfilerInfo::ForceGC — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f308-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="1f308-103">Wymusza wyrzucanie elementów bezużytecznych w środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="1f308-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f308-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f308-104">Syntax</span></span>  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1f308-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f308-105">Remarks</span></span>  
 <span data-ttu-id="1f308-106">`ForceGC` Metoda musi zostać wywołana tylko z wątku, który nigdy nie uruchomił kodu zarządzanego, a nie ma żadnych wywołania zwrotne profilera na swój stos.</span><span class="sxs-lookup"><span data-stu-id="1f308-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="1f308-107">Najwygodniej wdrożenia jest utworzenie oddzielnego wątku w ramach programu profilującego, który wywołuje `ForceGC` podczas zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="1f308-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f308-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f308-108">Requirements</span></span>  
 <span data-ttu-id="1f308-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f308-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f308-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1f308-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f308-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f308-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1f308-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1f308-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1f308-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f308-113">See also</span></span>

- [<span data-ttu-id="1f308-114">ICorProfilerInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1f308-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
