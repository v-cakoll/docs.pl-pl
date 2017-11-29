---
title: "ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64a43640d08acbab0bcf505cc8a5850784ff18ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="ec432-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec432-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="ec432-103">Pobiera wskaźnik do [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) obiekt zawierający dane tożsamości zestawu dla zestawów odwołuje się zestaw w określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="ec432-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec432-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec432-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec432-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec432-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="ec432-106">[in] Wskaźnik interfejsu do `IStream` zawierający ten zestaw ma zostać obliczone.</span><span class="sxs-lookup"><span data-stu-id="ec432-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ec432-107">[in] Podany dla przyszłych rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="ec432-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="ec432-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest tylko wartość, która obsługuje bieżącą wersję środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ec432-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="ec432-109">[in] Wskaźnik do [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) obiekt zawierający dane tożsamości zestawu dla zestawów, które mają być wykluczone z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="ec432-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="ec432-110">[out] Wskaźnik do adresu `ICLRReferenceAssemblyEnum` obiekt zawierający dane tożsamości zestawu dla zestawów odwołuje się zestaw w `pStream`, z wyłączeniem zestawów w `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="ec432-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec432-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ec432-111">Return Value</span></span>  
  
|<span data-ttu-id="ec432-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec432-112">HRESULT</span></span>|<span data-ttu-id="ec432-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ec432-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec432-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec432-114">S_OK</span></span>|<span data-ttu-id="ec432-115">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ec432-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="ec432-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ec432-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ec432-117">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ec432-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ec432-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ec432-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ec432-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ec432-119">The call timed out.</span></span>|  
|<span data-ttu-id="ec432-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ec432-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ec432-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ec432-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ec432-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ec432-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ec432-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ec432-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ec432-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ec432-124">E_FAIL</span></span>|<span data-ttu-id="ec432-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ec432-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ec432-126">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ec432-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ec432-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ec432-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec432-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec432-128">Remarks</span></span>  
 <span data-ttu-id="ec432-129">Obiekt wywołujący można wykluczyć zestaw odwołania do zestawów znanych na liście zwracanych.</span><span class="sxs-lookup"><span data-stu-id="ec432-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="ec432-130">Ten zestaw jest definiowana za pomocą `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="ec432-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec432-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec432-131">Requirements</span></span>  
 <span data-ttu-id="ec432-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec432-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec432-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ec432-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec432-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ec432-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec432-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec432-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec432-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec432-136">See Also</span></span>  
 [<span data-ttu-id="ec432-137">ICLRAssemblyIdentityManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="ec432-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="ec432-138">ICLRAssemblyReferenceList — interfejs</span><span class="sxs-lookup"><span data-stu-id="ec432-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="ec432-139">ICLRReferenceAssemblyEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="ec432-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
