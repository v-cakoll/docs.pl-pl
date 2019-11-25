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
ms.openlocfilehash: 5f327a2bb4fe316497614f14669907d514c20654
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089192"
---
# <a name="proxy-element-network-settings"></a>\<> elementu proxy (Ustawienia sieci)
Definiuje serwer proxy.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**proxy >**

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
|`bypassonlocal`|Określa, czy serwer proxy jest pomijany dla zasobów lokalnych. Zasoby lokalne obejmują serwer lokalny (`http://localhost`, `http://loopback` lub `http://127.0.0.1`) i identyfikator URI bez kropki (`http://webserver`). Wartość domyślna to `unspecified`.|  
|`proxyaddress`|Określa identyfikator URI serwera proxy do użycia.|  
|`scriptLocation`|Określa lokalizację skryptu konfiguracji. Nie należy używać atrybutu `bypassonlocal` z tym atrybutem. |  
|`usesystemdefault`|Określa, czy mają być używane ustawienia serwera proxy programu Internet Explorer. Jeśli zostanie ustawiona na `true`, kolejne atrybuty przesłonią ustawienia proxy programu Internet Explorer. Wartość domyślna to `unspecified`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).|  
  
## <a name="text-value"></a>Wartość tekstowa  
  
## <a name="remarks"></a>Uwagi  
 Element `proxy` definiuje serwer proxy dla aplikacji. Jeśli w pliku konfiguracji brakuje tego elementu, .NET Framework będzie używać ustawień serwera proxy w programie Internet Explorer.  
  
 Wartość atrybutu `proxyaddress` powinna być poprawnie sformułowanym jednolitym wskaźnikiem zasobów (URI).  
  
 Atrybut `scriptLocation` odnosi się do automatycznego wykrywania skryptów konfiguracji serwera proxy. Klasa <xref:System.Net.WebProxy> będzie podejmować próby zlokalizowania skryptu konfiguracji (o nazwie WPAD. dat), gdy opcja **Użyj skryptu automatycznej konfiguracji** jest zaznaczona w programie Internet Explorer. Jeśli `bypassonlocal` jest ustawiona na dowolną wartość, `scriptLocation` jest ignorowana.
  
 Użyj `usesystemdefault` atrybutu dla aplikacji .NET Framework w wersji 1,1, które są migrowane do wersji 2,0.  
  
 Wyjątek jest generowany, jeśli atrybut `proxyaddress` określa nieprawidłowy domyślny serwer proxy. Właściwość <xref:System.Exception.InnerException%2A> na wyjątku powinna zawierać więcej informacji o głównej przyczynie błędu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie używane są wartości domyślne z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwer proxy na potrzeby dostępu lokalnego.  
  
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
- [Schemat ustawień sieci](index.md)
