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
ms.openlocfilehash: 57cf4e9f79be8e705869cf986a586fcfb3359584
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435342"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="34fb5-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="34fb5-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="34fb5-103">Pobiera canonical zestawu danych tożsamości dla zestawu w określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="34fb5-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34fb5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34fb5-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34fb5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34fb5-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="34fb5-106">[in] Strumień zestawu, który ma zostać obliczone.</span><span class="sxs-lookup"><span data-stu-id="34fb5-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="34fb5-107">[in] Podany dla przyszłych rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="34fb5-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="34fb5-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT jest tylko wartość, która obsługuje bieżącą wersję środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="34fb5-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="34fb5-109">[out] Bufor zawierający nieprzezroczyste zestawu danych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="34fb5-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="34fb5-110">[w, out] Rozmiar `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="34fb5-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34fb5-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="34fb5-111">Return Value</span></span>  
  
|<span data-ttu-id="34fb5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34fb5-112">HRESULT</span></span>|<span data-ttu-id="34fb5-113">Opis</span><span class="sxs-lookup"><span data-stu-id="34fb5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34fb5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="34fb5-114">S_OK</span></span>|<span data-ttu-id="34fb5-115">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="34fb5-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="34fb5-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="34fb5-116">E_INVALIDARG</span></span>|<span data-ttu-id="34fb5-117">Podana `pStream` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="34fb5-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="34fb5-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="34fb5-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="34fb5-119">Rozmiar `pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="34fb5-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="34fb5-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34fb5-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34fb5-121">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="34fb5-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34fb5-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34fb5-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34fb5-123">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="34fb5-123">The call timed out.</span></span>|  
|<span data-ttu-id="34fb5-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34fb5-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34fb5-125">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="34fb5-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34fb5-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34fb5-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34fb5-127">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="34fb5-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34fb5-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34fb5-128">E_FAIL</span></span>|<span data-ttu-id="34fb5-129">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="34fb5-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34fb5-130">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="34fb5-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34fb5-131">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34fb5-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34fb5-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34fb5-132">Requirements</span></span>  
 <span data-ttu-id="34fb5-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34fb5-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34fb5-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34fb5-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34fb5-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34fb5-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34fb5-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34fb5-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34fb5-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34fb5-137">See Also</span></span>  
 [<span data-ttu-id="34fb5-138">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="34fb5-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="34fb5-139">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="34fb5-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
