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
ms.openlocfilehash: f97490e89e835716911072dbad5f70d8e55e76e6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805019"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="19a4c-102">IHostAssemblyStore::ProvideAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="19a4c-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="19a4c-103">Pobiera odwołanie do zestawu, który nie jest przywoływany przez [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , który jest zwracany z [IHostAssemblyManager:: GetNonHostStoreAssemblies —](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="19a4c-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="19a4c-104">Wywołania środowiska uruchomieniowego języka wspólnego (CLR) `ProvideAssembly` dla każdego zestawu, który nie znajduje się na liście.</span><span class="sxs-lookup"><span data-stu-id="19a4c-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19a4c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="19a4c-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19a4c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="19a4c-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="19a4c-107">podczas Wskaźnik do wystąpienia [AssemblyBindInfo —](assemblybindinfo-structure.md) , który jest używany przez hosta w celu określenia niektórych charakterystyk powiązań, w tym obecności lub braku jakichkolwiek zasad dotyczących wersji oraz zestawu, z którym ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="19a4c-107">[in] A pointer to an [AssemblyBindInfo](assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="19a4c-108">określoną Wskaźnik do unikatowego identyfikatora żądanego zestawu `IStream` .</span><span class="sxs-lookup"><span data-stu-id="19a4c-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="19a4c-109">określoną Wskaźnik do danych specyficznych dla hosta, który jest używany do określenia dowodu żądanego zestawu bez konieczności wywołania wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="19a4c-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="19a4c-110">`pHostContext`odpowiada <xref:System.Reflection.Assembly.HostContext%2A> właściwości zarządzanej <xref:System.Reflection.Assembly> klasy.</span><span class="sxs-lookup"><span data-stu-id="19a4c-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="19a4c-111">określoną Wskaźnik do adresu zawierającego `IStream` obraz przenośnego pliku wykonywalnego (PE), który ma zostać załadowany lub ma wartość null, jeśli nie można znaleźć zestawu.</span><span class="sxs-lookup"><span data-stu-id="19a4c-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="19a4c-112">określoną Wskaźnik na adres `IStream` , który zawiera informacje o debugowaniu programu (PDB) lub wartość null, jeśli nie można znaleźć pliku. pdb.</span><span class="sxs-lookup"><span data-stu-id="19a4c-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19a4c-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="19a4c-113">Return Value</span></span>  
  
|<span data-ttu-id="19a4c-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19a4c-114">HRESULT</span></span>|<span data-ttu-id="19a4c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="19a4c-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19a4c-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="19a4c-116">S_OK</span></span>|<span data-ttu-id="19a4c-117">`ProvideAssembly`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="19a4c-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="19a4c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19a4c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19a4c-119">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="19a4c-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="19a4c-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="19a4c-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="19a4c-121">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="19a4c-121">The call timed out.</span></span>|  
|<span data-ttu-id="19a4c-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="19a4c-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="19a4c-123">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="19a4c-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="19a4c-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="19a4c-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="19a4c-125">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="19a4c-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="19a4c-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19a4c-126">E_FAIL</span></span>|<span data-ttu-id="19a4c-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="19a4c-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="19a4c-128">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="19a4c-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="19a4c-129">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="19a4c-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="19a4c-130">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="19a4c-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="19a4c-131">Nie można zlokalizować żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="19a4c-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="19a4c-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="19a4c-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="19a4c-133">Rozmiar buforu określony przez `pAssemblyId` nie jest wystarczająco duży, aby pomieścić identyfikator, który chce zwrócić host.</span><span class="sxs-lookup"><span data-stu-id="19a4c-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19a4c-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19a4c-134">Remarks</span></span>  
 <span data-ttu-id="19a4c-135">Zwracana wartość tożsamości `pAssemblyId` jest określana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="19a4c-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="19a4c-136">Identyfikatory muszą być unikatowe w okresie istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="19a4c-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="19a4c-137">Środowisko CLR używa tej wartości jako unikatowego identyfikatora strumienia.</span><span class="sxs-lookup"><span data-stu-id="19a4c-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="19a4c-138">Sprawdza każdą wartość dla wartości `pAssemblyId` zwracanych przez inne wywołania do `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="19a4c-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="19a4c-139">Jeśli host zwraca tę samą `pAssemblyId` wartość dla innego `IStream` , środowisko CLR sprawdza, czy zawartość tego strumienia została już zamapowana.</span><span class="sxs-lookup"><span data-stu-id="19a4c-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="19a4c-140">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię obrazu zamiast mapowania nowej.</span><span class="sxs-lookup"><span data-stu-id="19a4c-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19a4c-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19a4c-141">Requirements</span></span>  
 <span data-ttu-id="19a4c-142">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19a4c-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19a4c-143">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19a4c-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19a4c-144">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="19a4c-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19a4c-145">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19a4c-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19a4c-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19a4c-146">See also</span></span>

- [<span data-ttu-id="19a4c-147">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="19a4c-147">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="19a4c-148">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="19a4c-148">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="19a4c-149">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="19a4c-149">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
