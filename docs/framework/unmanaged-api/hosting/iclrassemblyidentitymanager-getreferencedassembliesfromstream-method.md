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
ms.openlocfilehash: 4f06dd7b85446eec986055418d2cf558b9b5bd7a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615933"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="b9106-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="b9106-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="b9106-103">Pobiera wskaźnik do obiektu [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) , który zawiera dane tożsamości zestawu dla zestawów, do których odwołuje się zestaw w określonym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="b9106-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9106-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9106-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9106-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9106-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="b9106-106">podczas Wskaźnik interfejsu do `IStream` zawierającego zestaw, który ma zostać obliczony.</span><span class="sxs-lookup"><span data-stu-id="b9106-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b9106-107">podczas Udostępniane do przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="b9106-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="b9106-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest jedyną wartością, którą obsługuje bieżąca wersja środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="b9106-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="b9106-109">podczas Wskaźnik do obiektu [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , który zawiera dane tożsamości zestawu dla zestawów, z których mają zostać wykluczone `ppReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="b9106-109">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="b9106-110">określoną Wskaźnik do adresu `ICLRReferenceAssemblyEnum` obiektu, który zawiera dane tożsamości zestawu dla zestawów, do których odwołuje się zestaw `pStream` , z wyłączeniem zestawów w `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="b9106-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9106-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b9106-111">Return Value</span></span>  
  
|<span data-ttu-id="b9106-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9106-112">HRESULT</span></span>|<span data-ttu-id="b9106-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b9106-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9106-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9106-114">S_OK</span></span>|<span data-ttu-id="b9106-115">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="b9106-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="b9106-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9106-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9106-117">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b9106-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9106-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9106-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9106-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b9106-119">The call timed out.</span></span>|  
|<span data-ttu-id="b9106-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9106-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9106-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b9106-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9106-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9106-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9106-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="b9106-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9106-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9106-124">E_FAIL</span></span>|<span data-ttu-id="b9106-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b9106-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9106-126">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="b9106-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9106-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b9106-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9106-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9106-128">Remarks</span></span>  
 <span data-ttu-id="b9106-129">Obiekt wywołujący może zdecydować się na wykluczenie zestawu znanych odwołań do zestawu ze zwracanej listy.</span><span class="sxs-lookup"><span data-stu-id="b9106-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="b9106-130">Ten zestaw jest definiowany przez `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="b9106-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9106-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9106-131">Requirements</span></span>  
 <span data-ttu-id="b9106-132">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9106-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9106-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b9106-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9106-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b9106-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9106-135">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9106-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9106-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9106-136">See also</span></span>

- [<span data-ttu-id="b9106-137">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9106-137">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b9106-138">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b9106-138">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b9106-139">ICLRReferenceAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9106-139">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
