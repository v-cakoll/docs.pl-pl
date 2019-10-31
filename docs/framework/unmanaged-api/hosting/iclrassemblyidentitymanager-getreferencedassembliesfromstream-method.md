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
ms.openlocfilehash: f4c200ad23ff7a71298e84fda857912da53978a5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126684"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="dd148-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd148-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="dd148-103">Pobiera wskaźnik do obiektu [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) , który zawiera dane tożsamości zestawu dla zestawów, do których odwołuje się zestaw w określonym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="dd148-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd148-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd148-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd148-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd148-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="dd148-106">podczas Wskaźnik interfejsu do `IStream` zawierający zestaw do oceny.</span><span class="sxs-lookup"><span data-stu-id="dd148-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dd148-107">podczas Udostępniane do przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="dd148-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="dd148-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest jedyną wartością, którą obsługuje bieżąca wersja środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="dd148-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="dd148-109">podczas Wskaźnik do obiektu [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , który zawiera dane tożsamości zestawu dla zestawów, które mają zostać wykluczone z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="dd148-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="dd148-110">określoną Wskaźnik do adresu `ICLRReferenceAssemblyEnum` obiektu, który zawiera dane tożsamości zestawu dla zestawów, do których odwołuje się zestaw w `pStream`, z wyłączeniem zestawów w `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="dd148-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd148-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dd148-111">Return Value</span></span>  
  
|<span data-ttu-id="dd148-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd148-112">HRESULT</span></span>|<span data-ttu-id="dd148-113">Opis</span><span class="sxs-lookup"><span data-stu-id="dd148-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd148-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd148-114">S_OK</span></span>|<span data-ttu-id="dd148-115">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="dd148-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="dd148-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dd148-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dd148-117">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dd148-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dd148-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dd148-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dd148-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="dd148-119">The call timed out.</span></span>|  
|<span data-ttu-id="dd148-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd148-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dd148-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="dd148-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dd148-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dd148-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dd148-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="dd148-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dd148-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dd148-124">E_FAIL</span></span>|<span data-ttu-id="dd148-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dd148-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dd148-126">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="dd148-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dd148-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dd148-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd148-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd148-128">Remarks</span></span>  
 <span data-ttu-id="dd148-129">Obiekt wywołujący może zdecydować się na wykluczenie zestawu znanych odwołań do zestawu ze zwracanej listy.</span><span class="sxs-lookup"><span data-stu-id="dd148-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="dd148-130">Ten zestaw jest definiowany przez `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="dd148-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd148-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd148-131">Requirements</span></span>  
 <span data-ttu-id="dd148-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd148-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd148-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dd148-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd148-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd148-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd148-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd148-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd148-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd148-136">See also</span></span>

- [<span data-ttu-id="dd148-137">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd148-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="dd148-138">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd148-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="dd148-139">ICLRReferenceAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd148-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
