---
title: "ICorProfilerCallback::AppDomainCreationFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainCreationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d21198253e10434b37261d34cf12ef60c26f7e71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="22d86-102">ICorProfilerCallback::AppDomainCreationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="22d86-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="22d86-103">Powiadamia profilera, czy domena aplikacji została utworzona.</span><span class="sxs-lookup"><span data-stu-id="22d86-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d86-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22d86-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="22d86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22d86-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="22d86-106">[in] Określa domenę, która została utworzona.</span><span class="sxs-lookup"><span data-stu-id="22d86-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="22d86-107">[in] HRESULT, która wskazuje, czy Tworzenie domeny aplikacji została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="22d86-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22d86-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22d86-108">Remarks</span></span>  
 <span data-ttu-id="22d86-109">Identyfikator aplikacji jest nieprawidłowy dla żądania żadnych informacji do `AppDomainCreationFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="22d86-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="22d86-110">Niektóre elementy ładowania domeny aplikacji mogą nadal po `AppDomainCreationFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="22d86-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="22d86-111">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="22d86-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="22d86-112">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część tworzenia domeny aplikacji zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="22d86-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22d86-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22d86-113">Requirements</span></span>  
 <span data-ttu-id="22d86-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22d86-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22d86-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22d86-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22d86-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22d86-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22d86-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22d86-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d86-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22d86-118">See Also</span></span>  
 [<span data-ttu-id="22d86-119">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="22d86-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
