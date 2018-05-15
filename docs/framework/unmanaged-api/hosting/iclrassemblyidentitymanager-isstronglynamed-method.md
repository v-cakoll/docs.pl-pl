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
ms.openlocfilehash: 735ff725bc06c14da9821055a6a143f857548c30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="757a1-102">ICLRAssemblyIdentityManager::IsStronglyNamed — Metoda</span><span class="sxs-lookup"><span data-stu-id="757a1-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="757a1-103">Pobiera wartość wskazującą, czy określony zestaw ma silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="757a1-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="757a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="757a1-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="757a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="757a1-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="757a1-106">[in] Nieprzezroczyste canonical zestawu danych tożsamości zestawu do oceny.</span><span class="sxs-lookup"><span data-stu-id="757a1-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="757a1-107">[out] `true`, jeśli odwołuje się zestaw `pwzAssemblyIdentity` parametr jest silnie nazwanego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="757a1-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="757a1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="757a1-108">Return Value</span></span>  
  
|<span data-ttu-id="757a1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="757a1-109">HRESULT</span></span>|<span data-ttu-id="757a1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="757a1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="757a1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="757a1-111">S_OK</span></span>|<span data-ttu-id="757a1-112">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="757a1-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="757a1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="757a1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="757a1-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="757a1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="757a1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="757a1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="757a1-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="757a1-116">The call timed out.</span></span>|  
|<span data-ttu-id="757a1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="757a1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="757a1-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="757a1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="757a1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="757a1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="757a1-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="757a1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="757a1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="757a1-121">E_FAIL</span></span>|<span data-ttu-id="757a1-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="757a1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="757a1-123">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="757a1-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="757a1-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="757a1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="757a1-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="757a1-125">Requirements</span></span>  
 <span data-ttu-id="757a1-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="757a1-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="757a1-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="757a1-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="757a1-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="757a1-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="757a1-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="757a1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="757a1-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="757a1-130">See Also</span></span>  
 [<span data-ttu-id="757a1-131">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="757a1-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
