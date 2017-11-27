---
title: "ICorProfilerInfo::GetCurrentThreadID — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetCurrentThreadID
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 055a5f56f076cc29ca7ce5d45ecedd650e8f2f44
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="1b64a-102">ICorProfilerInfo::GetCurrentThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b64a-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="1b64a-103">Pobiera identyfikator bieżącego wątku, jeśli jest zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="1b64a-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b64a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b64a-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b64a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b64a-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="1b64a-106">[out] Wskaźnik do zwrócony identyfikator zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="1b64a-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b64a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b64a-107">Remarks</span></span>  
 <span data-ttu-id="1b64a-108">Jeśli bieżący wątek jest wątku czasu wykonywania wewnętrznego lub innych niezarządzany wątek `GetCurrentThreadID` zwraca CORPROF_E_NOT_MANAGED_THREAD jako HRESULT i wartość `pThreadId` parametr będzie równy null.</span><span class="sxs-lookup"><span data-stu-id="1b64a-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b64a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b64a-109">Requirements</span></span>  
 <span data-ttu-id="1b64a-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b64a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b64a-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b64a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b64a-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b64a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b64a-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b64a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b64a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b64a-114">See Also</span></span>  
 [<span data-ttu-id="1b64a-115">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="1b64a-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
