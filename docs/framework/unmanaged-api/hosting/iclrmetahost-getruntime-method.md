---
title: "ICLRMetaHost::GetRuntime — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.GetRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type: apiref
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6ebfa1af4b824f4fcd4247cd7d0a667488f3e3ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="15882-102">ICLRMetaHost::GetRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="15882-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="15882-103">Pobiera [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który odpowiada w przypadku konkretnej wersji środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="15882-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="15882-104">Ta metoda zastępuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcja używana z [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flagi.</span><span class="sxs-lookup"><span data-stu-id="15882-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15882-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="15882-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15882-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="15882-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="15882-107">[in] .NET Framework w wersji kompilacji przechowywane w metadanych, w formacie "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="15882-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="15882-108">*A*, *B*, i *X* są liczbami dziesiętnymi, które odpowiadają wersji głównej, wersja pomocnicza i numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="15882-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15882-109">Ten parametr musi być zgodna nazwę katalogu .NET Framework w wersji, pojawiającą się w ramach C:\Windows\Microsoft.NET\Framework lub C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="15882-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="15882-110">Przykładowe wartości to "v1.0.3705", "v1.1.4322", "v2.0.50727" i "v4.0. *X*", gdzie *X* zależy od numeru kompilacji zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="15882-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="15882-111">Prefiks "v" jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="15882-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="15882-112">[in] Identyfikator dla żądanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="15882-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="15882-113">Obecnie jedyną poprawną wartością dla tego parametru jest IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="15882-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="15882-114">[out] Wskaźnik do [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który odpowiada na wymagane środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="15882-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15882-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="15882-115">Return Value</span></span>  
 <span data-ttu-id="15882-116">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="15882-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="15882-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15882-117">HRESULT</span></span>|<span data-ttu-id="15882-118">Opis</span><span class="sxs-lookup"><span data-stu-id="15882-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15882-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="15882-119">S_OK</span></span>|<span data-ttu-id="15882-120">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="15882-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="15882-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="15882-121">E_POINTER</span></span>|<span data-ttu-id="15882-122">`pwzVersion`lub `ppRuntime` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="15882-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15882-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15882-123">Remarks</span></span>  
 <span data-ttu-id="15882-124">Ta metoda użyje spójnie interfejsy starszej wersji takie jak [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interfejsu i starsze funkcje takie jak przestarzałe `CorBindTo*` funkcje (zobacz [przestarzałe CLR funkcje hostingu](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) w hosting interfejsu API programu .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="15882-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="15882-125">Oznacza to środowiska uruchomieniowe, które są ładowane przy użyciu starszej wersji interfejsu API są widoczne dla nowego interfejsu API i środowisk uruchomieniowych, które są ładowane z nowym interfejsem API są widoczne dla starszej wersji interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="15882-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span> <span data-ttu-id="15882-126">.</span><span class="sxs-lookup"><span data-stu-id="15882-126">.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15882-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15882-127">Requirements</span></span>  
 <span data-ttu-id="15882-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15882-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15882-129">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="15882-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="15882-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="15882-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15882-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15882-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15882-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15882-132">See Also</span></span>  
 [<span data-ttu-id="15882-133">ICLRMetaHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="15882-133">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="15882-134">Przestarzałe hostingu interfejsy i współklasy środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="15882-134">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 [<span data-ttu-id="15882-135">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="15882-135">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="15882-136">Przestarzałe funkcje hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="15882-136">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="15882-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="15882-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
