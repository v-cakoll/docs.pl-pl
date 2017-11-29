---
title: "ICorProfilerInfo2::GetThreadAppDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetThreadAppDomain
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4c8e16bc3d0a886e44bded3c274e5c53b43d75ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="a2d4e-102">ICorProfilerInfo2::GetThreadAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2d4e-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="a2d4e-103">Pobiera identyfikator domeny aplikacji, w którym określony wątek jest w trakcie wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="a2d4e-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2d4e-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2d4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2d4e-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="a2d4e-106">[in] Identyfikator Określanie wątku.</span><span class="sxs-lookup"><span data-stu-id="a2d4e-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="a2d4e-107">[out] Wskaźnik do identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2d4e-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d4e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2d4e-108">Requirements</span></span>  
 <span data-ttu-id="a2d4e-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2d4e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d4e-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a2d4e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a2d4e-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2d4e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2d4e-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d4e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d4e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2d4e-113">See Also</span></span>  
 [<span data-ttu-id="a2d4e-114">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="a2d4e-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="a2d4e-115">ICorProfilerInfo2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="a2d4e-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
