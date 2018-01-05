---
title: "&lt;forceperformancecounteruniquesharedmemoryreads —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 602359b713adfd4adf90d3e18f5f434d50c92ef4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a>&lt;forceperformancecounteruniquesharedmemoryreads —&gt; — Element
Określa, czy PerfCounter.dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1.1 do określenia, czy ładowanie danych licznika wydajności z pamięci współużytkowanej specyficznego dla kategorii lub pamięci globalnej.  
  
 \<Konfiguracja >  
\<Runtime >  
\<forceperformancecounteruniquesharedmemoryreads — >  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Wskazuje, czy PerfCounter.dll używa CategoryOptions ustawienie rejestru w celu określenia, czy ładowanie danych licznika wydajności z pamięci współużytkowanej specyficznego dla kategorii lub globalnej pamięci.|  
  
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
 W wersjach programu .NET Framework, przed [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], uzgodnić wersji PerfCounter.dll, która została załadowana do środowiska wykonawczego, który został załadowany w procesie. Jeśli komputer ma zarówno programu .NET Framework w wersji 1.1 i [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] zainstalowany, aplikacji .NET Framework 1.1 czy ładowanie wersji .NET Framework 1.1 PerfCounter.dll. Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], najnowsza wersja zainstalowanego PerfCounter.dll został załadowany. Oznacza to, że załaduje aplikacji .NET Framework 1.1 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] wersji PerfCounter.dll Jeśli [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] jest zainstalowany na komputerze.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], gdy korzystanie z liczników wydajności, PerfCounter.dll sprawdza CategoryOptions wpisu rejestru dla każdego dostawcy określić, czy odczytywane z pamięci współużytkowanej specyficznego dla kategorii lub globalnej pamięci współdzielonej. .NET Framework 1.1 PerfCounter.dll nie odczytać tego wpisu rejestru, ponieważ nie został powiadomiony o pamięci współużytkowanej specyficznego dla kategorii; zawsze odczytuje z globalnej pamięci współdzielonej.  
  
 W celu zapewnienia zgodności z poprzednimi wersjami [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll nie sprawdza wpis rejestru CategoryOptions podczas uruchamiania aplikacji .NET Framework 1.1. Po prostu używa globalnej pamięci współdzielonej, podobnie jak PerfCounter.dll 1.1 programu .NET Framework. Jednak możesz wydać [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll, aby sprawdzić ustawienie rejestru, należy włączyć `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.  
  
> [!NOTE]
>  Włączanie `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu nie gwarantuje użytą pamięci współużytkowanej specyficznego dla kategorii. Aby włączyć ustawienie `true` tylko powoduje PerfCounter.dll do odwołania na ustawienie rejestru CategoryOptions. Ustawieniem domyślnym dla CategoryOptions jest użycie pamięci współużytkowanej specyficznego dla kategorii; można jednak zmienić CategoryOptions, aby wskazać, że powinny być używane globalnej pamięci współdzielonej.  
  
 Klucz rejestru, która zawiera ustawienie CategoryOptions jest HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance. Domyślnie CategoryOptions wynosi 3, który powoduje, że PerfCounter.dll do użycia pamięci współużytkowanej specyficznego dla kategorii. Jeśli CategoryOptions jest ustawiona na 0, PerfCounter.dll korzysta z globalnej pamięci współdzielonej. Dane wystąpienia zostanie ono użyte ponownie tylko wtedy, gdy nazwa wystąpienia, tworzony jest identyczny z wystąpieniem używane ponownie. Wszystkie wersje będzie można zapisywać do tej kategorii. Jeśli CategoryOptions jest ustawiona na 1, jest używany w globalnej pamięci współdzielonej, ale dane wystąpienia mogą być ponownie używane, jeśli nazwa kategorii jest taką samą długość jak kategoria używane ponownie.  
  
 Ustawienia wartości 0 i 1 może prowadzić do przecieki pamięci i wypełnianie zapasowej pamięci liczników wydajności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób określania, czy PerfCounter.dll powinien odwoływać się wpis rejestru CategoryOptions, aby określić, czy należy używać pamięci współużytkowanej specyficznego dla kategorii.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
