---
title: "IHostAssemblyStore::ProvideAssembly — Metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2097c1ea64e5e9a2a09e0ec57243624b05eeea65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="ebc90-102">IHostAssemblyStore::ProvideAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="ebc90-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="ebc90-103">Pobiera odwołanie do zestawu, który nie jest wywoływany przez [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwracanego z [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="ebc90-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="ebc90-104">Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `ProvideAssembly` dla każdego zestawu, który nie ma na liście.</span><span class="sxs-lookup"><span data-stu-id="ebc90-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc90-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebc90-105">Syntax</span></span>  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebc90-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebc90-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="ebc90-107">[in] Wskaźnik do [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) wystąpienia używanego przez hosta w celu ustalenia niektórych parametrów powiązania, w tym obecności lub braku dowolne zasady przechowywania wersji i które zestawu do powiązania.</span><span class="sxs-lookup"><span data-stu-id="ebc90-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="ebc90-108">[out] Wskaźnik do Unikatowy identyfikator dla żądanego zestawu dla tego `IStream`.</span><span class="sxs-lookup"><span data-stu-id="ebc90-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="ebc90-109">[out] Wskaźnik do dane specyficzne dla hosta, który służy do określania dowody żądany zestaw bez konieczności platformy wywołania wywołania.</span><span class="sxs-lookup"><span data-stu-id="ebc90-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="ebc90-110">`pHostContext`odpowiada <xref:System.Reflection.Assembly.HostContext%2A> właściwości zarządzanej <xref:System.Reflection.Assembly> klasy.</span><span class="sxs-lookup"><span data-stu-id="ebc90-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="ebc90-111">[out] Wskaźnik do adresu `IStream` zawierający obraz przenośny plik wykonywalny (PE), który można załadować lub wartość null, jeśli nie można odnaleźć zestawu.</span><span class="sxs-lookup"><span data-stu-id="ebc90-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="ebc90-112">[out] Wskaźnik do adresu `IStream` zawierający informacje o debugowaniu (PDB) program, lub wartość null, jeśli nie można odnaleźć pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="ebc90-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebc90-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ebc90-113">Return Value</span></span>  
  
|<span data-ttu-id="ebc90-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ebc90-114">HRESULT</span></span>|<span data-ttu-id="ebc90-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ebc90-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ebc90-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="ebc90-116">S_OK</span></span>|<span data-ttu-id="ebc90-117">`ProvideAssembly`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ebc90-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="ebc90-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ebc90-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ebc90-119">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ebc90-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ebc90-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ebc90-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ebc90-121">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ebc90-121">The call timed out.</span></span>|  
|<span data-ttu-id="ebc90-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ebc90-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ebc90-123">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ebc90-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ebc90-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ebc90-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ebc90-125">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ebc90-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ebc90-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ebc90-126">E_FAIL</span></span>|<span data-ttu-id="ebc90-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ebc90-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ebc90-128">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ebc90-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ebc90-129">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ebc90-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ebc90-130">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="ebc90-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="ebc90-131">Nie można zlokalizować żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ebc90-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="ebc90-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ebc90-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ebc90-133">Rozmiar buforu określony przez `pAssemblyId` nie jest wystarczająco duży do przechowywania identyfikator, który chce zwracać hosta.</span><span class="sxs-lookup"><span data-stu-id="ebc90-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebc90-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebc90-134">Remarks</span></span>  
 <span data-ttu-id="ebc90-135">Zwracane wartości tożsamości dla `pAssemblyId` jest określana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="ebc90-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="ebc90-136">Identyfikatory muszą być unikatowe w obrębie okres istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="ebc90-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="ebc90-137">Środowisko CLR używa tej wartości jako unikatowy identyfikator dla tego strumienia.</span><span class="sxs-lookup"><span data-stu-id="ebc90-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="ebc90-138">Sprawdza każdej wartości z wartościami dla `pAssemblyId` zwrócony przez inne wywołania `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="ebc90-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="ebc90-139">Jeśli host zwraca takie same `pAssemblyId` wartość dla innej `IStream`, CLR sprawdza, czy zawartość strumieniu już zostały zamapowane.</span><span class="sxs-lookup"><span data-stu-id="ebc90-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="ebc90-140">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię obrazu zamiast nowego mapowania.</span><span class="sxs-lookup"><span data-stu-id="ebc90-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebc90-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebc90-141">Requirements</span></span>  
 <span data-ttu-id="ebc90-142">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebc90-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebc90-143">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ebc90-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebc90-144">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebc90-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebc90-145">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebc90-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc90-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebc90-146">See Also</span></span>  
 [<span data-ttu-id="ebc90-147">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebc90-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="ebc90-148">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebc90-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="ebc90-149">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebc90-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
