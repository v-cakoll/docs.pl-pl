---
title: ICorProfilerInfo2::GetThreadAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32a69f948b936dd80ab364583dc2928778b34ba0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174411"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="76fdc-102">ICorProfilerInfo2::GetThreadAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="76fdc-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="76fdc-103">Pobiera identyfikator domeny aplikacji, w którym określony wątek jest w trakcie wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="76fdc-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76fdc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76fdc-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76fdc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76fdc-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="76fdc-106">[in] Identyfikator, określając wątku.</span><span class="sxs-lookup"><span data-stu-id="76fdc-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="76fdc-107">[out] Wskaźnik do Identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="76fdc-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76fdc-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76fdc-108">Requirements</span></span>  
 <span data-ttu-id="76fdc-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76fdc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76fdc-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="76fdc-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76fdc-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76fdc-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="76fdc-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="76fdc-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="76fdc-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76fdc-113">See also</span></span>

- [<span data-ttu-id="76fdc-114">ICorProfilerInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="76fdc-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="76fdc-115">ICorProfilerInfo2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="76fdc-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
