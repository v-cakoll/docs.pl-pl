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
# <a name="load-balancing"></a>Równoważenie obciążenia
Aby zwiększyć pojemność [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji ma limit skalować je przez wdrożenie ich do farmy serwerów z równoważeniem obciążenia. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacje mogą być równoważone za pomocą standardowego obciążenia równoważenia technik, w tym usługi równoważenia obciążenia oprogramowania, takie jak Windows Równoważenie obciążenia sieciowego, a także równoważenie urządzenia obciążenia oparte na sprzęcie.  
  
 W poniższych sekcjach omówiono zagadnienia dotyczące równoważenia obciążenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacje utworzone przy użyciu różnych powiązania dostarczane przez system.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Równoważenie obciążenia i powiązanie HTTP podstawowe  
 Z punktu widzenia równoważenia obciążenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacje, które komunikują się za pomocą <xref:System.ServiceModel.BasicHttpBinding> nie różnią się od innych typowych HTTP w sieci (statyczne zawartość HTML stron ASP.NET i usługi sieci Web ASMX). [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kanałów, które używają tego powiązania są z założenia bezstanowych, a następnie Zakończ ich połączeń po zamknięciu kanału. W efekcie <xref:System.ServiceModel.BasicHttpBinding> dobrze działa z istniejącymi równoważenia techniki obciążenia HTTP.  
  
 Domyślnie <xref:System.ServiceModel.BasicHttpBinding> wysyła nagłówka połączenia HTTP w wiadomości z `Keep-Alive` wartość, która umożliwia klientom nawiązanie połączenia trwałe do usług, które je obsługują. Ta konfiguracja zapewnia rozszerzoną przepływności, ponieważ wcześniej ustanowione, że połączenia mogą być ponownie używane do wysyłania kolejnych komunikatów na tym samym serwerze. Jednak ponownego użycia połączenia może spowodować klientów staną się silnie skojarzony z określonego serwera w farmie z równoważeniem obciążenia, co zmniejsza skuteczności równoważenia obciążenia okrężnego. Jeśli to zachowanie jest niepożądane, HTTP `Keep-Alive` można wyłączyć na serwerze przy użyciu <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> właściwości o <xref:System.ServiceModel.Channels.CustomBinding> lub zdefiniowanej przez użytkownika <xref:System.ServiceModel.Channels.Binding>. Poniższy przykład pokazuje, jak to zrobić przy użyciu konfiguracji.  
  
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
  
 Przy użyciu uproszczona konfiguracja wprowadzona w systemie [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], takie samo zachowanie można wykonywać przy użyciu następującej konfiguracji uproszczone.  
  
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
  
 Aby uzyskać więcej informacji na temat domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Równoważenie obciążenia i powiązania WSHttp i powiązanie WSDualHttp  
 Zarówno <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> może być o zrównoważonym obciążeniu przy użyciu technik równoważenia obciążenia HTTP, pod warunkiem kilka modyfikacje są dokonywane domyślne konfiguracji powiązania.  
  
-   Wyłącz ustanowienia kontekstu zabezpieczeń: można to zrobić przez ustawienie <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwość <xref:System.ServiceModel.WSHttpBinding> do `false`. Alternatywnie, jeśli sesji zabezpieczeń są wymagane, jest możliwość użycia sesji zabezpieczeń stanową, zgodnie z opisem w [Secure sesji](../../../docs/framework/wcf/feature-details/secure-sessions.md) tematu. Sesje zabezpieczeń stanową włączyć usługę pozostaje bezstanowych, jak wszystkie stanu sesji zabezpieczeń są przesyłane z każdym żądaniem jako część tokenu zabezpieczającego ochrony. Należy pamiętać, że aby włączyć sesji zabezpieczeń stanową, trzeba użyć <xref:System.ServiceModel.Channels.CustomBinding> lub zdefiniowanej przez użytkownika <xref:System.ServiceModel.Channels.Binding> jako niezbędną konfigurację ustawień nie są widoczne na <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> są dostarczane przez system.  
  
-   Nie należy używać niezawodnej sesji. Ta funkcja jest domyślnie wyłączona.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Powiązanie Net.TCP równoważenia obciążenia  
 <xref:System.ServiceModel.NetTcpBinding> Może być o zrównoważonym obciążeniu techniki równoważenia obciążenia dla warstwy adresów IP. Jednak <xref:System.ServiceModel.NetTcpBinding> pul połączeń TCP, aby domyślnie zmniejszenia opóźnienia połączenia. Jest to Optymalizacja oferująca koliduje z podstawowego mechanizmu równoważenia obciążenia. Wartość konfiguracji podstawowej optymalizacji <xref:System.ServiceModel.NetTcpBinding> jest limitu czasu dzierżawy, który jest częścią ustawienia puli połączeń. Pula połączeń powoduje, że stają się skojarzony z określonych serwerów w farmie połączeń z klientami. Jako okres istnienia tych połączeń zwiększyć (współczynnik kontrolowane przez ustawienia limitu czasu dzierżawy), rozkład obciążenia na różnych serwerach w farmie staje się równowagi. W związku z tym średnią wywołać wzrostu czasu. Tak, korzystając z <xref:System.ServiceModel.NetTcpBinding> w scenariuszach z równoważeniem obciążenia, Rozważ zmniejszenie domyślny limit czasu dzierżawy, używanym przez wiązanie. Limit czasu 30 sekund dzierżawy jest uzasadnione punkt początkowy dla scenariuszy z równoważeniem obciążenia, chociaż wartość optymalną jest zależny od aplikacji. Aby uzyskać więcej informacji dotyczących limitu czasu dzierżawy kanału i innych przydziały dla transportu, zobacz [przydziały dla transportu](../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Aby uzyskać najlepszą wydajność w scenariuszach z równoważeniem obciążenia, należy rozważyć użycie <xref:System.ServiceModel.NetTcpSecurity> (albo <xref:System.ServiceModel.SecurityMode.Transport> lub <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Zobacz też  
 [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
