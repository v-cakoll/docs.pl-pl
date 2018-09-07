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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4680187de7318a6438bf6a5e6bd7c5f3acd05c2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44059940"
---
# <a name="startupflags-enumeration"></a>STARTUP_FLAGS — Wyliczenie
Zawiera wartości, które wskazują zachowanie uruchamiania środowiska uruchomieniowego języka wspólnego (CLR). Domyślnie, wyrzucanie elementów bezużytecznych jest niewspółbieżne i tylko Biblioteka klasy podstawowej jest załadowana do obszaru neutralnej domeny.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`STARTUP_CONCURRENT_GC`|Określa, że powinny być używane współbieżne wyrzucanie elementów bezużytecznych. Jeśli obiekt wywołujący prosi o kompilację serwera i równoczesne wyrzucania elementów bezużytecznych na komputerze jednoprocesorowym, stacja robocza kompilacji i niewspółbieżnym wyrzucaniem elementów bezużytecznych zostaną uruchomione w zamian. **Uwaga:** współbieżne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacji, które są uruchomione przez środowisko WOW64 x86 emulatora w systemach 64-bitowych, które implementują architekturę Intel Itanium (wcześniej noszącą nazwę IA-64). Aby uzyskać więcej informacji o używaniu WOW64 w 64-bitowych systemach Windows, zobacz [uruchomiona 32-bitowych aplikacji](/windows/desktop/WinProg64/running-32-bit-applications).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Określa, że Optymalizacja programu ładującego powinna występować.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Określa, że żadne zespoły nie są ładowane jako niezależne od domeny.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Określa, że wszystkie zespoły są ładowane jako niezależne od domeny.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Określa, że wszystkie zestawy o silnej nazwie są ładowane jako niezależne od domeny.|  
|`STARTUP_LOADER_SAFEMODE`|Określa, że zasady wersji środowiska CLR nie zostaną zastosowane do wersji przekazania. Dokładna wersja określona w CLR zostanie załadowana. Podkładka nie ocenia uprawnień do ustalenia najnowszej zgodnej wersji.|  
|`STARTUP_LOADER_SETPREFERENCE`|Określa, że preferowanego czasu wykonywania zostanie ustawiona, ale faktycznie nie jest uruchomiony.|  
|`STARTUP_SERVER_GC`|Określa, że serwer wyrzucania elementów bezużytecznych zostanie użyty.|  
|`STARTUP_HOARD_GC_VM`|Określa, że wyrzucanie elementów bezużytecznych zostanie zachowana, aby adres wirtualny używany.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Określa, że mieszanie hostingu interfejsu będzie niemożliwe.|  
|`STARTUP_LEGACY_IMPERSONATION`|Określa, że personifikacja nie powinna przepływać przez punkty asynchroniczne domyślnie.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Określa, że stos pełnego wątku nie powinien być ustalony podczas uruchamiania wątku.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Określa, że zarządzane personifikacje i personifikacje osiągnięte przez platformę wywołania będą przepływać przez punkty asynchroniczne. Domyślnie tylko zarządzane impersonacje będą przepływać przez punkty asynchroniczne.|  
|`STARTUP_TRIM_GC_COMMIT`|Określa, że wyrzucanie elementów bezużytecznych będzie używać mniej przydzielonych miejsc, gdy brakuje pamięci systemowej. Zobacz `gcTrimCommitOnLowMemory` w [Optymalizacja udostępnionej usługi hostingu internetowego](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Określa, że śledzenie zdarzeń dla Windows (ETW) jest włączone dla typowych zdarzeń środowiska wykonawczego języka. Począwszy od systemów Windows Vista, śledzenie zdarzeń jest zawsze włączone, więc ta flaga nie ma wpływu. Zobacz [Kontrolowanie logowania w programie .NET Framework](../../../../docs/framework/performance/controlling-logging.md).|  
|`STARTUP_ARM`|Określa, czy jest włączone monitorowanie zasobów domen aplikacji. Zobacz <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> właściwości i [ \<appdomainresourcemonitoring — > Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
