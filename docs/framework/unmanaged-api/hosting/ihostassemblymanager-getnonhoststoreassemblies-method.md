---
title: IHostAssemblyManager::GetNonHostStoreAssemblies — Metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3680721c70ab69776c973913d929f7bdd9db3909
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779441"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="ac68a-102">IHostAssemblyManager::GetNonHostStoreAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac68a-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="ac68a-103">Pobiera wskaźnik interfejsu do [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) reprezentujący listę zestawów, które hosta oczekuje, że środowisko uruchomieniowe języka wspólnego (CLR) do załadowania.</span><span class="sxs-lookup"><span data-stu-id="ac68a-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac68a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac68a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac68a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac68a-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="ac68a-106">[out] Wskaźnik na adres `ICLRAssemblyReferenceList` zawierający listę odwołania do zestawów, do których host oczekuje środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="ac68a-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac68a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ac68a-107">Return Value</span></span>  
  
|<span data-ttu-id="ac68a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac68a-108">HRESULT</span></span>|<span data-ttu-id="ac68a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ac68a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac68a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac68a-110">S_OK</span></span>|<span data-ttu-id="ac68a-111">`GetNonHostStoreAssemblies` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="ac68a-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="ac68a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac68a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac68a-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ac68a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac68a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac68a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac68a-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ac68a-115">The call timed out.</span></span>|  
|<span data-ttu-id="ac68a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac68a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac68a-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="ac68a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac68a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac68a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac68a-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ac68a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac68a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac68a-120">E_FAIL</span></span>|<span data-ttu-id="ac68a-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ac68a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac68a-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ac68a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac68a-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ac68a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ac68a-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ac68a-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ac68a-125">Za mało pamięci była dostępna do utworzenia listy odwołań dla żądanego `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="ac68a-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac68a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac68a-126">Remarks</span></span>  
 <span data-ttu-id="ac68a-127">Środowisko CLR rozwiązuje odwołań za pomocą zestawu następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="ac68a-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="ac68a-128">Po pierwsze, konsultacje dotyczące listy odwołania do zestawów, zwracany przez `GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="ac68a-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="ac68a-129">Jeśli zestaw zostanie wyświetlone na liście, środowisko CLR zwykle wiąże do niego.</span><span class="sxs-lookup"><span data-stu-id="ac68a-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="ac68a-130">Jeśli zestaw nie ma na liście, a host ma pod warunkiem implementację [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), CLR wywołuje [ihostassemblystore::provideassembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) zezwalająca na hoście do dostarczania zestaw można powiązać.</span><span class="sxs-lookup"><span data-stu-id="ac68a-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="ac68a-131">W przeciwnym razie środowisko CLR nie może powiązać do zestawu.</span><span class="sxs-lookup"><span data-stu-id="ac68a-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="ac68a-132">Jeśli host ustawia `ppReferenceList` na wartość null, sondy pierwszego środowiska CLR wywołuje global assembly cache `ProvideAssembly`, a następnie sondy podstawy aplikacji, aby rozwiązać odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="ac68a-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac68a-133">Po zainicjowaniu, środowisko CLR wywołuje `GetNonHostStoreAssemblies` tylko raz.</span><span class="sxs-lookup"><span data-stu-id="ac68a-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="ac68a-134">Metoda nie jest ponownie wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ac68a-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac68a-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac68a-135">Requirements</span></span>  
 <span data-ttu-id="ac68a-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac68a-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac68a-137">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac68a-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac68a-138">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac68a-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac68a-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac68a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac68a-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac68a-140">See also</span></span>

- [<span data-ttu-id="ac68a-141">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac68a-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="ac68a-142">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac68a-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="ac68a-143">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac68a-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
