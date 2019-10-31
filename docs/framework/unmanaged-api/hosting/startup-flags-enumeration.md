---
title: STARTUP_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
ms.openlocfilehash: 1799e0af91fa6074f174120b29e2302a27230c62
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141458"
---
# <a name="startup_flags-enumeration"></a>STARTUP_FLAGS — Wyliczenie
Zawiera wartości, które wskazują zachowanie uruchamiania środowiska uruchomieniowego języka wspólnego (CLR). Domyślnie zbieranie elementów bezużytecznych nie jest współbieżne i tylko podstawowa Biblioteka klas jest ładowana do obszaru neutralnego dla domeny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|Określa, że należy użyć współbieżnego wyrzucania elementów bezużytecznych. Jeśli obiekt wywołujący prosi o kompilację serwera i współbieżne wyrzucanie elementów bezużytecznych na komputerze z jednym procesorem, zamiast tego uruchamiane są kompilacje stacji roboczej i niewspółbieżne odzyskiwanie pamięci. **Uwaga:**  Współbieżne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacjach korzystających z emulatora WOW64 x86 w systemach 64-bitowych, które implementują architekturę Intel Itanium (dawniej zwane IA-64). Aby uzyskać więcej informacji na temat korzystania z emulatora WOW64 w systemach 64-bitowych systemu Windows, zobacz [Uruchamianie aplikacji 32-bitowych](/windows/desktop/WinProg64/running-32-bit-applications).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Określa, że optymalizacja modułu ładującego jest wykonywana.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Określa, że żadne zestawy nie są ładowane jako niezależne od domeny.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Określa, że wszystkie zestawy są ładowane jako niezależne od domeny.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Określa, że wszystkie zestawy o silnych nazwach są ładowane jako niezależne od domeny.|  
|`STARTUP_LOADER_SAFEMODE`|Określa, że zasady wersji środowiska CLR nie będą stosowane do wersji przekazaną. Zostanie załadowana dokładna wersja określonego środowiska CLR. Podkładka nie szacuje zasad w celu ustalenia najnowszej zgodnej wersji.|  
|`STARTUP_LOADER_SETPREFERENCE`|Określa, że preferowane środowisko uruchomieniowe zostanie ustawione, ale w rzeczywistości nie zostanie uruchomione.|  
|`STARTUP_SERVER_GC`|Określa, że będą używane wyrzucanie elementów bezużytecznych serwera.|  
|`STARTUP_HOARD_GC_VM`|Określa, że wyrzucanie elementów bezużytecznych będzie utrzymywać używany adres wirtualny.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Określa, że mieszanie interfejsu hostingu nie będzie dozwolone.|  
|`STARTUP_LEGACY_IMPERSONATION`|Określa, że personifikacja nie powinna domyślnie przepływać się w punktach asynchronicznych.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Określa, że cały stos wątku nie powinien być zatwierdzany podczas uruchamiania wątku.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Określa, że zarządzane osoby odwołujące się i osoby niedochodzące za pośrednictwem wywołania platformy będą przepływać przez punkty asynchroniczne. Domyślnie tylko zarządzane osoby będą przepływać między punktami asynchronicznymi.|  
|`STARTUP_TRIM_GC_COMMIT`|Określa, że wyrzucanie elementów bezużytecznych będzie używać mniej zajmowanego miejsca, gdy ilość pamięci jest niska. Zobacz `gcTrimCommitOnLowMemory` w obszarze [Optymalizacja dla udostępnionego hostingu w sieci Web](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Określa, że śledzenie zdarzeń systemu Windows (ETW) jest włączone dla zdarzeń środowiska uruchomieniowego języka wspólnego. Począwszy od systemu Windows Vista, śledzenie zdarzeń jest zawsze włączone, więc ta flaga nie ma żadnego wpływu. Zobacz [kontrolowanie rejestrowania .NET Framework](../../../../docs/framework/performance/controlling-logging.md).|  
|`STARTUP_ARM`|Określa, że jest włączone monitorowanie zasobów domeny aplikacji. Zobacz Właściwość <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> i [\<appDomainResourceMonitoring > elementu](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
