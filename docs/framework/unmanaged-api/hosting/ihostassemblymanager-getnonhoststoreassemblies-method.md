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
ms.openlocfilehash: 9a1440be7011130b16d7112ae15026eb74856190
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501600"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="f9be7-102">IHostAssemblyManager::GetNonHostStoreAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9be7-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="f9be7-103">Pobiera wskaźnik interfejsu do [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , który reprezentuje listę zestawów, które host oczekuje na załadowanie środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f9be7-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9be7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9be7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9be7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9be7-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="f9be7-106">określoną Wskaźnik do adresu zawierającego `ICLRAssemblyReferenceList` listę odwołań do zestawów, które host oczekuje na załadowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="f9be7-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9be7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f9be7-107">Return Value</span></span>  
  
|<span data-ttu-id="f9be7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9be7-108">HRESULT</span></span>|<span data-ttu-id="f9be7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f9be7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9be7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9be7-110">S_OK</span></span>|<span data-ttu-id="f9be7-111">`GetNonHostStoreAssemblies`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="f9be7-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="f9be7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9be7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9be7-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9be7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9be7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9be7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9be7-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="f9be7-115">The call timed out.</span></span>|  
|<span data-ttu-id="f9be7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9be7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9be7-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f9be7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9be7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9be7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9be7-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="f9be7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9be7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9be7-120">E_FAIL</span></span>|<span data-ttu-id="f9be7-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f9be7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9be7-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="f9be7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9be7-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f9be7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f9be7-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f9be7-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f9be7-125">Za mało dostępnej pamięci, aby utworzyć listę odwołań dla żądanego elementu `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="f9be7-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9be7-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9be7-126">Remarks</span></span>  
 <span data-ttu-id="f9be7-127">Środowisko CLR rozpoznaje odwołania przy użyciu następującego zestawu wytycznych:</span><span class="sxs-lookup"><span data-stu-id="f9be7-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="f9be7-128">Najpierw sprawdza listę odwołań do zestawów zwracanych przez `GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="f9be7-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="f9be7-129">Jeśli zestaw znajduje się na liście, środowisko CLR tworzy je w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="f9be7-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="f9be7-130">Jeśli zestaw nie znajduje się na liście, a host dostarczył implementację [IHostAssemblyStore](ihostassemblystore-interface.md), środowisko CLR wywołuje [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) , aby umożliwić hostowi powiązanie z zestawem.</span><span class="sxs-lookup"><span data-stu-id="f9be7-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="f9be7-131">W przeciwnym razie środowisko CLR nie zostanie powiązane z zestawem.</span><span class="sxs-lookup"><span data-stu-id="f9be7-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="f9be7-132">Jeśli host `ppReferenceList` ma wartość null, środowisko CLR najpierw sonduje globalną pamięć podręczną zestawów, wywołuje `ProvideAssembly` , a następnie sonduje bazę aplikacji w celu rozpoznania odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="f9be7-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9be7-133">Po inicjacji, środowisko CLR wywołuje `GetNonHostStoreAssemblies` tylko raz.</span><span class="sxs-lookup"><span data-stu-id="f9be7-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="f9be7-134">Metoda nie jest ponownie wywoływana.</span><span class="sxs-lookup"><span data-stu-id="f9be7-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9be7-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9be7-135">Requirements</span></span>  
 <span data-ttu-id="f9be7-136">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9be7-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9be7-137">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f9be7-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9be7-138">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f9be7-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9be7-139">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9be7-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9be7-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9be7-140">See also</span></span>

- [<span data-ttu-id="f9be7-141">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f9be7-141">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f9be7-142">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f9be7-142">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="f9be7-143">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="f9be7-143">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
