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
ms.openlocfilehash: bb40ed65a2e34f1bf293e4c4c842d7db63d2eaa5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008446"
---
# <a name="metahost_policy_flags-enumeration"></a>METAHOST_POLICY_FLAGS — Wyliczenie
Program udostępnia zasady powiązań, które są wspólne dla większości hostów środowiska uruchomieniowego. To wyliczenie jest używane przez metodę [ICLRMetaHostPolicy:: GetRequestedRuntime —](iclrmetahostpolicy-getrequestedruntime-method.md) .  
  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|Definiuje zasady wysokiej zgodności, które nie uwzględnia żadnego środowiska uruchomieniowego języka wspólnego (CLR), który jest ładowany do bieżącego procesu. Zamiast tego uwzględnia tylko zainstalowaną CLRs i preferencje składnika, jak wynika z samego pliku zestawu, zadeklarowanej wbudowanej wersji lub pliku konfiguracji.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Stosuje zasady uaktualniania do wyniku powiązania wersji, gdy nie znaleziono dokładnego dopasowania, na podstawie zawartości HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\Policy\Upgrades. Ma to taki sam efekt jak [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Wyniki powiązań są zwracane, jeśli obraz dostarczony do wywołania został uruchomiony w nowym procesie. Obecnie program `GetRequestedRuntime` ignoruje zestaw zainstalowanych środowisk uruchomieniowych i tworzy powiązania z zestawem instalowanych środowisk uruchomieniowych. Ta flaga umożliwia hostowi określenie, które środowisko uruchomieniowe zostanie powiązane z tym, gdy zostanie uruchomiony.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Jeśli `GetRequestedRuntime` program nie może znaleźć środowiska uruchomieniowego zgodnego z parametrami wejściowymi, pojawia się okno dialogowe błędu. Począwszy od .NET Framework 4,5, to okno dialogowe błędu może przyjmować formę okna dialogowego funkcji systemu Windows z pytaniem, czy użytkownik chce włączyć odpowiednią funkcję.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime`używa obrazu procesu (i dowolnego odpowiedniego pliku konfiguracji) jako dodatkowego wejścia do procesu powiązania. Domyślnie program nie wraca `GetRequestedRuntime` do ścieżki obrazu procesu (zazwyczaj jest to plik exe używany do uruchomienia procesu) podczas określania środowiska uruchomieniowego, z którym ma zostać utworzone powiązanie.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`należy sprawdzić, czy odpowiednia jednostka SKU jest zainstalowana, gdy w pliku konfiguracji nie ma dostępnych informacji. Dzięki temu aplikacje, które nie mają plików konfiguracyjnych, mogą bezpiecznie kończyć się niepowodzeniem w mniejszych jednostkach SKU niż domyślna instalacja .NET Framework. Domyślnie program nie `GetRequestedRuntime` sprawdza, czy odpowiednia jednostka SKU jest zainstalowana, chyba że ATRYBUT SKU jest określony w elemencie pliku konfiguracji `<supportedRuntime />` .|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime`należy zignorować SEM_FAILCRITICALERRORS (ustawiane przez wywołanie funkcji [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) ) i wyświetlić okno dialogowe błędu. Domyślnie SEM_FAILCRITICALERRORS pomija okno dialogowe błędu. Być może został on odziedziczony z innego procesu, a błąd dyskretny może być niepożądany w Twoim scenariuszu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting — Wyliczenia](hosting-enumerations.md)
- [GetRequestedRuntime, metoda](iclrmetahostpolicy-getrequestedruntime-method.md)
