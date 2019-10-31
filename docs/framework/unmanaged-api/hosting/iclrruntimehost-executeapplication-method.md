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
ms.openlocfilehash: 4b56ffab8fb6a9ef70b51421f9cdc5535111e527
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120487"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="169bf-102">ICLRRuntimeHost::ExecuteApplication — Metoda</span><span class="sxs-lookup"><span data-stu-id="169bf-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="169bf-103">Używany w scenariuszach wdrażania ClickOnce opartych na manifestach, aby określić aplikację, która ma zostać aktywowana w nowej domenie.</span><span class="sxs-lookup"><span data-stu-id="169bf-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="169bf-104">Aby uzyskać więcej informacji na temat tych scenariuszy, zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="169bf-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="169bf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="169bf-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="169bf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="169bf-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="169bf-107">podczas Pełna nazwa aplikacji zgodnie z definicją dla <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="169bf-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="169bf-108">podczas Liczba ciągów zawartych w tablicy `ppwzManifestPaths`.</span><span class="sxs-lookup"><span data-stu-id="169bf-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="169bf-109">podczas Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="169bf-109">[in] Optional.</span></span> <span data-ttu-id="169bf-110">Tablica ciągów zawierająca ścieżki manifestu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="169bf-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="169bf-111">podczas Liczba ciągów zawartych w tablicy `ppwzActivationData`.</span><span class="sxs-lookup"><span data-stu-id="169bf-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="169bf-112">podczas Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="169bf-112">[in] Optional.</span></span> <span data-ttu-id="169bf-113">Tablica ciągów zawierająca dane aktywacji aplikacji, na przykład część ciągu zapytania w adresie URL dla aplikacji wdrożonych za pośrednictwem sieci Web.</span><span class="sxs-lookup"><span data-stu-id="169bf-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="169bf-114">określoną Wartość zwracana z punktu wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="169bf-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="169bf-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="169bf-115">Return Value</span></span>  
  
|<span data-ttu-id="169bf-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="169bf-116">HRESULT</span></span>|<span data-ttu-id="169bf-117">Opis</span><span class="sxs-lookup"><span data-stu-id="169bf-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="169bf-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="169bf-118">S_OK</span></span>|<span data-ttu-id="169bf-119">`ExecuteApplication` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="169bf-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="169bf-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="169bf-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="169bf-121">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="169bf-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="169bf-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="169bf-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="169bf-123">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="169bf-123">The call timed out.</span></span>|  
|<span data-ttu-id="169bf-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="169bf-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="169bf-125">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="169bf-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="169bf-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="169bf-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="169bf-127">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="169bf-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="169bf-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="169bf-128">E_FAIL</span></span>|<span data-ttu-id="169bf-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="169bf-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="169bf-130">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="169bf-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="169bf-131">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="169bf-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="169bf-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="169bf-132">Remarks</span></span>  
 <span data-ttu-id="169bf-133">`ExecuteApplication` służy do uaktywniania aplikacji ClickOnce w nowo utworzonej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="169bf-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="169bf-134">Parametr wyjściowy `pReturnValue` ma ustawioną wartość zwróconą przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="169bf-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="169bf-135">Jeśli podasz wartość null dla `pReturnValue`, `ExecuteApplication` nie powiedzie się, ale nie zwróci wartości.</span><span class="sxs-lookup"><span data-stu-id="169bf-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="169bf-136">Nie wywołuj metody [startowej](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) przed wywołaniem metody `ExecuteApplication` w celu aktywowania aplikacji opartej na manifeście.</span><span class="sxs-lookup"><span data-stu-id="169bf-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="169bf-137">Jeśli metoda `Start` jest wywoływana jako pierwsza, wywołanie metody `ExecuteApplication` zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="169bf-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="169bf-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="169bf-138">Requirements</span></span>  
 <span data-ttu-id="169bf-139">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="169bf-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="169bf-140">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="169bf-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="169bf-141">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="169bf-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="169bf-142">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="169bf-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169bf-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="169bf-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="169bf-144">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="169bf-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="169bf-145">SetAppDomainManager, metoda</span><span class="sxs-lookup"><span data-stu-id="169bf-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="169bf-146">Przewodnik: pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce za pomocą Projektanta</span><span class="sxs-lookup"><span data-stu-id="169bf-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
