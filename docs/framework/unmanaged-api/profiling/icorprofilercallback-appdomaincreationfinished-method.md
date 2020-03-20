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
ms.openlocfilehash: 8b3f7712436c001e5cd44f214f6edb06390abd41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177075"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="ebf36-102">ICorProfilerCallback::AppDomainCreationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="ebf36-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="ebf36-103">Powiadamia profiler, że domena aplikacji została utworzona.</span><span class="sxs-lookup"><span data-stu-id="ebf36-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf36-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebf36-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="ebf36-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebf36-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="ebf36-106">\[w] Identyfikuje domenę, która została utworzona.</span><span class="sxs-lookup"><span data-stu-id="ebf36-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="ebf36-107">\[w] HRESULT, który wskazuje, czy tworzenie domeny aplikacji zostało pomyślnie zakończone.</span><span class="sxs-lookup"><span data-stu-id="ebf36-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="ebf36-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebf36-108">Remarks</span></span>  
 <span data-ttu-id="ebf36-109">Identyfikator aplikacji nie jest prawidłowy dla `AppDomainCreationFinished` każdego żądania informacji, dopóki metoda nie zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="ebf36-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="ebf36-110">Niektóre części ładowania domeny aplikacji może `AppDomainCreationFinished` być kontynuowana po wywołaniu zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="ebf36-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="ebf36-111">Błąd HRESULT `hrStatus` w wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="ebf36-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ebf36-112">Jednak sukces HRESULT `hrStatus` w wskazuje tylko, że pierwsza część tworzenia domeny aplikacji powiodła się.</span><span class="sxs-lookup"><span data-stu-id="ebf36-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf36-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebf36-113">Requirements</span></span>  
 <span data-ttu-id="ebf36-114">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf36-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf36-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ebf36-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ebf36-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebf36-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebf36-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf36-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf36-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebf36-118">See also</span></span>

- [<span data-ttu-id="ebf36-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ebf36-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
