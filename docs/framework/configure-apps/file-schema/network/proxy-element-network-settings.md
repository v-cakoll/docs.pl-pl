---
title: <proxy> Element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 8df9bbf2615776c2e023f03401785da95b2226eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204825"
---
# <a name="proxy-element-network-settings"></a>\<Serwer proxy >, Element (ustawienia sieci)
Określa serwer proxy.  
  
 \<Konfiguracja >  
\<system.net>  
\<defaultProxy>  
\<proxy>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`autoDetect`|Określa, czy serwer proxy jest wykrywany automatycznie. Wartość domyślna to `unspecified`.|  
|`bypassonlocal`|Określa, czy serwer proxy jest pomijane dla zasobów lokalnych. Lokalne zasoby obejmują serwer lokalny (`http://localhost`, `http://loopback`, lub `http://127.0.0.1`) i identyfikator URI bez kropki (`http://webserver`). Wartość domyślna to `unspecified`.|  
|`proxyaddress`|Określa identyfikator URI do użycia serwera proxy.|  
|`scriptLocation`|Określa lokalizację skryptu konfiguracji. Nie używaj `bypassonlocal` atrybutu z tego atrybutu. |  
|`usesystemdefault`|Określa, czy ma być używany program Internet Explorer, ustawienia serwera proxy. Jeśli ustawiono `true`, kolejne atrybutów spowoduje przesłonięcie ustawień serwera proxy programu Internet Explorer. Wartość domyślna to `unspecified`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).|  
  
## <a name="text-value"></a>Wartość tekstowa  
  
## <a name="remarks"></a>Uwagi  
 `proxy` Element definiuje serwera proxy dla aplikacji. W przypadku braku tego elementu z pliku konfiguracji .NET Framework będą używać ustawień serwera proxy w programie Internet Explorer.  
  
 Wartość `proxyaddress` atrybut powinien być poprawnie sformułowany Uniform Resource Indicator (URI).  
  
 `scriptLocation` Atrybut odwołuje się do automatycznego wykrywania skrypty konfiguracji serwera proxy. <xref:System.Net.WebProxy> Klasy będzie podejmować próby zlokalizowania skryptu konfiguracji (zwykle o nazwie Wpad.dat) po **Użyj skryptu automatycznej konfiguracji** opcja jest zaznaczona w programie Internet Explorer. Jeśli `bypassonlocal` jest ustawiona na jakąkolwiek wartość `scriptLocation` jest ignorowana.
  
 Użyj `usesystemdefault` atrybutu dla aplikacji w wersji 1.1 programu .NET Framework, które jest przeprowadzana migracja do wersji 2.0.  
  
 Wyjątek jest generowany, jeśli `proxyaddress` atrybut określa nieprawidłowy domyślny serwer proxy. <xref:System.Exception.InnerException%2A> Właściwość w drodze wyjątku powinien mieć więcej informacji na temat przyczyny błędu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa ustawień domyślnych z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwera proxy dla dostępu do lokalnego.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
