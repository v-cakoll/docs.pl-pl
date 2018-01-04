---
title: Konfigurowanie aplikacji internetowych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6891f6e8081862fdbf0e9423a6b74fbea0d6e149
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="62bd6-102">Konfigurowanie aplikacji internetowych</span><span class="sxs-lookup"><span data-stu-id="62bd6-102">Configuring Internet Applications</span></span>
<span data-ttu-id="62bd6-103">[ \<System.Net > (ustawienia sieciowe) Element](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element konfiguracji zawiera informacje o konfiguracji sieci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="62bd6-103">The [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="62bd6-104">Przy użyciu [ \<system.Net > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) elementu, można ustawić serwerów proxy, Ustaw połączenie z parametrami zarządzania i dołączenie niestandardowe moduły uwierzytelniania i żądania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="62bd6-104">Using the [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="62bd6-105">[ \<DefaultProxy — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element definiuje zwrócony przez serwer proxy `GlobalProxySelection` klasy.</span><span class="sxs-lookup"><span data-stu-id="62bd6-105">The [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="62bd6-106">Wszelkie <xref:System.Net.HttpWebRequest> , która nie ma własną <xref:System.Net.HttpWebRequest.Proxy%2A> właściwość o określonej wartości używany domyślny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="62bd6-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="62bd6-107">Poza ustawieniem adres serwera proxy, można utworzyć listę adresów serwerów, które nie będzie używać serwera proxy, i może oznaczać, że nie należy używać serwera proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="62bd6-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="62bd6-108">Należy pamiętać, że ustawienia programu Microsoft Internet Explorer są łączone przy użyciu ustawień konfiguracyjnych z pierwszeństwo przed ostatnim z argumentami.</span><span class="sxs-lookup"><span data-stu-id="62bd6-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="62bd6-109">Poniższy przykład ustawia adres serwera proxy domyślne http://proxyserver, wskazuje, że serwer proxy nie powinna być używana dla adresów lokalnych i określa, że wszystkie żądania kierowane do serwerów znajdujących się w domenie contoso.com, należy pominąć serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="62bd6-109">The following example sets the default proxy server address to http://proxyserver, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="62bd6-110">Użyj [ \<connectionmanagement — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element, aby skonfigurować liczbę połączeń trwałych, które można wprowadzić do określonego serwera lub na inne serwery.</span><span class="sxs-lookup"><span data-stu-id="62bd6-110">Use the [\<connectionManagement> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="62bd6-111">Poniższy przykład konfiguruje aplikację do używania dwóch połączeń trwałych www.contoso.com serwera, cztery trwałego połączenia z serwerem o adresie IP 192.168.1.2 i jedno połączenie trwałe na inne serwery.</span><span class="sxs-lookup"><span data-stu-id="62bd6-111">The following example configures the application to use two persistent connections to the server www.contoso.com, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="62bd6-112">Moduły uwierzytelniania niestandardowego są skonfigurowane przy użyciu [ \<authenticationModules — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="62bd6-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="62bd6-113">Moduły uwierzytelniania niestandardowego musi implementować <xref:System.Net.IAuthenticationModule> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="62bd6-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="62bd6-114">Poniższy przykład konfiguruje moduł uwierzytelniania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="62bd6-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="62bd6-115">Można użyć [ \<webRequestModules — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element, aby skonfigurować aplikację do użycia niestandardowe moduły protokołem na żądanie informacji z zasobów w Internecie.</span><span class="sxs-lookup"><span data-stu-id="62bd6-115">You can use the [\<webRequestModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="62bd6-116">Określone moduły musi implementować <xref:System.Net.IWebRequestCreate> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="62bd6-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="62bd6-117">Można zastąpić domyślny HTTP, HTTPS i moduły żądania pliku, określając niestandardowego modułu w pliku konfiguracji, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="62bd6-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62bd6-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62bd6-118">See Also</span></span>  
 [<span data-ttu-id="62bd6-119">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="62bd6-119">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="62bd6-120">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="62bd6-120">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="62bd6-121">\<system.Net > (ustawienia sieciowe) — Element</span><span class="sxs-lookup"><span data-stu-id="62bd6-121">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
