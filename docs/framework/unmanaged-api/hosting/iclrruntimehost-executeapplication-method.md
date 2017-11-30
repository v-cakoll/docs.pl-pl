---
title: "ICLRRuntimeHost::ExecuteApplication — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteApplication
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3b43365ad208dae5b28b31cf494de37ca670d791
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="c7a50-102">ICLRRuntimeHost::ExecuteApplication — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7a50-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="c7a50-103">Używane w na podstawie manifestu scenariuszy wdrażania ClickOnce do określenia aplikacji do aktywacji w nowej domenie.</span><span class="sxs-lookup"><span data-stu-id="c7a50-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="c7a50-104">Aby uzyskać więcej informacji na temat tych scenariuszy, zobacz [zabezpieczenia ClickOnce i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="c7a50-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7a50-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7a50-105">Syntax</span></span>  
  
```  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7a50-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7a50-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="c7a50-107">[in] Pełna nazwa aplikacji, zgodnie z definicją <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="c7a50-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="c7a50-108">[in] Liczbę ciągów zawartych w `ppwzManifestPaths` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c7a50-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="c7a50-109">[in] Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c7a50-109">[in] Optional.</span></span> <span data-ttu-id="c7a50-110">Tablica ciągów, zawierająca ścieżek manifestu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7a50-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="c7a50-111">[in] Liczbę ciągów zawartych w `ppwzActivationData` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c7a50-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="c7a50-112">[in] Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c7a50-112">[in] Optional.</span></span> <span data-ttu-id="c7a50-113">Tablica ciąg zawierający dane aktywacji aplikacji, takich jak część ciągu zapytania adres URL aplikacje wdrożone za pośrednictwem sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c7a50-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="c7a50-114">[out] Wartość zwrócona z punktu wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7a50-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7a50-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c7a50-115">Return Value</span></span>  
  
|<span data-ttu-id="c7a50-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7a50-116">HRESULT</span></span>|<span data-ttu-id="c7a50-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c7a50-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7a50-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7a50-118">S_OK</span></span>|<span data-ttu-id="c7a50-119">`ExecuteApplication`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c7a50-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="c7a50-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7a50-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7a50-121">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="c7a50-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7a50-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7a50-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7a50-123">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="c7a50-123">The call timed out.</span></span>|  
|<span data-ttu-id="c7a50-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7a50-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7a50-125">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="c7a50-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7a50-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7a50-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7a50-127">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="c7a50-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7a50-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7a50-128">E_FAIL</span></span>|<span data-ttu-id="c7a50-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c7a50-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7a50-130">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="c7a50-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7a50-131">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c7a50-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7a50-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7a50-132">Remarks</span></span>  
 <span data-ttu-id="c7a50-133">`ExecuteApplication`Służy do aktywowania aplikacji ClickOnce w domenie nowo utworzonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7a50-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="c7a50-134">`pReturnValue` Parametr wyjściowy ma ustawioną wartość zwrócona przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c7a50-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="c7a50-135">Jeśli zostanie podana wartość null dla `pReturnValue`, `ExecuteApplication` nie kończy się niepowodzeniem, ale nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="c7a50-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7a50-136">Nie wywołuj [Metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda przed wywołaniem `ExecuteApplication` metodę, aby aktywować manifest aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7a50-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="c7a50-137">Jeśli `Start` metoda jest wywoływana po pierwsze, `ExecuteApplication` wywołanie metody zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c7a50-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7a50-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7a50-138">Requirements</span></span>  
 <span data-ttu-id="c7a50-139">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a50-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a50-140">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7a50-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7a50-141">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7a50-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7a50-142">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a50-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a50-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7a50-143">See Also</span></span>  
 <xref:System.ActivationContext>  
 <xref:System.AppDomainManager>  
 <xref:System.ApplicationIdentity>  
 [<span data-ttu-id="c7a50-144">ICLRRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="c7a50-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="c7a50-145">SetAppDomainManager — metoda</span><span class="sxs-lookup"><span data-stu-id="c7a50-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)  
 [<span data-ttu-id="c7a50-146">Wskazówki: Pobieranie zestawów na żądanie przy użyciu interfejsu API przy użyciu narzędzia Projektant wdrażania ClickOnce</span><span class="sxs-lookup"><span data-stu-id="c7a50-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
