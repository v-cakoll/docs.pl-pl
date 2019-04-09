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
ms.openlocfilehash: ddc4717c873e65311a8502e66f3edaf39dd89ff9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133805"
---
# <a name="configuring-internet-applications"></a>Konfigurowanie aplikacji internetowych
[ \<Przestrzeni nazw system.Net >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element konfiguracji zawiera informacje o konfiguracji sieci dla aplikacji. Przy użyciu [ \<przestrzeni nazw system.Net >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) elementu, ustaw serwerów proxy, Ustaw połączenie z parametrami zarządzania i obejmują moduły niestandardowe uwierzytelnianie i żądanie w aplikacji.  
  
 [ \<DefaultProxy >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element definiuje zwrócony przez serwer proxy `GlobalProxySelection` klasy. Wszelkie <xref:System.Net.HttpWebRequest> , nie ma swój własny <xref:System.Net.HttpWebRequest.Proxy%2A> właściwość o określonej wartości korzysta z domyślnego serwera proxy. Oprócz skonfigurowania adres serwera proxy, można utworzyć listę adresów serwerów, które nie będzie używać serwera proxy, a może wskazywać, że nie należy używać serwera proxy dla adresów lokalnych.  
  
 Jest to należy zwrócić uwagę, czy ustawienia programu Microsoft Internet Explorer są łączone z ustawienia konfiguracji z pierwszeństwem ostatnie wykonywanie.  
  
 Poniższy przykład ustawia domyślny serwer proxy adres serwera `http://proxyserver`, wskazuje, że serwer proxy nie powinna być używana dla adresów lokalnych i określa, czy wszystkich żądań do serwerów znajdujących się w domenie contoso.com, należy pominąć serwer proxy.  
  
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
  
 Użyj [ \<connectionManagement >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element, aby skonfigurować liczbę połączeń trwałych, które mogą być wykonane na określonym serwerze lub na inne serwery. Poniższy przykład umożliwia skonfigurowanie aplikacji do korzystania z dwóch trwałego połączenia z serwerem `www.contoso.com`, cztery trwałego połączenia z serwerem o adresie IP 192.168.1.2 i jedno połączenie trwałe na inne serwery.  
  
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
  
 Uwierzytelnianie niestandardowe moduły są skonfigurowane przy użyciu [ \<authenticationModules >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) elementu. Moduły niestandardowe uwierzytelnianie musi implementować <xref:System.Net.IAuthenticationModule> interfejsu.  
  
 Poniższy przykład umożliwia skonfigurowanie uwierzytelniania niestandardowego modułu.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Możesz użyć [ \<webRequestModules >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) elementu, aby skonfigurować aplikację na potrzeby niestandardowe moduły oparte na protokole żądanie informacji z zasobów internetowych. Określone moduły muszą implementować <xref:System.Net.IWebRequestCreate> interfejsu. Można zastąpić domyślny HTTP, HTTPS i pliku żądania modułów, określając niestandardowego modułu w pliku konfiguracji, jak w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Programowanie dla sieci w .NET Framework](../../../docs/framework/network-programming/index.md)
- [Schemat ustawień sieci](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [\<przestrzeni nazw system.Net >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
