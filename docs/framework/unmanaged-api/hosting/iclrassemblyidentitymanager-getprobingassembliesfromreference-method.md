---
title: "ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80ffc1cb4c1387aae673ec757b846c7075e20b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="d37f6-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference — Metoda</span><span class="sxs-lookup"><span data-stu-id="d37f6-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="d37f6-103">Pobiera [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) modułu wyliczającego dla tożsamości zestawu odwołuje się zestaw z typem określonym tożsamości.</span><span class="sxs-lookup"><span data-stu-id="d37f6-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d37f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d37f6-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d37f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d37f6-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="d37f6-106">[in] Nieprawidłowa wartość, która określa architektury procesora, zgodnie z definicją w pliku WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="d37f6-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d37f6-107">[in] Podany dla przyszłych rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="d37f6-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="d37f6-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest tylko wartość, która obsługuje bieżącą wersję środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d37f6-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="d37f6-109">[in] Nieprzezroczysta powiązanie tożsamości, zazwyczaj są zwracane po wywołaniu [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) lub [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d37f6-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="d37f6-110">[out] Wskaźnik interfejsu do `ICLRProbingAssemblyEnum` moduł wyliczający, który zawiera odwołania do zestawów odwołuje się zestaw identyfikowane przez `pwzReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="d37f6-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d37f6-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d37f6-111">Return Value</span></span>  
  
|<span data-ttu-id="d37f6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d37f6-112">HRESULT</span></span>|<span data-ttu-id="d37f6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d37f6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d37f6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d37f6-114">S_OK</span></span>|<span data-ttu-id="d37f6-115">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d37f6-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="d37f6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d37f6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d37f6-117">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d37f6-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d37f6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d37f6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d37f6-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d37f6-119">The call timed out.</span></span>|  
|<span data-ttu-id="d37f6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d37f6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d37f6-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d37f6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d37f6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d37f6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d37f6-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d37f6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d37f6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d37f6-124">E_FAIL</span></span>|<span data-ttu-id="d37f6-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d37f6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d37f6-126">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d37f6-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d37f6-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d37f6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d37f6-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d37f6-128">Requirements</span></span>  
 <span data-ttu-id="d37f6-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d37f6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d37f6-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d37f6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d37f6-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d37f6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d37f6-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d37f6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37f6-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d37f6-133">See Also</span></span>  
 [<span data-ttu-id="d37f6-134">ICLRAssemblyIdentityManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="d37f6-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="d37f6-135">ICLRAssemblyReferenceList — interfejs</span><span class="sxs-lookup"><span data-stu-id="d37f6-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="d37f6-136">ICLRProbingAssemblyEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="d37f6-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
