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
ms.openlocfilehash: 642d807fe7cb0cadb4d6fc5d8c390bf83f65d165
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496303"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="597c3-102">ICLRHostProtectionManager::SetProtectedCategories — Metoda</span><span class="sxs-lookup"><span data-stu-id="597c3-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="597c3-103">Określa, którymi kategoriami zarządzane typy i elementy członkowskie powinien zostać zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="597c3-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="597c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="597c3-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="597c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="597c3-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="597c3-106">[in] Kombinacji [eapicategories —](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) wartości, wskazujący, którymi kategoriami zarządzane typy i elementy członkowskie powinien zostać zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="597c3-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="597c3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="597c3-107">Return Value</span></span>  
  
|<span data-ttu-id="597c3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="597c3-108">HRESULT</span></span>|<span data-ttu-id="597c3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="597c3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="597c3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="597c3-110">S_OK</span></span>|<span data-ttu-id="597c3-111">`SetProtectedCategories` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="597c3-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="597c3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="597c3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="597c3-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="597c3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="597c3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="597c3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="597c3-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="597c3-115">The call timed out.</span></span>|  
|<span data-ttu-id="597c3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="597c3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="597c3-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="597c3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="597c3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="597c3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="597c3-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="597c3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="597c3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="597c3-120">E_FAIL</span></span>|<span data-ttu-id="597c3-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="597c3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="597c3-122">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="597c3-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="597c3-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="597c3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="597c3-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="597c3-124">Remarks</span></span>  
 <span data-ttu-id="597c3-125">Każdy `EApiCategories` wartość odnosi się do listy zarządzane typy i elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="597c3-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="597c3-126">`EApiCategories` Wyliczenie i `SetProtectedCategories` metody są bezpośrednio powiązane do zarządzanej <xref:System.Security.Permissions.HostProtectionAttribute> klasy, która służy do oznaczania zarządzane typy i elementy członkowskie, które udostępniają funkcje odpowiadającej kategorii opisanych przez `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="597c3-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="597c3-127">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.HostProtectionAttribute> i <xref:System.Security.Permissions.HostProtectionResource> wyliczenia, które odpowiadają bezpośrednio `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="597c3-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="597c3-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="597c3-128">Requirements</span></span>  
 <span data-ttu-id="597c3-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="597c3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="597c3-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="597c3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="597c3-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="597c3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="597c3-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="597c3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597c3-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="597c3-133">See also</span></span>
- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="597c3-134">EApiCategories, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="597c3-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="597c3-135">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="597c3-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="597c3-136">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="597c3-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
