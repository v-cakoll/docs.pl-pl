---
title: "ICLRRuntimeInfo::IsLoaded — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsLoaded
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac7ed77dd4cb141257a1b73ccd433c7d17ee1f38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="26a6a-102">ICLRRuntimeInfo::IsLoaded — Metoda</span><span class="sxs-lookup"><span data-stu-id="26a6a-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="26a6a-103">Wskazuje, czy środowisko uruchomieniowe języka wspólnego (CLR) skojarzone z [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu jest załadowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="26a6a-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="26a6a-104">Środowisko uruchomieniowe może zostać załadowany bez również uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="26a6a-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26a6a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="26a6a-105">Syntax</span></span>  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26a6a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="26a6a-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="26a6a-107">[in] Dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="26a6a-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="26a6a-108">[out] `true` Jeśli CLR jest załadowany do procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="26a6a-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26a6a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="26a6a-109">Return Value</span></span>  
 <span data-ttu-id="26a6a-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="26a6a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="26a6a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26a6a-111">HRESULT</span></span>|<span data-ttu-id="26a6a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="26a6a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26a6a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="26a6a-113">S_OK</span></span>|<span data-ttu-id="26a6a-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="26a6a-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="26a6a-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="26a6a-115">E_POINTER</span></span>|<span data-ttu-id="26a6a-116">`pbLoaded`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="26a6a-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26a6a-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26a6a-117">Remarks</span></span>  
 <span data-ttu-id="26a6a-118">Ta metoda jest zgodny z następujące funkcje i interfejsy:</span><span class="sxs-lookup"><span data-stu-id="26a6a-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
-   <span data-ttu-id="26a6a-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interfejsu (w programie .NET Framework w wersji 1 hostingu interfejsu API).</span><span class="sxs-lookup"><span data-stu-id="26a6a-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
-   <span data-ttu-id="26a6a-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu (w .NET Framework 2.0 hosting interfejsu API).</span><span class="sxs-lookup"><span data-stu-id="26a6a-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
-   <span data-ttu-id="26a6a-121">Przestarzały `CorBindTo*` funkcje (zobacz [przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) w hosting interfejsu API programu .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="26a6a-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="26a6a-122">Host może wywoływanie jednego z przestarzałe `CorBindTo*` funkcji, takich jak [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) funkcji, można utworzyć wystąpienia określonej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="26a6a-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="26a6a-123">Host może wywoływać [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) — metoda i określ numer wersji tego samego uzyskanie [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="26a6a-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="26a6a-124">Jeśli host następnie wywołuje `IsLoaded` metody w zwróconym [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu `pbLoaded` zwraca `true`; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="26a6a-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26a6a-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26a6a-125">Requirements</span></span>  
 <span data-ttu-id="26a6a-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26a6a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26a6a-127">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="26a6a-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="26a6a-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26a6a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26a6a-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26a6a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a6a-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26a6a-130">See Also</span></span>  
 [<span data-ttu-id="26a6a-131">ICLRRuntimeInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="26a6a-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="26a6a-132">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="26a6a-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="26a6a-133">Hosting</span><span class="sxs-lookup"><span data-stu-id="26a6a-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
