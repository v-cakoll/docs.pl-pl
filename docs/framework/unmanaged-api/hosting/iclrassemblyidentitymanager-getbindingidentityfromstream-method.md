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
ms.openlocfilehash: b30f6f5ce22290dc3750cef0171349ec5ff2f76a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126738"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="60543-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="60543-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="60543-103">Pobiera dane tożsamości zestawu kanonicznego dla zestawu w określonym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="60543-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60543-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60543-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60543-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60543-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="60543-106">podczas Strumień zestawu, który ma zostać obliczony.</span><span class="sxs-lookup"><span data-stu-id="60543-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="60543-107">podczas Udostępniane do przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="60543-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="60543-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest jedyną wartością, którą obsługuje bieżąca wersja środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="60543-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="60543-109">określoną Bufor zawierający dane tożsamości nieprzezroczystego zestawu.</span><span class="sxs-lookup"><span data-stu-id="60543-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="60543-110">[in. out] Rozmiar `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="60543-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60543-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="60543-111">Return Value</span></span>  
  
|<span data-ttu-id="60543-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60543-112">HRESULT</span></span>|<span data-ttu-id="60543-113">Opis</span><span class="sxs-lookup"><span data-stu-id="60543-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60543-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="60543-114">S_OK</span></span>|<span data-ttu-id="60543-115">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="60543-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="60543-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="60543-116">E_INVALIDARG</span></span>|<span data-ttu-id="60543-117">Podany `pStream` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="60543-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="60543-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="60543-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="60543-119">Rozmiar `pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="60543-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="60543-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="60543-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="60543-121">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="60543-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="60543-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="60543-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="60543-123">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="60543-123">The call timed out.</span></span>|  
|<span data-ttu-id="60543-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="60543-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="60543-125">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="60543-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="60543-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="60543-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="60543-127">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="60543-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="60543-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60543-128">E_FAIL</span></span>|<span data-ttu-id="60543-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="60543-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="60543-130">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="60543-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="60543-131">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="60543-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60543-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60543-132">Requirements</span></span>  
 <span data-ttu-id="60543-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60543-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60543-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="60543-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60543-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="60543-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60543-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60543-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60543-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60543-137">See also</span></span>

- [<span data-ttu-id="60543-138">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="60543-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="60543-139">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="60543-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
