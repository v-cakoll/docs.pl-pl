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
ms.openlocfilehash: 8f1eb2354536a436bd6ae41cf70bf11549982d5e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612596"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="d6eb3-102">ICorProfilerInfo::GetHandleFromThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="d6eb3-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="d6eb3-103">Identyfikator wątku jest mapowany na dojście wątku Win32.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6eb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6eb3-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6eb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6eb3-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d6eb3-106">[in] Identyfikator wątku, które mają być mapowane.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="d6eb3-107">[out] Wskaźnik do uchwytu wątku Win32.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6eb3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6eb3-108">Remarks</span></span>  
 <span data-ttu-id="d6eb3-109">Program profilujący musi wywołać Win32 `DuplicateHandle` funkcji w dojściu przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6eb3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6eb3-110">Requirements</span></span>  
 <span data-ttu-id="d6eb3-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6eb3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6eb3-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6eb3-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6eb3-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6eb3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6eb3-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6eb3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6eb3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6eb3-115">See also</span></span>
- [<span data-ttu-id="d6eb3-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d6eb3-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
