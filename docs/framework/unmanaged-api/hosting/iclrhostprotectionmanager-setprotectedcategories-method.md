---
title: "ICLRHostProtectionManager::SetProtectedCategories — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetProtectedCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 984a88a9b75a03f421f1dd3f834665fee932876a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="dbe9e-102">ICLRHostProtectionManager::SetProtectedCategories — Metoda</span><span class="sxs-lookup"><span data-stu-id="dbe9e-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="dbe9e-103">Określa, które kategorie typy zarządzane i elementów członkowskich powinien zostać zablokowany uruchomionych w częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe9e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbe9e-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbe9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbe9e-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="dbe9e-106">[in] Kombinację [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) wartości i wskazujący kategorie, które typy zarządzane i elementów członkowskich powinien zostać zablokowany w częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbe9e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dbe9e-107">Return Value</span></span>  
  
|<span data-ttu-id="dbe9e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbe9e-108">HRESULT</span></span>|<span data-ttu-id="dbe9e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="dbe9e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbe9e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbe9e-110">S_OK</span></span>|<span data-ttu-id="dbe9e-111">`SetProtectedCategories`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="dbe9e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dbe9e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dbe9e-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dbe9e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dbe9e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dbe9e-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-115">The call timed out.</span></span>|  
|<span data-ttu-id="dbe9e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dbe9e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dbe9e-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dbe9e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dbe9e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dbe9e-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dbe9e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbe9e-120">E_FAIL</span></span>|<span data-ttu-id="dbe9e-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dbe9e-122">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dbe9e-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbe9e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dbe9e-124">Remarks</span></span>  
 <span data-ttu-id="dbe9e-125">Każdy `EApiCategories` wartość odwołuje się do listy typy zarządzane i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="dbe9e-126">`EApiCategories` Wyliczenie i `SetProtectedCategories` metody są bezpośrednio związane do zarządzanej <xref:System.Security.Permissions.HostProtectionAttribute> klasy, która służy do oznaczania typy zarządzane i elementów członkowskich, które ujawnia możliwości odpowiadający kategorii opisanego przez `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="dbe9e-127">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.HostProtectionAttribute> i <xref:System.Security.Permissions.HostProtectionResource> wyliczenia, która odpowiada bezpośrednio `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="dbe9e-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe9e-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbe9e-128">Requirements</span></span>  
 <span data-ttu-id="dbe9e-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbe9e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbe9e-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbe9e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbe9e-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbe9e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbe9e-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbe9e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe9e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbe9e-133">See Also</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
 <xref:System.Security.Permissions.HostProtectionResource>  
 [<span data-ttu-id="dbe9e-134">EApiCategories — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="dbe9e-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="dbe9e-135">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="dbe9e-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="dbe9e-136">ICLRHostProtectionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="dbe9e-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
