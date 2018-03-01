---
title: "ICLRDomainManager::SetPropertiesForDefaultAppDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de72568f5908dc89c9a4105c927cfba6c7366b80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="0772b-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="0772b-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="0772b-103">Ustawia właściwości, które będą używane do inicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0772b-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0772b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0772b-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0772b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0772b-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="0772b-106">[in] Liczba wpisów w `pwszPropertyNames` i `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="0772b-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="0772b-107">[in] Tablica nazw właściwości, lub wartość null, jeśli nie ma żadnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="0772b-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="0772b-108">Obecnie nazwę tylko właściwości, która jest rozpoznawana przez tę metodę jest "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="0772b-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="0772b-109">[in] Tablica wartości właściwości lub wartość null, jeśli nie ma żadnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="0772b-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0772b-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0772b-110">Return Value</span></span>  
 <span data-ttu-id="0772b-111">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="0772b-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0772b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0772b-112">HRESULT</span></span>|<span data-ttu-id="0772b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0772b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0772b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0772b-114">S_OK</span></span>|<span data-ttu-id="0772b-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0772b-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="0772b-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="0772b-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="0772b-117">`pwszPropertyNames`zawiera nazwę właściwości, która nie jest rozpoznawana przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="0772b-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0772b-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0772b-118">Remarks</span></span>  
 <span data-ttu-id="0772b-119">Wartość właściwości "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" znajduje się lista zestawów, które mają warunkowe <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybut (APTCA) z <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flagi, które mają być widoczne dla częściowo zaufanego kodu wywołującego w domyślnej aplikacji domeny.</span><span class="sxs-lookup"><span data-stu-id="0772b-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0772b-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0772b-120">Requirements</span></span>  
 <span data-ttu-id="0772b-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0772b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0772b-122">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0772b-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0772b-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0772b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0772b-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0772b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0772b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0772b-125">See Also</span></span>  
 [<span data-ttu-id="0772b-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="0772b-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="0772b-127">ICLRDomainManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0772b-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
