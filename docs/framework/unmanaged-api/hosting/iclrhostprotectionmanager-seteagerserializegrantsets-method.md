---
title: ICLRHostProtectionManager::SetEagerSerializeGrantSets — Metoda
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948fd78ae2839bd24a44c8c0b806e32b1da7125f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729784"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="50a99-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets — Metoda</span><span class="sxs-lookup"><span data-stu-id="50a99-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="50a99-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="50a99-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a99-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50a99-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="50a99-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50a99-105">Return Value</span></span>  
  
|<span data-ttu-id="50a99-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50a99-106">HRESULT</span></span>|<span data-ttu-id="50a99-107">Opis</span><span class="sxs-lookup"><span data-stu-id="50a99-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50a99-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="50a99-108">S_OK</span></span>|<span data-ttu-id="50a99-109">`SetEagerSerializeGrantSets` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="50a99-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="50a99-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50a99-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50a99-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="50a99-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50a99-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50a99-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50a99-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="50a99-113">The call timed out.</span></span>|  
|<span data-ttu-id="50a99-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50a99-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50a99-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="50a99-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50a99-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50a99-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50a99-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="50a99-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50a99-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50a99-118">E_FAIL</span></span>|<span data-ttu-id="50a99-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="50a99-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50a99-120">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="50a99-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50a99-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="50a99-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50a99-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50a99-122">Requirements</span></span>  
 <span data-ttu-id="50a99-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50a99-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50a99-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50a99-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50a99-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50a99-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50a99-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50a99-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a99-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50a99-127">See also</span></span>
- [<span data-ttu-id="50a99-128">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="50a99-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="50a99-129">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="50a99-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
