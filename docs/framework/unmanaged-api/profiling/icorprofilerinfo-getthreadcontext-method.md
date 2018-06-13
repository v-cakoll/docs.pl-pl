---
title: ICorProfilerInfo::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acb4d67f41b1434fe8052a74e976907f24fecd31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453580"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="a25be-102">ICorProfilerInfo::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="a25be-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="a25be-103">Pobiera tożsamość kontekst, w obecnie skojarzony z określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="a25be-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a25be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a25be-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a25be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a25be-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="a25be-106">[in] Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="a25be-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="a25be-107">[out] Wskaźnik do Identyfikatora kontekstu aktualnie skojarzony z określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="a25be-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="a25be-108">Jeśli wątek został kontekst nie jest obecnie skojarzony z nim, ta funkcja zwróci CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="a25be-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a25be-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a25be-109">Requirements</span></span>  
 <span data-ttu-id="a25be-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a25be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a25be-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a25be-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a25be-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a25be-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a25be-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a25be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25be-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a25be-114">See Also</span></span>  
 [<span data-ttu-id="a25be-115">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a25be-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
