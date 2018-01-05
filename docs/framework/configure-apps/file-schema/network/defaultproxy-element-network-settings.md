---
title: "&lt;defaultProxy —&gt; — Element (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d0b09f5c845fc9a18c2a1dd919272c2924478eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultproxygt-element-network-settings"></a>&lt;defaultProxy —&gt; — Element (ustawienia sieciowe)
Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).  
  
 \<Konfiguracja >  
\<System.NET >  
\<defaultProxy — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
      <defaultProxy  
        enabled="true|false"  
        useDefaultCredentials="true|false">  
           <bypasslist> … </bypasslist>  
           <proxy> … </proxy>  
           <module> … </module>  
      </defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|`enabled`|Określa, czy jest używany serwer proxy sieci web. Wartość domyślna to `true`.|  
|`useDefaultCredentials`|Określa, czy dostępu do serwera proxy sieci web są używane domyślne poświadczenia dla tego hosta. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[bypasslist —](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Zawiera zestaw wyrażeń regularnych, opisujących adresów, które nie korzystają z serwera proxy.|  
|[Moduł](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|Dodaje nowy moduł serwera proxy aplikacji.|  
|[Serwer proxy](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|Definiuje serwera proxy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli defaultProxy — element jest pusta, ustawienia serwera proxy w programie Internet Explorer będzie używany. To zachowanie różni się od programu .NET Framework w wersji 1.1.  
  
 Jest zwracany wyjątek, jeśli [modułu](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element określa niepublicznego typu, nie jest pochodny typ <xref:System.Net.IWebProxy> klasy wystąpił wyjątek z domyślny konstruktor obiektu lub wystąpił wyjątek podczas Pobieranie określony system domyślny serwer proxy. <xref:System.Exception.InnerException%2A> Na wyjątku powinna mieć więcej informacji na temat przyczynę błędu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa ustawień domyślnych z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwera proxy na potrzeby dostępu lokalnego i contoso.com.  
  
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
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
