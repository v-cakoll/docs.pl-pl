---
title: Konfigurowanie aplikacji internetowych
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7c4755e13202f60df5704f6faefb3b279a30ce58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-internet-applications"></a>Konfigurowanie aplikacji internetowych
[ \<System.Net > (ustawienia sieciowe) Element](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element konfiguracji zawiera informacje o konfiguracji sieci dla aplikacji. Przy użyciu [ \<system.Net > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) elementu, można ustawić serwerów proxy, Ustaw połączenie z parametrami zarządzania i dołączenie niestandardowe moduły uwierzytelniania i żądania do aplikacji.  
  
 [ \<DefaultProxy — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element definiuje zwrócony przez serwer proxy `GlobalProxySelection` klasy. Wszelkie <xref:System.Net.HttpWebRequest> , która nie ma własną <xref:System.Net.HttpWebRequest.Proxy%2A> właściwość o określonej wartości używany domyślny serwer proxy. Poza ustawieniem adres serwera proxy, można utworzyć listę adresów serwerów, które nie będzie używać serwera proxy, i może oznaczać, że nie należy używać serwera proxy dla adresów lokalnych.  
  
 Należy pamiętać, że ustawienia programu Microsoft Internet Explorer są łączone przy użyciu ustawień konfiguracyjnych z pierwszeństwo przed ostatnim z argumentami.  
  
 Poniższy przykład ustawia domyślny serwer proxy adres serwera http://proxyserver, wskazuje, że serwer proxy nie powinna być używana dla adresów lokalnych i określa, że wszystkie żądania kierowane do serwerów znajdujących się w domenie contoso.com, należy pominąć serwer proxy.  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 Użyj [ \<connectionmanagement — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element, aby skonfigurować liczbę połączeń trwałych, które można wprowadzić do określonego serwera lub na inne serwery. Poniższy przykład konfiguruje aplikację do używania dwóch połączeń trwałych www.contoso.com serwera, cztery trwałego połączenia z serwerem o adresie IP 192.168.1.2 i jedno połączenie trwałe na inne serwery.  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 Moduły uwierzytelniania niestandardowego są skonfigurowane przy użyciu [ \<authenticationModules — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) elementu. Moduły uwierzytelniania niestandardowego musi implementować <xref:System.Net.IAuthenticationModule> interfejsu.  
  
 Poniższy przykład konfiguruje moduł uwierzytelniania niestandardowego.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Można użyć [ \<webRequestModules — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element, aby skonfigurować aplikację do użycia niestandardowe moduły protokołem na żądanie informacji z zasobów w Internecie. Określone moduły musi implementować <xref:System.Net.IWebRequestCreate> interfejsu. Można zastąpić domyślny HTTP, HTTPS i moduły żądania pliku, określając niestandardowego modułu w pliku konfiguracji, jak w poniższym przykładzie.  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Schemat ustawień sieci](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<system.Net > (ustawienia sieciowe) — Element](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
