---
title: ICLRHostProtectionManager::SetProtectedCategories — Metoda
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6c93566d0909f1dbef46862760d47ede478d51a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="f6c9a-102">ICLRHostProtectionManager::SetProtectedCategories — Metoda</span><span class="sxs-lookup"><span data-stu-id="f6c9a-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="f6c9a-103">Określa, które kategorie typy zarządzane i elementów członkowskich powinien zostać zablokowany uruchomionych w częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6c9a-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6c9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6c9a-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="f6c9a-106">[in] Kombinację [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) wartości i wskazujący kategorie, które typy zarządzane i elementów członkowskich powinien zostać zablokowany w częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6c9a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f6c9a-107">Return Value</span></span>  
  
|<span data-ttu-id="f6c9a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6c9a-108">HRESULT</span></span>|<span data-ttu-id="f6c9a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f6c9a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6c9a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f6c9a-110">S_OK</span></span>|<span data-ttu-id="f6c9a-111">`SetProtectedCategories` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="f6c9a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f6c9a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f6c9a-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f6c9a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f6c9a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f6c9a-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-115">The call timed out.</span></span>|  
|<span data-ttu-id="f6c9a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6c9a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f6c9a-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f6c9a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f6c9a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f6c9a-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f6c9a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f6c9a-120">E_FAIL</span></span>|<span data-ttu-id="f6c9a-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f6c9a-122">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f6c9a-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6c9a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6c9a-124">Remarks</span></span>  
 <span data-ttu-id="f6c9a-125">Każdy `EApiCategories` wartość odwołuje się do listy typy zarządzane i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="f6c9a-126">`EApiCategories` Wyliczenie i `SetProtectedCategories` metody są bezpośrednio związane do zarządzanej <xref:System.Security.Permissions.HostProtectionAttribute> klasy, która służy do oznaczania typy zarządzane i elementów członkowskich, które ujawnia możliwości odpowiadający kategorii opisanego przez `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="f6c9a-127">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.HostProtectionAttribute> i <xref:System.Security.Permissions.HostProtectionResource> wyliczenia, która odpowiada bezpośrednio `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="f6c9a-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6c9a-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6c9a-128">Requirements</span></span>  
 <span data-ttu-id="f6c9a-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6c9a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6c9a-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6c9a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6c9a-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6c9a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6c9a-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6c9a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c9a-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6c9a-133">See Also</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
 <xref:System.Security.Permissions.HostProtectionResource>  
 [<span data-ttu-id="f6c9a-134">EApiCategories, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f6c9a-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="f6c9a-135">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="f6c9a-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="f6c9a-136">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f6c9a-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
