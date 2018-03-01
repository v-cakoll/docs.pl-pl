---
title: "ICorProfilerInfo::GetThreadInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ab887cf4aaded260903cf1b91498c7641eeb0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="8258f-102">ICorProfilerInfo::GetThreadInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="8258f-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="8258f-103">Pobiera tożsamość bieżącego wątku Win32 dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8258f-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8258f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8258f-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8258f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8258f-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="8258f-106">[in] Identyfikator wątku, który można pobrać bieżącego identyfikatora Win32</span><span class="sxs-lookup"><span data-stu-id="8258f-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="8258f-107">[out] Wskaźnik do bieżącego wątku Win32 wątku określonego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="8258f-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8258f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8258f-108">Requirements</span></span>  
 <span data-ttu-id="8258f-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8258f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8258f-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8258f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8258f-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8258f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8258f-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8258f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8258f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8258f-113">See Also</span></span>  
 [<span data-ttu-id="8258f-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="8258f-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
