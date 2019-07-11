---
title: IHostAssemblyStore::ProvideAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5fab4ef0d67ab6b86510bd4b2f814d9456213fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763993"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="65ec3-102">IHostAssemblyStore::ProvideAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="65ec3-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="65ec3-103">Pobiera odwołanie do zestawu, który nie odwołuje się [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwrócone z [ihostassemblymanager::getnonhoststoreassemblies —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="65ec3-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="65ec3-104">Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `ProvideAssembly` dla każdego zestawu, który nie jest widoczna na liście.</span><span class="sxs-lookup"><span data-stu-id="65ec3-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ec3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="65ec3-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65ec3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="65ec3-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="65ec3-107">[in] Wskaźnik do [assemblybindinfo —](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) wystąpieniu, używany przez hosta do ustalenia niektórych parametrów powiązania, w tym obecność lub brak żadnych zasad przechowywania wersji i zestawu, które można powiązać.</span><span class="sxs-lookup"><span data-stu-id="65ec3-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="65ec3-108">[out] Wskaźnik na unikatowy identyfikator dla żądanego zestawu, w tym `IStream`.</span><span class="sxs-lookup"><span data-stu-id="65ec3-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="65ec3-109">[out] Wskaźnik do dane specyficzne dla hosta, który służy do określania dowód żądany zestaw bez konieczności platformy wywołania wywołania.</span><span class="sxs-lookup"><span data-stu-id="65ec3-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="65ec3-110">`pHostContext` odnosi się do <xref:System.Reflection.Assembly.HostContext%2A> właściwość zarządzaną <xref:System.Reflection.Assembly> klasy.</span><span class="sxs-lookup"><span data-stu-id="65ec3-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="65ec3-111">[out] Wskaźnik na adres `IStream` zawierający obraz przenośny plik wykonywalny (PE), aby zostać załadowane, lub wartość null, jeśli nie można odnaleźć zestawu.</span><span class="sxs-lookup"><span data-stu-id="65ec3-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="65ec3-112">[out] Wskaźnik na adres `IStream` który zawiera informacje o debugowaniu (PDB) programu, lub wartość null, jeśli nie można odnaleźć pliku .pdb.</span><span class="sxs-lookup"><span data-stu-id="65ec3-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65ec3-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="65ec3-113">Return Value</span></span>  
  
|<span data-ttu-id="65ec3-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65ec3-114">HRESULT</span></span>|<span data-ttu-id="65ec3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="65ec3-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65ec3-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="65ec3-116">S_OK</span></span>|<span data-ttu-id="65ec3-117">`ProvideAssembly` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="65ec3-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="65ec3-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65ec3-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65ec3-119">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="65ec3-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65ec3-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65ec3-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65ec3-121">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="65ec3-121">The call timed out.</span></span>|  
|<span data-ttu-id="65ec3-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65ec3-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65ec3-123">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="65ec3-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65ec3-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65ec3-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65ec3-125">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="65ec3-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65ec3-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65ec3-126">E_FAIL</span></span>|<span data-ttu-id="65ec3-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="65ec3-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65ec3-128">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="65ec3-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65ec3-129">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="65ec3-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="65ec3-130">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="65ec3-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="65ec3-131">Nie można odnaleźć żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="65ec3-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="65ec3-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="65ec3-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="65ec3-133">Rozmiar buforu określony przez `pAssemblyId` nie jest wystarczająco duży, aby pomieścić identyfikator, który chce hosta, aby zwrócić.</span><span class="sxs-lookup"><span data-stu-id="65ec3-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65ec3-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65ec3-134">Remarks</span></span>  
 <span data-ttu-id="65ec3-135">Zwracana wartość tożsamości dla `pAssemblyId` określonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="65ec3-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="65ec3-136">Identyfikatory muszą być unikatowe w obrębie okres istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="65ec3-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="65ec3-137">Środowisko CLR używa tej wartości jako unikatowy identyfikator dla strumienia.</span><span class="sxs-lookup"><span data-stu-id="65ec3-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="65ec3-138">Sprawdza każdej wartości w odniesieniu do wartości dla `pAssemblyId` zwracane przez inne wywołania do `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="65ec3-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="65ec3-139">Jeśli host zwraca takie same `pAssemblyId` wartość dla innego `IStream`, środowisko CLR sprawdza, czy zawartość strumieniu ma już zamapowana.</span><span class="sxs-lookup"><span data-stu-id="65ec3-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="65ec3-140">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię obrazu zamiast nowe mapowanie.</span><span class="sxs-lookup"><span data-stu-id="65ec3-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ec3-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65ec3-141">Requirements</span></span>  
 <span data-ttu-id="65ec3-142">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ec3-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ec3-143">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65ec3-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65ec3-144">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65ec3-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65ec3-145">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ec3-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ec3-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65ec3-146">See also</span></span>

- [<span data-ttu-id="65ec3-147">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="65ec3-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="65ec3-148">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="65ec3-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="65ec3-149">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="65ec3-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
