---
title: "IHostAssemblyManager::GetAssemblyStore — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager.GetAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d838ee8383a4e11f5d43c4a3751c4a90503906fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="19bec-102">IHostAssemblyManager::GetAssemblyStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="19bec-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="19bec-103">Pobiera wskaźnika interfejsu do [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) reprezentujący listę zestawów załadowanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="19bec-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19bec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19bec-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19bec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19bec-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="19bec-106">[out] Wskaźnik funkcji do `IHostAssemblyStore` wystąpienia, lub wartość null, jeśli host nie implementuje `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="19bec-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19bec-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="19bec-107">Return Value</span></span>  
  
|<span data-ttu-id="19bec-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19bec-108">HRESULT</span></span>|<span data-ttu-id="19bec-109">Opis</span><span class="sxs-lookup"><span data-stu-id="19bec-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19bec-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="19bec-110">S_OK</span></span>|<span data-ttu-id="19bec-111">`GetAssemblyStore`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="19bec-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="19bec-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19bec-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19bec-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="19bec-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="19bec-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="19bec-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="19bec-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="19bec-115">The call timed out.</span></span>|  
|<span data-ttu-id="19bec-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="19bec-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="19bec-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="19bec-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="19bec-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="19bec-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="19bec-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="19bec-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="19bec-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19bec-120">E_FAIL</span></span>|<span data-ttu-id="19bec-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="19bec-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="19bec-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="19bec-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="19bec-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="19bec-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="19bec-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="19bec-124">E_NOINTERFACE</span></span>|<span data-ttu-id="19bec-125">Host nie zapewniać implementację elementu `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="19bec-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19bec-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19bec-126">Remarks</span></span>  
 <span data-ttu-id="19bec-127">`IHostAssemblyStore`udostępnia metody umożliwiające hosta można powiązać do zestawów i modułów, niezależnie od środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="19bec-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="19bec-128">Hosty zwykle zawierają zestawu sklepami, aby umożliwić zestawy, które ma zostać załadowane z formatów innych niż system plików.</span><span class="sxs-lookup"><span data-stu-id="19bec-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19bec-129">Jeśli host nie implementuje `IHostAssemblyStore`, `GetAssemblyStore` powinien zwrócić wartość HRESULT E_NOINTERFACE i należy ustawić `ppAssemblyStore` na wartość null.</span><span class="sxs-lookup"><span data-stu-id="19bec-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19bec-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19bec-130">Requirements</span></span>  
 <span data-ttu-id="19bec-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19bec-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19bec-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="19bec-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19bec-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19bec-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19bec-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19bec-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19bec-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19bec-135">See Also</span></span>  
 [<span data-ttu-id="19bec-136">IHostAssemblyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="19bec-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="19bec-137">IHostAssemblyStore — interfejs</span><span class="sxs-lookup"><span data-stu-id="19bec-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
