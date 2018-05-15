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
ms.openlocfilehash: 26423837c173b5f18282a8aa480ae92ecc452489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="92380-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference — Metoda</span><span class="sxs-lookup"><span data-stu-id="92380-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="92380-103">Pobiera [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) modułu wyliczającego dla tożsamości zestawu odwołuje się zestaw z typem określonym tożsamości.</span><span class="sxs-lookup"><span data-stu-id="92380-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92380-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92380-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92380-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92380-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="92380-106">[in] Nieprawidłowa wartość, która określa architektury procesora, zgodnie z definicją w pliku WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="92380-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="92380-107">[in] Podany dla przyszłych rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="92380-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="92380-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest tylko wartość, która obsługuje bieżącą wersję środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="92380-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="92380-109">[in] Nieprzezroczysta powiązanie tożsamości, zazwyczaj są zwracane po wywołaniu [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) lub [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="92380-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="92380-110">[out] Wskaźnik interfejsu do `ICLRProbingAssemblyEnum` moduł wyliczający, który zawiera odwołania do zestawów odwołuje się zestaw identyfikowane przez `pwzReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="92380-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92380-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="92380-111">Return Value</span></span>  
  
|<span data-ttu-id="92380-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92380-112">HRESULT</span></span>|<span data-ttu-id="92380-113">Opis</span><span class="sxs-lookup"><span data-stu-id="92380-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92380-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="92380-114">S_OK</span></span>|<span data-ttu-id="92380-115">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="92380-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="92380-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92380-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92380-117">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="92380-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92380-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92380-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92380-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="92380-119">The call timed out.</span></span>|  
|<span data-ttu-id="92380-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92380-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92380-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="92380-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92380-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92380-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92380-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="92380-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92380-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92380-124">E_FAIL</span></span>|<span data-ttu-id="92380-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="92380-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92380-126">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="92380-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92380-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="92380-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92380-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92380-128">Requirements</span></span>  
 <span data-ttu-id="92380-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92380-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92380-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92380-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92380-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92380-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92380-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92380-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92380-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92380-133">See Also</span></span>  
 [<span data-ttu-id="92380-134">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="92380-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="92380-135">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="92380-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="92380-136">ICLRProbingAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="92380-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
