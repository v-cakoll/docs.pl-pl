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
ms.openlocfilehash: eed09a8149a21140ad61133f29391f86cb0fb929
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124469"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="059fd-102">IHostAssemblyStore::ProvideModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="059fd-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="059fd-103">Rozpoznaje moduł wewnątrz zestawu lub połączony (ale nie osadzony) plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="059fd-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="059fd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="059fd-104">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="059fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="059fd-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="059fd-106">podczas Wskaźnik do wystąpienia [ModuleBindInfo —](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) , który opisuje <xref:System.AppDomain>, zestaw i nazwę modułu żądanego modułu.</span><span class="sxs-lookup"><span data-stu-id="059fd-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="059fd-107">określoną Wskaźnik do unikatowego identyfikatora `IStream` zawierającego załadowany moduł.</span><span class="sxs-lookup"><span data-stu-id="059fd-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="059fd-108">określoną Wskaźnik do adresu obiektu `IStream`, który zawiera obraz przenośnego pliku wykonywalnego (PE), który ma zostać załadowany lub ma wartość null, jeśli nie można znaleźć modułu.</span><span class="sxs-lookup"><span data-stu-id="059fd-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="059fd-109">określoną Wskaźnik na adres `IStream` obiektu, który zawiera informacje o debugowaniu programu (PDB) dla żądanego modułu, lub wartość null, jeśli nie można znaleźć pliku. pdb.</span><span class="sxs-lookup"><span data-stu-id="059fd-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="059fd-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="059fd-110">Return Value</span></span>  
  
|<span data-ttu-id="059fd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="059fd-111">HRESULT</span></span>|<span data-ttu-id="059fd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="059fd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="059fd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="059fd-113">S_OK</span></span>|<span data-ttu-id="059fd-114">`ProvideModule` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="059fd-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="059fd-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="059fd-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="059fd-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="059fd-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="059fd-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="059fd-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="059fd-118">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="059fd-118">The call timed out.</span></span>|  
|<span data-ttu-id="059fd-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="059fd-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="059fd-120">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="059fd-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="059fd-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="059fd-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="059fd-122">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="059fd-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="059fd-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="059fd-123">E_FAIL</span></span>|<span data-ttu-id="059fd-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="059fd-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="059fd-125">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="059fd-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="059fd-126">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="059fd-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="059fd-127">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="059fd-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="059fd-128">Nie można zlokalizować żądanego zestawu lub połączonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="059fd-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="059fd-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="059fd-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="059fd-130">`pdwModuleId` nie jest wystarczająco duży, aby można było zawierać identyfikator, który chce zwrócić host.</span><span class="sxs-lookup"><span data-stu-id="059fd-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="059fd-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="059fd-131">Remarks</span></span>  
 <span data-ttu-id="059fd-132">Wartość tożsamości zwrócona dla `pdwModuleId` jest określona przez hosta.</span><span class="sxs-lookup"><span data-stu-id="059fd-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="059fd-133">Identyfikatory muszą być unikatowe w okresie istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="059fd-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="059fd-134">Środowisko CLR używa tej wartości jako unikatowego identyfikatora skojarzonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="059fd-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="059fd-135">Sprawdza każdą wartość w odniesieniu do wartości `pAssemblyId` zwracanych przez wywołania do [ProvideAssembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) i wartości dla `pdwModuleId` zwracanych przez inne wywołania do `ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="059fd-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="059fd-136">Jeśli host zwraca tę samą wartość identyfikatora dla innego `IStream`, środowisko CLR sprawdzi, czy zawartość tego strumienia została już zamapowana.</span><span class="sxs-lookup"><span data-stu-id="059fd-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="059fd-137">Jeśli tak, środowisko CLR ładuje istniejącą kopię obrazu zamiast mapowania nowej.</span><span class="sxs-lookup"><span data-stu-id="059fd-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="059fd-138">W związku z tym, identyfikator nie może również nakładać się na identyfikatory zestawu zwrócone z `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="059fd-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="059fd-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="059fd-139">Requirements</span></span>  
 <span data-ttu-id="059fd-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="059fd-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="059fd-141">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="059fd-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="059fd-142">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="059fd-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="059fd-143">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="059fd-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="059fd-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="059fd-144">See also</span></span>

- [<span data-ttu-id="059fd-145">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="059fd-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="059fd-146">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="059fd-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="059fd-147">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="059fd-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
