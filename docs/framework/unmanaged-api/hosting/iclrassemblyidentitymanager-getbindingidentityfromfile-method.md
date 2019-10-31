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
ms.openlocfilehash: 19d6a76d62680be91a7b9721912ca528edde7511
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126752"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="f706c-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="f706c-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="f706c-103">Pobiera dane powiązania tożsamości zestawu z określoną ścieżką do pliku.</span><span class="sxs-lookup"><span data-stu-id="f706c-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f706c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f706c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f706c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f706c-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="f706c-106">podczas Ścieżka do pliku do oceny.</span><span class="sxs-lookup"><span data-stu-id="f706c-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f706c-107">podczas Wartość wyliczenia [ECLRAssemblyIdentityFlags —](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) , która wskazuje typ tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="f706c-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="f706c-108">Udostępniane do przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="f706c-108">Provided for future extensibility.</span></span> <span data-ttu-id="f706c-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest jedyną wartością obsługiwaną przez środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="f706c-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="f706c-110">określoną Bufor zawierający dane tożsamości nieprzezroczystego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f706c-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="f706c-111">[in. out] Wskaźnik do rozmiaru `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="f706c-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f706c-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f706c-112">Return Value</span></span>  
  
|<span data-ttu-id="f706c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f706c-113">HRESULT</span></span>|<span data-ttu-id="f706c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f706c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f706c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f706c-115">S_OK</span></span>|<span data-ttu-id="f706c-116">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="f706c-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="f706c-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f706c-117">E_INVALIDARG</span></span>|<span data-ttu-id="f706c-118">Podany `pwzFilePath` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="f706c-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="f706c-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f706c-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f706c-120">Rozmiar `pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="f706c-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="f706c-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f706c-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f706c-122">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f706c-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f706c-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f706c-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f706c-124">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="f706c-124">The call timed out.</span></span>|  
|<span data-ttu-id="f706c-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f706c-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f706c-126">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f706c-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f706c-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f706c-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f706c-128">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="f706c-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f706c-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f706c-129">E_FAIL</span></span>|<span data-ttu-id="f706c-130">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f706c-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f706c-131">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="f706c-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f706c-132">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f706c-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f706c-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f706c-133">Remarks</span></span>  
 <span data-ttu-id="f706c-134">`GetBindingIdentityFromFile` jest zazwyczaj wywoływana dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="f706c-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="f706c-135">Pierwsze wywołanie dostarcza wartość null dla `pwzBuffer`, a metoda zwraca odpowiedni rozmiar w `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="f706c-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="f706c-136">Drugie wywołanie dostarcza odpowiednio przydzielony bufor, a metoda zwraca z rzeczywistymi danymi buforu po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="f706c-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f706c-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f706c-137">Requirements</span></span>  
 <span data-ttu-id="f706c-138">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f706c-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f706c-139">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f706c-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f706c-140">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f706c-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f706c-141">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f706c-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f706c-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f706c-142">See also</span></span>

- [<span data-ttu-id="f706c-143">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f706c-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="f706c-144">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="f706c-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f706c-145">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f706c-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
