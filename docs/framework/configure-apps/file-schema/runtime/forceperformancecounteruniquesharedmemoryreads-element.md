---
title: <forcePerformanceCounterUniqueSharedMemoryReads>, element
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e9073e48141bc6895d00c773c2d3d2cfeb260f6
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456464"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Element
Określa, czy PerfCounter.dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1.1 do określenia, czy można załadować danych licznika wydajności z pamięci współużytkowanej specyficznego dla kategorii lub globalnej pamięci.  
  
 \<Konfiguracja >  
\<runtime>  
\<forcePerformanceCounterUniqueSharedMemoryReads>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Wskazuje, czy PerfCounter.dll używa CategoryOptions ustawienia rejestru w celu ustalenia, czy można załadować danych licznika wydajności z pamięci współużytkowanej specyficznego dla kategorii lub pamięci globalnej.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|PerfCounter.dll nie używa CategoryOptions rejestru to ustawienie jest ustawieniem domyślnym.|  
|`true`|PerfCounter.dll użyj ustawienia rejestru CategoryOptions.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W wersjach programu .NET Framework przed [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], wersja PerfCounter.dll, który został załadowany odpowiadał do środowiska uruchomieniowego, który został załadowany w procesie. Jeśli komputer ma zarówno programu .NET Framework w wersji 1.1 i [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] zainstalowany, aplikacji programu .NET Framework 1.1 będzie załadować wersji .NET Framework 1.1 PerfCounter.dll. Począwszy od programu .NET Framework 4, zainstalowaną najnowszą wersję PerfCounter.dll jest ładowany. Oznacza to, że aplikacji .NET Framework 1.1 załaduje PerfCounter.dll w wersji .NET Framework 4, jeśli programu .NET Framework 4 jest zainstalowana na komputerze.  
  
 Zaczynając od programu .NET Framework 4, podczas korzystania z liczników wydajności, PerfCounter.dll sprawdza, czy wpis rejestru CategoryOptions dla każdego dostawcy ustalić, czy powinni przeczytać z pamięci współużytkowanej specyficznego dla kategorii lub globalnej pamięci współdzielonej. PerfCounter.dll 1.1 programu .NET Framework nie odczytać ten wpis rejestru, ponieważ nie ma informacji o pamięci współużytkowanej specyficznego dla kategorii; zawsze odczytuje z globalnej pamięci współdzielonej.  
  
 W celu zapewnienia zgodności z poprzednimi wersjami PerfCounter.dll 4 programu .NET Framework nie sprawdza wpis rejestru CategoryOptions, podczas uruchamiania w aplikacji .NET Framework 1.1. Po prostu używa globalnej pamięci współdzielonej, podobnie jak PerfCounter.dll 1.1 programu .NET Framework. Jednak można nakazać PerfCounter.dll 4 .NET Framework, aby sprawdzić ustawienia rejestru, włączając `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.  
  
> [!NOTE]
>  Włączanie `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu nie gwarantuje posłuży pamięci współużytkowanej w poszczególnych kategoriach. Ustawienie jest włączone do `true` tylko powoduje, że PerfCounter.dll k odkazu CategoryOptions ustawienie rejestru. Ustawieniem domyślnym dla CategoryOptions jest użycie pamięci współużytkowanej specyficznego dla kategorii; można jednak zmienić CategoryOptions, aby wskazać, że globalne pamięci współużytkowanej powinien być używany.  
  
 Klucz rejestru, który zawiera ustawienia CategoryOptions jest HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance. Domyślnie CategoryOptions jest równa 3, który powoduje, że PerfCounter.dll do użycia pamięci współużytkowanej w poszczególnych kategoriach. Jeśli CategoryOptions jest równa 0, PerfCounter.dll korzysta z globalnej pamięci współdzielonej. Dane wystąpienia zostanie ponownie użyty tylko wtedy, gdy nazwę wystąpienia, tworzona jest taka sama jak wystąpienie używane ponownie. Wszystkie wersje będą mogli zapisywać do tej kategorii. Jeśli CategoryOptions jest ustawiona na 1, jest używany w globalnej pamięci współdzielonej, ale dane wystąpienia mogą być ponownie używane, jeśli nazwa kategorii jest tę samą długość jak kategoria używane ponownie.  
  
 Ustawienia 0 i 1 może prowadzić do przecieków pamięci i wypełnianie się pamięci licznika wydajności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że PerfCounter.dll powinny odwoływać się CategoryOptions wpis rejestru w celu ustalenia, czy należy używać w niej Pamięć współużytkowana specyficznego dla kategorii.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
