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
ms.openlocfilehash: 9290fd70b17b5a6456d85cb4b037ebbc62e028f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763977"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="842a2-102">IHostAssemblyStore::ProvideModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="842a2-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="842a2-103">Usuwa plik zasobów modułu w zestawie lub połączone (ale nie embedded).</span><span class="sxs-lookup"><span data-stu-id="842a2-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="842a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="842a2-104">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="842a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="842a2-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="842a2-106">[in] Wskaźnik do [modulebindinfo —](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) wystąpienia, opisujący żądany moduł <xref:System.AppDomain>, zestawu i nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="842a2-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="842a2-107">[out] Wskaźnik do Unikatowy identyfikator `IStream` zawierający załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="842a2-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="842a2-108">[out] Wskaźnik na adres `IStream` obiekt, który zawiera obraz przenośny plik wykonywalny (PE), który można załadować lub wartość null, jeśli nie można odnaleźć modułu.</span><span class="sxs-lookup"><span data-stu-id="842a2-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="842a2-109">[out] Wskaźnik na adres `IStream` obiekt, który zawiera informacje o debugowaniu (PDB) program dla żądanego modułu, lub wartość null, jeśli nie można odnaleźć pliku .pdb.</span><span class="sxs-lookup"><span data-stu-id="842a2-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="842a2-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="842a2-110">Return Value</span></span>  
  
|<span data-ttu-id="842a2-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="842a2-111">HRESULT</span></span>|<span data-ttu-id="842a2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="842a2-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="842a2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="842a2-113">S_OK</span></span>|<span data-ttu-id="842a2-114">`ProvideModule` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="842a2-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="842a2-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="842a2-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="842a2-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="842a2-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="842a2-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="842a2-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="842a2-118">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="842a2-118">The call timed out.</span></span>|  
|<span data-ttu-id="842a2-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="842a2-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="842a2-120">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="842a2-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="842a2-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="842a2-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="842a2-122">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="842a2-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="842a2-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="842a2-123">E_FAIL</span></span>|<span data-ttu-id="842a2-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="842a2-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="842a2-125">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="842a2-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="842a2-126">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="842a2-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="842a2-127">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="842a2-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="842a2-128">Nie można zlokalizować żądanego zestawu lub zasobu połączonego.</span><span class="sxs-lookup"><span data-stu-id="842a2-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="842a2-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="842a2-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="842a2-130">`pdwModuleId` nie jest wystarczająco duży, aby zawierała identyfikator, który chce hosta, aby zwrócić.</span><span class="sxs-lookup"><span data-stu-id="842a2-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="842a2-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="842a2-131">Remarks</span></span>  
 <span data-ttu-id="842a2-132">Zwracana wartość tożsamości dla `pdwModuleId` określonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="842a2-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="842a2-133">Identyfikatory muszą być unikatowe w obrębie okres istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="842a2-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="842a2-134">Środowisko CLR używa tej wartości jako unikatowy identyfikator dla skojarzonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="842a2-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="842a2-135">Sprawdza każdej wartości w odniesieniu do wartości dla `pAssemblyId` zwracane przez wywołania do [provideassembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) i przed wartości `pdwModuleId` zwracane przez inne wywołania do `ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="842a2-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="842a2-136">Jeśli host zwraca taką samą wartość identyfikatora dla innego `IStream`, środowisko CLR sprawdza, czy zawartość strumieniu ma już zamapowana.</span><span class="sxs-lookup"><span data-stu-id="842a2-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="842a2-137">Jeśli tak, środowisko CLR ładuje istniejącą kopię obrazu zamiast nowe mapowanie.</span><span class="sxs-lookup"><span data-stu-id="842a2-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="842a2-138">W związku z tym, identyfikator także nie może nakładać o identyfikatorach zestawu zwróciło `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="842a2-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="842a2-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="842a2-139">Requirements</span></span>  
 <span data-ttu-id="842a2-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="842a2-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="842a2-141">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="842a2-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="842a2-142">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="842a2-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="842a2-143">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="842a2-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="842a2-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="842a2-144">See also</span></span>

- [<span data-ttu-id="842a2-145">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="842a2-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="842a2-146">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="842a2-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="842a2-147">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="842a2-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
