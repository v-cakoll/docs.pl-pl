---
title: ICLRMetaHost::GetRuntime — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 273891b0814d9383d9640c79f5df959f2b9398b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707911"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="1256f-102">ICLRMetaHost::GetRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="1256f-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="1256f-103">Pobiera [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który odnosi się do określonej wersji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="1256f-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="1256f-104">Ta metoda zastępuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcja używana z [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flagi.</span><span class="sxs-lookup"><span data-stu-id="1256f-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1256f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1256f-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1256f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1256f-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="1256f-107">[in] Wersja kompilacji programu .NET Framework, które są przechowywane w metadanych, w formacie "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="1256f-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="1256f-108">*A*, *B*, i *X* są liczby dziesiętne, które odpowiadają wersji głównej, pomocniczej wersji i numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1256f-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1256f-109">Ten parametr musi odpowiadać nazwie katalogu dla .NET Framework w wersji, wyświetlaną w obszarze C:\Windows\Microsoft.NET\Framework lub C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="1256f-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="1256f-110">Przykładowe wartości są "wartości v1.0.3705", "v1.1.4322" i "v2.0.50727" oraz "v4.0. *X*", gdzie *X* zależy od numeru kompilacji zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="1256f-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="1256f-111">Prefiks "v" jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="1256f-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="1256f-112">[in] Identyfikator dla żądanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1256f-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="1256f-113">Obecnie jedyną prawidłową wartością tego parametru jest IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="1256f-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="1256f-114">[out] Wskaźnik do [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który odnosi się do żądanego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1256f-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1256f-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1256f-115">Return Value</span></span>  
 <span data-ttu-id="1256f-116">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="1256f-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1256f-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1256f-117">HRESULT</span></span>|<span data-ttu-id="1256f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="1256f-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1256f-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="1256f-119">S_OK</span></span>|<span data-ttu-id="1256f-120">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1256f-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="1256f-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1256f-121">E_POINTER</span></span>|<span data-ttu-id="1256f-122">`pwzVersion` lub `ppRuntime` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="1256f-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1256f-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1256f-123">Remarks</span></span>  
 <span data-ttu-id="1256f-124">Ta metoda użyje spójne interfejsy starszej wersji takich jak [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) funkcji interfejsu i starszej wersji, takich jak przestarzałego `CorBindTo*` funkcji (zobacz [przestarzałe CLR funkcje hostingu](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) w programie .NET Framework 2.0, hostowanie interfejsu API).</span><span class="sxs-lookup"><span data-stu-id="1256f-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="1256f-125">Oznacza to środowisk wykonawczych, które są ładowane przy użyciu starszej wersji interfejsu API są widoczne dla nowego interfejsu API i środowisk wykonawczych, które są ładowane przy użyciu nowego interfejsu API są widoczne dla starszej wersji interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="1256f-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span> <span data-ttu-id="1256f-126">.</span><span class="sxs-lookup"><span data-stu-id="1256f-126">.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1256f-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1256f-127">Requirements</span></span>  
 <span data-ttu-id="1256f-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1256f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1256f-129">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1256f-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1256f-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1256f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1256f-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1256f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1256f-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1256f-132">See also</span></span>
- [<span data-ttu-id="1256f-133">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="1256f-133">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="1256f-134">Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="1256f-134">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="1256f-135">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="1256f-135">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="1256f-136">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="1256f-136">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="1256f-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="1256f-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
