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
ms.openlocfilehash: ee4dc87383153ae4e8df0a3bed7cce5220e65405
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048634"
---
# <a name="configuring-internet-applications"></a>Konfigurowanie aplikacji internetowych
Element konfiguracji [ \<system.Net> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/system-net-element-network-settings.md) zawiera informacje o konfiguracji sieci dla aplikacji. Korzystając z elementu [ \<system.Net> (Ustawienia sieciowe),](../configure-apps/file-schema/network/system-net-element-network-settings.md) można ustawić serwery proxy, ustawić parametry zarządzania połączeniami oraz uwzględnić niestandardowe moduły uwierzytelniania i żądania w aplikacji.  
  
 [ \<DefaultProxy> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element definiuje serwer proxy `GlobalProxySelection` zwrócony przez klasę. Każdy, <xref:System.Net.HttpWebRequest> kto nie <xref:System.Net.HttpWebRequest.Proxy%2A> ma własnej właściwości ustawionej na określoną wartość, używa domyślnego serwera proxy. Oprócz ustawienia adresu serwera proxy można utworzyć listę adresów serwera, które nie będą używać serwera proxy, i można wskazać, że serwer proxy nie powinien być używany dla adresów lokalnych.  
  
 Należy pamiętać, że ustawienia programu Microsoft Internet Explorer są połączone z ustawieniami konfiguracji, przy czym pierwszeństwo mają te ostatnie.  
  
 Poniższy przykład ustawia domyślny `http://proxyserver`adres serwera proxy na , wskazuje, że serwer proxy nie powinien być używany dla adresów lokalnych i określa, że wszystkie żądania do serwerów znajdujących się w domenie contoso.com powinny pomijać serwer proxy.  
  
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
  
 Użyj elementu [ \<connectionManagement> Element (Ustawienia sieciowe),](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) aby skonfigurować liczbę trwałych połączeń, które mogą być nawiązywane z określonym serwerem lub wszystkimi innymi serwerami. Poniższy przykład konfiguruje aplikację do używania `www.contoso.com`dwóch trwałych połączeń z serwerem , czterech trwałych połączeń z serwerem o adresie IP 192.168.1.2 i jednego połączenia trwałego ze wszystkimi innymi serwerami.  
  
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
  
 Niestandardowe moduły uwierzytelniania są konfigurowane za pomocą elementu [ \<authenticationModules> Element (Ustawienia sieciowe).](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) Niestandardowe moduły uwierzytelniania muszą implementować <xref:System.Net.IAuthenticationModule> interfejs.  
  
 W poniższym przykładzie konfiguruje niestandardowy moduł uwierzytelniania.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Za pomocą elementu [ \<webRequestModules> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) można skonfigurować aplikację do używania niestandardowych modułów specyficznych dla protokołu do żądania informacji z zasobów internetowych. Określone moduły muszą <xref:System.Net.IWebRequestCreate> implementować interfejs. Domyślne moduły żądań HTTP, HTTPS i plików można zastąpić, określając moduł niestandardowy w pliku konfiguracyjnym, tak jak w poniższym przykładzie.  
  
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

- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Schemat ustawień sieci](../configure-apps/file-schema/network/index.md)
- [\<system.Net element> (ustawienia sieciowe)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
