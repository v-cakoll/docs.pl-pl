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
ms.openlocfilehash: 9ac041db64a874cc143657c601f30e4482dd2462
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="ad0a5-102">ICLRMetaHost::RequestRuntimeLoadedNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad0a5-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="ad0a5-103">Udostępnia funkcję wywołania zwrotnego, które na pewno jest wywoływana, gdy wspólne środowisko uruchomieniowe (języka wspólnego CLR) w wersji językowej jest ładowana jako pierwsza, ale jeszcze nie uruchomiono.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="ad0a5-104">Ta metoda zastępuje [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad0a5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad0a5-105">Syntax</span></span>  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad0a5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad0a5-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="ad0a5-107">[in] Funkcja wywołania zwrotnego, które jest wywoływane, gdy nowe środowisko uruchomieniowe został załadowany.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad0a5-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ad0a5-108">Return Value</span></span>  
 <span data-ttu-id="ad0a5-109">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ad0a5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad0a5-110">HRESULT</span></span>|<span data-ttu-id="ad0a5-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ad0a5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad0a5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad0a5-112">S_OK</span></span>|<span data-ttu-id="ad0a5-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="ad0a5-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ad0a5-114">E_POINTER</span></span>|<span data-ttu-id="ad0a5-115">`pCallbackFunction` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad0a5-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad0a5-116">Remarks</span></span>  
 <span data-ttu-id="ad0a5-117">Wywołania zwrotnego działa w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ad0a5-117">The callback works in the following way:</span></span>  
  
-   <span data-ttu-id="ad0a5-118">Wywołanie zwrotne jest wywoływane tylko wtedy, gdy środowisko wykonawcze jest załadowany po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
-   <span data-ttu-id="ad0a5-119">Wywołanie zwrotne nie jest wywoływany w przypadku współużytkowane obciążeń tego samego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
-   <span data-ttu-id="ad0a5-120">W przypadku obciążeń runtime nie obsługującą wywołań funkcji wywołania zwrotnego są serializowane.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="ad0a5-121">Funkcja wywołania zwrotnego zawiera następujące prototypu:</span><span class="sxs-lookup"><span data-stu-id="ad0a5-121">The callback function has the following prototype:</span></span>  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="ad0a5-122">Prototypy funkcji wywołania zwrotnego są następujące:</span><span class="sxs-lookup"><span data-stu-id="ad0a5-122">The callback function prototypes are as follows:</span></span>  
  
-   <span data-ttu-id="ad0a5-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="ad0a5-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   <span data-ttu-id="ad0a5-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="ad0a5-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="ad0a5-125">Jeśli host zamierza obciążenia lub spowodować innego środowiska uruchomieniowego do załadowania w sposób współużytkowane `pfnCallbackThreadSet` i `pfnCallbackThreadUnset` parametrów, które są podane podczas wywołania zwrotnego funkcja musi być używany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ad0a5-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
-   <span data-ttu-id="ad0a5-126">`pfnCallbackThreadSet` musi zostać wywołany w wątku, który może spowodować, że obciążenia środowiska wykonawczego przed próbą takie obciążenia.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
-   <span data-ttu-id="ad0a5-127">`pfnCallbackThreadUnset` musi być wywoływana, gdy wątek już spowoduje obciążenia środowiska uruchomieniowego (i przed powrotem z wywołania zwrotnego początkowej).</span><span class="sxs-lookup"><span data-stu-id="ad0a5-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
-   <span data-ttu-id="ad0a5-128">`pfnCallbackThreadSet` i `pfnCallbackThreadUnset` są nie obsługującą.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad0a5-129">Host aplikacji nie mogą wywoływać `pfnCallbackThreadSet` i `pfnCallbackThreadUnset` poza zakresem `pCallbackFunction` parametru.</span><span class="sxs-lookup"><span data-stu-id="ad0a5-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad0a5-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad0a5-130">Requirements</span></span>  
 <span data-ttu-id="ad0a5-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad0a5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad0a5-132">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ad0a5-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ad0a5-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad0a5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad0a5-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad0a5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0a5-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad0a5-135">See Also</span></span>  
 [<span data-ttu-id="ad0a5-136">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad0a5-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="ad0a5-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="ad0a5-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
