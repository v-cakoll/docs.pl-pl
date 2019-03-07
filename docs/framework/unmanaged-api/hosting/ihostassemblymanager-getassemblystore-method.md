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
ms.openlocfilehash: fd4b538bc7090f07511273808afa039be0ef558e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497122"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="d549a-102">IHostAssemblyManager::GetAssemblyStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="d549a-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="d549a-103">Pobiera wskaźnik interfejsu do [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) reprezentujący listę zestawy, ładowane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="d549a-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d549a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d549a-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d549a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d549a-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="d549a-106">[out] Wskaźnik funkcji `IHostAssemblyStore` wystąpienia lub wartość null, jeśli host nie implementuje `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="d549a-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d549a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d549a-107">Return Value</span></span>  
  
|<span data-ttu-id="d549a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d549a-108">HRESULT</span></span>|<span data-ttu-id="d549a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d549a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d549a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d549a-110">S_OK</span></span>|<span data-ttu-id="d549a-111">`GetAssemblyStore` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="d549a-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="d549a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d549a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d549a-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d549a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d549a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d549a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d549a-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d549a-115">The call timed out.</span></span>|  
|<span data-ttu-id="d549a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d549a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d549a-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="d549a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d549a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d549a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d549a-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d549a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d549a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d549a-120">E_FAIL</span></span>|<span data-ttu-id="d549a-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d549a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d549a-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d549a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d549a-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d549a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d549a-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="d549a-124">E_NOINTERFACE</span></span>|<span data-ttu-id="d549a-125">Host nie zawiera implementacji `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="d549a-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d549a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d549a-126">Remarks</span></span>  
 <span data-ttu-id="d549a-127">`IHostAssemblyStore` udostępnia metody, które umożliwiają hosta do powiązania do zestawów i modułów, niezależnie od środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d549a-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="d549a-128">Hosty zwykle zapewniają zestawu sklepami, aby umożliwić kompilacji został załadowany z formatów innych niż system plików.</span><span class="sxs-lookup"><span data-stu-id="d549a-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d549a-129">Jeśli host nie implementuje `IHostAssemblyStore`, `GetAssemblyStore` powinna zwrócić wartość HRESULT E_NOINTERFACE i należy ustawić `ppAssemblyStore` na wartość null.</span><span class="sxs-lookup"><span data-stu-id="d549a-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d549a-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d549a-130">Requirements</span></span>  
 <span data-ttu-id="d549a-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d549a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d549a-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d549a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d549a-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d549a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d549a-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d549a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d549a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d549a-135">See also</span></span>
- [<span data-ttu-id="d549a-136">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d549a-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="d549a-137">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="d549a-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
