---
title: IHostAssemblyStore::ProvideModule — Metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e07e2c3f2c6000f5a081b13316c269f322b1ef8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078341"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="78cf4-102">IHostAssemblyStore::ProvideModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="78cf4-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="78cf4-103">Usuwa plik zasobów modułu w zestawie lub połączone (ale nie embedded).</span><span class="sxs-lookup"><span data-stu-id="78cf4-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78cf4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78cf4-104">Syntax</span></span>  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78cf4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78cf4-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="78cf4-106">[in] Wskaźnik do [modulebindinfo —](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) wystąpienia, opisujący żądany moduł <xref:System.AppDomain>, zestawu i nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="78cf4-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="78cf4-107">[out] Wskaźnik do Unikatowy identyfikator `IStream` zawierający załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="78cf4-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="78cf4-108">[out] Wskaźnik na adres `IStream` obiekt, który zawiera obraz przenośny plik wykonywalny (PE), który można załadować lub wartość null, jeśli nie można odnaleźć modułu.</span><span class="sxs-lookup"><span data-stu-id="78cf4-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="78cf4-109">[out] Wskaźnik na adres `IStream` obiekt, który zawiera informacje o debugowaniu (PDB) program dla żądanego modułu, lub wartość null, jeśli nie można odnaleźć pliku .pdb.</span><span class="sxs-lookup"><span data-stu-id="78cf4-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78cf4-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="78cf4-110">Return Value</span></span>  
  
|<span data-ttu-id="78cf4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78cf4-111">HRESULT</span></span>|<span data-ttu-id="78cf4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="78cf4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78cf4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="78cf4-113">S_OK</span></span>|<span data-ttu-id="78cf4-114">`ProvideModule` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="78cf4-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="78cf4-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78cf4-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78cf4-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="78cf4-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78cf4-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78cf4-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78cf4-118">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="78cf4-118">The call timed out.</span></span>|  
|<span data-ttu-id="78cf4-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78cf4-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78cf4-120">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="78cf4-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78cf4-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78cf4-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78cf4-122">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="78cf4-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78cf4-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78cf4-123">E_FAIL</span></span>|<span data-ttu-id="78cf4-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="78cf4-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78cf4-125">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="78cf4-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78cf4-126">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="78cf4-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="78cf4-127">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="78cf4-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="78cf4-128">Nie można zlokalizować żądanego zestawu lub zasobu połączonego.</span><span class="sxs-lookup"><span data-stu-id="78cf4-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="78cf4-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="78cf4-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="78cf4-130">`pdwModuleId` nie jest wystarczająco duży, aby zawierała identyfikator, który chce hosta, aby zwrócić.</span><span class="sxs-lookup"><span data-stu-id="78cf4-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78cf4-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78cf4-131">Remarks</span></span>  
 <span data-ttu-id="78cf4-132">Zwracana wartość tożsamości dla `pdwModuleId` określonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="78cf4-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="78cf4-133">Identyfikatory muszą być unikatowe w obrębie okres istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="78cf4-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="78cf4-134">Środowisko CLR używa tej wartości jako unikatowy identyfikator dla skojarzonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="78cf4-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="78cf4-135">Sprawdza każdej wartości w odniesieniu do wartości dla `pAssemblyId` zwracane przez wywołania do [provideassembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) i przed wartości `pdwModuleId` zwracane przez inne wywołania do `ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="78cf4-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="78cf4-136">Jeśli host zwraca taką samą wartość identyfikatora dla innego `IStream`, środowisko CLR sprawdza, czy zawartość strumieniu ma już zamapowana.</span><span class="sxs-lookup"><span data-stu-id="78cf4-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="78cf4-137">Jeśli tak, środowisko CLR ładuje istniejącą kopię obrazu zamiast nowe mapowanie.</span><span class="sxs-lookup"><span data-stu-id="78cf4-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="78cf4-138">W związku z tym, identyfikator także nie może nakładać o identyfikatorach zestawu zwróciło `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="78cf4-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78cf4-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78cf4-139">Requirements</span></span>  
 <span data-ttu-id="78cf4-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78cf4-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78cf4-141">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78cf4-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78cf4-142">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78cf4-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78cf4-143">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78cf4-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78cf4-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78cf4-144">See also</span></span>

- [<span data-ttu-id="78cf4-145">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="78cf4-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="78cf4-146">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="78cf4-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="78cf4-147">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="78cf4-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
