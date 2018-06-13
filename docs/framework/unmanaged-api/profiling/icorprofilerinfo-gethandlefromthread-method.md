---
title: ICorProfilerInfo::GetHandleFromThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9658ad8a1963d3747fb7c23dce84790a30b17db3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453225"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="8b979-102">ICorProfilerInfo::GetHandleFromThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b979-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="8b979-103">Identyfikator wątku jest mapowany na dojście wątku Win32.</span><span class="sxs-lookup"><span data-stu-id="8b979-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b979-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b979-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b979-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b979-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="8b979-106">[in] Identyfikator wątku, aby mógł zostać zmapowany.</span><span class="sxs-lookup"><span data-stu-id="8b979-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="8b979-107">[out] Wskaźnik do dojście wątku Win32.</span><span class="sxs-lookup"><span data-stu-id="8b979-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b979-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b979-108">Remarks</span></span>  
 <span data-ttu-id="8b979-109">Profiler należy wywołać Win32 `DuplicateHandle` funkcja na uchwycie przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="8b979-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b979-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b979-110">Requirements</span></span>  
 <span data-ttu-id="8b979-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b979-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b979-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b979-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b979-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b979-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b979-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b979-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b979-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b979-115">See Also</span></span>  
 [<span data-ttu-id="8b979-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b979-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
