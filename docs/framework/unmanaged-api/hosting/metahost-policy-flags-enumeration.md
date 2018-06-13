---
title: METAHOST_POLICY_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f980fb1336adaf43091e41b9e42ea008b00c033f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447288"
---
# <a name="metahostpolicyflags-enumeration"></a>METAHOST_POLICY_FLAGS — Wyliczenie
Udostępnia zasady powiązania, które są wspólne dla większości hosty w czasie wykonywania. To wyliczenie jest używany przez [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|Definiuje zasady zgodności wysokiej, który nie należy wziąć pod uwagę wszystkie środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany do bieżącego procesu. Zamiast tego traktuje tylko zainstalowany CLRs i preferencji składnika, ponieważ sam plik zestawu, zadeklarowane skompilowany przed wersji lub plik konfiguracji.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Dotyczy zasad uaktualniania wersji wynik wiązania nie znaleziono dokładnego dopasowania, na podstawie zawartości HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades. Jest to ten sam efekt co [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Powiązania są zwracane tak, jakby uruchomiono obrazu dostarczonego do wywołania w nowego procesu. Obecnie `GetRequestedRuntime` ignoruje zbiór obciążana środowisk uruchomieniowych i wiąże z zestawu zainstalowanych środowisk uruchomieniowych. Ta flaga umożliwia hosta określić, które środowiska uruchomieniowego EXE zostanie z nim powiązane po jej uruchomieniu.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Okno dialogowe błędu jest wyświetlana, jeśli `GetRequestedRuntime` nie może znaleźć środowiska uruchomieniowego, która jest zgodna z parametrów wejściowych. Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], to okno dialogowe błędu może mieć postać z pytaniem, czy użytkownik chce włączyć funkcję odpowiednie okno dialogowe funkcji systemu Windows.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` używa obraz procesu (i wszelkie w odpowiednim pliku konfiguracyjnym) jako dodatkowe dane wejściowe proces wiązania. Domyślnie `GetRequestedRuntime` nie wracały do ścieżka obrazu procesu (zazwyczaj EXE, który został użyty do uruchamiania procesu) podczas określania czasu wykonywania, aby powiązać.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` musi sprawdzić, czy odpowiednie jednostki SKU jest zainstalowany, gdy informacje są niedostępne w pliku konfiguracji. Dzięki temu aplikacje, które nie mają plików konfiguracyjnych niepowodzenie bezpiecznie na mniejsze jednostki SKU niż domyślna instalacja programu .NET Framework. Domyślnie `GetRequestedRuntime` nie sprawdza, czy odpowiednie jednostki SKU jest zainstalowany, chyba że jednostka SKU nie jest określony w pliku konfiguracyjnym `<supportedRuntime />` elementu.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` musi sprawdzić, czy odpowiednie jednostki SKU jest zainstalowany, gdy informacje są niedostępne w pliku konfiguracji. Dzięki temu aplikacje, które nie mają plików konfiguracyjnych niepowodzenie bezpiecznie na mniejsze jednostki SKU niż domyślna instalacja programu .NET Framework. Domyślnie `GetRequestedRuntime` nie sprawdza, czy odpowiednie jednostki SKU jest zainstalowany, chyba że jednostka SKU nie jest określony w pliku konfiguracyjnym `<supportedRuntime />` elementu.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` Parametr SEM_FAILCRITICALERRORS ignorować (który jest ustawiony przez wywołanie [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) funkcji) i wyświetlenie okna dialogowego błędu. Domyślnie parametr SEM_FAILCRITICALERRORS powoduje pominięcie okna dialogowego błędu. Zostało odziedziczone od innego procesu, a dyskretnej błędu może być niepożądane w danym scenariuszu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Metahost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [GetRequestedRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
