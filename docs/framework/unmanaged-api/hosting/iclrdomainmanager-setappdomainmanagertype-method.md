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
ms.openlocfilehash: 5c61e2e1208cec0bda1492964a8d02bd71f5a1c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129328"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="5c1c7-102">ICLRDomainManager::SetAppDomainManagerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c1c7-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="5c1c7-103">Określa typ, który pochodzi od klasy <xref:System.AppDomainManager?displayProperty=nameWithType>, Menedżera domeny aplikacji, który będzie używany do inicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c1c7-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c1c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c1c7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c1c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c1c7-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="5c1c7-106">podczas Nazwa wyświetlana zestawu zawierającego typ Menedżera domeny aplikacji; na przykład: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="5c1c7-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="5c1c7-107">podczas Nazwa typu Menedżera domeny aplikacji, łącznie z przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="5c1c7-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="5c1c7-108">podczas Kombinacja [EInitializeNewDomainFlags —](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) wartości wyliczenia, które zawierają informacje o Menedżerze domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c1c7-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c1c7-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5c1c7-109">Return Value</span></span>  
 <span data-ttu-id="5c1c7-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="5c1c7-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5c1c7-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c1c7-111">HRESULT</span></span>|<span data-ttu-id="5c1c7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5c1c7-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c1c7-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c1c7-113">S_OK</span></span>|<span data-ttu-id="5c1c7-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5c1c7-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5c1c7-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c1c7-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c1c7-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5c1c7-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c1c7-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c1c7-117">Remarks</span></span>  
 <span data-ttu-id="5c1c7-118">Obecnie jedyną zdefiniowaną wartością `dwInitializeDomainFlags` jest `eInitializeNewDomainFlags_NoSecurityChanges`, która informuje środowisko uruchomieniowe języka wspólnego (CLR), że Menedżer domeny aplikacji nie zmodyfikuje ustawień zabezpieczeń podczas wykonywania metody <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5c1c7-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5c1c7-119">Dzięki temu środowisko CLR optymalizuje ładowanie zestawów, które mają atrybut warunkowego <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA).</span><span class="sxs-lookup"><span data-stu-id="5c1c7-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="5c1c7-120">Może to spowodować znaczne zwiększenie czasu uruchamiania, jeśli zamknięcie przechodnie tego zestawu zestawów jest duże.</span><span class="sxs-lookup"><span data-stu-id="5c1c7-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5c1c7-121">Jeśli host określi `eInitializeNewDomainFlags_NoSecurityChanges` dla Menedżera domeny aplikacji, zostanie zgłoszony <xref:System.InvalidOperationException>, Jeśli podjęto próbę zmodyfikowania zabezpieczeń domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c1c7-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="5c1c7-122">Wywołanie metody [ICLRControl:: SetAppDomainManagerType —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)jest równoznaczne z wywołaniem `ICLRDomainManager::SetAppDomainManagerType` z `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="5c1c7-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c1c7-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c1c7-123">Requirements</span></span>  
 <span data-ttu-id="5c1c7-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c1c7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c1c7-125">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="5c1c7-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5c1c7-126">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5c1c7-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c1c7-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c1c7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c1c7-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c1c7-128">See also</span></span>

- [<span data-ttu-id="5c1c7-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="5c1c7-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="5c1c7-130">ICLRDomainManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5c1c7-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="5c1c7-131">EInitializeNewDomainFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5c1c7-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
