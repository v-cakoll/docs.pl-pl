---
title: "IHostAssemblyManager::GetAssemblyStore — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 347947622601475147663b8838bef5f36a1f7e32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="f5c2d-102">IHostAssemblyManager::GetAssemblyStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5c2d-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="f5c2d-103">Pobiera wskaźnika interfejsu do [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) reprezentujący listę zestawów załadowanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c2d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5c2d-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5c2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5c2d-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="f5c2d-106">[out] Wskaźnik funkcji do `IHostAssemblyStore` wystąpienia, lub wartość null, jeśli host nie implementuje `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5c2d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f5c2d-107">Return Value</span></span>  
  
|<span data-ttu-id="f5c2d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5c2d-108">HRESULT</span></span>|<span data-ttu-id="f5c2d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f5c2d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5c2d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5c2d-110">S_OK</span></span>|<span data-ttu-id="f5c2d-111">`GetAssemblyStore`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="f5c2d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5c2d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5c2d-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5c2d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5c2d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5c2d-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-115">The call timed out.</span></span>|  
|<span data-ttu-id="f5c2d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5c2d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5c2d-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5c2d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5c2d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5c2d-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5c2d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5c2d-120">E_FAIL</span></span>|<span data-ttu-id="f5c2d-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5c2d-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5c2d-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f5c2d-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="f5c2d-124">E_NOINTERFACE</span></span>|<span data-ttu-id="f5c2d-125">Host nie zapewniać implementację elementu `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5c2d-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5c2d-126">Remarks</span></span>  
 <span data-ttu-id="f5c2d-127">`IHostAssemblyStore`udostępnia metody umożliwiające hosta można powiązać do zestawów i modułów, niezależnie od środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="f5c2d-128">Hosty zwykle zawierają zestawu sklepami, aby umożliwić zestawy, które ma zostać załadowane z formatów innych niż system plików.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5c2d-129">Jeśli host nie implementuje `IHostAssemblyStore`, `GetAssemblyStore` powinien zwrócić wartość HRESULT E_NOINTERFACE i należy ustawić `ppAssemblyStore` na wartość null.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5c2d-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5c2d-130">Requirements</span></span>  
 <span data-ttu-id="f5c2d-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5c2d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5c2d-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5c2d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5c2d-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5c2d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5c2d-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5c2d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c2d-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5c2d-135">See Also</span></span>  
 [<span data-ttu-id="f5c2d-136">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5c2d-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="f5c2d-137">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5c2d-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
