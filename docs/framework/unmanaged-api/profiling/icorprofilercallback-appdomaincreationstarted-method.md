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
ms.openlocfilehash: 2bffa383734a96a32595b018fd6d9b3dc62d5526
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484761"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="d1a9f-102">ICorProfilerCallback::AppDomainCreationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1a9f-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="d1a9f-103">Powiadamia program profilujący, że trwa tworzenie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d1a9f-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1a9f-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1a9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1a9f-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="d1a9f-106">[in] Określa domenę, która jest tworzona.</span><span class="sxs-lookup"><span data-stu-id="d1a9f-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1a9f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1a9f-107">Remarks</span></span>  
 <span data-ttu-id="d1a9f-108">Identyfikator jest nieprawidłowy dla każdego żądania informacje do momentu [icorprofilercallback::appdomaincreationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d1a9f-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1a9f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1a9f-109">Requirements</span></span>  
 <span data-ttu-id="d1a9f-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1a9f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1a9f-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1a9f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1a9f-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1a9f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1a9f-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1a9f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a9f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1a9f-114">See also</span></span>
- [<span data-ttu-id="d1a9f-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1a9f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
