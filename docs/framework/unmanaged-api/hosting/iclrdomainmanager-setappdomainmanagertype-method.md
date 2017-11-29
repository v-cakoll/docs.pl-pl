---
title: "ICLRDomainManager::SetAppDomainManagerType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17c99d21155d8f985ea455e171067855edcafedc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="6ef2e-102">ICLRDomainManager::SetAppDomainManagerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ef2e-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="6ef2e-103">Określa typ pochodny <xref:System.AppDomainManager?displayProperty=nameWithType> klasy Menedżer domeny aplikacji, które będą używane do inicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6ef2e-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ef2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ef2e-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ef2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ef2e-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="6ef2e-106">[in] Wyświetlana nazwa zestawu zawierającego typ Menedżer domeny aplikacji; na przykład: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="6ef2e-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="6ef2e-107">[in] Nazwa typu Menedżer domeny aplikacji, włącznie z przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="6ef2e-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="6ef2e-108">[in] Kombinację [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) wartości wyliczenia, które zawierają informacje dotyczące Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6ef2e-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ef2e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6ef2e-109">Return Value</span></span>  
 <span data-ttu-id="6ef2e-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="6ef2e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6ef2e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ef2e-111">HRESULT</span></span>|<span data-ttu-id="6ef2e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6ef2e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ef2e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ef2e-113">S_OK</span></span>|<span data-ttu-id="6ef2e-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6ef2e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6ef2e-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ef2e-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ef2e-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6ef2e-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ef2e-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ef2e-117">Remarks</span></span>  
 <span data-ttu-id="6ef2e-118">Obecnie tylko określone wartości `dwInitializeDomainFlags` jest `eInitializeNewDomainFlags_NoSecurityChanges`, który określa, że środowisko uruchomieniowe języka wspólnego (CLR) czy Menedżer domeny aplikacji nie spowoduje jej modyfikacji ustawień zabezpieczeń podczas wykonywania <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6ef2e-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6ef2e-119">Dzięki temu CLR w celu zoptymalizowania ładowania zestawów, które mają warunkowe <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA).</span><span class="sxs-lookup"><span data-stu-id="6ef2e-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="6ef2e-120">Może to spowodować znaczne ulepszenia w chwili uruchomienia Jeśli przechodnie zamknięcia to zbiór zestawów jest duży.</span><span class="sxs-lookup"><span data-stu-id="6ef2e-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ef2e-121">Jeśli host Określa `eInitializeNewDomainFlags_NoSecurityChanges` Menedżera domeny aplikacji, <xref:System.InvalidOperationException> jest generowany, jeśli wszystkie próby zmodyfikowania bezpieczeństwa domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6ef2e-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="6ef2e-122">Wywoływanie [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)jest odpowiednikiem wywołania metody `ICLRDomainManager::SetAppDomainManagerType` z `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="6ef2e-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ef2e-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ef2e-123">Requirements</span></span>  
 <span data-ttu-id="6ef2e-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ef2e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ef2e-125">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6ef2e-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6ef2e-126">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ef2e-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ef2e-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ef2e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef2e-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ef2e-128">See Also</span></span>  
 [<span data-ttu-id="6ef2e-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="6ef2e-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="6ef2e-130">ICLRDomainManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="6ef2e-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [<span data-ttu-id="6ef2e-131">EInitializeNewDomainFlags — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6ef2e-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
