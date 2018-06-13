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
ms.openlocfilehash: 8b604e1d7fc3d3c8adf7d95bd95843bc0110dbc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440021"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="aad93-102">IHostAssemblyStore::ProvideModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="aad93-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="aad93-103">Usuwa plik zasobów modułu w ramach zestawu lub połączony (ale nie embedded).</span><span class="sxs-lookup"><span data-stu-id="aad93-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aad93-104">Syntax</span></span>  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aad93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aad93-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="aad93-106">[in] Wskaźnik do [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) wystąpienia opisujący żądany moduł <xref:System.AppDomain>, zestawu i nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="aad93-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="aad93-107">[out] Wskaźnik do Unikatowy identyfikator `IStream` zawierający załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="aad93-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="aad93-108">[out] Wskaźnik do adresu `IStream` obiektu, który zawiera obraz przenośny plik wykonywalny (PE), który można załadować lub wartość null, jeśli nie można odnaleźć modułu.</span><span class="sxs-lookup"><span data-stu-id="aad93-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="aad93-109">[out] Wskaźnik do adresu `IStream` obiektu, który zawiera informacje o debugowaniu (PDB) program dla żądanego modułu lub wartość null, jeśli nie można odnaleźć pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="aad93-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aad93-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aad93-110">Return Value</span></span>  
  
|<span data-ttu-id="aad93-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aad93-111">HRESULT</span></span>|<span data-ttu-id="aad93-112">Opis</span><span class="sxs-lookup"><span data-stu-id="aad93-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aad93-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="aad93-113">S_OK</span></span>|<span data-ttu-id="aad93-114">`ProvideModule` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aad93-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="aad93-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aad93-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aad93-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="aad93-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aad93-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aad93-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aad93-118">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="aad93-118">The call timed out.</span></span>|  
|<span data-ttu-id="aad93-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aad93-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aad93-120">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="aad93-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aad93-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aad93-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aad93-122">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="aad93-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aad93-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aad93-123">E_FAIL</span></span>|<span data-ttu-id="aad93-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="aad93-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aad93-125">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="aad93-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aad93-126">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aad93-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aad93-127">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="aad93-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="aad93-128">Nie można zlokalizować żądanego zestawu lub zasobu połączonego.</span><span class="sxs-lookup"><span data-stu-id="aad93-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="aad93-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="aad93-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="aad93-130">`pdwModuleId` nie jest wystarczająco duży, aby zawierać identyfikator, który chce zwracać hosta.</span><span class="sxs-lookup"><span data-stu-id="aad93-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aad93-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aad93-131">Remarks</span></span>  
 <span data-ttu-id="aad93-132">Zwracane wartości tożsamości dla `pdwModuleId` jest określana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="aad93-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="aad93-133">Identyfikatory muszą być unikatowe w obrębie okres istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="aad93-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="aad93-134">Środowisko CLR używa tej wartości jako unikatowy identyfikator dla tego strumienia skojarzone.</span><span class="sxs-lookup"><span data-stu-id="aad93-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="aad93-135">Sprawdza każdej wartości z wartościami dla `pAssemblyId` zwrócony przez wywołania [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) i wartościami dla `pdwModuleId` zwrócony przez inne wywołania `ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="aad93-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="aad93-136">Jeśli host zwraca tej samej wartości identyfikatora dla innej `IStream`, CLR sprawdza, czy zawartość strumieniu już zostały zamapowane.</span><span class="sxs-lookup"><span data-stu-id="aad93-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="aad93-137">Jeśli tak, CLR ładuje istniejącą kopię obrazu zamiast nowego mapowania.</span><span class="sxs-lookup"><span data-stu-id="aad93-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="aad93-138">W związku z tym identyfikatorem musi również nie mogą się pokrywać o identyfikatorach zestaw zwrócony z `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="aad93-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aad93-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aad93-139">Requirements</span></span>  
 <span data-ttu-id="aad93-140">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aad93-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aad93-141">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aad93-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aad93-142">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aad93-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aad93-143">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aad93-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad93-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aad93-144">See Also</span></span>  
 [<span data-ttu-id="aad93-145">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="aad93-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="aad93-146">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aad93-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="aad93-147">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="aad93-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
