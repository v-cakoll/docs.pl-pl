---
title: ICorProfilerInfo::GetCurrentThreadID — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 802072f3a0151aabc5ca5796df57ea7c694a2070
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179039"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="5848d-102">ICorProfilerInfo::GetCurrentThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="5848d-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="5848d-103">Pobiera identyfikator bieżącego wątku, jeśli jest wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="5848d-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5848d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5848d-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5848d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5848d-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="5848d-106">[out] Wskaźnik do zwrócony identyfikator wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="5848d-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5848d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5848d-107">Remarks</span></span>  
 <span data-ttu-id="5848d-108">Jeśli bieżący wątek jest Wątek wewnętrznego środowiska uruchomieniowego lub innych wątek niezarządzany `GetCurrentThreadID` zwraca CORPROF_E_NOT_MANAGED_THREAD jako HRESULT i wartością zwróconą `pThreadId` parametr będzie równy null.</span><span class="sxs-lookup"><span data-stu-id="5848d-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5848d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5848d-109">Requirements</span></span>  
 <span data-ttu-id="5848d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5848d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5848d-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5848d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5848d-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5848d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5848d-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5848d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5848d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5848d-114">See also</span></span>

- [<span data-ttu-id="5848d-115">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="5848d-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
