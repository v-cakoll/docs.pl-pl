---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: 1a1bc7609042422de876fe167a9e61655aaf62b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176412"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="6b87c-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b87c-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="6b87c-103">Wywołuje określoną metodę określonego typu w określonym zestawie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="6b87c-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b87c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b87c-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b87c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b87c-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="6b87c-106">[w] Ścieżka <xref:System.Reflection.Assembly> do, która definiuje, <xref:System.Type> którego metoda ma być wywoływana.</span><span class="sxs-lookup"><span data-stu-id="6b87c-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="6b87c-107">[w] <xref:System.Type> Nazwa, która definiuje metodę do wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b87c-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="6b87c-108">[w] Nazwa metody do wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b87c-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="6b87c-109">[w] Parametr string, aby przejść do metody.</span><span class="sxs-lookup"><span data-stu-id="6b87c-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="6b87c-110">[na zewnątrz] Wartość całkowita zwrócona przez metodę wywoływaną.</span><span class="sxs-lookup"><span data-stu-id="6b87c-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b87c-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b87c-111">Return Value</span></span>  
  
|<span data-ttu-id="6b87c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b87c-112">HRESULT</span></span>|<span data-ttu-id="6b87c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6b87c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b87c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b87c-114">S_OK</span></span>|<span data-ttu-id="6b87c-115">`ExecuteInDefaultAppDomain`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6b87c-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="6b87c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b87c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b87c-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6b87c-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b87c-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b87c-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b87c-119">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6b87c-119">The call timed out.</span></span>|  
|<span data-ttu-id="6b87c-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b87c-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b87c-121">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="6b87c-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b87c-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b87c-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b87c-123">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="6b87c-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b87c-124">E_fail</span><span class="sxs-lookup"><span data-stu-id="6b87c-124">E_FAIL</span></span>|<span data-ttu-id="6b87c-125">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="6b87c-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b87c-126">Jeśli metoda zwraca E_FAIL, crl nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6b87c-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="6b87c-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6b87c-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b87c-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b87c-128">Remarks</span></span>  
 <span data-ttu-id="6b87c-129">Wywoływana metoda musi mieć następujący podpis:</span><span class="sxs-lookup"><span data-stu-id="6b87c-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="6b87c-130">gdzie `pwzMethodName` reprezentuje nazwę wywoływanej metody `pwzArgument` i reprezentuje wartość ciągu przekazane jako parametr do tej metody.</span><span class="sxs-lookup"><span data-stu-id="6b87c-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="6b87c-131">Jeśli wartość HRESULT jest ustawiona na `pReturnValue` S_OK, jest ustawiona na wartość całkowitą zwracaną przez wywoływaną metodę.</span><span class="sxs-lookup"><span data-stu-id="6b87c-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="6b87c-132">W `pReturnValue` przeciwnym razie nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="6b87c-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b87c-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b87c-133">Requirements</span></span>  
 <span data-ttu-id="6b87c-134">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b87c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b87c-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b87c-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b87c-136">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b87c-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b87c-137">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b87c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b87c-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b87c-138">See also</span></span>

- [<span data-ttu-id="6b87c-139">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b87c-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
