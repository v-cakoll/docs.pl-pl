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
ms.openlocfilehash: 37167b7a9aefa6cd9d5e4df043e8bbc1b0514261
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504124"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime — Metoda

Udostępnia interfejs preferowanej wersji środowiska uruchomieniowego języka wspólnego (CLR) na podstawie zasad hostingu, zestawu zarządzanego, ciągu wersji i strumienia konfiguracji. Ta metoda nie ładuje ani nie aktywuje środowiska CLR, ale po prostu zwraca interfejs [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , który reprezentuje wynik zasad. Ta metoda zastępuje metody [GetRequestedRuntimeInfo —](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion —](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost —](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md)i [GetCORRequiredVersion —](getcorrequiredversion-function.md) .

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
|`dwPolicyFlags`|podczas Wymagane. Określa element członkowski wyliczenia [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) , reprezentujący zasady powiązań i dowolną liczbę modyfikatorów. Jedyne obecnie dostępne zasady są [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).<br /><br /> Modyfikatory obejmują [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)i [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).|
|`pwzBinary`|podczas Obowiązkowe. Określa ścieżkę pliku zestawu.|
|`pCfgStream`|podczas Obowiązkowe. Określa plik konfiguracji jako <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> .|
|`pwzVersion`|[in. out] Obowiązkowe. Określa lub zwraca preferowaną wersję środowiska CLR do załadowania.|
|`pcchVersion`|[in. out] Wymagane. Określa oczekiwany rozmiar `pwzVersion` jako dane wejściowe, aby uniknąć przekroczeń buforu. Jeśli `pwzVersion` ma wartość null, `pcchVersion` zawiera oczekiwany rozmiar `pwzVersion` `GetRequestedRuntime` zwracanego elementu, aby zezwolić na wstępne alokację; w przeciwnym razie `pcchVersion` zawiera liczbę znaków, do których zapisano `pwzVersion` .|
|`pwzImageVersion`|określoną Obowiązkowe. Gdy `GetRequestedRuntime` zwraca, zawiera wersję środowiska CLR odpowiadającą zwróconemu interfejsowi [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .|
|`pcchImageVersion`|[in. out] Obowiązkowe. Określa rozmiar `pwzImageVersion` jako dane wejściowe, aby uniknąć przekroczenia buforu. Jeśli `pwzImageVersion` ma wartość null, `pcchImageVersion` zawiera wymagany rozmiar `pwzImageVersion` , gdy `GetRequestedRuntime` zwraca, aby umożliwić wstępne przydzielanie.|
|`pdwConfigFlags`|określoną Obowiązkowe. Jeśli program `GetRequestedRuntime` używa pliku konfiguracji podczas procesu powiązania, w przypadku jego powracania `pdwConfigFlags` zawiera [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) wartość, która wskazuje, czy [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) element ma `useLegacyV2RuntimeActivationPolicy` ustawiony atrybut i wartość atrybutu. Zastosuj maskę [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) , aby `pdwConfigFlags` uzyskać odpowiednie wartości `useLegacyV2RuntimeActivationPolicy` .|
|`riid`|podczas Określa identyfikator interfejsu IID_ICLRRuntimeInfo dla żądanego interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .|
|`ppRuntime`|określoną Gdy `GetRequestedRuntime` zwraca, zawiera wskaźnik do odpowiedniego interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .|

## <a name="remarks"></a>Uwagi

Gdy ta metoda zakończy się pomyślnie, ma efekt po stronie łączenia dodatkowych flag z bieżącymi domyślnymi flagami uruchamiania zwróconego interfejsu środowiska uruchomieniowego, jeśli i tylko wtedy, gdy co najmniej jeden z następujących elementów znajduje się w tym strumieniu konfiguracji w `<configuration><runtime>` sekcji:

- `<gcServer enabled="true"/>`przyczyny `STARTUP_SERVER_GC` do ustawienia.

- `<etwEnable enabled="true"/>`przyczyny `STARTUP_ETW` do ustawienia.

- `<appDomainResourceMonitoring enabled="true"/>`przyczyny `STARTUP_ARM` do ustawienia.

`STARTUP_FLAGS`Wartość domyślna to liczba bitowa lub kombinacja wartości ustawionych na podstawie poprzedniej listy z domyślnymi flagami uruchamiania.

## <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.

|HRESULT|Opis|
|-------------|-----------------|
|S_OK|Metoda została ukończona pomyślnie.|
|E_POINTER|`pwzVersion`nie ma wartości null i `pcchVersion` ma wartość null.<br /><br /> -lub-<br /><br /> `pwzImageVersion`nie ma wartości null i `pcchImageVersion` ma wartość null.|
|E_INVALIDARG|`dwPolicyFlags`nie określono `METAHOST_POLICY_HIGHCOMPAT` .|
|ERROR_INSUFFICIENT_BUFFER|Przydzieloną pamięć `pwzVersion` jest niewystarczająca.<br /><br /> -lub-<br /><br /> Przydzieloną pamięć `pwzImageVersion` jest niewystarczająca.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags`zawiera METAHOST_POLICY_APPLY_UPGRADE_POLICY i i `pwzVersion` `pcchVersion` ma wartość null.|

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** Obiekt ServiceHost. h

**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll

**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICLRMetaHostPolicy, interfejs](iclrmetahostpolicy-interface.md)
- [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
