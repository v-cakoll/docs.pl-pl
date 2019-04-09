---
title: ICLRAssemblyIdentityManager::IsStronglyNamed — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.IsStronglyNamed
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 166583f690fc7ed80f80cf2cf5cd5b0348708cc3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159721"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="97d3c-102">ICLRAssemblyIdentityManager::IsStronglyNamed — Metoda</span><span class="sxs-lookup"><span data-stu-id="97d3c-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="97d3c-103">Pobiera wartość wskazującą, czy określony zestaw ma silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="97d3c-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d3c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97d3c-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97d3c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97d3c-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="97d3c-106">[in] Nieprzezroczysty canonical zestawu danych tożsamości zestawu, który ma zostać obliczone.</span><span class="sxs-lookup"><span data-stu-id="97d3c-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="97d3c-107">[out] `true`, jeśli odwołuje się zestaw `pwzAssemblyIdentity` parametr jest silnie nazwane; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="97d3c-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97d3c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="97d3c-108">Return Value</span></span>  
  
|<span data-ttu-id="97d3c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97d3c-109">HRESULT</span></span>|<span data-ttu-id="97d3c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="97d3c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97d3c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="97d3c-111">S_OK</span></span>|<span data-ttu-id="97d3c-112">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="97d3c-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="97d3c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97d3c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97d3c-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="97d3c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="97d3c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97d3c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97d3c-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="97d3c-116">The call timed out.</span></span>|  
|<span data-ttu-id="97d3c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97d3c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97d3c-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="97d3c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97d3c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97d3c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97d3c-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="97d3c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97d3c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97d3c-121">E_FAIL</span></span>|<span data-ttu-id="97d3c-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="97d3c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97d3c-123">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="97d3c-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97d3c-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="97d3c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97d3c-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97d3c-125">Requirements</span></span>  
 <span data-ttu-id="97d3c-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97d3c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d3c-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97d3c-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97d3c-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97d3c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="97d3c-129">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="97d3c-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="97d3c-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97d3c-130">See also</span></span>

- [<span data-ttu-id="97d3c-131">ICLRAssemblyIdentityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="97d3c-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
