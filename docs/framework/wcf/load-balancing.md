---
title: Równoważenie obciążenia
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: 2a0644ea17db2923f5729feda40f3b2bff364231
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660752"
---
# <a name="load-balancing"></a><span data-ttu-id="068f1-102">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="068f1-102">Load Balancing</span></span>
<span data-ttu-id="068f1-103">Jednym ze sposobów, aby zwiększyć jej pojemność aplikacji Windows Communication Foundation (WCF) jest Skaluj je automatycznie przez wdrażanie ich do farmy serwerów z równoważeniem obciążenia.</span><span class="sxs-lookup"><span data-stu-id="068f1-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="068f1-104">Aplikacji WCF może być równoważone za pomocą standardowych równoważenia technik, w tym oprogramowania równoważenia obciążenia, takich jak Windows Równoważenie obciążenia sieciowego, a także oparte na sprzęcie równoważenia urządzenia.</span><span class="sxs-lookup"><span data-stu-id="068f1-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="068f1-105">W poniższych sekcjach omówiono zagadnienia dotyczące aplikacji WCF utworzone przy użyciu różnych powiązania dostarczane przez system równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="068f1-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="068f1-106">Równoważenie obciążenia za pomocą powiązania protokołu HTTP podstawowe</span><span class="sxs-lookup"><span data-stu-id="068f1-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="068f1-107">Z punktu widzenia Równoważenie obciążenia, aplikacji WCF, które komunikują się za pomocą <xref:System.ServiceModel.BasicHttpBinding> są inne niż inne typowe rodzaje HTTP w sieci (statyczne zawartość HTML strony ASP.NET i usług sieci Web ASMX).</span><span class="sxs-lookup"><span data-stu-id="068f1-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="068f1-108">Kanały programu WCF, korzystające z tego wiązania są założenia bezstanowe i zakończyć swoje połączenia, po zamknięciu kanału.</span><span class="sxs-lookup"><span data-stu-id="068f1-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="068f1-109">W efekcie <xref:System.ServiceModel.BasicHttpBinding> dobrze działa z istniejącymi równoważenia technik obciążenia HTTP.</span><span class="sxs-lookup"><span data-stu-id="068f1-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="068f1-110">Domyślnie <xref:System.ServiceModel.BasicHttpBinding> wysyła nagłówek połączenia HTTP w komunikatach o `Keep-Alive` wartość, która umożliwia klientom ustanowienia połączeń trwałych usług, które je obsługują.</span><span class="sxs-lookup"><span data-stu-id="068f1-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="068f1-111">Ta konfiguracja zapewnia zwiększoną przepływność, ponieważ wcześniej ustanowione, że połączenia mogą być ponownie używane do wysyłania kolejnych komunikatów na ten sam serwer.</span><span class="sxs-lookup"><span data-stu-id="068f1-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="068f1-112">Jednak ponowne użycie połączenia może spowodować klientom stają się silnie skojarzona z określonego serwera w farmie ze zrównoważonym obciążeniem, co zmniejsza skuteczności równoważenia obciążenia działania okrężnego.</span><span class="sxs-lookup"><span data-stu-id="068f1-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="068f1-113">Jeśli to zachowanie jest niepożądany, HTTP `Keep-Alive` można wyłączyć na serwerze za pomocą <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> właściwość o <xref:System.ServiceModel.Channels.CustomBinding> lub zdefiniowany przez użytkownika <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="068f1-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="068f1-114">Poniższy przykład pokazuje, jak to zrobić za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="068f1-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="068f1-115">Za pomocą uproszczona konfiguracja wprowadzona w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], samo można osiągnąć przy użyciu następującej konfiguracji uproszczone.</span><span class="sxs-lookup"><span data-stu-id="068f1-115">Using the simplified configuration introduced in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="068f1-116">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="068f1-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="068f1-117">Równoważenie obciążenia za pomocą powiązania WSHttp i powiązanie WSDualHttp</span><span class="sxs-lookup"><span data-stu-id="068f1-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="068f1-118">Zarówno <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> może być ze zrównoważonym obciążeniem przy użyciu technik równoważenia obciążenia HTTP, pod warunkiem kilka modyfikacje są dokonywane na domyślne powiązania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="068f1-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
-   <span data-ttu-id="068f1-119">Wyłącz ustanawiania kontekstu zabezpieczeń: można to osiągnąć przez ustawienie <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwość <xref:System.ServiceModel.WSHttpBinding> do `false`.</span><span class="sxs-lookup"><span data-stu-id="068f1-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="068f1-120">Alternatywnie, jeśli sesje zabezpieczeń są wymagane, jest możliwość użycia sesji zabezpieczeń stanową, zgodnie z opisem w [Secure sesje](../../../docs/framework/wcf/feature-details/secure-sessions.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="068f1-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](../../../docs/framework/wcf/feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="068f1-121">Sesje zabezpieczeń stanową włączyć usługi jest zachowywana bezstanowe cały stan sesji zabezpieczeń są przesyłane z każdym żądaniem jako część tokenu zabezpieczającego ochrony.</span><span class="sxs-lookup"><span data-stu-id="068f1-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="068f1-122">Należy pamiętać, że aby włączyć sesji zabezpieczeń stanową, trzeba użyć <xref:System.ServiceModel.Channels.CustomBinding> lub zdefiniowany przez użytkownika <xref:System.ServiceModel.Channels.Binding> jako niezbędną konfigurację ustawienia nie są widoczne na <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> są dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="068f1-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
-   <span data-ttu-id="068f1-123">Nie używaj niezawodnych sesji.</span><span class="sxs-lookup"><span data-stu-id="068f1-123">Do not use reliable sessions.</span></span> <span data-ttu-id="068f1-124">Ta funkcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="068f1-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="068f1-125">Powiązanie Net.TCP równoważenia obciążenia</span><span class="sxs-lookup"><span data-stu-id="068f1-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="068f1-126"><xref:System.ServiceModel.NetTcpBinding> Może być ze zrównoważonym obciążeniem technik równoważenia obciążenia dla warstwy IP.</span><span class="sxs-lookup"><span data-stu-id="068f1-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="068f1-127">Jednak <xref:System.ServiceModel.NetTcpBinding> pul połączeń TCP domyślnie, aby zmniejszyć czas oczekiwania na połączenie.</span><span class="sxs-lookup"><span data-stu-id="068f1-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="068f1-128">Jest to optymalizacji, które będzie zakłócać podstawowy mechanizm równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="068f1-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="068f1-129">Wartość podstawowa konfiguracja optymalizacji <xref:System.ServiceModel.NetTcpBinding> jest limit czasu dzierżawy, który jest częścią ustawienia puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="068f1-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="068f1-130">Pula połączeń powoduje, że połączeń klientów z stają się skojarzona z określonych serwerów w farmie.</span><span class="sxs-lookup"><span data-stu-id="068f1-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="068f1-131">Jak okres istnienia tych połączeń można zwiększyć (współczynnik kontrolowane przez ustawienie limitu czasu dzierżawy), dystrybucji obciążenia na różnych serwerach w farmie staje się niezrównoważone.</span><span class="sxs-lookup"><span data-stu-id="068f1-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="068f1-132">W wyniku średnią wywołać wzrostu czasu.</span><span class="sxs-lookup"><span data-stu-id="068f1-132">As a result the average call time increases.</span></span> <span data-ttu-id="068f1-133">Tak, korzystając z <xref:System.ServiceModel.NetTcpBinding> w scenariuszach ze zrównoważonym obciążeniem, należy rozważyć zmniejszenie domyślny limit czasu dzierżawy, używanym przez wiązanie.</span><span class="sxs-lookup"><span data-stu-id="068f1-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="068f1-134">Limit czasu dzierżawy 30 sekund jest uzasadnione punkt początkowy dla scenariuszy z równoważeniem obciążenia, mimo że wartość optymalną jest zależne od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="068f1-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="068f1-135">Aby uzyskać więcej informacji na temat limitu czasu dzierżawy kanału i innych przydziały dla transportu, zobacz [przydziały dla transportu](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="068f1-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="068f1-136">Aby uzyskać najlepszą wydajność w scenariuszach ze zrównoważonym obciążeniem, należy wziąć pod uwagę przy użyciu <xref:System.ServiceModel.NetTcpSecurity> (albo <xref:System.ServiceModel.SecurityMode.Transport> lub <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="068f1-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="068f1-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="068f1-137">See also</span></span>
- [<span data-ttu-id="068f1-138">Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="068f1-138">Internet Information Services Hosting Best Practices</span></span>](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
