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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133805"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="a3769-102">Konfigurowanie aplikacji internetowych</span><span class="sxs-lookup"><span data-stu-id="a3769-102">Configuring Internet Applications</span></span>
<span data-ttu-id="a3769-103">[ \<Przestrzeni nazw system.Net >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element konfiguracji zawiera informacje o konfiguracji sieci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3769-103">The [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="a3769-104">Przy użyciu [ \<przestrzeni nazw system.Net >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) elementu, ustaw serwerów proxy, Ustaw połączenie z parametrami zarządzania i obejmują moduły niestandardowe uwierzytelnianie i żądanie w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3769-104">Using the [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="a3769-105">[ \<DefaultProxy >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element definiuje zwrócony przez serwer proxy `GlobalProxySelection` klasy.</span><span class="sxs-lookup"><span data-stu-id="a3769-105">The [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="a3769-106">Wszelkie <xref:System.Net.HttpWebRequest> , nie ma swój własny <xref:System.Net.HttpWebRequest.Proxy%2A> właściwość o określonej wartości korzysta z domyślnego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a3769-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="a3769-107">Oprócz skonfigurowania adres serwera proxy, można utworzyć listę adresów serwerów, które nie będzie używać serwera proxy, a może wskazywać, że nie należy używać serwera proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="a3769-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="a3769-108">Jest to należy zwrócić uwagę, czy ustawienia programu Microsoft Internet Explorer są łączone z ustawienia konfiguracji z pierwszeństwem ostatnie wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="a3769-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="a3769-109">Poniższy przykład ustawia domyślny serwer proxy adres serwera `http://proxyserver`, wskazuje, że serwer proxy nie powinna być używana dla adresów lokalnych i określa, czy wszystkich żądań do serwerów znajdujących się w domenie contoso.com, należy pominąć serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="a3769-109">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="a3769-110">Użyj [ \<connectionManagement >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element, aby skonfigurować liczbę połączeń trwałych, które mogą być wykonane na określonym serwerze lub na inne serwery.</span><span class="sxs-lookup"><span data-stu-id="a3769-110">Use the [\<connectionManagement> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="a3769-111">Poniższy przykład umożliwia skonfigurowanie aplikacji do korzystania z dwóch trwałego połączenia z serwerem `www.contoso.com`, cztery trwałego połączenia z serwerem o adresie IP 192.168.1.2 i jedno połączenie trwałe na inne serwery.</span><span class="sxs-lookup"><span data-stu-id="a3769-111">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="a3769-112">Uwierzytelnianie niestandardowe moduły są skonfigurowane przy użyciu [ \<authenticationModules >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a3769-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="a3769-113">Moduły niestandardowe uwierzytelnianie musi implementować <xref:System.Net.IAuthenticationModule> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a3769-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="a3769-114">Poniższy przykład umożliwia skonfigurowanie uwierzytelniania niestandardowego modułu.</span><span class="sxs-lookup"><span data-stu-id="a3769-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="a3769-115">Możesz użyć [ \<webRequestModules >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) elementu, aby skonfigurować aplikację na potrzeby niestandardowe moduły oparte na protokole żądanie informacji z zasobów internetowych.</span><span class="sxs-lookup"><span data-stu-id="a3769-115">You can use the [\<webRequestModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="a3769-116">Określone moduły muszą implementować <xref:System.Net.IWebRequestCreate> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a3769-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="a3769-117">Można zastąpić domyślny HTTP, HTTPS i pliku żądania modułów, określając niestandardowego modułu w pliku konfiguracji, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a3769-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3769-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3769-118">See also</span></span>

- [<span data-ttu-id="a3769-119">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a3769-119">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
- [<span data-ttu-id="a3769-120">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="a3769-120">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="a3769-121">\<przestrzeni nazw system.Net >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a3769-121">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
