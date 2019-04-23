---
title: ICorProfilerCallback::AppDomainShutdownFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d927bd21903bda6fd8a34992145eb495a3342382
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081960"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="8ee5e-102">ICorProfilerCallback::AppDomainShutdownFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ee5e-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="8ee5e-103">Powiadamia program profilujący, że zostało zwolnione z procesu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ee5e-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ee5e-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ee5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ee5e-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="8ee5e-106">[in] Określa domenę, w której są przechowywane zestawy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ee5e-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="8ee5e-107">[in] Wartość HRESULT, która wskazuje, czy domena aplikacji został pomyślnie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="8ee5e-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ee5e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ee5e-108">Remarks</span></span>  
 <span data-ttu-id="8ee5e-109">Wartość `appDomainId` jest nieprawidłowa dla żądania informacji po [icorprofilercallback::appdomainshutdownstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="8ee5e-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="8ee5e-110">Niektóre części rozładowywania domeny aplikacji może kontynuować po `AppDomainCreationFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8ee5e-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="8ee5e-111">Błąd HRESULT w `hrStatus` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="8ee5e-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="8ee5e-112">Jednak sukcesów wartość HRESULT w `hrStatus` wskazuje tylko, że pierwsza część rozładowywania domeny aplikacji zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8ee5e-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ee5e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ee5e-113">Requirements</span></span>  
 <span data-ttu-id="8ee5e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ee5e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ee5e-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ee5e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ee5e-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ee5e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ee5e-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ee5e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee5e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ee5e-118">See also</span></span>

- [<span data-ttu-id="8ee5e-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ee5e-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
