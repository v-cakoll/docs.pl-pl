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
ms.openlocfilehash: 5e1c1b1984c63bedb3c073f45a7b9a3574afdcec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615686"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="de2a2-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="de2a2-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="de2a2-103">Ustawia właściwości, które zostaną użyte do zainicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de2a2-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de2a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de2a2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de2a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de2a2-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="de2a2-106">podczas Liczba wpisów w `pwszPropertyNames` i `pwszPropertyValues` .</span><span class="sxs-lookup"><span data-stu-id="de2a2-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="de2a2-107">podczas Tablica nazw właściwości lub wartość null, jeśli nie ma żadnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="de2a2-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="de2a2-108">Obecnie jedyną nazwą właściwości, która jest rozpoznawana przez tę metodę, jest "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="de2a2-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="de2a2-109">podczas Tablica wartości właściwości lub wartość null, jeśli nie ma żadnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="de2a2-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de2a2-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="de2a2-110">Return Value</span></span>  
 <span data-ttu-id="de2a2-111">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="de2a2-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="de2a2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de2a2-112">HRESULT</span></span>|<span data-ttu-id="de2a2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="de2a2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de2a2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="de2a2-114">S_OK</span></span>|<span data-ttu-id="de2a2-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="de2a2-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="de2a2-116">HRESULT_FROM_WIN32 (ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="de2a2-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="de2a2-117">`pwszPropertyNames`zawiera nazwę właściwości, która nie jest rozpoznawana przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="de2a2-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de2a2-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de2a2-118">Remarks</span></span>  
 <span data-ttu-id="de2a2-119">Wartość właściwości "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" to lista zestawów, które mają atrybut Conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) z <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flagą, które mają być widoczne dla częściowo zaufanych wywołujących w domenie aplikacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="de2a2-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de2a2-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de2a2-120">Requirements</span></span>  
 <span data-ttu-id="de2a2-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de2a2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de2a2-122">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="de2a2-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="de2a2-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="de2a2-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de2a2-124">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de2a2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de2a2-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de2a2-125">See also</span></span>

- [<span data-ttu-id="de2a2-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="de2a2-126">Hosting</span></span>](index.md)
- [<span data-ttu-id="de2a2-127">ICLRDomainManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="de2a2-127">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
