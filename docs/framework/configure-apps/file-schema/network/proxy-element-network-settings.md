---
title: <proxy>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154793"
---
# <a name="proxy-element-network-settings"></a>\<element> serwera proxy (ustawienia sieciowe)
Definiuje serwer proxy.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>proxy**

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
|`autoDetect`|Określa, czy serwer proxy jest wykrywany automatycznie. Wartością domyślną jest `unspecified`.|  
|`bypassonlocal`|Określa, czy serwer proxy jest pomijany dla zasobów lokalnych. Zasoby lokalne obejmują serwer`http://localhost` `http://loopback`lokalny `http://127.0.0.1`( , , lub )`http://webserver`i identyfikator URI bez kropki ( ). Wartością domyślną jest `unspecified`.|  
|`proxyaddress`|Określa identyfikator URI serwera proxy do użycia.|  
|`scriptLocation`|Określa lokalizację skryptu konfiguracji. Nie należy `bypassonlocal` używać atrybutu z tym atrybutem. |  
|`usesystemdefault`|Określa, czy mają być używane ustawienia serwera proxy programu Internet Explorer. Jeśli ustawiona na `true`, kolejne atrybuty zastąpią ustawienia serwera proxy programu Internet Explorer. Wartością domyślną jest `unspecified`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Konfiguruje serwer proxy Protokołu transferu hipertekstu (HTTP).|  
  
## <a name="text-value"></a>Wartość tekstowa  
  
## <a name="remarks"></a>Uwagi  
 Element `proxy` definiuje serwer proxy dla aplikacji. Jeśli w pliku konfiguracyjnym brakuje tego elementu, program .NET Framework użyje ustawień serwera proxy w programie Internet Explorer.  
  
 Wartość atrybutu `proxyaddress` powinna być dobrze sformułowanym wskaźnikiem jednolitego zasobu (URI).  
  
 Atrybut `scriptLocation` odnosi się do automatycznego wykrywania skryptów konfiguracji serwera proxy. Klasa <xref:System.Net.WebProxy> spróbuje zlokalizować skrypt konfiguracji (zwykle o nazwie Wpad.dat) po wybraniu opcji **Użyj skryptu konfiguracji automatycznej** w programie Internet Explorer. Jeśli `bypassonlocal` jest ustawiona `scriptLocation` na dowolną wartość, jest ignorowana.
  
 Użyj `usesystemdefault` atrybutu dla aplikacji .NET Framework w wersji 1.1, które są migrowane do wersji 2.0.  
  
 Wyjątek jest zgłaszany, `proxyaddress` jeśli atrybut określa nieprawidłowy domyślny serwer proxy. Właściwość <xref:System.Exception.InnerException%2A> na wyjątek powinien mieć więcej informacji na temat głównej przyczyny błędu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto wartości domyślnych z serwera proxy programu Internet Explorer, określono adres serwera proxy i pominięto serwer proxy dostępu lokalnego.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
