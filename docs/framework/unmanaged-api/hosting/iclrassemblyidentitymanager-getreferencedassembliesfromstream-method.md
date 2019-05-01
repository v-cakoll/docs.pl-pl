---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d6f93ee7870c9d81394ee55c5574c52c2aea50a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969978"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="aea49-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="aea49-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="aea49-103">Pobiera wskaźnik do [iclrreferenceassemblyenum —](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) obiekt, który zawiera dane o tożsamości zestawu dla zestawów odwołuje się zestaw w określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="aea49-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea49-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aea49-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aea49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aea49-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="aea49-106">[in] Wskaźnik interfejsu do `IStream` zawierającego zestaw, który ma zostać obliczone.</span><span class="sxs-lookup"><span data-stu-id="aea49-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="aea49-107">[in] Podana dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="aea49-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="aea49-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT stanowi jedyną wartość, która obsługuje bieżącą wersję środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="aea49-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="aea49-109">[in] Wskaźnik do [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) obiekt, który zawiera dane o tożsamości zestawu dla zestawów, które mają być wykluczone z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="aea49-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="aea49-110">[out] Wskaźnik na adres `ICLRReferenceAssemblyEnum` obiekt, który zawiera dane o tożsamości zestawu dla zestawów odwołuje się zestaw w `pStream`, z wyłączeniem zestawów w `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="aea49-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aea49-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aea49-111">Return Value</span></span>  
  
|<span data-ttu-id="aea49-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aea49-112">HRESULT</span></span>|<span data-ttu-id="aea49-113">Opis</span><span class="sxs-lookup"><span data-stu-id="aea49-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aea49-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="aea49-114">S_OK</span></span>|<span data-ttu-id="aea49-115">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aea49-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="aea49-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aea49-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aea49-117">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="aea49-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aea49-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aea49-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aea49-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="aea49-119">The call timed out.</span></span>|  
|<span data-ttu-id="aea49-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aea49-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aea49-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="aea49-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aea49-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aea49-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aea49-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="aea49-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aea49-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aea49-124">E_FAIL</span></span>|<span data-ttu-id="aea49-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="aea49-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aea49-126">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="aea49-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aea49-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aea49-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aea49-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aea49-128">Remarks</span></span>  
 <span data-ttu-id="aea49-129">Obiekt wywołujący, można wykluczyć zestaw odwołania do zestawu znanych z liście zwracanych.</span><span class="sxs-lookup"><span data-stu-id="aea49-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="aea49-130">Ten zestaw jest definiowany przez `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="aea49-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aea49-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aea49-131">Requirements</span></span>  
 <span data-ttu-id="aea49-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aea49-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aea49-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aea49-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aea49-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aea49-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aea49-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aea49-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea49-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aea49-136">See also</span></span>

- [<span data-ttu-id="aea49-137">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aea49-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="aea49-138">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="aea49-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="aea49-139">ICLRReferenceAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="aea49-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
