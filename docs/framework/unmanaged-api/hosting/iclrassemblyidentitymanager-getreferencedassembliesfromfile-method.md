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
ms.openlocfilehash: 3c4f673d88594e86004c6d51a4d58a0ac4642875
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615946"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="a60b0-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="a60b0-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="a60b0-103">Pobiera wystąpienie [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) , które zawiera listę zestawów, do których odwołuje się zestaw w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="a60b0-103">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a60b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a60b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a60b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a60b0-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="a60b0-106">podczas Ścieżka do zestawu, który ma zostać obliczony.</span><span class="sxs-lookup"><span data-stu-id="a60b0-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a60b0-107">podczas Udostępniane do przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="a60b0-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="a60b0-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest jedyną wartością, którą obsługuje bieżąca wersja środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a60b0-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="a60b0-109">podczas Wskaźnik do obiektu [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , który reprezentuje zestawy, które powinny być wykluczone z `ppReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="a60b0-109">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="a60b0-110">określoną Wskaźnik do adresu `ICLRReferenceAssemblyEnum` obiektu, który zawiera dane tożsamości zestawu dla zestawów, do których odwołuje się zestaw `pwzFilePath` , z wyłączeniem zestawów reprezentowanych przez `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="a60b0-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a60b0-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a60b0-111">Return Value</span></span>  
  
|<span data-ttu-id="a60b0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a60b0-112">HRESULT</span></span>|<span data-ttu-id="a60b0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a60b0-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a60b0-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a60b0-114">S_OK</span></span>|<span data-ttu-id="a60b0-115">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="a60b0-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="a60b0-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a60b0-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a60b0-117">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a60b0-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a60b0-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a60b0-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a60b0-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a60b0-119">The call timed out.</span></span>|  
|<span data-ttu-id="a60b0-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a60b0-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a60b0-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a60b0-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a60b0-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a60b0-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a60b0-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a60b0-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a60b0-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a60b0-124">E_FAIL</span></span>|<span data-ttu-id="a60b0-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a60b0-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a60b0-126">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="a60b0-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a60b0-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a60b0-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a60b0-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a60b0-128">Remarks</span></span>  
 <span data-ttu-id="a60b0-129">Obiekt wywołujący może zdecydować się na wykluczenie zestawu znanych odwołań do zestawu ze zwracanej listy.</span><span class="sxs-lookup"><span data-stu-id="a60b0-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="a60b0-130">Ten zestaw jest definiowany przez `pExcludeAssembliesList` parametr.</span><span class="sxs-lookup"><span data-stu-id="a60b0-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a60b0-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a60b0-131">Requirements</span></span>  
 <span data-ttu-id="a60b0-132">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a60b0-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a60b0-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a60b0-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a60b0-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a60b0-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a60b0-135">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a60b0-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a60b0-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a60b0-136">See also</span></span>

- [<span data-ttu-id="a60b0-137">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a60b0-137">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="a60b0-138">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a60b0-138">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="a60b0-139">ICLRReferenceAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a60b0-139">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
