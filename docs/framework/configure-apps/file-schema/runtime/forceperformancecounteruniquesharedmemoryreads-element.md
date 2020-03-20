---
title: <forcePerformanceCounterUniqueSharedMemoryReads>, element
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154143"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryCzyty> element
Określa, czy plik PerfCounter.dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1.1 w celu określenia, czy dane licznika wydajności mają być ładowane z pamięci współużytkowanej specyficznej dla kategorii, czy z pamięci globalnej.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemory Odczyty>**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Wskazuje, czy plik PerfCounter.dll używa ustawienia rejestru CategoryOptions w celu określenia, czy dane licznika wydajności mają być ładowane z pamięci współużytkowanej specyficznej dla kategorii, czy z pamięci globalnej.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Plik PerfCounter.dll nie używa ustawienia rejestru CategoryOptions Jest to ustawienie domyślne.|  
|`true`|Plik PerfCounter.dll używa ustawienia rejestru CategoryOptions.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W wersjach programu .NET Framework przed programem .NET Framework 4 załadowana wersja pliku PerfCounter.dll odpowiadała czasowi wykonawczemu, który został załadowany w procesie. Jeśli na komputerze zainstalowano zarówno program .NET Framework w wersji 1.1, jak i program .NET Framework 2.0, aplikacja .NET Framework 1.1 załadowałaby wersję pliku .NET Framework 1.1 pliku PerfCounter.dll. Począwszy od programu .NET Framework 4, jest ładowana najnowsza zainstalowana wersja pliku PerfCounter.dll. Oznacza to, że aplikacja .NET Framework 1.1 załaduje wersję programu .NET Framework 4 pliku PerfCounter.dll, jeśli na komputerze jest zainstalowana gra .NET Framework 4.  
  
 Począwszy od programu .NET Framework 4, podczas korzystania z liczników wydajności, PerfCounter.dll sprawdza wpis rejestru CategoryOptions dla każdego dostawcy, aby ustalić, czy powinien on odczytywać z pamięci współużytkowanej specyficznej dla kategorii lub globalnej pamięci współdzielonej. .NET Framework 1.1 PerfCounter.dll nie odczytuje tego wpisu rejestru, ponieważ nie jest świadomy pamięci współużytkowanej specyficznej dla kategorii; zawsze odczytuje z globalnej pamięci współdzielonej.  
  
 W celu zapewnienia zgodności z powrotem plik .NET Framework 4 PerfCounter.dll nie sprawdza wpisu rejestru CategoryOptions podczas uruchamiania w aplikacji .NET Framework 1.1. Po prostu używa globalnej pamięci współużytkowanej, podobnie jak .NET Framework 1.1 PerfCounter.dll. Można jednak poinstruować plik .NET Framework 4 PerfCounter.dll, aby `<forcePerformanceCounterUniqueSharedMemoryReads>` sprawdziły ustawienie rejestru, włączając ten element.  
  
> [!NOTE]
> Włączenie `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu nie gwarantuje, że będzie używana pamięć współdzielona dla danej kategorii. Ustawienie włączone `true` powoduje tylko PerfCounter.dll do odwołania się do ustawienia rejestru CategoryOptions. Domyślnym ustawieniem dla CategoryOptions jest użycie pamięci współużytkowanej specyficznej dla kategorii; można jednak zmienić CategoryOptions, aby wskazać, że powinna być używana globalna pamięć współdzielona.  
  
 Klucz rejestru zawierający ustawienie CategoryOptions to HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance. Domyślnie CategoryOptions jest ustawiona na 3, co nakazuje PerfCounter.dll używać pamięci współużytkowanej specyficzne dla kategorii. Jeśli CategoryOptions jest ustawiona na 0, PerfCounter.dll używa globalnej pamięci współdzielonej. Dane wystąpienia będą ponownie używać tylko wtedy, gdy nazwa tworzonego wystąpienia jest identyczna z wystąpieniem, które jest ponownie używane. Wszystkie wersje będą mogły pisać do kategorii. Jeśli CategoryOptions jest ustawiona na 1, używana jest globalna pamięć współdzielona, ale dane wystąpienia mogą być ponownie użyte, jeśli nazwa kategorii ma taką samą długość jak kategoria, która jest ponownie używana.  
  
 Ustawienia 0 i 1 mogą prowadzić do przecieków pamięci i zapełnienia pamięci licznika wydajności.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak określić, że PerfCounter.dll powinien odwoływać się do wpisu rejestru CategoryOptions, aby ustalić, czy należy używać pamięci współużytkowanej specyficznej dla kategorii.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
