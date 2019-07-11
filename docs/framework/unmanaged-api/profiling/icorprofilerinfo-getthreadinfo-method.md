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
ms.openlocfilehash: 405d5ff49ba7bc2e5204f00cf50c30822354e56d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775585"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="744c5-102">ICorProfilerInfo::GetThreadInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="744c5-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="744c5-103">Pobiera bieżącą tożsamość wątku Win32 dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="744c5-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="744c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="744c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="744c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="744c5-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="744c5-106">[in] Identyfikator wątku, dla którego należy pobrać bieżącego identyfikatora Win32</span><span class="sxs-lookup"><span data-stu-id="744c5-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="744c5-107">[out] Wskaźnik do określonego wątku bieżący wątek Win32 identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="744c5-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="744c5-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="744c5-108">Requirements</span></span>  
 <span data-ttu-id="744c5-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="744c5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="744c5-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="744c5-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="744c5-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="744c5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="744c5-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="744c5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744c5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="744c5-113">See also</span></span>

- [<span data-ttu-id="744c5-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="744c5-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
