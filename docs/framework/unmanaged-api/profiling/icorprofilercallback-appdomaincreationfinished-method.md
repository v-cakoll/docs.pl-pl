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
ms.openlocfilehash: 76f56971223154d3ed966c272081049adf30de54
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500497"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="04e6c-102">ICorProfilerCallback::AppDomainCreationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="04e6c-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="04e6c-103">Powiadamia profiler o utworzeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="04e6c-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04e6c-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="04e6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04e6c-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="04e6c-106">\[w programie] identyfikuje domenę, która została utworzona.</span><span class="sxs-lookup"><span data-stu-id="04e6c-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="04e6c-107">\[w] wynik HRESULT wskazujący, czy Tworzenie domeny aplikacji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="04e6c-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="04e6c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04e6c-108">Remarks</span></span>  
 <span data-ttu-id="04e6c-109">Identyfikator aplikacji nie jest prawidłowy dla żadnego żądania informacji, dopóki `AppDomainCreationFinished` Metoda nie zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="04e6c-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="04e6c-110">Niektóre części ładowania domeny aplikacji mogą być kontynuowane po `AppDomainCreationFinished` wywołaniu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="04e6c-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="04e6c-111">Błąd HRESULT w elemencie `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="04e6c-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="04e6c-112">Jednak powodzenie HRESULT w programie `hrStatus` wskazuje tylko, że pierwsza część tworzenia domeny aplikacji zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="04e6c-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e6c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04e6c-113">Requirements</span></span>  
 <span data-ttu-id="04e6c-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e6c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e6c-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="04e6c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04e6c-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="04e6c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04e6c-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e6c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e6c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04e6c-118">See also</span></span>

- [<span data-ttu-id="04e6c-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="04e6c-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
