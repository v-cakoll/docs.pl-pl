---
title: <defaultProxy>, element (ustawienia sieci)
description: <defaultProxy>Element ustawienia sieci konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol) w .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 915fdc96dbd4d417f9c9e6aa3ff96de3026491ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504605"
---
# <a name="defaultproxy-element-network-settings"></a>\<defaultProxy>, element (ustawienia sieci)
Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|`enabled`|Określa, czy używany jest serwer proxy sieci Web. Wartość domyślna to `true`.|  
|`useDefaultCredentials`|Określa, czy domyślne poświadczenia dla tego hosta są używane w celu uzyskania dostępu do serwera proxy sieci Web. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.|  
|[elementu](module-element-network-settings.md)|Dodaje nowy moduł proxy do aplikacji.|  
|[proxy](proxy-element-network-settings.md)|Definiuje serwer proxy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli element defaultProxy jest pusty, zostaną użyte ustawienia serwera proxy z programu Internet Explorer. To zachowanie różni się od wersji 1,1 .NET Framework.  
  
 Wyjątek jest zgłaszany, jeśli element [module](module-element-network-settings.md) określa typ niepubliczny, typ nie jest wyprowadzany z <xref:System.Net.IWebProxy> klasy, wystąpił wyjątek z konstruktora bez parametrów tego obiektu lub wystąpił wyjątek podczas pobierania domyślnego serwera proxy określonego przez system. <xref:System.Exception.InnerException%2A>Właściwość wyjątku powinna zawierać więcej informacji o głównej przyczynie błędu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie używane są wartości domyślne z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwer proxy na potrzeby lokalnego dostępu i contoso.com.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
