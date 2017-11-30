---
title: "ICorProfilerInfo::GetHandleFromThread — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetHandleFromThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be925bbbcc86785feae28353dbc6563974aae2c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="0860e-102">ICorProfilerInfo::GetHandleFromThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="0860e-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="0860e-103">Identyfikator wątku jest mapowany na dojście wątku Win32.</span><span class="sxs-lookup"><span data-stu-id="0860e-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0860e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0860e-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0860e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0860e-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="0860e-106">[in] Identyfikator wątku, aby mógł zostać zmapowany.</span><span class="sxs-lookup"><span data-stu-id="0860e-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="0860e-107">[out] Wskaźnik do dojście wątku Win32.</span><span class="sxs-lookup"><span data-stu-id="0860e-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0860e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0860e-108">Remarks</span></span>  
 <span data-ttu-id="0860e-109">Profiler należy wywołać Win32 `DuplicateHandle` funkcja na uchwycie przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="0860e-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0860e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0860e-110">Requirements</span></span>  
 <span data-ttu-id="0860e-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0860e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0860e-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0860e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0860e-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0860e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0860e-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0860e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0860e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0860e-115">See Also</span></span>  
 [<span data-ttu-id="0860e-116">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="0860e-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
