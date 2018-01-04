---
title: "ICLRRuntimeHost::ExecuteInDefaultAppDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec4cf37150cab7b52066a884b6fe117b0e611106
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="40773-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="40773-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="40773-103">Wywołuje metodę określonej określonego typu w określonym zestawie zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="40773-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40773-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40773-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40773-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40773-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="40773-106">[in] Ścieżka do <xref:System.Reflection.Assembly> definiuje <xref:System.Type> metody, której ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="40773-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="40773-107">[in] Nazwa <xref:System.Type> definiuje metody do wywołania.</span><span class="sxs-lookup"><span data-stu-id="40773-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="40773-108">[in] Nazwa metody do wywołania.</span><span class="sxs-lookup"><span data-stu-id="40773-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="40773-109">[in] Parametr ciągu do przekazania do metody.</span><span class="sxs-lookup"><span data-stu-id="40773-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="40773-110">[out] Wartość całkowita zwracany przez metodę wywołana.</span><span class="sxs-lookup"><span data-stu-id="40773-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40773-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="40773-111">Return Value</span></span>  
  
|<span data-ttu-id="40773-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40773-112">HRESULT</span></span>|<span data-ttu-id="40773-113">Opis</span><span class="sxs-lookup"><span data-stu-id="40773-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40773-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="40773-114">S_OK</span></span>|<span data-ttu-id="40773-115">`ExecuteInDefaultAppDomain`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="40773-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="40773-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="40773-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="40773-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="40773-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="40773-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="40773-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="40773-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="40773-119">The call timed out.</span></span>|  
|<span data-ttu-id="40773-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="40773-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="40773-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="40773-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="40773-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="40773-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="40773-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="40773-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="40773-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="40773-124">E_FAIL</span></span>|<span data-ttu-id="40773-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="40773-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="40773-126">Jeśli metoda zwraca E_FAIL, listy CRL nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="40773-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="40773-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="40773-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40773-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40773-128">Remarks</span></span>  
 <span data-ttu-id="40773-129">Wywołana metoda musi mieć następującą sygnaturą:</span><span class="sxs-lookup"><span data-stu-id="40773-129">The invoked method must have the following signature:</span></span>  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="40773-130">gdzie `pwzMethodName` reprezentuje nazwę wywoływanej metody i `pwzArgument` reprezentuje wartość ciągu przekazany jako parametr tej metody.</span><span class="sxs-lookup"><span data-stu-id="40773-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="40773-131">Jeśli wartość HRESULT jest ustawiona na wartość S_OK, `pReturnValue` ma ustawioną wartość całkowita zwracany przez metodę wywołana.</span><span class="sxs-lookup"><span data-stu-id="40773-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="40773-132">W przeciwnym razie `pReturnValue` nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="40773-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40773-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40773-133">Requirements</span></span>  
 <span data-ttu-id="40773-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40773-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40773-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40773-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40773-136">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40773-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40773-137">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40773-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40773-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40773-138">See Also</span></span>  
 [<span data-ttu-id="40773-139">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="40773-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
