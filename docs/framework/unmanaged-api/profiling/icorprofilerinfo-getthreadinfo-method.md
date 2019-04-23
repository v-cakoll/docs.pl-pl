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
ms.openlocfilehash: 0631afe149c7a179a6cda4b5e491ad28653ddee9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111920"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="7e1e3-102">ICorProfilerInfo::GetThreadInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e1e3-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="7e1e3-103">Pobiera bieżącą tożsamość wątku Win32 dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="7e1e3-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e1e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e1e3-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e1e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e1e3-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="7e1e3-106">[in] Identyfikator wątku, dla którego należy pobrać bieżącego identyfikatora Win32</span><span class="sxs-lookup"><span data-stu-id="7e1e3-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="7e1e3-107">[out] Wskaźnik do określonego wątku bieżący wątek Win32 identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="7e1e3-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e1e3-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e1e3-108">Requirements</span></span>  
 <span data-ttu-id="7e1e3-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e1e3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e1e3-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e1e3-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e1e3-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e1e3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e1e3-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e1e3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e1e3-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e1e3-113">See also</span></span>

- [<span data-ttu-id="7e1e3-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e1e3-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
