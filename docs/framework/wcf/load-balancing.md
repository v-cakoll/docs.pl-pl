---
title: Równoważenie obciążenia
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: a444df2b05803ec54c5bd9030ce12209cfe9bd07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183990"
---
# <a name="load-balancing"></a><span data-ttu-id="996b9-102">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="996b9-102">Load Balancing</span></span>
<span data-ttu-id="996b9-103">Jednym ze sposobów zwiększenia pojemności aplikacji Windows Communication Foundation (WCF) jest skalowanie ich w poziomie przez wdrożenie ich w farmie serwerów z równoważeniem obciążenia.</span><span class="sxs-lookup"><span data-stu-id="996b9-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="996b9-104">Aplikacje WCF można równoważyć obciążenie przy użyciu standardowych technik równoważenia obciążenia, w tym programowych modułów równoważenia obciążenia, takich jak równoważenie obciążenia sieciowego systemu Windows, a także sprzętowych urządzeń równoważących obciążenie.</span><span class="sxs-lookup"><span data-stu-id="996b9-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="996b9-105">W poniższych sekcjach omówiono zagadnienia dotyczące równoważenia obciążenia aplikacje WCF utworzone przy użyciu różnych powiązań dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="996b9-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="996b9-106">Równoważenie obciążenia za pomocą podstawowego powiązania HTTP</span><span class="sxs-lookup"><span data-stu-id="996b9-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="996b9-107">Z punktu widzenia równoważenia obciążenia aplikacje <xref:System.ServiceModel.BasicHttpBinding> WCF, które komunikują się przy użyciu nie różnią się od innych typowych typów ruchu sieciowego HTTP (statyczna zawartość HTML, ASP.NET stron lub asmx web services).</span><span class="sxs-lookup"><span data-stu-id="996b9-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="996b9-108">Kanały WCF, które używają tego powiązania są z natury bezstanowe i kończą swoje połączenia po zamknięciu kanału.</span><span class="sxs-lookup"><span data-stu-id="996b9-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="996b9-109">W związku <xref:System.ServiceModel.BasicHttpBinding> z tym działa dobrze z istniejących technik równoważenia obciążenia HTTP.</span><span class="sxs-lookup"><span data-stu-id="996b9-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="996b9-110">Domyślnie <xref:System.ServiceModel.BasicHttpBinding> wysyła nagłówek HTTP połączenia w `Keep-Alive` wiadomościach o wartości, która umożliwia klientom ustanawianie trwałych połączeń z usługami, które je obsługują.</span><span class="sxs-lookup"><span data-stu-id="996b9-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="996b9-111">Ta konfiguracja oferuje zwiększoną przepływność, ponieważ wcześniej ustanowione połączenia mogą być ponownie za pomocą wysyłania kolejnych wiadomości do tego samego serwera.</span><span class="sxs-lookup"><span data-stu-id="996b9-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="996b9-112">Jednak ponowne użycie połączenia może spowodować, że klienci staną się silnie skojarzone z określonym serwerem w farmie z równoważeniem obciążenia, co zmniejsza skuteczność równoważenia obciążenia okrężnego.</span><span class="sxs-lookup"><span data-stu-id="996b9-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="996b9-113">Jeśli to zachowanie jest `Keep-Alive` niepożądane, protokół HTTP <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> można wyłączyć <xref:System.ServiceModel.Channels.CustomBinding> na serwerze przy użyciu właściwości z lub zdefiniowanym przez <xref:System.ServiceModel.Channels.Binding>użytkownika .</span><span class="sxs-lookup"><span data-stu-id="996b9-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="996b9-114">W poniższym przykładzie pokazano, jak to zrobić przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="996b9-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="996b9-115">Za pomocą uproszczonej konfiguracji wprowadzonej w programie .NET Framework 4 to samo zachowanie można wykonać przy użyciu następującej uproszczonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="996b9-115">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="996b9-116">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [uproszczona konfiguracja usług WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="996b9-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="996b9-117">Równoważenie obciążenia za pomocą powiązania WSHttp i powiązania WSDualHttp</span><span class="sxs-lookup"><span data-stu-id="996b9-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="996b9-118">Zarówno <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> może być równoważenie obciążenia przy użyciu technik równoważenia obciążenia HTTP pod warunkiem, że kilka modyfikacji są dokonywane w domyślnej konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="996b9-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="996b9-119">Wyłącz ustanowienie kontekstu zabezpieczeń: można to osiągnąć <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> poprzez <xref:System.ServiceModel.WSHttpBinding> ustawienie `false`właściwości na do .</span><span class="sxs-lookup"><span data-stu-id="996b9-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="996b9-120">Alternatywnie, jeśli sesje zabezpieczeń są wymagane, można użyć stanowych sesji zabezpieczeń, zgodnie z opisem w temacie [Bezpieczne sesje.](./feature-details/secure-sessions.md)</span><span class="sxs-lookup"><span data-stu-id="996b9-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](./feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="996b9-121">Sesje zabezpieczeń stanowych umożliwiają usługi pozostają bezstanowe, jak cały stan dla sesji zabezpieczeń jest przesyłany z każdego żądania jako część tokenu zabezpieczającego ochrony.</span><span class="sxs-lookup"><span data-stu-id="996b9-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="996b9-122">Należy zauważyć, że aby włączyć stanową sesję <xref:System.ServiceModel.Channels.CustomBinding> zabezpieczeń, konieczne <xref:System.ServiceModel.Channels.Binding> jest użycie lub zdefiniowane <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSDualHttpBinding> przez użytkownika jako niezbędne ustawienia konfiguracji nie są widoczne i które są dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="996b9-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="996b9-123">Nie należy używać niezawodnych sesji.</span><span class="sxs-lookup"><span data-stu-id="996b9-123">Do not use reliable sessions.</span></span> <span data-ttu-id="996b9-124">Ta funkcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="996b9-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="996b9-125">Równoważenie obciążenia powiązaniem Net.TCP</span><span class="sxs-lookup"><span data-stu-id="996b9-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="996b9-126">Można <xref:System.ServiceModel.NetTcpBinding> równoważyć obciążenie przy użyciu technik równoważenia obciążenia w warstwie IP.</span><span class="sxs-lookup"><span data-stu-id="996b9-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="996b9-127">Jednak <xref:System.ServiceModel.NetTcpBinding> pule połączeń TCP domyślnie zmniejszyć opóźnienie połączenia.</span><span class="sxs-lookup"><span data-stu-id="996b9-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="996b9-128">Jest to optymalizacja, która zakłóca podstawowy mechanizm równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="996b9-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="996b9-129">Podstawową wartością konfiguracji <xref:System.ServiceModel.NetTcpBinding> do optymalizacji jest limit czasu dzierżawy, który jest częścią ustawień puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="996b9-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="996b9-130">Buforowanie połączeń powoduje, że połączenia klientów stają się skojarzone z określonymi serwerami w farmie.</span><span class="sxs-lookup"><span data-stu-id="996b9-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="996b9-131">Wraz ze wzrostem okresu istnienia tych połączeń (współczynnik kontrolowany przez ustawienie limitu czasu dzierżawy), rozkład obciążenia na różnych serwerach w farmie staje się niezrównoważony.</span><span class="sxs-lookup"><span data-stu-id="996b9-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="996b9-132">W rezultacie średni czas połączenia wzrasta.</span><span class="sxs-lookup"><span data-stu-id="996b9-132">As a result the average call time increases.</span></span> <span data-ttu-id="996b9-133">Dlatego podczas <xref:System.ServiceModel.NetTcpBinding> korzystania z scenariuszy z równoważeniem obciążenia należy rozważyć zmniejszenie domyślnego limitu czasu dzierżawy używanego przez powiązanie.</span><span class="sxs-lookup"><span data-stu-id="996b9-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="996b9-134">Limit czasu dzierżawy 30-sekundowy jest rozsądnym punktem wyjścia dla scenariuszy z równoważenia obciążenia, chociaż optymalna wartość jest zależna od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="996b9-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="996b9-135">Aby uzyskać więcej informacji na temat limitu czasu dzierżawy kanału i innych przydziałów transportu, zobacz [Przydziały transportu](./feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="996b9-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="996b9-136">Aby uzyskać najlepszą wydajność w scenariuszach <xref:System.ServiceModel.NetTcpSecurity> z <xref:System.ServiceModel.SecurityMode.Transport> równoważenia obciążenia, należy rozważyć użycie (albo lub <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="996b9-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="996b9-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="996b9-137">See also</span></span>

- [<span data-ttu-id="996b9-138">Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="996b9-138">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
