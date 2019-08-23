---
title: IHostAssemblyManager::GetAssemblyStore — Metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62965fa928522052b6885769e02c0211ca8d3fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937934"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="9decb-102">IHostAssemblyManager::GetAssemblyStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="9decb-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="9decb-103">Pobiera wskaźnik interfejsu do [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , który reprezentuje listę zestawów załadowanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="9decb-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9decb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9decb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9decb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9decb-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="9decb-106">określoną Wskaźnik funkcji do `IHostAssemblyStore` wystąpienia lub wartość null, Jeśli host nie implementuje `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="9decb-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9decb-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9decb-107">Return Value</span></span>  
  
|<span data-ttu-id="9decb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9decb-108">HRESULT</span></span>|<span data-ttu-id="9decb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9decb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9decb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9decb-110">S_OK</span></span>|<span data-ttu-id="9decb-111">`GetAssemblyStore`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="9decb-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="9decb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9decb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9decb-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9decb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9decb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9decb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9decb-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="9decb-115">The call timed out.</span></span>|  
|<span data-ttu-id="9decb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9decb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9decb-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="9decb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9decb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9decb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9decb-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="9decb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9decb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9decb-120">E_FAIL</span></span>|<span data-ttu-id="9decb-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9decb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9decb-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="9decb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9decb-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9decb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9decb-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="9decb-124">E_NOINTERFACE</span></span>|<span data-ttu-id="9decb-125">Host nie oferuje implementacji programu `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="9decb-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9decb-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9decb-126">Remarks</span></span>  
 <span data-ttu-id="9decb-127">`IHostAssemblyStore`dostarcza metody, które umożliwiają hostowi powiązanie z zestawami i modułami niezależnie od środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="9decb-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="9decb-128">Hosty zwykle zapewniają magazyny zestawów pozwalające ładować zestawy z formatów innych niż system plików.</span><span class="sxs-lookup"><span data-stu-id="9decb-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9decb-129">Jeśli host nie jest zaimplementowany `IHostAssemblyStore`, `GetAssemblyStore` powinien zwrócić wartość HRESULT elementu E_NOINTERFACE i powinien mieć ustawioną `ppAssemblyStore` wartość null.</span><span class="sxs-lookup"><span data-stu-id="9decb-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9decb-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9decb-130">Requirements</span></span>  
 <span data-ttu-id="9decb-131">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9decb-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9decb-132">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9decb-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9decb-133">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9decb-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9decb-134">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9decb-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9decb-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9decb-135">See also</span></span>

- [<span data-ttu-id="9decb-136">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9decb-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="9decb-137">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="9decb-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
