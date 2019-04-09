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
ms.openlocfilehash: 35dac5fd000f5ae30af917e3813239b2e365e64a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153988"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="2eb9b-102">ICorProfilerCallback::AppDomainCreationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="2eb9b-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="2eb9b-103">Powiadamia program profilujący, że utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2eb9b-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eb9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2eb9b-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="2eb9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2eb9b-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="2eb9b-106">[in] Identyfikuje domeny, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="2eb9b-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="2eb9b-107">[in] Wartość HRESULT, która wskazuje, czy Tworzenie domeny aplikacji została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2eb9b-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2eb9b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2eb9b-108">Remarks</span></span>  
 <span data-ttu-id="2eb9b-109">Identyfikator aplikacji jest nieprawidłowa dla każdego żądania informacje do momentu `AppDomainCreationFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="2eb9b-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="2eb9b-110">Niektóre części podczas ładowania domeny aplikacji może kontynuować po `AppDomainCreationFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2eb9b-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="2eb9b-111">Błąd HRESULT w `hrStatus` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="2eb9b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="2eb9b-112">Jednak sukcesów wartość HRESULT w `hrStatus` wskazuje tylko, że pierwsza część tworzenia domeny aplikacji zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2eb9b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eb9b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2eb9b-113">Requirements</span></span>  
 <span data-ttu-id="2eb9b-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eb9b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eb9b-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2eb9b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2eb9b-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2eb9b-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2eb9b-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2eb9b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2eb9b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2eb9b-118">See also</span></span>

- [<span data-ttu-id="2eb9b-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2eb9b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
