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
ms.openlocfilehash: a93d700c9c398076d87156cd2eb9c6d0d08cccfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124488"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="7be43-102">IHostAssemblyStore::ProvideAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="7be43-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="7be43-103">Pobiera odwołanie do zestawu, który nie jest przywoływany przez [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , który jest zwracany z [IHostAssemblyManager:: GetNonHostStoreAssemblies —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="7be43-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="7be43-104">Wywołania środowiska uruchomieniowego języka wspólnego (CLR) `ProvideAssembly` dla każdego zestawu, który nie znajduje się na liście.</span><span class="sxs-lookup"><span data-stu-id="7be43-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be43-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7be43-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7be43-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7be43-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="7be43-107">podczas Wskaźnik do wystąpienia [AssemblyBindInfo —](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) , który jest używany przez hosta w celu określenia niektórych charakterystyk powiązań, w tym obecności lub braku jakichkolwiek zasad dotyczących wersji oraz zestawu, z którym ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="7be43-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="7be43-108">określoną Wskaźnik do unikatowego identyfikatora żądanego zestawu dla tego `IStream`.</span><span class="sxs-lookup"><span data-stu-id="7be43-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="7be43-109">określoną Wskaźnik do danych specyficznych dla hosta, który jest używany do określenia dowodu żądanego zestawu bez konieczności wywołania wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="7be43-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="7be43-110">`pHostContext` odpowiada właściwości <xref:System.Reflection.Assembly.HostContext%2A> klasy zarządzanej <xref:System.Reflection.Assembly>.</span><span class="sxs-lookup"><span data-stu-id="7be43-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="7be43-111">określoną Wskaźnik do adresu `IStream`, który zawiera obraz przenośnego pliku wykonywalnego (PE), który ma zostać załadowany lub ma wartość null, jeśli nie można znaleźć zestawu.</span><span class="sxs-lookup"><span data-stu-id="7be43-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="7be43-112">określoną Wskaźnik na adres `IStream`, który zawiera informacje o debugowaniu programu (PDB), lub wartość null, jeśli nie można znaleźć pliku. pdb.</span><span class="sxs-lookup"><span data-stu-id="7be43-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7be43-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7be43-113">Return Value</span></span>  
  
|<span data-ttu-id="7be43-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7be43-114">HRESULT</span></span>|<span data-ttu-id="7be43-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7be43-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7be43-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="7be43-116">S_OK</span></span>|<span data-ttu-id="7be43-117">`ProvideAssembly` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="7be43-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="7be43-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7be43-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7be43-119">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7be43-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7be43-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7be43-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7be43-121">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="7be43-121">The call timed out.</span></span>|  
|<span data-ttu-id="7be43-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7be43-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7be43-123">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7be43-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7be43-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7be43-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7be43-125">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="7be43-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7be43-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7be43-126">E_FAIL</span></span>|<span data-ttu-id="7be43-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7be43-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7be43-128">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="7be43-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7be43-129">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7be43-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7be43-130">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="7be43-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="7be43-131">Nie można zlokalizować żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7be43-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="7be43-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7be43-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7be43-133">Rozmiar buforu określony przez `pAssemblyId` nie jest wystarczająco duży, aby pomieścić identyfikator, który chce zwrócić host.</span><span class="sxs-lookup"><span data-stu-id="7be43-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7be43-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7be43-134">Remarks</span></span>  
 <span data-ttu-id="7be43-135">Wartość tożsamości zwrócona dla `pAssemblyId` jest określona przez hosta.</span><span class="sxs-lookup"><span data-stu-id="7be43-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="7be43-136">Identyfikatory muszą być unikatowe w okresie istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="7be43-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="7be43-137">Środowisko CLR używa tej wartości jako unikatowego identyfikatora strumienia.</span><span class="sxs-lookup"><span data-stu-id="7be43-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="7be43-138">Sprawdza każdą wartość w odniesieniu do wartości `pAssemblyId` zwracanych przez inne wywołania do `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="7be43-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="7be43-139">Jeśli host zwróci tę samą `pAssemblyId` wartość dla innego `IStream`, środowisko CLR sprawdzi, czy zawartość tego strumienia została już zamapowana.</span><span class="sxs-lookup"><span data-stu-id="7be43-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="7be43-140">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię obrazu zamiast mapowania nowej.</span><span class="sxs-lookup"><span data-stu-id="7be43-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7be43-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7be43-141">Requirements</span></span>  
 <span data-ttu-id="7be43-142">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7be43-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7be43-143">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7be43-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7be43-144">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7be43-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7be43-145">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7be43-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be43-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7be43-146">See also</span></span>

- [<span data-ttu-id="7be43-147">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="7be43-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7be43-148">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7be43-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="7be43-149">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="7be43-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
