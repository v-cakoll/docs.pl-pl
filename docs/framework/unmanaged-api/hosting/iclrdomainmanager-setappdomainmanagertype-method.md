---
title: ICLRDomainManager::SetAppDomainManagerType — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea10f9b7d23d8ca6a94d05cac6e586b434c000d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="9f141-102">ICLRDomainManager::SetAppDomainManagerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="9f141-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="9f141-103">Określa typ pochodny <xref:System.AppDomainManager?displayProperty=nameWithType> klasy Menedżer domeny aplikacji, które będą używane do inicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f141-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f141-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f141-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f141-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f141-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="9f141-106">[in] Wyświetlana nazwa zestawu zawierającego typ Menedżer domeny aplikacji; na przykład: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="9f141-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="9f141-107">[in] Nazwa typu Menedżer domeny aplikacji, włącznie z przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="9f141-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="9f141-108">[in] Kombinację [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) wartości wyliczenia, które zawierają informacje dotyczące Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f141-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f141-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9f141-109">Return Value</span></span>  
 <span data-ttu-id="9f141-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="9f141-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9f141-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9f141-111">HRESULT</span></span>|<span data-ttu-id="9f141-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9f141-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f141-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f141-113">S_OK</span></span>|<span data-ttu-id="9f141-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9f141-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="9f141-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9f141-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9f141-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="9f141-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f141-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f141-117">Remarks</span></span>  
 <span data-ttu-id="9f141-118">Obecnie tylko określone wartości `dwInitializeDomainFlags` jest `eInitializeNewDomainFlags_NoSecurityChanges`, który określa, że środowisko uruchomieniowe języka wspólnego (CLR) czy Menedżer domeny aplikacji nie spowoduje jej modyfikacji ustawień zabezpieczeń podczas wykonywania <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9f141-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9f141-119">Dzięki temu CLR w celu zoptymalizowania ładowania zestawów, które mają warunkowe <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA).</span><span class="sxs-lookup"><span data-stu-id="9f141-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="9f141-120">Może to spowodować znaczne ulepszenia w chwili uruchomienia Jeśli przechodnie zamknięcia to zbiór zestawów jest duży.</span><span class="sxs-lookup"><span data-stu-id="9f141-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f141-121">Jeśli host Określa `eInitializeNewDomainFlags_NoSecurityChanges` Menedżera domeny aplikacji, <xref:System.InvalidOperationException> jest generowany, jeśli wszystkie próby zmodyfikowania bezpieczeństwa domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f141-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="9f141-122">Wywoływanie [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)jest odpowiednikiem wywołania metody `ICLRDomainManager::SetAppDomainManagerType` z `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="9f141-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f141-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f141-123">Requirements</span></span>  
 <span data-ttu-id="9f141-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f141-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f141-125">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9f141-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9f141-126">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9f141-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f141-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f141-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f141-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f141-128">See Also</span></span>  
 [<span data-ttu-id="9f141-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="9f141-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="9f141-130">ICLRDomainManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9f141-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [<span data-ttu-id="9f141-131">EInitializeNewDomainFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9f141-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
