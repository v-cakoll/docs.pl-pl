---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c42297e848844617ffdc6c85c81846b5805eb4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984766"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="bafcb-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="bafcb-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="bafcb-103">Ustawia właściwości, które będą używane do zainicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bafcb-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bafcb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bafcb-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bafcb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bafcb-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="bafcb-106">[in] Liczba wpisów w `pwszPropertyNames` i `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="bafcb-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="bafcb-107">[in] Tablica nazw właściwości lub wartość null, jeśli nie ma żadnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="bafcb-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="bafcb-108">Obecnie nazwa tylko właściwości, który jest rozpoznawany przez tę metodę jest "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="bafcb-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="bafcb-109">[in] Tablica wartości właściwości lub wartość null, jeśli nie ma żadnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="bafcb-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bafcb-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bafcb-110">Return Value</span></span>  
 <span data-ttu-id="bafcb-111">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="bafcb-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bafcb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bafcb-112">HRESULT</span></span>|<span data-ttu-id="bafcb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bafcb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bafcb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="bafcb-114">S_OK</span></span>|<span data-ttu-id="bafcb-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bafcb-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="bafcb-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="bafcb-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="bafcb-117">`pwszPropertyNames` zawiera nazwę właściwości, który nie jest rozpoznawany przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="bafcb-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bafcb-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bafcb-118">Remarks</span></span>  
 <span data-ttu-id="bafcb-119">Wartość właściwości "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" znajduje się lista zestawów, które mają warunkową <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA) z <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flagi, które mają być widoczne dla częściowo zaufanego kodu wywołującego w domyślnej aplikacji w domenie.</span><span class="sxs-lookup"><span data-stu-id="bafcb-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bafcb-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bafcb-120">Requirements</span></span>  
 <span data-ttu-id="bafcb-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bafcb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bafcb-122">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bafcb-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bafcb-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bafcb-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bafcb-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bafcb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bafcb-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bafcb-125">See also</span></span>

- [<span data-ttu-id="bafcb-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="bafcb-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="bafcb-127">ICLRDomainManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bafcb-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
