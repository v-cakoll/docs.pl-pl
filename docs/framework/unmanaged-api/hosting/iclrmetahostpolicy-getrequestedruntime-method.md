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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1516b6661402ee71448e0d6987e4ed32a0ce5296
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371466"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime — Metoda

Udostępnia interfejs dla preferowaną wersję środowiska uruchomieniowego języka wspólnego (CLR) na podstawie zasad hostingu, zestaw zarządzany, ciąg wersji i konfiguracji strumienia. Ta metoda bez faktycznego obciążenia lub aktywacji środowiska CLR, ale po prostu zwraca [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który reprezentuje wyników zasad. Ta metoda zastępuje [getrequestedruntimeinfo —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [getrequestedruntimeversion —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [corbindtoruntimehost —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), i [getcorrequiredversion —](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) metody.

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

#### <a name="parameters"></a>Parametry

|Nazwa|Opis|
|----------|-----------------|
|`dwPolicyFlags`|[in] Wymagane. Określa członka [metahost_policy_flags —](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) wyliczenia, reprezentujący zasad tworzenia powiązań i dowolną liczbę modyfikatorów. Tylko zasady, które jest obecnie dostępna jest [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Modyfikatory obejmują [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), i [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|
|`pwzBinary`|[in] Opcjonalnie. Określa ścieżkę pliku zestawu.|
|`pCfgStream`|[in] Opcjonalnie. Określa plik konfiguracyjny jako <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|`pwzVersion`|[out w] Opcjonalnie. Określa, czy zwraca preferowaną wersję środowiska CLR do załadowania.|
|`pcchVersion`|[out w] Wymagane. Określa rozmiar oczekiwany `pwzVersion` jako dane wejściowe, aby uniknąć przepełnienia buforu. Jeśli `pwzVersion` ma wartość null, `pcchVersion` zawiera oczekiwanego rozmiaru `pwzVersion` podczas `GetRequestedRuntime` zwraca, aby umożliwić wstępnej alokacji; w przeciwnym razie `pcchVersion` zawiera liczbę znaków zapisywane `pwzVersion`.|
|`pwzImageVersion`|[out] Opcjonalnie. Gdy `GetRequestedRuntime` zwraca, zawiera wersję CLR do odpowiednich [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu, który jest zwracany.|
|`pcchImageVersion`|[out w] Opcjonalnie. Określa rozmiar `pwzImageVersion` jako dane wejściowe, aby uniknąć przepełnienia buforu. Jeśli `pwzImageVersion` ma wartość null, `pcchImageVersion` zawiera wymagany rozmiar `pwzImageVersion` podczas `GetRequestedRuntime` zwraca, aby umożliwić wstępnej alokacji.|
|`pdwConfigFlags`|[out] Opcjonalnie. Jeśli `GetRequestedRuntime` korzysta z pliku konfiguracji w procesie powiązania, gdy zwraca ono `pdwConfigFlags` zawiera [metahost_config_flags —](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) wartość wskazującą, czy [ \<uruchamiania >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) element ma `useLegacyV2RuntimeActivationPolicy` atrybutu zestawu, a wartość atrybutu. Zastosuj [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) maski do `pdwConfigFlags` można pobrać wartości dotyczą `useLegacyV2RuntimeActivationPolicy`.|
|`riid`|[in] Określa identyfikator interfejsu IID_ICLRRuntimeInfo żądany [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu.|
|`ppRuntime`|[out] Gdy `GetRequestedRuntime` zwraca, zawiera wskaźnik do odpowiednich [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu.|

## <a name="remarks"></a>Uwagi

Gdy metoda ta powiedzie się, ma efekt ubocznym łączenia dodatkowe flagi z bieżące flagi uruchamiania domyślnego interfejsu zwrócone środowiska uruchomieniowego, tylko wtedy, gdy co najmniej jeden z następujących elementów istnieje w usłudze stream konfiguracji w ramach `<configuration><runtime>` sekcja:

- `<gcServer enabled="true"/>` powoduje, że `STARTUP_SERVER_GC` do ustawienia.

- `<etwEnable enabled="true"/>` powoduje, że `STARTUP_ETW` do ustawienia.

- `<appDomainResourceMonitoring enabled="true"/>` powoduje, że `STARTUP_ARM` do ustawienia.

Wynikowy domyślne `STARTUP_FLAGS` wartość jest bitową kombinacją OR wartości, które są konfigurowane z powyższej listy z użyciem flag domyślnego uruchamiania.

## <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.

|HRESULT|Opis|
|-------------|-----------------|
|S_OK|Metoda została ukończona pomyślnie.|
|E_POINTER|`pwzVersion` nie ma wartości null i `pcchVersion` ma wartość null.<br /><br /> —lub—<br /><br /> `pwzImageVersion` nie ma wartości null i `pcchImageVersion` ma wartość null.|
|E_INVALIDARG|`dwPolicyFlags` nie określono `METAHOST_POLICY_HIGHCOMPAT`.|
|ERROR_INSUFFICIENT_BUFFER|Pamięć przydzielona do `pwzVersion` jest niewystarczająca.<br /><br /> —lub—<br /><br /> Pamięć przydzielona do `pwzImageVersion` jest niewystarczająca.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` obejmuje METAHOST_POLICY_APPLY_UPGRADE_POLICY i wartościami `pwzVersion` i `pcchVersion` mają wartość null.|

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** MetaHost.h

**Biblioteka:** Dołączony jako zasób w MSCorEE.dll

**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICLRMetaHostPolicy, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)
- [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
