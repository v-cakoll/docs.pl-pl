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
ms.openlocfilehash: 1a96af0c66d85c7eec9a97be3ba8c756b1e91849
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486678"
---
# <a name="metahostpolicyflags-enumeration"></a>METAHOST_POLICY_FLAGS — Wyliczenie
Udostępnia zasady powiązania, które są wspólne dla większości hosty środowiska uruchomieniowego. To wyliczenie jest używane przez [iclrmetahostpolicy::getrequestedruntime —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.  
  
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
|`METAHOST_POLICY_HIGHCOMPAT`|Definiuje zasady wysokiej zgodności z poprzednią wersją, który nie należy wziąć pod uwagę wszystkie środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany do bieżącego procesu. Zamiast tego traktuje tylko zainstalowane CLRs i preferencje dotyczące składnika, ponieważ sam plik zestawu, zadeklarowany oparta na wersji lub plik konfiguracji.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Dotyczy zasad uaktualniania wersji wynik powiązania dokładne dopasowanie nie zostanie znaleziony, na podstawie zawartości HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades. Ma to taki sam skutek jak [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Powiązanie wyniki są zwracane, tak, jakby obrazu dostarczonego wywołania zostały uruchomione w ramach nowego procesu. Obecnie `GetRequestedRuntime` ignoruje zbiór obciążana środowisk uruchomieniowych i wiąże względem zestawu zainstalowanych modułów wykonawczych. Ta flaga umożliwia hostowi na określenie środowiska uruchomieniowego, który powiąże EXE po jej uruchomieniu.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Wyświetlane jest okno dialogowe błędu, jeśli `GetRequestedRuntime` nie może odnaleźć środowiska uruchomieniowego, który jest zgodny z parametrami wejściowymi. Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], to okno dialogowe błędu może mieć postać Windows funkcji okno dialogowe z pytaniem, czy użytkownik chce włączyć funkcję odpowiednie.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` używa obrazu procesu (i wszelkie odpowiedni plik konfiguracji) jako dodatkowe dane wejściowe do przetworzenia powiązania. Domyślnie `GetRequestedRuntime` nie wrócił do ścieżki obrazu procesu (zwykle EXE, który został użyty do uruchamiania procesu) podczas określania środowiska uruchomieniowego, można powiązać.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` należy sprawdzić, czy odpowiednią jednostkę SKU jest zainstalowany, gdy żadne informacje nie będzie dostępna w pliku konfiguracji. Dzięki temu aplikacje, które nie mają plików konfiguracyjnych do elegancko nie powieść się na mniejsze jednostki SKU niż domyślnej instalacji programu .NET Framework. Domyślnie `GetRequestedRuntime` nie sprawdza, czy odpowiednią jednostkę SKU jest zainstalowany, chyba że jednostka SKU nie jest określony w pliku konfiguracyjnym `<supportedRuntime />` elementu.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` należy sprawdzić, czy odpowiednią jednostkę SKU jest zainstalowany, gdy żadne informacje nie będzie dostępna w pliku konfiguracji. Dzięki temu aplikacje, które nie mają plików konfiguracyjnych do elegancko nie powieść się na mniejsze jednostki SKU niż domyślnej instalacji programu .NET Framework. Domyślnie `GetRequestedRuntime` nie sprawdza, czy odpowiednią jednostkę SKU jest zainstalowany, chyba że jednostka SKU nie jest określony w pliku konfiguracyjnym `<supportedRuntime />` elementu.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` powinien ignorować SEM_FAILCRITICALERRORS (który jest ustawiony przez wywołanie metody [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) funkcji) i wyświetlenie okna dialogowego błędu. Domyślnie SEM_FAILCRITICALERRORS powoduje pominięcie okna dialogowego błędu. Zostało odziedziczone z innego procesu, a dyskretnej błędu może być niepożądane w danym scenariuszu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Metahost.h  
  
 **Biblioteka:** dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [GetRequestedRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
