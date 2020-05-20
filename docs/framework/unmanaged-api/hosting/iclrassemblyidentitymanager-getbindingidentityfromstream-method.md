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
ms.openlocfilehash: abba19600616cad8ba3377ae2ebb23459449d2a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615985"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="db106-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="db106-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="db106-103">Pobiera dane tożsamości zestawu kanonicznego dla zestawu w określonym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="db106-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db106-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db106-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db106-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db106-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="db106-106">podczas Strumień zestawu, który ma zostać obliczony.</span><span class="sxs-lookup"><span data-stu-id="db106-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="db106-107">podczas Udostępniane do przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="db106-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="db106-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest jedyną wartością, którą obsługuje bieżąca wersja środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="db106-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="db106-109">określoną Bufor zawierający dane tożsamości nieprzezroczystego zestawu.</span><span class="sxs-lookup"><span data-stu-id="db106-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="db106-110">[in. out] Rozmiar `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="db106-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db106-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="db106-111">Return Value</span></span>  
  
|<span data-ttu-id="db106-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db106-112">HRESULT</span></span>|<span data-ttu-id="db106-113">Opis</span><span class="sxs-lookup"><span data-stu-id="db106-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db106-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="db106-114">S_OK</span></span>|<span data-ttu-id="db106-115">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="db106-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="db106-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="db106-116">E_INVALIDARG</span></span>|<span data-ttu-id="db106-117">Podana `pStream` wartość jest równa null.</span><span class="sxs-lookup"><span data-stu-id="db106-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="db106-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="db106-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="db106-119">Rozmiar `pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="db106-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="db106-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db106-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db106-121">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="db106-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db106-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db106-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db106-123">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="db106-123">The call timed out.</span></span>|  
|<span data-ttu-id="db106-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db106-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db106-125">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="db106-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db106-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db106-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db106-127">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="db106-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db106-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db106-128">E_FAIL</span></span>|<span data-ttu-id="db106-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="db106-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db106-130">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="db106-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db106-131">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db106-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db106-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db106-132">Requirements</span></span>  
 <span data-ttu-id="db106-133">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db106-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db106-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="db106-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db106-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="db106-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db106-136">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db106-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db106-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db106-137">See also</span></span>

- [<span data-ttu-id="db106-138">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="db106-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="db106-139">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="db106-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
