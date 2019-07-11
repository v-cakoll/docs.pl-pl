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
ms.openlocfilehash: 28feddffff7dc5dba1860b3d2d1327a17bd08190
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772948"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="8dff8-102">ICLRDomainManager::SetAppDomainManagerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="8dff8-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="8dff8-103">Określa typ pochodną <xref:System.AppDomainManager?displayProperty=nameWithType> klasy Menedżer domeny aplikacji, która będzie służyć do zainicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8dff8-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dff8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8dff8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dff8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dff8-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="8dff8-106">[in] Nazwa wyświetlana zestawu, który zawiera typ Menedżera domeny aplikacji; na przykład: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="8dff8-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="8dff8-107">[in] Nazwa typu Menedżer domeny aplikacji, włącznie z przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="8dff8-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="8dff8-108">[in] Kombinacji [einitializenewdomainflags —](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) wartości wyliczenia, które zawierają informacje dotyczące Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8dff8-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dff8-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8dff8-109">Return Value</span></span>  
 <span data-ttu-id="8dff8-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="8dff8-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8dff8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8dff8-111">HRESULT</span></span>|<span data-ttu-id="8dff8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8dff8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8dff8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8dff8-113">S_OK</span></span>|<span data-ttu-id="8dff8-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8dff8-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="8dff8-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8dff8-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8dff8-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8dff8-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dff8-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8dff8-117">Remarks</span></span>  
 <span data-ttu-id="8dff8-118">Obecnie tylko określone wartości `dwInitializeDomainFlags` jest `eInitializeNewDomainFlags_NoSecurityChanges`, informuje środowisko uruchomieniowe języka wspólnego (CLR), czy Menedżer domeny aplikacji nie będą modyfikować ustawień zabezpieczeń podczas wykonywania <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8dff8-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8dff8-119">Dzięki temu CLR do optymalizacji ładowania zestawów, które mają warunkową <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA).</span><span class="sxs-lookup"><span data-stu-id="8dff8-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="8dff8-120">Może to spowodować znaczne ulepszenia w czasie uruchamiania Jeśli przechodnie zamknięcia ten zbiór zestawów jest duży.</span><span class="sxs-lookup"><span data-stu-id="8dff8-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8dff8-121">Jeśli host Określa `eInitializeNewDomainFlags_NoSecurityChanges` dla Menedżera domeny aplikacji, <xref:System.InvalidOperationException> jest generowany, jeśli wszystkie podejmowana jest próba zmodyfikowania bezpieczeństwa domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8dff8-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="8dff8-122">Wywoływanie [iclrcontrol::setappdomainmanagertype —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metodą jest równoważne z wywoływaniem `ICLRDomainManager::SetAppDomainManagerType` z `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="8dff8-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dff8-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8dff8-123">Requirements</span></span>  
 <span data-ttu-id="8dff8-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dff8-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dff8-125">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8dff8-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8dff8-126">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8dff8-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8dff8-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dff8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dff8-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8dff8-128">See also</span></span>

- [<span data-ttu-id="8dff8-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="8dff8-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="8dff8-130">ICLRDomainManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8dff8-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="8dff8-131">EInitializeNewDomainFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8dff8-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
