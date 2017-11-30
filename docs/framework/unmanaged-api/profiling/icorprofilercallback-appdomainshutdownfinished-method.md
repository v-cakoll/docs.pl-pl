---
title: "ICorProfilerCallback::AppDomainShutdownFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainShutdownFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 443f5cd48693d6ac3ce732746666bd2d5e3786fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="f656d-102">ICorProfilerCallback::AppDomainShutdownFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="f656d-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="f656d-103">Powiadamia profilera, czy został zwolniony z procesu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f656d-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f656d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f656d-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f656d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f656d-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="f656d-106">[in] Identyfikuje domenę, w której są przechowywane zestawów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f656d-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="f656d-107">[in] HRESULT, która wskazuje, czy domena aplikacji został pomyślnie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="f656d-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f656d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f656d-108">Remarks</span></span>  
 <span data-ttu-id="f656d-109">Wartość `appDomainId` jest nieprawidłowa dla żądania informacji po [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) zwraca metody.</span><span class="sxs-lookup"><span data-stu-id="f656d-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="f656d-110">Niektóre elementy zwolnienie domeny aplikacji mogą nadal po `AppDomainCreationFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="f656d-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="f656d-111">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="f656d-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f656d-112">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część zwolnienie domeny aplikacji zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f656d-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f656d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f656d-113">Requirements</span></span>  
 <span data-ttu-id="f656d-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f656d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f656d-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f656d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f656d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f656d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f656d-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f656d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f656d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f656d-118">See Also</span></span>  
 [<span data-ttu-id="f656d-119">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="f656d-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
