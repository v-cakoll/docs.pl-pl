---
title: ICorProfilerInfo::GetThreadInfo — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f68565977551a54244f3caf6a0250f67005a6ecf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="c51c4-102">ICorProfilerInfo::GetThreadInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="c51c4-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="c51c4-103">Pobiera tożsamość bieżącego wątku Win32 dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="c51c4-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c51c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c51c4-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c51c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c51c4-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="c51c4-106">[in] Identyfikator wątku, który można pobrać bieżącego identyfikatora Win32</span><span class="sxs-lookup"><span data-stu-id="c51c4-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="c51c4-107">[out] Wskaźnik do bieżącego wątku Win32 wątku określonego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="c51c4-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c51c4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c51c4-108">Requirements</span></span>  
 <span data-ttu-id="c51c4-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c51c4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c51c4-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c51c4-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c51c4-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c51c4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c51c4-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c51c4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51c4-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c51c4-113">See Also</span></span>  
 [<span data-ttu-id="c51c4-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="c51c4-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
