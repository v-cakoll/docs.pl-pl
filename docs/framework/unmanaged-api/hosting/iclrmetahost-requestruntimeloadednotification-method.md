---
title: ICLRMetaHost::RequestRuntimeLoadedNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f3ac053f12cb4bc37ab0bd16036fb561f8f176c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519128"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="1cccd-102">ICLRMetaHost::RequestRuntimeLoadedNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="1cccd-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="1cccd-103">Oferuje funkcję wywołania zwrotnego, która może być wywoływana, gdy typowe wersję środowiska uruchomieniowego (języka wspólnego CLR) języka jest ładowana jako pierwsza, ale jeszcze nie rozpoczęty.</span><span class="sxs-lookup"><span data-stu-id="1cccd-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="1cccd-104">Ta metoda zastępuje [lockclrversion —](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="1cccd-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cccd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1cccd-105">Syntax</span></span>  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cccd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cccd-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="1cccd-107">[in] Funkcja wywołania zwrotnego, która jest wywoływana po załadowaniu nowego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1cccd-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cccd-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1cccd-108">Return Value</span></span>  
 <span data-ttu-id="1cccd-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="1cccd-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1cccd-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1cccd-110">HRESULT</span></span>|<span data-ttu-id="1cccd-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1cccd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1cccd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1cccd-112">S_OK</span></span>|<span data-ttu-id="1cccd-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1cccd-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="1cccd-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1cccd-114">E_POINTER</span></span>|<span data-ttu-id="1cccd-115">`pCallbackFunction` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="1cccd-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cccd-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1cccd-116">Remarks</span></span>  
 <span data-ttu-id="1cccd-117">Wywołanie zwrotne działa w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1cccd-117">The callback works in the following way:</span></span>  
  
-   <span data-ttu-id="1cccd-118">Wywołanie zwrotne jest wywoływane tylko wtedy, gdy środowisko uruchomieniowe jest ładowany po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="1cccd-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
-   <span data-ttu-id="1cccd-119">Wywołanie zwrotne nie jest wywoływany w przypadku obciążeń współużytkowane tego samego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1cccd-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
-   <span data-ttu-id="1cccd-120">W przypadku obciążeń nie obsługującą środowiska uruchomieniowego są serializowane wywołania do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1cccd-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="1cccd-121">Funkcja wywołania zwrotnego zawiera poniższy prototyp:</span><span class="sxs-lookup"><span data-stu-id="1cccd-121">The callback function has the following prototype:</span></span>  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="1cccd-122">Prototypy funkcji wywołania zwrotnego są następujące:</span><span class="sxs-lookup"><span data-stu-id="1cccd-122">The callback function prototypes are as follows:</span></span>  
  
-   <span data-ttu-id="1cccd-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="1cccd-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   <span data-ttu-id="1cccd-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="1cccd-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="1cccd-125">Jeśli host zamierza obciążenia lub powodują, że innego środowiska uruchomieniowego do załadowania w sposób współużytkowane `pfnCallbackThreadSet` i `pfnCallbackThreadUnset` parametry, które znajdują się w wywołania zwrotnego funkcji muszą być używane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1cccd-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
-   <span data-ttu-id="1cccd-126">`pfnCallbackThreadSet` musi zostać wywołany przez wątek, który może spowodować obciążenia środowiska uruchomieniowego, przed próbą takie obciążenia.</span><span class="sxs-lookup"><span data-stu-id="1cccd-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
-   <span data-ttu-id="1cccd-127">`pfnCallbackThreadUnset` musi być wywoływana, gdy wątek już nie spowoduje obciążenia środowiska uruchomieniowego (i przed powrotem po początkowej wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="1cccd-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
-   <span data-ttu-id="1cccd-128">`pfnCallbackThreadSet` i `pfnCallbackThreadUnset` są nie obsługującą.</span><span class="sxs-lookup"><span data-stu-id="1cccd-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cccd-129">Hostowanie aplikacji nie mogą wywoływać `pfnCallbackThreadSet` i `pfnCallbackThreadUnset` poza zakresem `pCallbackFunction` parametru.</span><span class="sxs-lookup"><span data-stu-id="1cccd-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cccd-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1cccd-130">Requirements</span></span>  
 <span data-ttu-id="1cccd-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cccd-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cccd-132">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1cccd-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1cccd-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1cccd-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1cccd-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cccd-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cccd-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cccd-135">See also</span></span>
- [<span data-ttu-id="1cccd-136">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="1cccd-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="1cccd-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="1cccd-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
