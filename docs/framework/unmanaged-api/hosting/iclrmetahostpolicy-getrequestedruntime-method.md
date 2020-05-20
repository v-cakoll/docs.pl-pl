---
title: ICLRMetaHostPolicy::GetRequestedRuntime — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy.GetRequestedRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type:
- apiref
ms.openlocfilehash: 52da5ec7ccd6ce48871e13a94f5957fa00d2a613
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703549"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a><span data-ttu-id="32f6c-102">ICLRMetaHostPolicy::GetRequestedRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="32f6c-102">ICLRMetaHostPolicy::GetRequestedRuntime Method</span></span>

<span data-ttu-id="32f6c-103">Udostępnia interfejs preferowanej wersji środowiska uruchomieniowego języka wspólnego (CLR) na podstawie zasad hostingu, zestawu zarządzanego, ciągu wersji i strumienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="32f6c-103">Provides an interface to a preferred version of the common language runtime (CLR) based on a hosting policy, managed assembly, version string, and configuration stream.</span></span> <span data-ttu-id="32f6c-104">Ta metoda nie ładuje ani nie aktywuje środowiska CLR, ale po prostu zwraca interfejs [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , który reprezentuje wynik zasad.</span><span class="sxs-lookup"><span data-stu-id="32f6c-104">This method does not actually load or activate the CLR, but simply returns the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents the policy result.</span></span> <span data-ttu-id="32f6c-105">Ta metoda zastępuje metody [GetRequestedRuntimeInfo —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)i [GetCORRequiredVersion —](getcorrequiredversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="32f6c-105">This method supersedes the [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), and [GetCORRequiredVersion](getcorrequiredversion-function.md) methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="32f6c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="32f6c-106">Syntax</span></span>

```cpp
HRESULT GetRequestedRuntime(
    [in]  METAHOST_POLICY_FLAGS dwPolicyFlags,
    [in]  LPCWSTR pwzBinary,
    [in]  IStream *pCfgStream,
    [in, out, size_is(*pcchVersion)] LPWSTR pwzVersion,
    [in, out]  DWORD *pcchVersion,
    [out, size_is(*pcchImageVersion)] LPWSTR pwzImageVersion,
    [in, out]  DWORD *pcchImageVersion,
    [out] DWORD *pdwConfigFlags,
    [in]  REFIID  riid
    [out, iid_is(riid), retval] LPVOID *ppRuntime);
```

## <a name="parameters"></a><span data-ttu-id="32f6c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="32f6c-107">Parameters</span></span>

|<span data-ttu-id="32f6c-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="32f6c-108">Name</span></span>|<span data-ttu-id="32f6c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="32f6c-109">Description</span></span>|
|----------|-----------------|
|`dwPolicyFlags`|<span data-ttu-id="32f6c-110">podczas Wymagane.</span><span class="sxs-lookup"><span data-stu-id="32f6c-110">[in] Required.</span></span> <span data-ttu-id="32f6c-111">Określa element członkowski wyliczenia [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) , reprezentujący zasady powiązań i dowolną liczbę modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="32f6c-111">Specifies a member of the [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration, representing a binding policy, and any number of modifiers.</span></span> <span data-ttu-id="32f6c-112">Jedyne obecnie dostępne zasady są [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="32f6c-112">The only policy that is currently available is [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span></span><br /><br /> <span data-ttu-id="32f6c-113">Modyfikatory obejmują [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)i [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="32f6c-113">Modifiers include [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md), and [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span></span>|
|`pwzBinary`|<span data-ttu-id="32f6c-114">podczas Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="32f6c-114">[in] Optional.</span></span> <span data-ttu-id="32f6c-115">Określa ścieżkę pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="32f6c-115">Specifies the assembly file path.</span></span>|
|`pCfgStream`|<span data-ttu-id="32f6c-116">podczas Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="32f6c-116">[in] Optional.</span></span> <span data-ttu-id="32f6c-117">Określa plik konfiguracji jako <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="32f6c-117">Specifies the configuration file as a <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span></span>|
|`pwzVersion`|<span data-ttu-id="32f6c-118">[in. out] Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="32f6c-118">[in, out] Optional.</span></span> <span data-ttu-id="32f6c-119">Określa lub zwraca preferowaną wersję środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="32f6c-119">Specifies or returns the preferred CLR version to be loaded.</span></span>|
|`pcchVersion`|<span data-ttu-id="32f6c-120">[in. out] Wymagane.</span><span class="sxs-lookup"><span data-stu-id="32f6c-120">[in, out] Required.</span></span> <span data-ttu-id="32f6c-121">Określa oczekiwany rozmiar `pwzVersion` jako dane wejściowe, aby uniknąć przekroczeń buforu.</span><span class="sxs-lookup"><span data-stu-id="32f6c-121">Specifies the expected size of `pwzVersion` as input, to avoid buffer overruns.</span></span> <span data-ttu-id="32f6c-122">Jeśli `pwzVersion` ma wartość null, `pcchVersion` zawiera oczekiwany rozmiar `pwzVersion` `GetRequestedRuntime` zwracanego elementu, aby zezwolić na wstępne alokację; w przeciwnym razie `pcchVersion` zawiera liczbę znaków, do których zapisano `pwzVersion` .</span><span class="sxs-lookup"><span data-stu-id="32f6c-122">If `pwzVersion` is null, `pcchVersion` contains the expected size of `pwzVersion` when `GetRequestedRuntime` returns, to allow pre-allocation; otherwise, `pcchVersion` contains the number of characters written to `pwzVersion`.</span></span>|
|`pwzImageVersion`|<span data-ttu-id="32f6c-123">określoną Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="32f6c-123">[out] Optional.</span></span> <span data-ttu-id="32f6c-124">Gdy `GetRequestedRuntime` zwraca, zawiera wersję środowiska CLR odpowiadającą zwróconemu interfejsowi [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="32f6c-124">When `GetRequestedRuntime` returns, contains the CLR version corresponding to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that is returned.</span></span>|
|`pcchImageVersion`|<span data-ttu-id="32f6c-125">[in. out] Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="32f6c-125">[in, out] Optional.</span></span> <span data-ttu-id="32f6c-126">Określa rozmiar `pwzImageVersion` jako dane wejściowe, aby uniknąć przekroczenia buforu.</span><span class="sxs-lookup"><span data-stu-id="32f6c-126">Specifies the size of `pwzImageVersion` as input to avoid buffer overruns.</span></span> <span data-ttu-id="32f6c-127">Jeśli `pwzImageVersion` ma wartość null, `pcchImageVersion` zawiera wymagany rozmiar `pwzImageVersion` , gdy `GetRequestedRuntime` zwraca, aby umożliwić wstępne przydzielanie.</span><span class="sxs-lookup"><span data-stu-id="32f6c-127">If `pwzImageVersion` is null, `pcchImageVersion` contains the required size of `pwzImageVersion` when `GetRequestedRuntime` returns, to allow pre-allocation.</span></span>|
|`pdwConfigFlags`|<span data-ttu-id="32f6c-128">określoną Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="32f6c-128">[out] Optional.</span></span> <span data-ttu-id="32f6c-129">Jeśli program `GetRequestedRuntime` używa pliku konfiguracji podczas procesu powiązania, w przypadku jego powracania `pdwConfigFlags` zawiera [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) wartość, która wskazuje, czy element [ \<>uruchomienia](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) ma `useLegacyV2RuntimeActivationPolicy` ustawiony atrybut i wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="32f6c-129">If `GetRequestedRuntime` uses a configuration file during the binding process, when it returns, `pdwConfigFlags` contains a [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) value that indicates whether the [\<startup>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) element has the `useLegacyV2RuntimeActivationPolicy` attribute set, and the value of the attribute.</span></span> <span data-ttu-id="32f6c-130">Zastosuj maskę [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) , aby `pdwConfigFlags` uzyskać odpowiednie wartości `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="32f6c-130">Apply the [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) mask to `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|
|`riid`|<span data-ttu-id="32f6c-131">podczas Określa identyfikator interfejsu IID_ICLRRuntimeInfo dla żądanego interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="32f6c-131">[in] Specifies the interface identifier IID_ICLRRuntimeInfo for the requested [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|
|`ppRuntime`|<span data-ttu-id="32f6c-132">określoną Gdy `GetRequestedRuntime` zwraca, zawiera wskaźnik do odpowiedniego interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="32f6c-132">[out] When `GetRequestedRuntime` returns, contains a pointer to the corresponding [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|

## <a name="remarks"></a><span data-ttu-id="32f6c-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32f6c-133">Remarks</span></span>

<span data-ttu-id="32f6c-134">Gdy ta metoda zakończy się pomyślnie, ma efekt po stronie łączenia dodatkowych flag z bieżącymi domyślnymi flagami uruchamiania zwróconego interfejsu środowiska uruchomieniowego, jeśli i tylko wtedy, gdy co najmniej jeden z następujących elementów znajduje się w tym strumieniu konfiguracji w `<configuration><runtime>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="32f6c-134">When this method succeeds, it has the side effect of combining additional flags with the current default startup flags of the returned runtime interface, if and only if one or more of the following elements exist in the configuration stream within the `<configuration><runtime>` section:</span></span>

- <span data-ttu-id="32f6c-135">`<gcServer enabled="true"/>`przyczyny `STARTUP_SERVER_GC` do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="32f6c-135">`<gcServer enabled="true"/>` causes `STARTUP_SERVER_GC` to be set.</span></span>

- <span data-ttu-id="32f6c-136">`<etwEnable enabled="true"/>`przyczyny `STARTUP_ETW` do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="32f6c-136">`<etwEnable enabled="true"/>` causes `STARTUP_ETW` to be set.</span></span>

- <span data-ttu-id="32f6c-137">`<appDomainResourceMonitoring enabled="true"/>`przyczyny `STARTUP_ARM` do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="32f6c-137">`<appDomainResourceMonitoring enabled="true"/>` causes `STARTUP_ARM` to be set.</span></span>

<span data-ttu-id="32f6c-138">`STARTUP_FLAGS`Wartość domyślna to liczba bitowa lub kombinacja wartości ustawionych na podstawie poprzedniej listy z domyślnymi flagami uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="32f6c-138">The resulting default `STARTUP_FLAGS` value is the bitwise OR combination of the values that are set from the preceding list with the default startup flags.</span></span>

## <a name="return-value"></a><span data-ttu-id="32f6c-139">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="32f6c-139">Return Value</span></span>

<span data-ttu-id="32f6c-140">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="32f6c-140">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="32f6c-141">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32f6c-141">HRESULT</span></span>|<span data-ttu-id="32f6c-142">Opis</span><span class="sxs-lookup"><span data-stu-id="32f6c-142">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="32f6c-143">S_OK</span><span class="sxs-lookup"><span data-stu-id="32f6c-143">S_OK</span></span>|<span data-ttu-id="32f6c-144">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="32f6c-144">The method completed successfully.</span></span>|
|<span data-ttu-id="32f6c-145">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="32f6c-145">E_POINTER</span></span>|<span data-ttu-id="32f6c-146">`pwzVersion`nie ma wartości null i `pcchVersion` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="32f6c-146">`pwzVersion` is not null and `pcchVersion` is null.</span></span><br /><br /> <span data-ttu-id="32f6c-147">-lub-</span><span class="sxs-lookup"><span data-stu-id="32f6c-147">-or-</span></span><br /><br /> <span data-ttu-id="32f6c-148">`pwzImageVersion`nie ma wartości null i `pcchImageVersion` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="32f6c-148">`pwzImageVersion` is not null and `pcchImageVersion` is null.</span></span>|
|<span data-ttu-id="32f6c-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="32f6c-149">E_INVALIDARG</span></span>|<span data-ttu-id="32f6c-150">`dwPolicyFlags`nie określono `METAHOST_POLICY_HIGHCOMPAT` .</span><span class="sxs-lookup"><span data-stu-id="32f6c-150">`dwPolicyFlags` does not specify `METAHOST_POLICY_HIGHCOMPAT`.</span></span>|
|<span data-ttu-id="32f6c-151">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="32f6c-151">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="32f6c-152">Przydzieloną pamięć `pwzVersion` jest niewystarczająca.</span><span class="sxs-lookup"><span data-stu-id="32f6c-152">The memory allocated to `pwzVersion` is inadequate.</span></span><br /><br /> <span data-ttu-id="32f6c-153">-lub-</span><span class="sxs-lookup"><span data-stu-id="32f6c-153">-or-</span></span><br /><br /> <span data-ttu-id="32f6c-154">Przydzieloną pamięć `pwzImageVersion` jest niewystarczająca.</span><span class="sxs-lookup"><span data-stu-id="32f6c-154">The memory allocated to `pwzImageVersion` is inadequate.</span></span>|
|<span data-ttu-id="32f6c-155">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="32f6c-155">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="32f6c-156">`dwPolicyFlags`zawiera METAHOST_POLICY_APPLY_UPGRADE_POLICY i i `pwzVersion` `pcchVersion` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="32f6c-156">`dwPolicyFlags` includes METAHOST_POLICY_APPLY_UPGRADE_POLICY, and both `pwzVersion` and `pcchVersion` are null.</span></span>|

## <a name="requirements"></a><span data-ttu-id="32f6c-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32f6c-157">Requirements</span></span>

<span data-ttu-id="32f6c-158">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32f6c-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="32f6c-159">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="32f6c-159">**Header:** MetaHost.h</span></span>

<span data-ttu-id="32f6c-160">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="32f6c-160">**Library:** Included as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="32f6c-161">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32f6c-161">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="32f6c-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32f6c-162">See also</span></span>

- [<span data-ttu-id="32f6c-163">ICLRMetaHostPolicy, interfejs</span><span class="sxs-lookup"><span data-stu-id="32f6c-163">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)
- [<span data-ttu-id="32f6c-164">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="32f6c-164">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="32f6c-165">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="32f6c-165">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="32f6c-166">Hosting</span><span class="sxs-lookup"><span data-stu-id="32f6c-166">Hosting</span></span>](index.md)
