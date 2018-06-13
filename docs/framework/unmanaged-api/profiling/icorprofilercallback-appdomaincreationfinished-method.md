---
title: ICorProfilerCallback::AppDomainCreationFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b0017cff43f7a1b1bdd90806f50abb374a96dadf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450427"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="1e2fb-102">ICorProfilerCallback::AppDomainCreationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="1e2fb-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="1e2fb-103">Powiadamia profilera, czy domena aplikacji została utworzona.</span><span class="sxs-lookup"><span data-stu-id="1e2fb-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e2fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1e2fb-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e2fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1e2fb-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="1e2fb-106">[in] Określa domenę, która została utworzona.</span><span class="sxs-lookup"><span data-stu-id="1e2fb-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="1e2fb-107">[in] HRESULT, która wskazuje, czy Tworzenie domeny aplikacji została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1e2fb-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e2fb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e2fb-108">Remarks</span></span>  
 <span data-ttu-id="1e2fb-109">Identyfikator aplikacji jest nieprawidłowy dla żądania żadnych informacji do `AppDomainCreationFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="1e2fb-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="1e2fb-110">Niektóre elementy ładowania domeny aplikacji mogą nadal po `AppDomainCreationFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1e2fb-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="1e2fb-111">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="1e2fb-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="1e2fb-112">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część tworzenia domeny aplikacji zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1e2fb-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e2fb-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1e2fb-113">Requirements</span></span>  
 <span data-ttu-id="1e2fb-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e2fb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e2fb-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1e2fb-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e2fb-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e2fb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e2fb-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e2fb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2fb-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e2fb-118">See Also</span></span>  
 [<span data-ttu-id="1e2fb-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="1e2fb-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
