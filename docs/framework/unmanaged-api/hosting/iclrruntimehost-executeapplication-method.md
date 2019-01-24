---
title: ICLRRuntimeHost::ExecuteApplication — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a68c210c8c87597e2f3e664ff67ff4ba3557323d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656365"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="cf292-102">ICLRRuntimeHost::ExecuteApplication — Metoda</span><span class="sxs-lookup"><span data-stu-id="cf292-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="cf292-103">Używane w oparte na manifeście scenariusze wdrażania technologii ClickOnce do określenia aplikacji zostanie uaktywniony w nowej domenie.</span><span class="sxs-lookup"><span data-stu-id="cf292-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="cf292-104">Aby uzyskać więcej informacji na temat tych scenariuszy, zobacz [wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="cf292-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf292-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf292-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="cf292-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf292-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="cf292-107">[in] Pełna nazwa aplikacji, zgodnie z definicją <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="cf292-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="cf292-108">[in] Liczbę ciągów zawartych w `ppwzManifestPaths` tablicy.</span><span class="sxs-lookup"><span data-stu-id="cf292-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="cf292-109">[in] Opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="cf292-109">[in] Optional.</span></span> <span data-ttu-id="cf292-110">Tablica ciągu, który zawiera ścieżki manifestu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf292-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="cf292-111">[in] Liczbę ciągów zawartych w `ppwzActivationData` tablicy.</span><span class="sxs-lookup"><span data-stu-id="cf292-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="cf292-112">[in] Opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="cf292-112">[in] Optional.</span></span> <span data-ttu-id="cf292-113">Tablica ciągu, który zawiera dane aktywacji aplikacji, takich jak część ciągu zapytania adresu URL dla aplikacji wdrożonych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cf292-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="cf292-114">[out] Wartość zwrócona z punktu wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf292-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf292-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cf292-115">Return Value</span></span>  
  
|<span data-ttu-id="cf292-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf292-116">HRESULT</span></span>|<span data-ttu-id="cf292-117">Opis</span><span class="sxs-lookup"><span data-stu-id="cf292-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf292-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf292-118">S_OK</span></span>|<span data-ttu-id="cf292-119">`ExecuteApplication` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="cf292-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="cf292-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cf292-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cf292-121">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="cf292-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cf292-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cf292-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cf292-123">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="cf292-123">The call timed out.</span></span>|  
|<span data-ttu-id="cf292-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cf292-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cf292-125">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="cf292-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cf292-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cf292-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cf292-127">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="cf292-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cf292-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cf292-128">E_FAIL</span></span>|<span data-ttu-id="cf292-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cf292-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cf292-130">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="cf292-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cf292-131">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cf292-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf292-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf292-132">Remarks</span></span>  
 <span data-ttu-id="cf292-133">`ExecuteApplication` Służy do aktywowania aplikacji ClickOnce w domenie nowo utworzonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf292-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="cf292-134">`pReturnValue` Parametr wyjściowy jest ustawiona na wartość zwracaną przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="cf292-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="cf292-135">Jeśli podasz wartość null dla `pReturnValue`, `ExecuteApplication` nie kończy się niepowodzeniem, ale nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="cf292-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cf292-136">Nie wywołuj [Metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda przed wywołaniem `ExecuteApplication` metodę, aby aktywować manifestu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf292-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="cf292-137">Jeśli `Start` najpierw jest wywoływana metoda `ExecuteApplication` wywołania metody zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="cf292-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf292-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf292-138">Requirements</span></span>  
 <span data-ttu-id="cf292-139">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf292-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf292-140">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf292-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf292-141">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf292-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf292-142">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf292-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf292-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf292-143">See also</span></span>
- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="cf292-144">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf292-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="cf292-145">SetAppDomainManager, metoda</span><span class="sxs-lookup"><span data-stu-id="cf292-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="cf292-146">Przewodnik: Pobieranie zestawów na żądanie przy użyciu interfejsu API wdrażania ClickOnce za pomocą Projektanta</span><span class="sxs-lookup"><span data-stu-id="cf292-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
