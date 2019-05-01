---
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e926fb2753367370e9aca726806eb8747e32048
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985130"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="dc68d-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference — Metoda</span><span class="sxs-lookup"><span data-stu-id="dc68d-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="dc68d-103">Pobiera [iclrprobingassemblyenum —](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) modułu wyliczającego dla tożsamości zestawu odwołuje się zestaw z typem określonej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="dc68d-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc68d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc68d-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc68d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc68d-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="dc68d-106">[in] Prawidłowa wartość, która określa z architekturą procesora, zgodnie z definicją w pliku WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="dc68d-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dc68d-107">[in] Podana dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="dc68d-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="dc68d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT stanowi jedyną wartość, która obsługuje bieżącą wersję środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="dc68d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="dc68d-109">[in] Nieprzezroczysty powiązanie tożsamości, zwykle zwrócony z wywołania do [iclrassemblyidentitymanager::getbindingidentityfromfile —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) lub [iclrassemblyidentitymanager::getbindingidentityfromstream —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="dc68d-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="dc68d-110">[out] Wskaźnik interfejsu do `ICLRProbingAssemblyEnum` moduł wyliczający, który zawiera odwołania do zestawów odwołuje się zestaw identyfikowane przez `pwzReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="dc68d-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc68d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dc68d-111">Return Value</span></span>  
  
|<span data-ttu-id="dc68d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc68d-112">HRESULT</span></span>|<span data-ttu-id="dc68d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="dc68d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc68d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc68d-114">S_OK</span></span>|<span data-ttu-id="dc68d-115">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dc68d-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="dc68d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc68d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc68d-117">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="dc68d-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dc68d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dc68d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dc68d-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="dc68d-119">The call timed out.</span></span>|  
|<span data-ttu-id="dc68d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dc68d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dc68d-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="dc68d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dc68d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dc68d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dc68d-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="dc68d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dc68d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc68d-124">E_FAIL</span></span>|<span data-ttu-id="dc68d-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dc68d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dc68d-126">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="dc68d-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dc68d-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dc68d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc68d-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc68d-128">Requirements</span></span>  
 <span data-ttu-id="dc68d-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc68d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc68d-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc68d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc68d-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc68d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc68d-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc68d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc68d-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc68d-133">See also</span></span>

- [<span data-ttu-id="dc68d-134">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dc68d-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="dc68d-135">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="dc68d-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="dc68d-136">ICLRProbingAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="dc68d-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
