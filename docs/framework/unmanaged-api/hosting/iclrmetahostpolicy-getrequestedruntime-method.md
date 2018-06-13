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
ms.openlocfilehash: e01affb5edb8b0766edf8548ae34cf8220bcc62d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436049"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime — Metoda
Udostępnia interfejs do preferowanego wersji środowisko uruchomieniowe języka wspólnego (CLR) na podstawie zasad hostingu, zestaw zarządzany, ciąg wersji i konfiguracji strumienia. Ta metoda nie faktycznie obciążenia lub aktywować CLR, ale po prostu zwraca [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który reprezentuje wyników zasad. Ta metoda zastępuje [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), i [GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`dwPolicyFlags`|[in] Wymagane. Określa członkiem [metahost_policy_flags —](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) wyliczenie reprezentujące zasad powiązania i dowolną liczbę modyfikatorów. Tylko zasady, które jest obecnie dostępny jest [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Modyfikatory obejmują [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), i [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|  
|`pwzBinary`|[in] Opcjonalne. Określa ścieżkę pliku zestawu.|  
|`pCfgStream`|[in] Opcjonalne. Określa plik konfiguracyjny jako <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|  
|`pwzVersion`|[w, out] Opcjonalne. Określa, czy zwraca preferowany wersji środowiska CLR do załadowania.|  
|`pcchVersion`|[w, out] Wymagane. Określa rozmiar oczekiwany `pwzVersion` jako dane wejściowe, aby uniknąć przepełnienia buforu. Jeśli `pwzVersion` ma wartość null, `pcchVersion` zawiera oczekiwanego rozmiaru `pwzVersion` podczas `GetRequestedRuntime` zwraca, aby umożliwić wstępnej alokacji; w przeciwnym razie `pcchVersion` zawiera liczbę znaków zapisane `pwzVersion`.|  
|`pwzImageVersion`|[out] Opcjonalne. Gdy `GetRequestedRuntime` zwraca, zawiera wersję środowiska CLR do odpowiadającego [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który jest zwracany.|  
|`pcchImageVersion`|[w, out] Opcjonalne. Określa rozmiar `pwzImageVersion` jako dane wejściowe, aby uniknąć przepełnienia buforu. Jeśli `pwzImageVersion` ma wartość null, `pcchImageVersion` zawiera wymagany rozmiar `pwzImageVersion` podczas `GetRequestedRuntime` zwraca, aby umożliwić wstępnej alokacji.|  
|`pdwConfigFlags`|[out] Opcjonalne. Jeśli `GetRequestedRuntime` używany plik konfiguracji podczas procesu powiązanie, gdy powróci ona `pdwConfigFlags` zawiera [METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) wartość wskazującą, czy [ \<uruchamiania >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) element ma `useLegacyV2RuntimeActivationPolicy` atrybutu zestawu, a wartość atrybutu. Zastosuj [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) maski do `pdwConfigFlags` można pobrać wartości odpowiadających `useLegacyV2RuntimeActivationPolicy`.|  
|`riid`|[in] Określa identyfikator interfejsu IID_ICLRRuntimeInfo dla żądanego [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu.|  
|`ppRuntime`|[out] Gdy `GetRequestedRuntime` zwraca, zawiera wskaźnik do odpowiadającego [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy ta metoda zakończy się powodzeniem, składa się z efektem ubocznym łączenia dodatkowe flagi z flagami bieżącego uruchomienia domyślnego interfejsu środowiska wykonawczego zwrócony tylko wtedy, gdy co najmniej jedna z następujących elementów istnieje w strumieniu konfiguracji w ramach `<configuration><runtime>` sekcja:  
  
-   `<gcServer enabled="true"/>` powoduje, że `STARTUP_SERVER_GC` należy ustawić wartość.  
  
-   `<etwEnable enabled="true"/>` powoduje, że `STARTUP_ETW` należy ustawić wartość.  
  
-   `<appDomainResourceMonitoring enabled="true"/>` powoduje, że `STARTUP_ARM` należy ustawić wartość.  
  
 Wynikowa domyślne `STARTUP_FLAGS` bitowe połączenie lub wartości, które są ustawione wymienionych na liście z flagami uruchamiania domyślną wartość.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pwzVersion` nie ma wartości null i `pcchVersion` ma wartość null.<br /><br /> —lub—<br /><br /> `pwzImageVersion` nie ma wartości null i `pcchImageVersion` ma wartość null.|  
|E_INVALIDARG|`dwPolicyFlags` nie określono `METAHOST_POLICY_HIGHCOMPAT`.|  
|ERROR_INSUFFICIENT_BUFFER|Ilość pamięci przydzielona do `pwzVerison` jest nieodpowiedni.<br /><br /> —lub—<br /><br /> Ilość pamięci przydzielona do `pwzImageVerison` jest nieodpowiedni.|  
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` obejmuje METAHOST_POLICY_APPLY_UPGRADE_POLICY i obie `pwzVersion` i `pcchVersion` mają wartość null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRMetaHostPolicy, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
