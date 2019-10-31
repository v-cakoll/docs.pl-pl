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
ms.openlocfilehash: be59acea8eadb0da9e3cd26cf17eb9e1617c3575
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141061"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="452ec-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets — Metoda</span><span class="sxs-lookup"><span data-stu-id="452ec-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="452ec-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="452ec-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="452ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="452ec-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="452ec-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="452ec-105">Return Value</span></span>  
  
|<span data-ttu-id="452ec-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="452ec-106">HRESULT</span></span>|<span data-ttu-id="452ec-107">Opis</span><span class="sxs-lookup"><span data-stu-id="452ec-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="452ec-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="452ec-108">S_OK</span></span>|<span data-ttu-id="452ec-109">`SetEagerSerializeGrantSets` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="452ec-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="452ec-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="452ec-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="452ec-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="452ec-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="452ec-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="452ec-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="452ec-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="452ec-113">The call timed out.</span></span>|  
|<span data-ttu-id="452ec-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="452ec-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="452ec-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="452ec-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="452ec-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="452ec-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="452ec-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="452ec-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="452ec-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="452ec-118">E_FAIL</span></span>|<span data-ttu-id="452ec-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="452ec-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="452ec-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="452ec-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="452ec-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="452ec-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="452ec-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="452ec-122">Requirements</span></span>  
 <span data-ttu-id="452ec-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="452ec-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="452ec-124">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="452ec-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="452ec-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="452ec-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="452ec-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="452ec-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="452ec-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="452ec-127">See also</span></span>

- [<span data-ttu-id="452ec-128">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="452ec-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="452ec-129">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="452ec-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
