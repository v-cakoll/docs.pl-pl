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
# <a name="configuring-internet-applications"></a><span data-ttu-id="b506f-102">Konfigurowanie aplikacji internetowych</span><span class="sxs-lookup"><span data-stu-id="b506f-102">Configuring Internet Applications</span></span>
<span data-ttu-id="b506f-103">Element konfiguracji [ \<system.Net> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/system-net-element-network-settings.md) zawiera informacje o konfiguracji sieci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b506f-103">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="b506f-104">Korzystając z elementu [ \<system.Net> (Ustawienia sieciowe),](../configure-apps/file-schema/network/system-net-element-network-settings.md) można ustawić serwery proxy, ustawić parametry zarządzania połączeniami oraz uwzględnić niestandardowe moduły uwierzytelniania i żądania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b506f-104">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="b506f-105">[ \<DefaultProxy> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element definiuje serwer proxy `GlobalProxySelection` zwrócony przez klasę.</span><span class="sxs-lookup"><span data-stu-id="b506f-105">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="b506f-106">Każdy, <xref:System.Net.HttpWebRequest> kto nie <xref:System.Net.HttpWebRequest.Proxy%2A> ma własnej właściwości ustawionej na określoną wartość, używa domyślnego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="b506f-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="b506f-107">Oprócz ustawienia adresu serwera proxy można utworzyć listę adresów serwera, które nie będą używać serwera proxy, i można wskazać, że serwer proxy nie powinien być używany dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="b506f-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="b506f-108">Należy pamiętać, że ustawienia programu Microsoft Internet Explorer są połączone z ustawieniami konfiguracji, przy czym pierwszeństwo mają te ostatnie.</span><span class="sxs-lookup"><span data-stu-id="b506f-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="b506f-109">Poniższy przykład ustawia domyślny `http://proxyserver`adres serwera proxy na , wskazuje, że serwer proxy nie powinien być używany dla adresów lokalnych i określa, że wszystkie żądania do serwerów znajdujących się w domenie contoso.com powinny pomijać serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="b506f-109">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="b506f-110">Użyj elementu [ \<connectionManagement> Element (Ustawienia sieciowe),](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) aby skonfigurować liczbę trwałych połączeń, które mogą być nawiązywane z określonym serwerem lub wszystkimi innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="b506f-110">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="b506f-111">Poniższy przykład konfiguruje aplikację do używania `www.contoso.com`dwóch trwałych połączeń z serwerem , czterech trwałych połączeń z serwerem o adresie IP 192.168.1.2 i jednego połączenia trwałego ze wszystkimi innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="b506f-111">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="b506f-112">Niestandardowe moduły uwierzytelniania są konfigurowane za pomocą elementu [ \<authenticationModules> Element (Ustawienia sieciowe).](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b506f-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="b506f-113">Niestandardowe moduły uwierzytelniania muszą implementować <xref:System.Net.IAuthenticationModule> interfejs.</span><span class="sxs-lookup"><span data-stu-id="b506f-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="b506f-114">W poniższym przykładzie konfiguruje niestandardowy moduł uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="b506f-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="b506f-115">Za pomocą elementu [ \<webRequestModules> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) można skonfigurować aplikację do używania niestandardowych modułów specyficznych dla protokołu do żądania informacji z zasobów internetowych.</span><span class="sxs-lookup"><span data-stu-id="b506f-115">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="b506f-116">Określone moduły muszą <xref:System.Net.IWebRequestCreate> implementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="b506f-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="b506f-117">Domyślne moduły żądań HTTP, HTTPS i plików można zastąpić, określając moduł niestandardowy w pliku konfiguracyjnym, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b506f-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b506f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b506f-118">See also</span></span>

- [<span data-ttu-id="b506f-119">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b506f-119">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="b506f-120">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="b506f-120">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="b506f-121">\<system.Net element> (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="b506f-121">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
