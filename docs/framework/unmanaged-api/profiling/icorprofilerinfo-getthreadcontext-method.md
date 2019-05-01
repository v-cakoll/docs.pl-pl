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
ms.openlocfilehash: f26fd93d42a709249936815d3c29ae572482f427
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992046"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="8404b-102">ICorProfilerInfo::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="8404b-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="8404b-103">Pobiera tożsamość kontekstu aktualnie skojarzone z określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8404b-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8404b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8404b-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8404b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8404b-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="8404b-106">[in] Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="8404b-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="8404b-107">[out] Wskaźnik do identyfikator kontekstu, obecnie skojarzonego z określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8404b-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="8404b-108">Jeśli wątek ma kontekst nie jest obecnie skojarzony z nim, ta funkcja zwróci CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="8404b-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8404b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8404b-109">Requirements</span></span>  
 <span data-ttu-id="8404b-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8404b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8404b-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8404b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8404b-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8404b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8404b-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8404b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8404b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8404b-114">See also</span></span>

- [<span data-ttu-id="8404b-115">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="8404b-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
