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
# <a name="configuring-internet-applications"></a><span data-ttu-id="9dd0f-104">Konfigurowanie aplikacji internetowych</span><span class="sxs-lookup"><span data-stu-id="9dd0f-104">Configuring Internet Applications</span></span>
<span data-ttu-id="9dd0f-105">Element konfiguracji [ \<system.Net> element (Ustawienia sieci)](../configure-apps/file-schema/network/system-net-element-network-settings.md) zawiera informacje o konfiguracji sieci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-105">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="9dd0f-106">Za pomocą elementu [ \<system.Net> (ustawień sieciowych)](../configure-apps/file-schema/network/system-net-element-network-settings.md) można ustawić serwery proxy, ustawić parametry zarządzania połączeniami i dołączyć niestandardowe moduły uwierzytelniania i żądania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-106">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="9dd0f-107">Element [ \<defaultProxy> (Ustawienia sieci)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) definiuje serwer proxy zwracany przez `GlobalProxySelection` klasę.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-107">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="9dd0f-108">Wszystkie <xref:System.Net.HttpWebRequest> właściwości, które nie mają przypisanej <xref:System.Net.HttpWebRequest.Proxy%2A> do określonej wartości, używają domyślnego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-108">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="9dd0f-109">Oprócz ustawiania adresu serwera proxy można utworzyć listę adresów serwerów, które nie będą używać serwera proxy, i można wskazać, że serwer proxy nie powinien być używany dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-109">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="9dd0f-110">Należy pamiętać, że ustawienia programu Microsoft Internet Explorer są łączone z ustawieniami konfiguracji z ostatnim pierwszeństwem.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-110">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="9dd0f-111">Poniższy przykład ustawia domyślny adres serwera proxy na `http://proxyserver` , wskazuje, że serwer proxy nie powinien być używany do adresów lokalnych, i określa, że wszystkie żądania kierowane do serwerów znajdujących się w domenie contoso.com powinny ominąć serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-111">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="9dd0f-112">Aby skonfigurować liczbę połączeń trwałych, które mogą zostać wprowadzone do określonego serwera lub do wszystkich innych serwerów, użyj elementu [ \<connectionManagement> (ustawień sieciowych)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) .</span><span class="sxs-lookup"><span data-stu-id="9dd0f-112">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="9dd0f-113">Poniższy przykład konfiguruje aplikację do używania dwóch trwałych połączeń z serwerem `www.contoso.com` , czterech stałych połączeń z serwerem z adresem IP 192.168.1.2 i jednego połączenia trwałego z innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-113">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="9dd0f-114">Niestandardowe moduły uwierzytelniania są konfigurowane przy użyciu elementu [ \<authenticationModules> (Ustawienia sieci)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) .</span><span class="sxs-lookup"><span data-stu-id="9dd0f-114">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="9dd0f-115">Niestandardowe moduły uwierzytelniania muszą implementować <xref:System.Net.IAuthenticationModule> interfejs.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-115">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="9dd0f-116">Poniższy przykład służy do konfigurowania niestandardowego modułu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-116">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="9dd0f-117">Za pomocą elementu [ \<webRequestModules> (ustawień sieci)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) można skonfigurować aplikację do używania niestandardowych modułów specyficznych dla protokołu, aby żądać informacji z zasobów internetowych.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-117">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="9dd0f-118">Określone moduły muszą implementować <xref:System.Net.IWebRequestCreate> interfejs.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-118">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="9dd0f-119">Można zastąpić domyślne moduły HTTP, HTTPS i File Request przez określenie niestandardowego modułu w pliku konfiguracji, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-119">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9dd0f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9dd0f-120">See also</span></span>

- [<span data-ttu-id="9dd0f-121">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9dd0f-121">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="9dd0f-122">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="9dd0f-122">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="9dd0f-123">\<system.Net>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="9dd0f-123">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
