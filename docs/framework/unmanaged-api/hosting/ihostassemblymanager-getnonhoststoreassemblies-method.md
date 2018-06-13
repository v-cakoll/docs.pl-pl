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
ms.openlocfilehash: b0da548d5d5cc22eb6754859a802afa4d82fac89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438392"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="d284f-102">IHostAssemblyManager::GetNonHostStoreAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="d284f-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="d284f-103">Pobiera wskaźnika interfejsu do [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) reprezentujący listę zestawów, które host oczekuje środowisko uruchomieniowe języka wspólnego (CLR) do załadowania.</span><span class="sxs-lookup"><span data-stu-id="d284f-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d284f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d284f-104">Syntax</span></span>  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d284f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d284f-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="d284f-106">[out] Wskaźnik do adresu `ICLRAssemblyReferenceList` zawierający listę odwołań do zestawów, które host oczekuje można załadować środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d284f-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d284f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d284f-107">Return Value</span></span>  
  
|<span data-ttu-id="d284f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d284f-108">HRESULT</span></span>|<span data-ttu-id="d284f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d284f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d284f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d284f-110">S_OK</span></span>|<span data-ttu-id="d284f-111">`GetNonHostStoreAssemblies` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d284f-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="d284f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d284f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d284f-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d284f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d284f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d284f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d284f-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d284f-115">The call timed out.</span></span>|  
|<span data-ttu-id="d284f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d284f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d284f-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d284f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d284f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d284f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d284f-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d284f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d284f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d284f-120">E_FAIL</span></span>|<span data-ttu-id="d284f-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d284f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d284f-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d284f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d284f-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d284f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d284f-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d284f-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d284f-125">Za mało pamięci była dostępna utworzyć listę odwołania dla żądanego `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="d284f-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d284f-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d284f-126">Remarks</span></span>  
 <span data-ttu-id="d284f-127">Środowisko CLR rozpoznaje odwołań za pomocą zestawu następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="d284f-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
-   <span data-ttu-id="d284f-128">Najpierw należy go sprawdza listy odwołania do zestawów zwrócony przez `GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="d284f-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
-   <span data-ttu-id="d284f-129">Jeśli zestaw znajduje się na liście, CLR powiązanie go normalnie.</span><span class="sxs-lookup"><span data-stu-id="d284f-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
-   <span data-ttu-id="d284f-130">Jeśli zestaw nie ma na liście, a host udostępnił implementacja [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), wywołania CLR [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) umożliwia hosta do dostarczania zestaw do powiązania.</span><span class="sxs-lookup"><span data-stu-id="d284f-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
-   <span data-ttu-id="d284f-131">W przeciwnym razie wartość CLR nie może powiązać zestawu.</span><span class="sxs-lookup"><span data-stu-id="d284f-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="d284f-132">Jeśli host ustawia `ppReferenceList` równej null, sond pierwszy CLR wywołuje globalnej pamięci podręcznej zestawów, `ProvideAssembly`, a następnie sondy baza aplikacji można rozpoznać odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d284f-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d284f-133">Po zainicjowaniu, wywołuje CLR `GetNonHostStoreAssemblies` tylko raz.</span><span class="sxs-lookup"><span data-stu-id="d284f-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="d284f-134">Metoda nie zostanie ponownie wywołany.</span><span class="sxs-lookup"><span data-stu-id="d284f-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d284f-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d284f-135">Requirements</span></span>  
 <span data-ttu-id="d284f-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d284f-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d284f-137">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d284f-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d284f-138">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d284f-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d284f-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d284f-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d284f-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d284f-140">See Also</span></span>  
 [<span data-ttu-id="d284f-141">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="d284f-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="d284f-142">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d284f-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="d284f-143">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="d284f-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
