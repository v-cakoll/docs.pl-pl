---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eac70f35e3c4c0beab0842f24702213a98fbaae3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478495"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="07b42-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="07b42-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="07b42-103">Pobiera [iclrreferenceassemblyenum —](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) wystąpienia, które zawiera listę zestawów, które odwołuje się zestaw w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="07b42-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07b42-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07b42-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07b42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07b42-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="07b42-106">[in] Ścieżka do zestawu, który ma zostać obliczone.</span><span class="sxs-lookup"><span data-stu-id="07b42-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="07b42-107">[in] Podana dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="07b42-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="07b42-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT stanowi jedyną wartość, która obsługuje bieżącą wersję środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="07b42-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="07b42-109">[in] Wskaźnik do [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) obiekt, który reprezentuje zestawów, które powinny być wykluczone z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="07b42-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="07b42-110">[out] Wskaźnik na adres `ICLRReferenceAssemblyEnum` obiekt, który zawiera dane o tożsamości zestawu dla zestawów odwołuje się zestaw w `pwzFilePath`, z wyłączeniem zestawów, reprezentowane przez `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="07b42-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07b42-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="07b42-111">Return Value</span></span>  
  
|<span data-ttu-id="07b42-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07b42-112">HRESULT</span></span>|<span data-ttu-id="07b42-113">Opis</span><span class="sxs-lookup"><span data-stu-id="07b42-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07b42-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="07b42-114">S_OK</span></span>|<span data-ttu-id="07b42-115">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="07b42-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="07b42-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="07b42-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="07b42-117">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="07b42-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="07b42-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07b42-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="07b42-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="07b42-119">The call timed out.</span></span>|  
|<span data-ttu-id="07b42-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="07b42-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="07b42-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="07b42-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="07b42-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="07b42-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="07b42-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="07b42-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="07b42-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="07b42-124">E_FAIL</span></span>|<span data-ttu-id="07b42-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="07b42-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="07b42-126">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="07b42-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="07b42-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="07b42-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07b42-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07b42-128">Remarks</span></span>  
 <span data-ttu-id="07b42-129">Obiekt wywołujący, można wykluczyć zestaw odwołania do zestawu znanych z liście zwracanych.</span><span class="sxs-lookup"><span data-stu-id="07b42-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="07b42-130">Ten zestaw jest definiowany przez `pExcludeAssembliesList` parametru.</span><span class="sxs-lookup"><span data-stu-id="07b42-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07b42-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07b42-131">Requirements</span></span>  
 <span data-ttu-id="07b42-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07b42-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07b42-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="07b42-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07b42-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07b42-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07b42-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07b42-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b42-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07b42-136">See also</span></span>
- [<span data-ttu-id="07b42-137">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="07b42-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="07b42-138">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="07b42-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="07b42-139">ICLRReferenceAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="07b42-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
