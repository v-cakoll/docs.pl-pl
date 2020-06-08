---
title: Konfigurowanie aplikacji internetowych
description: Dowiedz się, jak za pomocą elementu <system.Net> skonfigurować aplikacje internetowe w .NET Framework. Ten artykuł zawiera przykładowy kod.
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
ms.openlocfilehash: 760a4ac7cec9abeabfc372c3be5bd3860a6fb03a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502642"
---
# <a name="configuring-internet-applications"></a>Konfigurowanie aplikacji internetowych
Element konfiguracji [ \<system.Net> element (Ustawienia sieci)](../configure-apps/file-schema/network/system-net-element-network-settings.md) zawiera informacje o konfiguracji sieci dla aplikacji. Za pomocą elementu [ \<system.Net> (ustawień sieciowych)](../configure-apps/file-schema/network/system-net-element-network-settings.md) można ustawić serwery proxy, ustawić parametry zarządzania połączeniami i dołączyć niestandardowe moduły uwierzytelniania i żądania w aplikacji.  
  
 Element [ \<defaultProxy> (Ustawienia sieci)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) definiuje serwer proxy zwracany przez `GlobalProxySelection` klasę. Wszystkie <xref:System.Net.HttpWebRequest> właściwości, które nie mają przypisanej <xref:System.Net.HttpWebRequest.Proxy%2A> do określonej wartości, używają domyślnego serwera proxy. Oprócz ustawiania adresu serwera proxy można utworzyć listę adresów serwerów, które nie będą używać serwera proxy, i można wskazać, że serwer proxy nie powinien być używany dla adresów lokalnych.  
  
 Należy pamiętać, że ustawienia programu Microsoft Internet Explorer są łączone z ustawieniami konfiguracji z ostatnim pierwszeństwem.  
  
 Poniższy przykład ustawia domyślny adres serwera proxy na `http://proxyserver` , wskazuje, że serwer proxy nie powinien być używany do adresów lokalnych, i określa, że wszystkie żądania kierowane do serwerów znajdujących się w domenie contoso.com powinny ominąć serwer proxy.  
  
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
  
 Aby skonfigurować liczbę połączeń trwałych, które mogą zostać wprowadzone do określonego serwera lub do wszystkich innych serwerów, użyj elementu [ \<connectionManagement> (ustawień sieciowych)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) . Poniższy przykład konfiguruje aplikację do używania dwóch trwałych połączeń z serwerem `www.contoso.com` , czterech stałych połączeń z serwerem z adresem IP 192.168.1.2 i jednego połączenia trwałego z innymi serwerami.  
  
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
  
 Niestandardowe moduły uwierzytelniania są konfigurowane przy użyciu elementu [ \<authenticationModules> (Ustawienia sieci)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) . Niestandardowe moduły uwierzytelniania muszą implementować <xref:System.Net.IAuthenticationModule> interfejs.  
  
 Poniższy przykład służy do konfigurowania niestandardowego modułu uwierzytelniania.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Za pomocą elementu [ \<webRequestModules> (ustawień sieci)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) można skonfigurować aplikację do używania niestandardowych modułów specyficznych dla protokołu, aby żądać informacji z zasobów internetowych. Określone moduły muszą implementować <xref:System.Net.IWebRequestCreate> interfejs. Można zastąpić domyślne moduły HTTP, HTTPS i File Request przez określenie niestandardowego modułu w pliku konfiguracji, jak w poniższym przykładzie.  
  
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

- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Schemat ustawień sieci](../configure-apps/file-schema/network/index.md)
- [\<system.Net>— Element (Ustawienia sieci)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
