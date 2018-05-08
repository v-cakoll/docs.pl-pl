---
title: '&lt;gcconcurrent —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee00c3a307523d2cae831274630ad6828cd9daf6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltgcconcurrentgt-element"></a>&lt;gcconcurrent —&gt; — Element
Określa, czy środowisko uruchomieniowe języka wspólnego wyrzucanie elementów bezużytecznych jest uruchamiana w oddzielnym wątku.  
  
 \<Konfiguracja >  
\<runtime>  
\<gcconcurrent — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe działa jednocześnie wyrzucanie elementów bezużytecznych.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie równoczesne wyrzucanie elementów bezużytecznych.|  
|`true`|Uruchamia współbieżnego wyrzucania elementów bezużytecznych. Domyślnie włączone.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Przed programu .NET Framework 4 stacji roboczej wyrzucanie elementów bezużytecznych obsługiwane współbieżne odzyskiwanie pamięci, wykonać wyrzucanie elementów bezużytecznych w tle w oddzielnym wątku. W .NET Framework 4 współbieżne odzyskiwanie pamięci został zastąpiony przez wykaz Globalny, który wykonuje także wyrzucanie elementów bezużytecznych w tle w oddzielnym wątku tła. Począwszy od programu .NET Framework 4.5, pamięci w tle stały się dostępne w pamięci serwera. `<gcConcurrent>` Element określa, czy środowisko uruchomieniowe wykonuje albo równoczesnych lub tło wyrzucanie elementów bezużytecznych, jeśli jest dostępna lub czy wykonuje odzyskiwanie pamięci na pierwszym planie.  
  
> [!WARNING]
>  Począwszy od programu .NET Framework 4, współbieżne odzyskiwanie pamięci jest zastępowany przez odzyskiwanie pamięci w tle. Warunki *równoczesnych* i *tła* są używane zamiennie w dokumentacji programu .NET Framework. Aby wyłączyć odzyskiwanie pamięci w tle, należy użyć `<gcConcurrent>` elementu, zgodnie z opisem w tym artykule.  
  
 Domyślnie używa środowiska wykonawczego równoczesnych oraz odzyskiwanie pamięci w tle, który jest zoptymalizowana pod kątem opóźnień. Jeśli aplikacja wymaga interakcji z użytkownikiem duże, pozostaw współbieżne odzyskiwanie pamięci włączone, aby zminimalizować czas wstrzymania aplikacji do wykonywania wyrzucanie elementów bezużytecznych. Jeśli ustawisz `enabled` atrybutu `<gcConcurrent>` elementu `false`, środowisko uruchomieniowe używa niewspółbieżnego pamięci, która jest zoptymalizowana pod kątem przepływności. Następujący plik konfiguracji wyłącza odzyskiwanie pamięci w tle.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 W przypadku `<gcConcurrentSetting>` ustawienia w pliku konfiguracji komputera, określa wartość domyślną dla wszystkich aplikacji .NET Framework. Ustawienie pliku konfiguracji maszyny zastępuje ustawienie pliku konfiguracji aplikacji.  
  
 Aby uzyskać więcej informacji na temat równoczesnych i odzyskiwanie pamięci w tle, zobacz sekcję "współbieżne odzyskiwanie pamięci" w [podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../../../docs/standard/garbage-collection/fundamentals.md) tematu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia włączenie współbieżne odzyskiwanie pamięci.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Podstawy dotyczące odzyskiwania pamięci](../../../../../docs/standard/garbage-collection/fundamentals.md)
