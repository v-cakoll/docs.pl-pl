---
title: "ICLRHostProtectionManager::SetEagerSerializeGrantSets — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1d2bb2ecc4ae7edb4edbaa3ff36650c70c82daf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="d2511-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2511-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="d2511-103">Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d2511-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2511-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2511-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d2511-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d2511-105">Return Value</span></span>  
  
|<span data-ttu-id="d2511-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2511-106">HRESULT</span></span>|<span data-ttu-id="d2511-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d2511-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2511-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2511-108">S_OK</span></span>|<span data-ttu-id="d2511-109">`SetEagerSerializeGrantSets`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d2511-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="d2511-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d2511-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d2511-111">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d2511-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d2511-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d2511-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d2511-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d2511-113">The call timed out.</span></span>|  
|<span data-ttu-id="d2511-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d2511-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d2511-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d2511-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d2511-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d2511-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d2511-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d2511-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d2511-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2511-118">E_FAIL</span></span>|<span data-ttu-id="d2511-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d2511-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d2511-120">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d2511-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d2511-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d2511-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2511-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2511-122">Requirements</span></span>  
 <span data-ttu-id="d2511-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2511-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2511-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2511-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2511-125">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2511-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2511-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2511-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2511-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2511-127">See Also</span></span>  
 [<span data-ttu-id="d2511-128">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2511-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="d2511-129">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2511-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
