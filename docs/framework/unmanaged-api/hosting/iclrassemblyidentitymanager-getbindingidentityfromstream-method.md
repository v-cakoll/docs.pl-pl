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
ms.openlocfilehash: 6dc4e3adf5adec1aa4626a31b6a9391e2a04f1ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098593"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="28687-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="28687-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="28687-103">Pobiera dane tożsamości canonical zestawu dla zestawu w określonej usłudze stream.</span><span class="sxs-lookup"><span data-stu-id="28687-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28687-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28687-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28687-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28687-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="28687-106">[in] Strumień zestawu, który ma zostać obliczone.</span><span class="sxs-lookup"><span data-stu-id="28687-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="28687-107">[in] Podana dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="28687-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="28687-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT stanowi jedyną wartość, która obsługuje bieżącą wersję środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="28687-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="28687-109">[out] Bufor zawierający zestaw nieprzezroczyste danych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="28687-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="28687-110">[out w] Rozmiar `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="28687-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28687-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="28687-111">Return Value</span></span>  
  
|<span data-ttu-id="28687-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28687-112">HRESULT</span></span>|<span data-ttu-id="28687-113">Opis</span><span class="sxs-lookup"><span data-stu-id="28687-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28687-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="28687-114">S_OK</span></span>|<span data-ttu-id="28687-115">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="28687-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="28687-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="28687-116">E_INVALIDARG</span></span>|<span data-ttu-id="28687-117">Podane `pStream` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="28687-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="28687-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="28687-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="28687-119">Rozmiar `pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="28687-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="28687-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28687-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28687-121">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="28687-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28687-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28687-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28687-123">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="28687-123">The call timed out.</span></span>|  
|<span data-ttu-id="28687-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28687-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28687-125">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="28687-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28687-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28687-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28687-127">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="28687-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28687-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28687-128">E_FAIL</span></span>|<span data-ttu-id="28687-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="28687-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28687-130">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="28687-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28687-131">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="28687-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28687-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28687-132">Requirements</span></span>  
 <span data-ttu-id="28687-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28687-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28687-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28687-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28687-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28687-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="28687-136">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="28687-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="28687-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28687-137">See also</span></span>

- [<span data-ttu-id="28687-138">ICLRAssemblyIdentityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="28687-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="28687-139">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="28687-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
