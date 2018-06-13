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
ms.openlocfilehash: 690dbb5659ce991b7c4921fbd85c246da54eff0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453044"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="1af48-102">ICorProfilerInfo2::GetThreadAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="1af48-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="1af48-103">Pobiera identyfikator domeny aplikacji, w którym określony wątek jest w trakcie wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="1af48-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1af48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1af48-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1af48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1af48-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="1af48-106">[in] Identyfikator Określanie wątku.</span><span class="sxs-lookup"><span data-stu-id="1af48-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="1af48-107">[out] Wskaźnik do identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1af48-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1af48-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1af48-108">Requirements</span></span>  
 <span data-ttu-id="1af48-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1af48-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1af48-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1af48-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1af48-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1af48-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1af48-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1af48-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af48-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1af48-113">See Also</span></span>  
 [<span data-ttu-id="1af48-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="1af48-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="1af48-115">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1af48-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
