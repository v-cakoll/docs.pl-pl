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
ms.openlocfilehash: bc1d3ffc34cd74d68bf10cb677b68f0a75bb7c67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="startupflags-enumeration"></a>STARTUP_FLAGS — Wyliczenie
Zawiera wartości, które wskazują zachowanie uruchamiania środowisko uruchomieniowe języka wspólnego (CLR). Domyślnie, wyrzucanie elementów bezużytecznych jest niewspółbieżnego i tylko biblioteki klasy podstawowej są ładowane do obszaru neutralne dla domen.  
  
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
|`STARTUP_CONCURRENT_GC`|Określa, czy ma być używany współbieżne odzyskiwanie pamięci. Jeśli element wywołujący pyta o kompilacji serwera i współbieżne odzyskiwanie pamięci na komputerze z jednym procesorem, należy zamiast tego uruchomić są kompilacji stacji roboczej i niewspółbieżnego wyrzucanie elementów bezużytecznych. **Uwaga:** współbieżne odzyskiwanie pamięci nie jest obsługiwany w aplikacji, które są uruchomione WOW64 x86 emulator na 64-bitowe systemy, które implementują architektura Intel Itanium (nazywanych IA-64). Aby uzyskać więcej informacji o używaniu WOW64 na 64-bitowym systemie Windows, temacie [uruchomiona 32-bitowych aplikacji](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Określa, że ma miejsce tej optymalizacji modułu ładującego.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Określa, że zestawy nie są ładowane jako neutralne dla domen.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Określa, że wszystkie zestawy są ładowane jako neutralne dla domen.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Określa, że wszystkie zestawy o silnych nazwach są ładowane jako neutralne dla domen.|  
|`STARTUP_LOADER_SAFEMODE`|Określa, że zasady wersji środowiska CLR nie zostaną zastosowane do wersji przekazano. Zostanie załadowana dokładnej wersji określony środowiska CLR. Podkładka nie może oszacować zasady, aby określić najnowszą zgodnej wersji.|  
|`STARTUP_LOADER_SETPREFERENCE`|Określa, że preferowanego środowiska uruchomieniowego zostanie ustawiony, ale faktycznie nie jest uruchomiona.|  
|`STARTUP_SERVER_GC`|Określa użytą pamięci serwera.|  
|`STARTUP_HOARD_GC_VM`|Określa, że wyrzucanie elementów bezużytecznych zachowa wirtualny adres używany.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Określa, czy mieszanie interfejsu obsługi będzie niemożliwe.|  
|`STARTUP_LEGACY_IMPERSONATION`|Określa, czy personifikacja nie powinien przepływ między punktami asynchroniczne domyślnie.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Określa, że stosu wątku pełne nie powinny być zatwierdzone, gdy wątek zacznie działać.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Określa, że zarządzane impersonations i impersonations, stosując platformy wywoływał będą przepływać między punktami asynchronicznego. Domyślnie tylko zarządzane impersonations będą przepływać między punktami asynchronicznego.|  
|`STARTUP_TRIM_GC_COMMIT`|Określa, że wyrzucanie elementów bezużytecznych będzie używać mniej przydzielone miejsce, gdy jest za mało pamięci systemu. Zobacz `gcTrimCommitOnLowMemory` w [optymalizacji usługi hostingu sieci Web udostępnionego](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Określa, że śledzenie zdarzeń systemu Windows (ETW) jest włączone dla zdarzenia środowiska uruchomieniowego języka wspólnego. Począwszy od systemu Windows Vista, śledzenie zdarzeń jest zawsze włączony, dlatego ta flaga nie ma wpływu. Zobacz [kontrolowanie .NET Framework rejestrowania](../../../../docs/framework/performance/controlling-logging.md).|  
|`STARTUP_ARM`|Określa, czy jest włączone monitorowanie zasobów domen aplikacji. Zobacz <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> właściwości i [ \<appdomainresourcemonitoring — > elementu](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
