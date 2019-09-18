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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048634"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="3c88a-102">Konfigurowanie aplikacji internetowych</span><span class="sxs-lookup"><span data-stu-id="3c88a-102">Configuring Internet Applications</span></span>
<span data-ttu-id="3c88a-103">Element konfiguracji system .NET [> (Ustawienia sieci) zawiera informacje o konfiguracji sieci dla aplikacji. \<](../configure-apps/file-schema/network/system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3c88a-103">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="3c88a-104">Za pomocą elementu [ System.net>element(Ustawieniasieci)możnaustawićserweryproxy,ustawićparametryzarządzaniapołączeniamiiuwzględnićniestandardoweuwierzytelnianieimodułyżądańwaplikacji.\<](../configure-apps/file-schema/network/system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3c88a-104">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="3c88a-105">`GlobalProxySelection` [ ElementdefaultProxy>(Ustawieniasieci)definiujeserwer\<](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) proxy zwracany przez klasę.</span><span class="sxs-lookup"><span data-stu-id="3c88a-105">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="3c88a-106">Wszystkie <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebRequest.Proxy%2A> właściwości, które nie mają przypisanej do określonej wartości, używają domyślnego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="3c88a-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="3c88a-107">Oprócz ustawiania adresu serwera proxy można utworzyć listę adresów serwerów, które nie będą używać serwera proxy, i można wskazać, że serwer proxy nie powinien być używany dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="3c88a-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="3c88a-108">Należy pamiętać, że ustawienia programu Microsoft Internet Explorer są łączone z ustawieniami konfiguracji z ostatnim pierwszeństwem.</span><span class="sxs-lookup"><span data-stu-id="3c88a-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="3c88a-109">Poniższy przykład ustawia domyślny adres serwera proxy na `http://proxyserver`, wskazuje, że serwer proxy nie powinien być używany do adresów lokalnych, i określa, że wszystkie żądania kierowane do serwerów znajdujących się w domenie contoso.com powinny ominąć serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="3c88a-109">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="3c88a-110">Użyj elementu connectionManagement > [(Ustawienia sieci), aby skonfigurować liczbę trwałych połączeń, które mogą zostać wprowadzone do określonego serwera lub do wszystkich innych serwerów. \<](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3c88a-110">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="3c88a-111">Poniższy przykład konfiguruje aplikację do używania dwóch trwałych połączeń z serwerem `www.contoso.com`, czterech stałych połączeń z serwerem z adresem IP 192.168.1.2 i jednego połączenia trwałego z innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="3c88a-111">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="3c88a-112">Niestandardowe moduły uwierzytelniania są konfigurowane za pomocą [ \<elementu authenticationModules > (Ustawienia sieci)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) .</span><span class="sxs-lookup"><span data-stu-id="3c88a-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="3c88a-113">Niestandardowe moduły uwierzytelniania muszą implementować <xref:System.Net.IAuthenticationModule> interfejs.</span><span class="sxs-lookup"><span data-stu-id="3c88a-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="3c88a-114">Poniższy przykład służy do konfigurowania niestandardowego modułu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3c88a-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="3c88a-115">Za pomocą [ \<elementu webRequestModules > (Ustawienia sieci)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) można skonfigurować aplikację do używania niestandardowych modułów specyficznych dla protokołu, aby żądać informacji z zasobów internetowych.</span><span class="sxs-lookup"><span data-stu-id="3c88a-115">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="3c88a-116">Określone moduły muszą implementować <xref:System.Net.IWebRequestCreate> interfejs.</span><span class="sxs-lookup"><span data-stu-id="3c88a-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="3c88a-117">Można zastąpić domyślne moduły HTTP, HTTPS i File Request przez określenie niestandardowego modułu w pliku konfiguracji, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3c88a-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c88a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c88a-118">See also</span></span>

- [<span data-ttu-id="3c88a-119">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3c88a-119">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="3c88a-120">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="3c88a-120">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="3c88a-121">\<System .net >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="3c88a-121">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
