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
ms.openlocfilehash: 6a0f6dc9d2559bafed416d409063088d2f51c27d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445214"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="5574e-102">ICorProfilerCallback::AppDomainCreationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="5574e-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="5574e-103">Powiadamia profiler o tworzeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5574e-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5574e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5574e-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5574e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5574e-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="5574e-106">podczas Identyfikuje domenę, która jest tworzona.</span><span class="sxs-lookup"><span data-stu-id="5574e-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5574e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5574e-107">Remarks</span></span>  
 <span data-ttu-id="5574e-108">Identyfikator nie jest prawidłowy dla żadnego żądania informacji, dopóki nie zostanie wywołana metoda [ICorProfilerCallback:: AppDomainCreationFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5574e-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5574e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5574e-109">Requirements</span></span>  
 <span data-ttu-id="5574e-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5574e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5574e-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5574e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5574e-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5574e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5574e-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5574e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5574e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5574e-114">See also</span></span>

- [<span data-ttu-id="5574e-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="5574e-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
