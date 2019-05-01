---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3d5e53dd0845fbd01dbd9d20ce8feef12748c04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985182"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="6b282-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b282-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="6b282-103">Pobiera tożsamość zestawu, wiązanie danych do zestawu w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="6b282-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b282-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b282-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b282-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b282-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="6b282-106">[in] Ścieżka do pliku, który ma zostać obliczone.</span><span class="sxs-lookup"><span data-stu-id="6b282-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6b282-107">[in] Wartość [eclrassemblyidentityflags —](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) wyliczenie, które wskazuje typ tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="6b282-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="6b282-108">Podana dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="6b282-108">Provided for future extensibility.</span></span> <span data-ttu-id="6b282-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT stanowi jedyną wartość, która obsługuje środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="6b282-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="6b282-110">[out] Bufor zawierający zestaw nieprzezroczyste danych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="6b282-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="6b282-111">[out w] Wskaźnik do rozmiaru `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="6b282-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b282-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b282-112">Return Value</span></span>  
  
|<span data-ttu-id="6b282-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b282-113">HRESULT</span></span>|<span data-ttu-id="6b282-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6b282-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b282-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b282-115">S_OK</span></span>|<span data-ttu-id="6b282-116">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6b282-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="6b282-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6b282-117">E_INVALIDARG</span></span>|<span data-ttu-id="6b282-118">Podane `pwzFilePath` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="6b282-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="6b282-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6b282-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="6b282-120">Rozmiar `pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="6b282-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="6b282-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b282-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b282-122">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b282-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b282-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b282-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b282-124">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b282-124">The call timed out.</span></span>|  
|<span data-ttu-id="6b282-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b282-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b282-126">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="6b282-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b282-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b282-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b282-128">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6b282-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b282-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b282-129">E_FAIL</span></span>|<span data-ttu-id="6b282-130">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6b282-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b282-131">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6b282-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b282-132">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6b282-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b282-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b282-133">Remarks</span></span>  
 <span data-ttu-id="6b282-134">`GetBindingIdentityFromFile` jest zazwyczaj wywoływana dwa razy.</span><span class="sxs-lookup"><span data-stu-id="6b282-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="6b282-135">Pierwsze wywołanie dostarcza wartość null dla `pwzBuffer`, a metoda zwraca odpowiedni rozmiar w `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="6b282-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="6b282-136">Drugie wywołanie dostarcza odpowiednio przydzielonego buforu, a metoda zwraca wartość z danymi rzeczywiste bufor po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="6b282-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b282-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b282-137">Requirements</span></span>  
 <span data-ttu-id="6b282-138">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b282-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b282-139">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b282-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b282-140">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b282-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b282-141">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b282-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b282-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b282-142">See also</span></span>

- [<span data-ttu-id="6b282-143">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b282-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="6b282-144">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b282-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="6b282-145">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b282-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
