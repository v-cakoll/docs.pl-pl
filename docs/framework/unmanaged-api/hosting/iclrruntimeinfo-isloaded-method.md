---
title: ICLRRuntimeInfo::IsLoaded — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ff1723cb481ee946e0c5c433009d3d6d7460cf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="56ad4-102">ICLRRuntimeInfo::IsLoaded — Metoda</span><span class="sxs-lookup"><span data-stu-id="56ad4-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="56ad4-103">Wskazuje, czy środowisko uruchomieniowe języka wspólnego (CLR) skojarzone z [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu jest załadowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="56ad4-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="56ad4-104">Środowisko uruchomieniowe może zostać załadowany bez również uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="56ad4-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ad4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="56ad4-105">Syntax</span></span>  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56ad4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="56ad4-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="56ad4-107">[in] Dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="56ad4-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="56ad4-108">[out] `true` Jeśli CLR jest załadowany do procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="56ad4-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56ad4-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="56ad4-109">Return Value</span></span>  
 <span data-ttu-id="56ad4-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="56ad4-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="56ad4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56ad4-111">HRESULT</span></span>|<span data-ttu-id="56ad4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="56ad4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56ad4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="56ad4-113">S_OK</span></span>|<span data-ttu-id="56ad4-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="56ad4-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="56ad4-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="56ad4-115">E_POINTER</span></span>|<span data-ttu-id="56ad4-116">`pbLoaded` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="56ad4-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56ad4-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56ad4-117">Remarks</span></span>  
 <span data-ttu-id="56ad4-118">Ta metoda jest zgodny z następujące funkcje i interfejsy:</span><span class="sxs-lookup"><span data-stu-id="56ad4-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
-   <span data-ttu-id="56ad4-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interfejsu (w programie .NET Framework w wersji 1 hostingu interfejsu API).</span><span class="sxs-lookup"><span data-stu-id="56ad4-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
-   <span data-ttu-id="56ad4-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu (w .NET Framework 2.0 hosting interfejsu API).</span><span class="sxs-lookup"><span data-stu-id="56ad4-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
-   <span data-ttu-id="56ad4-121">Przestarzały `CorBindTo*` funkcje (zobacz [przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) w hosting interfejsu API programu .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="56ad4-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="56ad4-122">Host może wywoływanie jednego z przestarzałe `CorBindTo*` funkcji, takich jak [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) funkcji, można utworzyć wystąpienia określonej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="56ad4-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="56ad4-123">Host może wywoływać [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) — metoda i określ numer wersji tego samego uzyskanie [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="56ad4-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="56ad4-124">Jeśli host następnie wywołuje `IsLoaded` metody w zwróconym [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu `pbLoaded` zwraca `true`; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="56ad4-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56ad4-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56ad4-125">Requirements</span></span>  
 <span data-ttu-id="56ad4-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56ad4-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56ad4-127">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="56ad4-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="56ad4-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56ad4-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56ad4-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56ad4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ad4-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56ad4-130">See Also</span></span>  
 [<span data-ttu-id="56ad4-131">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="56ad4-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="56ad4-132">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="56ad4-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="56ad4-133">Hosting</span><span class="sxs-lookup"><span data-stu-id="56ad4-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
