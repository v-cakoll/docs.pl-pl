---
title: Równoważenie obciążenia
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: 572537826074dd51b56f1cae9edb767708bc1c3d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321030"
---
# <a name="load-balancing"></a><span data-ttu-id="e5f7e-102">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="e5f7e-102">Load Balancing</span></span>
<span data-ttu-id="e5f7e-103">Jednym ze sposobów zwiększenia pojemności aplikacji Windows Communication Foundation (WCF) jest skalowanie ich przez wdrożenie ich do farmy serwerów z równoważeniem obciążenia.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="e5f7e-104">Aplikacje WCF mogą być zrównoważone obciążenie przy użyciu standardowych technik równoważenia obciążenia, w tym programowych modułów równoważenia obciążenia, takich jak równoważenie obciążenia sieciowego systemu Windows, a także urządzenia równoważenia obciążenia opartego na sprzęcie.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="e5f7e-105">W poniższych sekcjach omówiono zagadnienia dotyczące równoważenia obciążenia aplikacji WCF utworzonych przy użyciu różnych powiązań dostarczanych przez system.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="e5f7e-106">Równoważenie obciążenia przy użyciu podstawowego powiązania HTTP</span><span class="sxs-lookup"><span data-stu-id="e5f7e-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="e5f7e-107">Z punktu widzenia równoważenia obciążenia aplikacje WCF, które komunikują się przy użyciu <xref:System.ServiceModel.BasicHttpBinding>, nie różnią się od innych typów ruchu sieciowego protokołu HTTP (statyczna zawartość HTML, ASP.NET stron lub ASMX usługi sieci Web).</span><span class="sxs-lookup"><span data-stu-id="e5f7e-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="e5f7e-108">Kanały WCF korzystające z tego powiązania są z natury bezstanowe i przerywają połączenia po zamknięciu kanału.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="e5f7e-109">W związku z tym <xref:System.ServiceModel.BasicHttpBinding> dobrze sprawdza się w przypadku istniejących technik równoważenia obciążenia HTTP.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="e5f7e-110">Domyślnie <xref:System.ServiceModel.BasicHttpBinding> wysyła nagłówek HTTP połączenia w komunikatach z wartością `Keep-Alive`, co umożliwia klientom ustanawianie trwałych połączeń z usługami, które je obsługują.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="e5f7e-111">Ta konfiguracja zapewnia zwiększoną przepływność, ponieważ wcześniej ustanowiono połączenia mogą być ponownie używane do wysyłania kolejnych komunikatów do tego samego serwera.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="e5f7e-112">Jednak ponowne użycie połączenia może spowodować, że klienci staną się silnie powiązane z określonym serwerem w farmie z równoważeniem obciążenia, co zmniejsza efektywność równoważenia obciążenia z działaniem okrężnym.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="e5f7e-113">Jeśli takie zachowanie jest niepożądane, można wyłączyć HTTP `Keep-Alive` na serwerze przy użyciu właściwości <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> z <xref:System.ServiceModel.Channels.CustomBinding> lub <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="e5f7e-114">Poniższy przykład pokazuje, jak to zrobić za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-114">The following example shows how to do this using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service   
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"   
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e5f7e-115">Przy użyciu uproszczonej konfiguracji wprowadzonej w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] takie samo zachowanie można wykonać przy użyciu następującej uproszczonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-115">Using the simplified configuration introduced in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e5f7e-116">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e5f7e-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="e5f7e-117">Równoważenie obciążenia za pomocą powiązania WSHttp i powiązania WSDualHttp</span><span class="sxs-lookup"><span data-stu-id="e5f7e-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="e5f7e-118">Zarówno <xref:System.ServiceModel.WSHttpBinding>, jak i <xref:System.ServiceModel.WSDualHttpBinding> można zrównoważyć obciążenie przy użyciu technik równoważenia obciążenia HTTP, pod warunkiem, że wprowadzono kilka modyfikacji domyślnych konfiguracji powiązań.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="e5f7e-119">Wyłącz zakładanie kontekstu zabezpieczeń: można to osiągnąć przez ustawienie właściwości <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> w <xref:System.ServiceModel.WSHttpBinding> na `false`.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="e5f7e-120">Alternatywnie, jeśli są wymagane sesje zabezpieczeń, możliwe jest użycie stanowych sesji zabezpieczeń zgodnie z opisem w temacie [bezpieczne sesje](./feature-details/secure-sessions.md) .</span><span class="sxs-lookup"><span data-stu-id="e5f7e-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](./feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="e5f7e-121">Bezstanowe sesje zabezpieczeń umożliwiają usłudze, która pozostanie bez zmian, ponieważ wszystkie Stany sesji zabezpieczeń są przesyłane z każdym żądaniem jako część tokenu zabezpieczeń ochrony.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="e5f7e-122">Należy pamiętać, że aby włączyć bezstanową sesję zabezpieczeń, należy użyć <xref:System.ServiceModel.Channels.CustomBinding> lub zdefiniowanej przez użytkownika <xref:System.ServiceModel.Channels.Binding>, ponieważ niezbędne ustawienia konfiguracji nie są widoczne na <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding>, które są dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="e5f7e-123">Nie używaj niezawodnych sesji.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-123">Do not use reliable sessions.</span></span> <span data-ttu-id="e5f7e-124">Ta funkcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="e5f7e-125">Równoważenie obciążenia powiązania net. TCP</span><span class="sxs-lookup"><span data-stu-id="e5f7e-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="e5f7e-126">@No__t-0 można zrównoważyć obciążenie przy użyciu technik równoważenia obciążenia warstwy IP.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="e5f7e-127">Jednak domyślnie pule <xref:System.ServiceModel.NetTcpBinding> protokołu TCP w celu zmniejszenia opóźnień połączenia.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="e5f7e-128">Jest to Optymalizacja, która zakłóca podstawowy mechanizm równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="e5f7e-129">Podstawowa wartość konfiguracji służąca do optymalizowania <xref:System.ServiceModel.NetTcpBinding> to limit czasu dzierżawy, który jest częścią ustawień puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="e5f7e-130">Buforowanie połączeń powoduje, że połączenia klienckie są skojarzone z konkretnymi serwerami w farmie.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="e5f7e-131">W miarę wzrostu okresu istnienia tych połączeń (czynniki kontrolowane przez ustawienie limitu czasu dzierżawy) rozkład obciążenia na różnych serwerach w farmie jest niezrównoważony.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="e5f7e-132">W wyniku tego średniego czasu wywołania wzrasta.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-132">As a result the average call time increases.</span></span> <span data-ttu-id="e5f7e-133">Dlatego w przypadku używania <xref:System.ServiceModel.NetTcpBinding> w scenariuszach z równoważeniem obciążenia należy rozważyć zmniejszenie domyślnego limitu czasu dzierżawy używanego przez powiązanie.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="e5f7e-134">Limit czasu dzierżawy 30 sekund to rozsądny punkt początkowy dla scenariuszy o zrównoważonym obciążeniu, chociaż optymalna wartość jest zależna od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5f7e-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="e5f7e-135">Aby uzyskać więcej informacji na temat limitu czasu dzierżawy kanału i innych przydziałów transportu, zobacz [przydziały transportowe](./feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="e5f7e-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="e5f7e-136">Aby uzyskać najlepszą wydajność w scenariuszach z równoważeniem obciążenia, należy rozważyć użycie <xref:System.ServiceModel.NetTcpSecurity> (albo <xref:System.ServiceModel.SecurityMode.Transport> lub <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="e5f7e-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f7e-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5f7e-137">See also</span></span>

- [<span data-ttu-id="e5f7e-138">Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="e5f7e-138">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
