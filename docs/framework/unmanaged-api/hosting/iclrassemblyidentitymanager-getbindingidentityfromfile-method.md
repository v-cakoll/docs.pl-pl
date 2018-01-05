---
title: "ICLRAssemblyIdentityManager::GetBindingIdentityFromFile — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5456d2747bb9c55d73fcc377036f5df1e8b10db0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="b2e0a-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2e0a-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="b2e0a-103">Pobiera tożsamość zestawu powiązania danych dla zestawu przy użyciu określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2e0a-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2e0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2e0a-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="b2e0a-106">[in] Ścieżka do pliku, który ma zostać obliczone.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b2e0a-107">[in] Wartość [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) wyliczenia wskazująca typ tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="b2e0a-108">Podany dla przyszłych rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-108">Provided for future extensibility.</span></span> <span data-ttu-id="b2e0a-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest to jedyna wartość, która obsługuje środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="b2e0a-110">[out] Bufor zawierający nieprzezroczyste zestawu danych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="b2e0a-111">[w, out] Wskaźnik do rozmiaru `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2e0a-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b2e0a-112">Return Value</span></span>  
  
|<span data-ttu-id="b2e0a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2e0a-113">HRESULT</span></span>|<span data-ttu-id="b2e0a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b2e0a-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2e0a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2e0a-115">S_OK</span></span>|<span data-ttu-id="b2e0a-116">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="b2e0a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b2e0a-117">E_INVALIDARG</span></span>|<span data-ttu-id="b2e0a-118">Podana `pwzFilePath` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="b2e0a-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b2e0a-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b2e0a-120">Rozmiar `pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="b2e0a-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2e0a-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2e0a-122">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2e0a-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2e0a-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2e0a-124">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-124">The call timed out.</span></span>|  
|<span data-ttu-id="b2e0a-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2e0a-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2e0a-126">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2e0a-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2e0a-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2e0a-128">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2e0a-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2e0a-129">E_FAIL</span></span>|<span data-ttu-id="b2e0a-130">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2e0a-131">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2e0a-132">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2e0a-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2e0a-133">Remarks</span></span>  
 <span data-ttu-id="b2e0a-134">`GetBindingIdentityFromFile`jest zazwyczaj wywoływana dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="b2e0a-135">Pierwsze wywołanie dostarcza wartość null dla `pwzBuffer`, a metoda zwraca odpowiedni rozmiar w `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="b2e0a-136">Drugie wywołanie dostarcza odpowiednio przydzielonego buforu, a metoda zwraca przy użyciu rzeczywistego buforu danych po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="b2e0a-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2e0a-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2e0a-137">Requirements</span></span>  
 <span data-ttu-id="b2e0a-138">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2e0a-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2e0a-139">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2e0a-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2e0a-140">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2e0a-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2e0a-141">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2e0a-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e0a-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2e0a-142">See Also</span></span>  
 [<span data-ttu-id="b2e0a-143">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2e0a-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="b2e0a-144">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2e0a-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="b2e0a-145">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2e0a-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
