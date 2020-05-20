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
ms.openlocfilehash: 5cf6f942add3d090cf830e71a545b9f4d4f69f00
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703166"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="3f62d-102">ICLRHostProtectionManager::SetProtectedCategories — Metoda</span><span class="sxs-lookup"><span data-stu-id="3f62d-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="3f62d-103">Określa kategorie typów zarządzanych i elementów członkowskich, które mają być blokowane z uruchamiania w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="3f62d-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f62d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f62d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f62d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f62d-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="3f62d-106">podczas Kombinacja wartości [EApiCategories —](eapicategories-enumeration.md) , wskazujących kategorie typów zarządzanych i elementów członkowskich, które powinny być blokowane w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="3f62d-106">[in] A combination of [EApiCategories](eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f62d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3f62d-107">Return Value</span></span>  
  
|<span data-ttu-id="3f62d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f62d-108">HRESULT</span></span>|<span data-ttu-id="3f62d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3f62d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f62d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f62d-110">S_OK</span></span>|<span data-ttu-id="3f62d-111">`SetProtectedCategories`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="3f62d-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="3f62d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3f62d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3f62d-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3f62d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3f62d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3f62d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3f62d-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="3f62d-115">The call timed out.</span></span>|  
|<span data-ttu-id="3f62d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3f62d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3f62d-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="3f62d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3f62d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3f62d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3f62d-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="3f62d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3f62d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3f62d-120">E_FAIL</span></span>|<span data-ttu-id="3f62d-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3f62d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3f62d-122">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="3f62d-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3f62d-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3f62d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f62d-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f62d-124">Remarks</span></span>  
 <span data-ttu-id="3f62d-125">Każda `EApiCategories` wartość odnosi się do listy typów zarządzanych i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="3f62d-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="3f62d-126">`EApiCategories`Wyliczenie i `SetProtectedCategories` Metoda są bezpośrednio powiązane z klasą zarządzaną <xref:System.Security.Permissions.HostProtectionAttribute> , która jest używana do oznaczania typów zarządzanych i członków, które uwidaczniają możliwości odpowiadające kategoriom opisanym przez `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="3f62d-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="3f62d-127">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.HostProtectionAttribute> i <xref:System.Security.Permissions.HostProtectionResource> Wyliczenie, które bezpośrednio odnosi się do `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="3f62d-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f62d-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f62d-128">Requirements</span></span>  
 <span data-ttu-id="3f62d-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f62d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f62d-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3f62d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f62d-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3f62d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f62d-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f62d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f62d-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f62d-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="3f62d-134">EApiCategories, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3f62d-134">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="3f62d-135">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3f62d-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="3f62d-136">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3f62d-136">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
