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
ms.openlocfilehash: 1b07029990ef529ded57bc569beff1061ad0f938
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140870"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime — Metoda

Udostępnia interfejs preferowanej wersji środowiska uruchomieniowego języka wspólnego (CLR) na podstawie zasad hostingu, zestawu zarządzanego, ciągu wersji i strumienia konfiguracji. Ta metoda nie ładuje ani nie aktywuje środowiska CLR, ale po prostu zwraca interfejs [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , który reprezentuje wynik zasad. Ta metoda zastępuje metody [GetRequestedRuntimeInfo —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)i [GetCORRequiredVersion —](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) .

## <a name="syntax"></a>Składnia

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

## <a name="parameters"></a>Parametry

|Nazwa|Opis|
|----------|-----------------|
|`dwPolicyFlags`|podczas Wymagane. Określa element członkowski wyliczenia [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) , reprezentujący zasady powiązań i dowolną liczbę modyfikatorów. Jedyne dostępne zasady to [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Modyfikatory obejmują [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)i [METAHOST_POLICY_ ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|
|`pwzBinary`|podczas Obowiązkowe. Określa ścieżkę pliku zestawu.|
|`pCfgStream`|podczas Obowiązkowe. Określa plik konfiguracji jako <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|`pwzVersion`|[in. out] Obowiązkowe. Określa lub zwraca preferowaną wersję środowiska CLR do załadowania.|
|`pcchVersion`|[in. out] Wymagane. Określa oczekiwany rozmiar `pwzVersion` jako dane wejściowe, aby uniknąć przekroczeń buforu. Jeśli `pwzVersion` ma wartość null, `pcchVersion` zawiera oczekiwany rozmiar `pwzVersion`, gdy `GetRequestedRuntime` zwraca wartość, aby umożliwić wstępne przydzielanie; w przeciwnym razie `pcchVersion` zawiera liczbę znaków zapisanych do `pwzVersion`.|
|`pwzImageVersion`|określoną Obowiązkowe. Gdy `GetRequestedRuntime` zwraca, zawiera wersję środowiska CLR odpowiadającą zwróconemu interfejsowi [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) .|
|`pcchImageVersion`|[in. out] Obowiązkowe. Określa rozmiar `pwzImageVersion` jako dane wejściowe, aby uniknąć przekroczeń buforu. Jeśli `pwzImageVersion` ma wartość null, `pcchImageVersion` zawiera wymagany rozmiar `pwzImageVersion`, gdy `GetRequestedRuntime` zwraca wartość, aby umożliwić wstępne przydzielanie.|
|`pdwConfigFlags`|określoną Obowiązkowe. Jeśli `GetRequestedRuntime` używa pliku konfiguracji podczas procesu powiązania, w przypadku powracania `pdwConfigFlags` zawiera wartość [METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) , która wskazuje, czy [\<> uruchamiania](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) elementu ma ustawiony atrybut `useLegacyV2RuntimeActivationPolicy` i wartość atrybut. Zastosuj maskę [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) , aby `pdwConfigFlags` uzyskać wartości istotne dla `useLegacyV2RuntimeActivationPolicy`.|
|`riid`|podczas Określa identyfikator interfejsu IID_ICLRRuntimeInfo dla żądanego interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) .|
|`ppRuntime`|określoną Gdy `GetRequestedRuntime` zwraca, zawiera wskaźnik do odpowiedniego interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) .|

## <a name="remarks"></a>Uwagi

Gdy ta metoda zakończy się pomyślnie, ma wpływ na połączenie dodatkowych flag z bieżącymi domyślnymi flagami uruchamiania zwróconego interfejsu środowiska uruchomieniowego, jeśli i tylko wtedy, gdy co najmniej jeden z następujących elementów istnieje w strumieniu konfiguracji w ramach `<configuration><runtime>` Paragraf

- `<gcServer enabled="true"/>` powoduje, że `STARTUP_SERVER_GC` być ustawiony.

- `<etwEnable enabled="true"/>` powoduje, że `STARTUP_ETW` być ustawiony.

- `<appDomainResourceMonitoring enabled="true"/>` powoduje, że `STARTUP_ARM` być ustawiony.

Wartość domyślna `STARTUP_FLAGS` jest wartością bitową lub kombinacją wartości, które są ustawione na podstawie poprzedniej listy z domyślnymi flagami uruchamiania.

## <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.

|HRESULT|Opis|
|-------------|-----------------|
|S_OK|Metoda została ukończona pomyślnie.|
|E_POINTER|`pwzVersion` nie ma wartości null i `pcchVersion` ma wartość null.<br /><br /> —lub—<br /><br /> `pwzImageVersion` nie ma wartości null i `pcchImageVersion` ma wartość null.|
|E_INVALIDARG|`dwPolicyFlags` nie określa `METAHOST_POLICY_HIGHCOMPAT`.|
|ERROR_INSUFFICIENT_BUFFER|Pamięć przypisana do `pwzVersion` jest niewystarczająca.<br /><br /> —lub—<br /><br /> Pamięć przypisana do `pwzImageVersion` jest niewystarczająca.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` zawiera METAHOST_POLICY_APPLY_UPGRADE_POLICY, a oba `pwzVersion` i `pcchVersion` mają wartość null.|

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** Obiekt ServiceHost. h

**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll

**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICLRMetaHostPolicy, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)
- [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
