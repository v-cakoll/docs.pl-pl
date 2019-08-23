---
title: <forcePerformanceCounterUniqueSharedMemoryReads>, element
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29fbe951b955c97e39ebaf80885729a45c1a3fd7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927395"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Element
Określa, czy funkcja kończąca PerfCounter. dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1,1, aby określić, czy ładować dane liczników wydajności z pamięci współdzielonej określonej dla kategorii, czy z pamięci globalnej.  
  
 \<> konfiguracji  
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
|`enabled`|Atrybut wymagany.<br /><br /> Wskazuje, czy funkcja kończąca PerfCounter. dll używa ustawienia rejestru CategoryOptions w celu ustalenia, czy dane liczników wydajności mają być ładowane z pamięci współdzielonej określonej dla kategorii, czy z pamięci globalnej.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Funkcja kończąca PerfCounter. dll nie używa ustawienia rejestru CategoryOptions jest to ustawienie domyślne.|  
|`true`|Funkcja kończąca PerfCounter. dll używa ustawienia rejestru CategoryOptions.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W wersjach .NET Framework przed .NET Framework 4, wersja funkcja kończąca PerfCounter. dll, która została załadowana, odpowiada środowisko uruchomieniowe, które zostało załadowane w procesie. Jeśli na komputerze zainstalowano zarówno .NET Framework w wersji 1,1, jak i .NET Framework 2,0, aplikacja .NET Framework 1,1 załaduje .NET Framework 1,1 wersji funkcja kończąca PerfCounter. dll. Począwszy od .NET Framework 4, zostanie załadowana Najnowsza zainstalowana wersja funkcja kończąca PerfCounter. dll. Oznacza to, że aplikacja .NET Framework 1,1 będzie ładować wersję programu funkcja kończąca PerfCounter. dll w wersji .NET Framework 4, jeśli na komputerze zainstalowano .NET Framework 4.  
  
 Począwszy od .NET Framework 4, podczas zużywania liczników wydajności, funkcja kończąca PerfCounter. dll sprawdza wpis rejestru CategoryOptions dla każdego dostawcy, aby określić, czy powinien on zostać odczytany z udostępnionej pamięci lub globalnej pamięci udostępnionej. .NET Framework 1,1 funkcja kończąca PerfCounter. dll nie odczytuje tego wpisu rejestru, ponieważ nie ma on informacji o pamięci współdzielonej określonej dla kategorii; zawsze odczytuje z globalnej pamięci współdzielonej.  
  
 W celu zapewnienia zgodności z poprzednimi wersjami .NET Framework 4 funkcja kończąca PerfCounter. dll nie sprawdza wpisu rejestru CategoryOptions w przypadku uruchamiania w aplikacji .NET Framework 1,1. Po prostu używa globalnej pamięci współdzielonej, podobnie jak .NET Framework 1,1 funkcja kończąca PerfCounter. dll. Można jednak wydać polecenie .NET Framework 4 funkcja kończąca PerfCounter. dll, aby sprawdzić ustawienie rejestru przez włączenie `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.  
  
> [!NOTE]
> `<forcePerformanceCounterUniqueSharedMemoryReads>` Włączenie elementu nie gwarantuje, że zostanie użyta udostępniona pamięć określona w kategorii. Ustawienie "Enabled `true` " powoduje tylko, że funkcja kończąca PerfCounter. dll odwołuje się do ustawienia rejestru CategoryOptions. Ustawieniem domyślnym dla CategoryOptions jest użycie pamięci współużytkowanej określonej dla kategorii; można jednak zmienić CategoryOptions, aby wskazać, że powinna być używana globalna pamięć współdzielona.  
  
 Klucz rejestru zawierający ustawienie CategoryOptions jest HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\< CategoryName \Performance.\> Domyślnie CategoryOptions jest ustawiana na 3, która instruuje funkcja kończąca PerfCounter. dll, aby użyć udostępnionej pamięci określonej dla kategorii. Jeśli wartość CategoryOptions jest równa 0, funkcja kończąca PerfCounter. dll używa globalnej pamięci współdzielonej. Dane wystąpienia będą ponownie używane tylko wtedy, gdy nazwa tworzonego wystąpienia jest identyczna z ponownie używanym wystąpieniem. Wszystkie wersje będą mogły zapisywać w kategorii. Jeśli CategoryOptions jest ustawiona na 1, używana jest globalna pamięć współdzielona, ale dane wystąpienia mogą być ponownie używane, jeśli nazwa kategorii ma taką samą długość jak kategoria używana ponownie.  
  
 Ustawienia 0 i 1 mogą prowadzić do przecieków pamięci i wypełniania pamięci licznika wydajności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że funkcja kończąca PerfCounter. dll powinna odwoływać się do wpisu rejestru CategoryOptions, aby określić, czy powinien on używać pamięci współdzielonej specyficznej dla kategorii.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
