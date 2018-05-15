---
title: ICorProfilerCallback::AppDomainCreationStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 141fd99ab0a96b20bfe06f1eb8612dd92b6cccc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="29d9a-102">ICorProfilerCallback::AppDomainCreationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="29d9a-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="29d9a-103">Powiadamia profiler jest tworzony domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29d9a-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29d9a-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29d9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29d9a-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="29d9a-106">[in] Określa domenę, która jest tworzona.</span><span class="sxs-lookup"><span data-stu-id="29d9a-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29d9a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29d9a-107">Remarks</span></span>  
 <span data-ttu-id="29d9a-108">Identyfikator jest nieprawidłowy dla żądania żadnych informacji do [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="29d9a-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d9a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29d9a-109">Requirements</span></span>  
 <span data-ttu-id="29d9a-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29d9a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d9a-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29d9a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29d9a-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29d9a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29d9a-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29d9a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d9a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29d9a-114">See Also</span></span>  
 [<span data-ttu-id="29d9a-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="29d9a-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
