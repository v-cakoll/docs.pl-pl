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
ms.openlocfilehash: 17f7c985b27adbbb2a5c7ddc2bb62fc93a099a45
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763133"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="0d267-102">ICorProfilerCallback::AppDomainCreationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="0d267-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="0d267-103">Powiadamia program profilujący, że trwa tworzenie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d267-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d267-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d267-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d267-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d267-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="0d267-106">[in] Określa domenę, która jest tworzona.</span><span class="sxs-lookup"><span data-stu-id="0d267-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d267-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d267-107">Remarks</span></span>  
 <span data-ttu-id="0d267-108">Identyfikator jest nieprawidłowy dla każdego żądania informacje do momentu [icorprofilercallback::appdomaincreationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="0d267-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d267-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d267-109">Requirements</span></span>  
 <span data-ttu-id="0d267-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d267-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d267-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d267-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d267-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d267-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d267-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d267-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d267-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d267-114">See also</span></span>

- [<span data-ttu-id="0d267-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d267-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
