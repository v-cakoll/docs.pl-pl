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
ms.openlocfilehash: a028d2a8116de4df79f662ee8b2768e6e070428a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141402"
---
# <a name="metahost_policy_flags-enumeration"></a>METAHOST_POLICY_FLAGS — Wyliczenie
Program udostępnia zasady powiązań, które są wspólne dla większości hostów środowiska uruchomieniowego. To wyliczenie jest używane przez metodę [ICLRMetaHostPolicy:: GetRequestedRuntime —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`METAHOST_POLICY_HIGHCOMPAT`|Definiuje zasady wysokiej zgodności, które nie uwzględnia żadnego środowiska uruchomieniowego języka wspólnego (CLR), który jest ładowany do bieżącego procesu. Zamiast tego uwzględnia tylko zainstalowaną CLRs i preferencje składnika, jak wynika z samego pliku zestawu, zadeklarowanej wbudowanej wersji lub pliku konfiguracji.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Stosuje zasady uaktualniania do wyniku powiązania wersji, gdy nie znaleziono dokładnego dopasowania, na podstawie zawartości HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades. Ma to taki sam efekt jak [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Wyniki powiązań są zwracane, jeśli obraz dostarczony do wywołania został uruchomiony w nowym procesie. Obecnie `GetRequestedRuntime` ignoruje zestaw plików wykonywalnych do załadowania i tworzy powiązania z zestawem zainstalowanych środowisk uruchomieniowych. Ta flaga umożliwia hostowi określenie, które środowisko uruchomieniowe zostanie powiązane z tym, gdy zostanie uruchomiony.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Gdy `GetRequestedRuntime` nie może znaleźć środowiska uruchomieniowego zgodnego z parametrami wejściowymi, zostanie wyświetlone okno dialogowe błędu. Począwszy od .NET Framework 4,5, to okno dialogowe błędu może przyjmować formę okna dialogowego funkcji systemu Windows z pytaniem, czy użytkownik chce włączyć odpowiednią funkcję.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` używa obrazu procesu (i dowolnego odpowiedniego pliku konfiguracji) jako dodatkowego wejścia do procesu powiązania. Domyślnie `GetRequestedRuntime` nie wraca do ścieżki obrazu procesu (zazwyczaj jest to plik EXE używany do uruchomienia procesu) podczas określania środowiska uruchomieniowego, z którym ma zostać utworzone powiązanie.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` musi sprawdzić, czy odpowiednia jednostka SKU jest zainstalowana, gdy w pliku konfiguracji nie ma dostępnych informacji. Dzięki temu aplikacje, które nie mają plików konfiguracyjnych, mogą bezpiecznie kończyć się niepowodzeniem w mniejszych jednostkach SKU niż domyślna instalacja .NET Framework. Domyślnie `GetRequestedRuntime` nie sprawdza, czy odpowiednia jednostka SKU jest zainstalowana, chyba że atrybut SKU jest określony w pliku konfiguracji `<supportedRuntime />` elemencie.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` powinien ignorować SEM_FAILCRITICALERRORS (ustawiany przez wywołanie funkcji [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) ) i wyświetlić okno dialogowe błędu. Domyślnie SEM_FAILCRITICALERRORS pomija okno dialogowe błędu. Być może został on odziedziczony z innego procesu, a błąd dyskretny może być niepożądany w Twoim scenariuszu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [GetRequestedRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
