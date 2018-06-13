---
title: ICLRControl::SetAppDomainManagerType — Metoda
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be778fed910b2cbdbf5e9ae7754abae437ef6bec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433737"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="06c68-102">ICLRControl::SetAppDomainManagerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="06c68-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="06c68-103">Ustawia typ pochodny typu <xref:System.AppDomainManager> jako typ menedżerom domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06c68-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06c68-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06c68-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06c68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06c68-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="06c68-106">[in] Nazwa zestawu, w którym żądany typ pochodny <xref:System.AppDomainManager> jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="06c68-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="06c68-107">[in] Nazwa typu w `pwzAppDomainManagerAssembly` parametr, który implementuje możliwości <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="06c68-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06c68-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="06c68-108">Return Value</span></span>  
  
|<span data-ttu-id="06c68-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06c68-109">HRESULT</span></span>|<span data-ttu-id="06c68-110">Opis</span><span class="sxs-lookup"><span data-stu-id="06c68-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06c68-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="06c68-111">S_OK</span></span>|<span data-ttu-id="06c68-112">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="06c68-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="06c68-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="06c68-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="06c68-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="06c68-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="06c68-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="06c68-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="06c68-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="06c68-116">The call timed out.</span></span>|  
|<span data-ttu-id="06c68-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="06c68-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="06c68-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="06c68-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="06c68-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="06c68-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="06c68-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="06c68-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="06c68-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="06c68-121">E_FAIL</span></span>|<span data-ttu-id="06c68-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="06c68-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="06c68-123">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="06c68-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="06c68-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="06c68-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06c68-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06c68-125">Requirements</span></span>  
 <span data-ttu-id="06c68-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06c68-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06c68-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="06c68-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="06c68-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06c68-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06c68-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06c68-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06c68-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06c68-130">See Also</span></span>  
 [<span data-ttu-id="06c68-131">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="06c68-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="06c68-132">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="06c68-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
