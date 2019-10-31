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
ms.openlocfilehash: 23f868bba2dc058d99f1c5c09e9b311b1ff3634a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140890"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="87e54-102">ICLRMetaHost::RequestRuntimeLoadedNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="87e54-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="87e54-103">Zapewnia funkcję wywołania zwrotnego, która jest gwarantowana, gdy wersja środowiska uruchomieniowego języka wspólnego (CLR) jest najpierw ładowana, ale jeszcze nie została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="87e54-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="87e54-104">Ta metoda zastępuje funkcję [LockClrVersion —](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="87e54-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e54-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="87e54-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87e54-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="87e54-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="87e54-107">podczas Funkcja wywołania zwrotnego, która jest wywoływana po załadowaniu nowego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="87e54-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87e54-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="87e54-108">Return Value</span></span>  
 <span data-ttu-id="87e54-109">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="87e54-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="87e54-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87e54-110">HRESULT</span></span>|<span data-ttu-id="87e54-111">Opis</span><span class="sxs-lookup"><span data-stu-id="87e54-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87e54-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="87e54-112">S_OK</span></span>|<span data-ttu-id="87e54-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="87e54-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="87e54-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="87e54-114">E_POINTER</span></span>|<span data-ttu-id="87e54-115">`pCallbackFunction` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="87e54-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87e54-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87e54-116">Remarks</span></span>  
 <span data-ttu-id="87e54-117">Wywołanie zwrotne działa w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="87e54-117">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="87e54-118">Wywołanie zwrotne jest wywoływane tylko wtedy, gdy środowisko uruchomieniowe jest ładowane po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="87e54-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="87e54-119">Wywołanie zwrotne nie jest wywoływane dla obciążeń współużytkowanych tego samego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="87e54-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="87e54-120">W przypadku obciążeń środowiska uruchomieniowego, które nie są współużytkowane, wywołania funkcji wywołania zwrotnego są serializowane.</span><span class="sxs-lookup"><span data-stu-id="87e54-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="87e54-121">Funkcja wywołania zwrotnego ma następujący prototyp:</span><span class="sxs-lookup"><span data-stu-id="87e54-121">The callback function has the following prototype:</span></span>  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="87e54-122">Prototypy funkcji wywołania zwrotnego są następujące:</span><span class="sxs-lookup"><span data-stu-id="87e54-122">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="87e54-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="87e54-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="87e54-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="87e54-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="87e54-125">Jeśli host zamierza załadować lub spowodować załadowanie innego środowiska uruchomieniowego w sposób współużytkowany, należy użyć parametrów `pfnCallbackThreadSet` i `pfnCallbackThreadUnset`, które są dostępne w funkcji wywołania zwrotnego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="87e54-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="87e54-126">`pfnCallbackThreadSet` musi być wywoływana przez wątek, który może spowodować obciążenie w czasie wykonywania przed próbą takiego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="87e54-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="87e54-127">należy wywołać `pfnCallbackThreadUnset`, gdy wątek nie będzie już powodował obciążenia w czasie wykonywania (i przed powrotem z początkowego wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="87e54-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="87e54-128">`pfnCallbackThreadSet` i `pfnCallbackThreadUnset` są zarówno niewspółpracujące.</span><span class="sxs-lookup"><span data-stu-id="87e54-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87e54-129">Aplikacje hosta nie mogą wywoływać `pfnCallbackThreadSet` i `pfnCallbackThreadUnset` poza zakresem parametru `pCallbackFunction`.</span><span class="sxs-lookup"><span data-stu-id="87e54-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e54-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87e54-130">Requirements</span></span>  
 <span data-ttu-id="87e54-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87e54-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e54-132">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="87e54-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="87e54-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87e54-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87e54-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87e54-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e54-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87e54-135">See also</span></span>

- [<span data-ttu-id="87e54-136">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="87e54-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="87e54-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="87e54-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
