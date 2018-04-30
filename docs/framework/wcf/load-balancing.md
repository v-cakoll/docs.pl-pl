---
title: Równoważenie obciążenia
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe13c4aee41cd7af188ccaea77b3c0af07603e2c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="load-balancing"></a><span data-ttu-id="f6313-102">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="f6313-102">Load Balancing</span></span>
<span data-ttu-id="f6313-103">Aby zwiększyć pojemność [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji ma limit skalować je przez wdrożenie ich do farmy serwerów z równoważeniem obciążenia.</span><span class="sxs-lookup"><span data-stu-id="f6313-103">One way to increase the capacity of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications is to scale them out by deploying them into a load-balanced server farm.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f6313-104"> aplikacje mogą być równoważone za pomocą standardowego obciążenia równoważenia technik, w tym usługi równoważenia obciążenia oprogramowania, takie jak Windows Równoważenie obciążenia sieciowego, a także równoważenie urządzenia obciążenia oparte na sprzęcie.</span><span class="sxs-lookup"><span data-stu-id="f6313-104"> applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="f6313-105">W poniższych sekcjach omówiono zagadnienia dotyczące równoważenia obciążenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacje utworzone przy użyciu różnych powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="f6313-105">The following sections discuss considerations for load balancing [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="f6313-106">Równoważenie obciążenia i powiązanie HTTP podstawowe</span><span class="sxs-lookup"><span data-stu-id="f6313-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="f6313-107">Z punktu widzenia równoważenia obciążenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacje, które komunikują się za pomocą <xref:System.ServiceModel.BasicHttpBinding> nie różnią się od innych typowych HTTP w sieci (statyczne zawartość HTML stron ASP.NET i usługi sieci Web ASMX).</span><span class="sxs-lookup"><span data-stu-id="f6313-107">From the perspective of load balancing, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f6313-108"> kanałów, które używają tego powiązania są z założenia bezstanowych, a następnie Zakończ ich połączeń po zamknięciu kanału.</span><span class="sxs-lookup"><span data-stu-id="f6313-108"> channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="f6313-109">W efekcie <xref:System.ServiceModel.BasicHttpBinding> dobrze działa z istniejącymi równoważenia techniki obciążenia HTTP.</span><span class="sxs-lookup"><span data-stu-id="f6313-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="f6313-110">Domyślnie <xref:System.ServiceModel.BasicHttpBinding> wysyła nagłówka połączenia HTTP w wiadomości z `Keep-Alive` wartość, która umożliwia klientom nawiązanie połączenia trwałe do usług, które je obsługują.</span><span class="sxs-lookup"><span data-stu-id="f6313-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="f6313-111">Ta konfiguracja zapewnia rozszerzoną przepływności, ponieważ wcześniej ustanowione, że połączenia mogą być ponownie używane do wysyłania kolejnych komunikatów na tym samym serwerze.</span><span class="sxs-lookup"><span data-stu-id="f6313-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="f6313-112">Jednak ponownego użycia połączenia może spowodować klientów staną się silnie skojarzony z określonego serwera w farmie z równoważeniem obciążenia, co zmniejsza skuteczności równoważenia obciążenia okrężnego.</span><span class="sxs-lookup"><span data-stu-id="f6313-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="f6313-113">Jeśli to zachowanie jest niepożądane, HTTP `Keep-Alive` można wyłączyć na serwerze przy użyciu <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> właściwości o <xref:System.ServiceModel.Channels.CustomBinding> lub zdefiniowanej przez użytkownika <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="f6313-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="f6313-114">Poniższy przykład pokazuje, jak to zrobić przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f6313-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="f6313-115">Przy użyciu uproszczona konfiguracja wprowadzona w systemie [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], takie samo zachowanie można wykonywać przy użyciu następującej konfiguracji uproszczone.</span><span class="sxs-lookup"><span data-stu-id="f6313-115">Using the simplified configuration introduced in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="f6313-116">Aby uzyskać więcej informacji na temat domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f6313-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="f6313-117">Równoważenie obciążenia i powiązania WSHttp i powiązanie WSDualHttp</span><span class="sxs-lookup"><span data-stu-id="f6313-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="f6313-118">Zarówno <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> może być o zrównoważonym obciążeniu przy użyciu technik równoważenia obciążenia HTTP, pod warunkiem kilka modyfikacje są dokonywane domyślne konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6313-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
-   <span data-ttu-id="f6313-119">Wyłącz ustanowienia kontekstu zabezpieczeń: można to zrobić przez ustawienie <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwość <xref:System.ServiceModel.WSHttpBinding> do `false`.</span><span class="sxs-lookup"><span data-stu-id="f6313-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="f6313-120">Alternatywnie, jeśli sesji zabezpieczeń są wymagane, jest możliwość użycia sesji zabezpieczeń stanową, zgodnie z opisem w [Secure sesji](../../../docs/framework/wcf/feature-details/secure-sessions.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f6313-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](../../../docs/framework/wcf/feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="f6313-121">Sesje zabezpieczeń stanową włączyć usługę pozostaje bezstanowych, jak wszystkie stanu sesji zabezpieczeń są przesyłane z każdym żądaniem jako część tokenu zabezpieczającego ochrony.</span><span class="sxs-lookup"><span data-stu-id="f6313-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="f6313-122">Należy pamiętać, że aby włączyć sesji zabezpieczeń stanową, trzeba użyć <xref:System.ServiceModel.Channels.CustomBinding> lub zdefiniowanej przez użytkownika <xref:System.ServiceModel.Channels.Binding> jako niezbędną konfigurację ustawień nie są widoczne na <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> są dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="f6313-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
-   <span data-ttu-id="f6313-123">Nie należy używać niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="f6313-123">Do not use reliable sessions.</span></span> <span data-ttu-id="f6313-124">Ta funkcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="f6313-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="f6313-125">Powiązanie Net.TCP równoważenia obciążenia</span><span class="sxs-lookup"><span data-stu-id="f6313-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="f6313-126"><xref:System.ServiceModel.NetTcpBinding> Może być o zrównoważonym obciążeniu techniki równoważenia obciążenia dla warstwy adresów IP.</span><span class="sxs-lookup"><span data-stu-id="f6313-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="f6313-127">Jednak <xref:System.ServiceModel.NetTcpBinding> pul połączeń TCP, aby domyślnie zmniejszenia opóźnienia połączenia.</span><span class="sxs-lookup"><span data-stu-id="f6313-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="f6313-128">Jest to Optymalizacja oferująca koliduje z podstawowego mechanizmu równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="f6313-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="f6313-129">Wartość konfiguracji podstawowej optymalizacji <xref:System.ServiceModel.NetTcpBinding> jest limitu czasu dzierżawy, który jest częścią ustawienia puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="f6313-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="f6313-130">Pula połączeń powoduje, że stają się skojarzony z określonych serwerów w farmie połączeń z klientami.</span><span class="sxs-lookup"><span data-stu-id="f6313-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="f6313-131">Jako okres istnienia tych połączeń zwiększyć (współczynnik kontrolowane przez ustawienia limitu czasu dzierżawy), rozkład obciążenia na różnych serwerach w farmie staje się równowagi.</span><span class="sxs-lookup"><span data-stu-id="f6313-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="f6313-132">W związku z tym średnią wywołać wzrostu czasu.</span><span class="sxs-lookup"><span data-stu-id="f6313-132">As a result the average call time increases.</span></span> <span data-ttu-id="f6313-133">Tak, korzystając z <xref:System.ServiceModel.NetTcpBinding> w scenariuszach z równoważeniem obciążenia, Rozważ zmniejszenie domyślny limit czasu dzierżawy, używanym przez wiązanie.</span><span class="sxs-lookup"><span data-stu-id="f6313-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="f6313-134">Limit czasu 30 sekund dzierżawy jest uzasadnione punkt początkowy dla scenariuszy z równoważeniem obciążenia, chociaż wartość optymalną jest zależny od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f6313-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="f6313-135">Aby uzyskać więcej informacji dotyczących limitu czasu dzierżawy kanału i innych przydziały dla transportu, zobacz [przydziały dla transportu](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="f6313-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="f6313-136">Aby uzyskać najlepszą wydajność w scenariuszach z równoważeniem obciążenia, należy rozważyć użycie <xref:System.ServiceModel.NetTcpSecurity> (albo <xref:System.ServiceModel.SecurityMode.Transport> lub <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="f6313-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6313-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6313-137">See Also</span></span>  
 [<span data-ttu-id="f6313-138">Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="f6313-138">Internet Information Services Hosting Best Practices</span></span>](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
