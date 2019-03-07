---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6590b455717dfdb3ea43e3622b494e2169047337
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469616"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="8c5b0-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c5b0-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="8c5b0-103">Pobiera dane tożsamości canonical zestawu dla zestawu w określonej usłudze stream.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c5b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c5b0-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c5b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c5b0-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="8c5b0-106">[in] Strumień zestawu, który ma zostać obliczone.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8c5b0-107">[in] Podana dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="8c5b0-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT stanowi jedyną wartość, która obsługuje bieżącą wersję środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="8c5b0-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="8c5b0-109">[out] Bufor zawierający zestaw nieprzezroczyste danych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="8c5b0-110">[out w] Rozmiar `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c5b0-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8c5b0-111">Return Value</span></span>  
  
|<span data-ttu-id="8c5b0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c5b0-112">HRESULT</span></span>|<span data-ttu-id="8c5b0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8c5b0-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c5b0-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c5b0-114">S_OK</span></span>|<span data-ttu-id="8c5b0-115">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="8c5b0-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8c5b0-116">E_INVALIDARG</span></span>|<span data-ttu-id="8c5b0-117">Podane `pStream` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="8c5b0-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8c5b0-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8c5b0-119">Rozmiar `pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="8c5b0-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c5b0-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c5b0-121">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c5b0-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c5b0-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c5b0-123">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-123">The call timed out.</span></span>|  
|<span data-ttu-id="8c5b0-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c5b0-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c5b0-125">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c5b0-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c5b0-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c5b0-127">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c5b0-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c5b0-128">E_FAIL</span></span>|<span data-ttu-id="8c5b0-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c5b0-130">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c5b0-131">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8c5b0-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c5b0-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c5b0-132">Requirements</span></span>  
 <span data-ttu-id="8c5b0-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c5b0-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c5b0-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c5b0-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c5b0-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c5b0-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c5b0-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c5b0-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c5b0-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c5b0-137">See also</span></span>
- [<span data-ttu-id="8c5b0-138">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c5b0-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8c5b0-139">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c5b0-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
