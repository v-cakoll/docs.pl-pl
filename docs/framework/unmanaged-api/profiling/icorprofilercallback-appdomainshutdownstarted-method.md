---
title: ICorProfilerCallback::AppDomainShutdownStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9d1cf182eaf6f245baa5d898bac3ca7d3190234
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763092"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="25769-102">ICorProfilerCallback::AppDomainShutdownStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="25769-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="25769-103">Powiadamia program profilujący, że Trwa zwalnianie domeny aplikacji z procesu.</span><span class="sxs-lookup"><span data-stu-id="25769-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25769-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25769-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25769-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25769-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="25769-106">[in] Określa domenę, w której są przechowywane zestawy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="25769-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25769-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25769-107">Remarks</span></span>  
 <span data-ttu-id="25769-108">Wartość `appDomainId` jest nieprawidłowy w przypadku każdego żądania informacji po `AppDomainShutdownStarted` metoda zwraca — jest to programu profilującego ostatniego masz szansę, aby uzyskać informacje na temat tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="25769-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25769-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25769-109">Requirements</span></span>  
 <span data-ttu-id="25769-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25769-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25769-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="25769-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25769-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25769-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25769-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25769-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25769-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25769-114">See also</span></span>

- [<span data-ttu-id="25769-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="25769-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
