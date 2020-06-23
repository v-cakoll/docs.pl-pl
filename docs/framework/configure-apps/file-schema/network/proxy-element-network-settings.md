---
title: <proxy>, element (ustawienia sieci)
description: <proxy>Element ustawienia sieci definiuje opcje serwera proxy w .NET Framework. Ten artykuł zawiera przykład.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 8ae30b8c29dcf3aaa183ff295c7ee8592322797f
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141784"
---
# <a name="proxy-element-network-settings"></a>\<proxy>, element (ustawienia sieci)
Definiuje serwer proxy.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a>Składnia  
  
```xml  
<proxy
  autoDetect="True|False|Unspecified"
  bypassonlocal="True|False|Unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="True|False|Unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`autoDetect`|Określa, czy serwer proxy jest wykrywany automatycznie. Wartość domyślna to `Unspecified`.|  
|`bypassonlocal`|Określa, czy serwer proxy jest pomijany dla zasobów lokalnych. Zasoby lokalne obejmują serwer lokalny ( `http://localhost` , `http://loopback` lub `http://127.0.0.1` ) oraz identyfikator URI bez kropki ( `http://webserver` ). Wartość domyślna to `Unspecified`.|  
|`proxyaddress`|Określa identyfikator URI serwera proxy do użycia.|  
|`scriptLocation`|Określa lokalizację skryptu konfiguracji. Nie należy używać `bypassonlocal` atrybutu z tym atrybutem. |  
|`usesystemdefault`|Określa, czy mają być używane ustawienia serwera proxy programu Internet Explorer. Jeśli jest ustawiona na `True` , kolejne atrybuty zastąpią ustawienia proxy programu Internet Explorer. Wartość domyślna to `Unspecified`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).|  
  
## <a name="text-value"></a>Wartość tekstowa  
  
## <a name="remarks"></a>Uwagi  
 `proxy`Element definiuje serwer proxy dla aplikacji. Jeśli w pliku konfiguracji brakuje tego elementu, .NET Framework będzie używać ustawień serwera proxy w programie Internet Explorer.  
  
 Wartość `proxyaddress` atrybutu powinna być poprawnie sformułowanym jednolitym wskaźnikiem zasobów (URI).  
  
 Ten `scriptLocation` atrybut odnosi się do automatycznego wykrywania skryptów konfiguracji serwera proxy. <xref:System.Net.WebProxy>Klasa podejmie próbę zlokalizowania skryptu konfiguracji (o nazwie WPAD. dat), gdy opcja **Użyj skryptu automatycznej konfiguracji** jest zaznaczona w programie Internet Explorer. Jeśli `bypassonlocal` jest ustawiona na dowolną wartość, `scriptLocation` jest ignorowana.
  
 Użyj `usesystemdefault` atrybutu dla aplikacji .NET Framework w wersji 1,1, które są migrowane do wersji 2,0.  
  
 Wyjątek jest generowany, jeśli `proxyaddress` atrybut określa nieprawidłowy domyślny serwer proxy. <xref:System.Exception.InnerException%2A>Właściwość wyjątku powinna zawierać więcej informacji o głównej przyczynie błędu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie używane są wartości domyślne z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwer proxy na potrzeby dostępu lokalnego.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
