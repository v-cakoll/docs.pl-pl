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
# <a name="load-balancing"></a>Równoważenie obciążenia
Jednym ze sposobów zwiększenia pojemności aplikacji Windows Communication Foundation (WCF) jest skalowanie ich w poziomie przez wdrożenie ich w farmie serwerów z równoważeniem obciążenia. Aplikacje WCF można równoważyć obciążenie przy użyciu standardowych technik równoważenia obciążenia, w tym programowych modułów równoważenia obciążenia, takich jak równoważenie obciążenia sieciowego systemu Windows, a także sprzętowych urządzeń równoważących obciążenie.  
  
 W poniższych sekcjach omówiono zagadnienia dotyczące równoważenia obciążenia aplikacje WCF utworzone przy użyciu różnych powiązań dostarczonych przez system.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Równoważenie obciążenia za pomocą podstawowego powiązania HTTP  
 Z punktu widzenia równoważenia obciążenia aplikacje <xref:System.ServiceModel.BasicHttpBinding> WCF, które komunikują się przy użyciu nie różnią się od innych typowych typów ruchu sieciowego HTTP (statyczna zawartość HTML, ASP.NET stron lub asmx web services). Kanały WCF, które używają tego powiązania są z natury bezstanowe i kończą swoje połączenia po zamknięciu kanału. W związku <xref:System.ServiceModel.BasicHttpBinding> z tym działa dobrze z istniejących technik równoważenia obciążenia HTTP.  
  
 Domyślnie <xref:System.ServiceModel.BasicHttpBinding> wysyła nagłówek HTTP połączenia w `Keep-Alive` wiadomościach o wartości, która umożliwia klientom ustanawianie trwałych połączeń z usługami, które je obsługują. Ta konfiguracja oferuje zwiększoną przepływność, ponieważ wcześniej ustanowione połączenia mogą być ponownie za pomocą wysyłania kolejnych wiadomości do tego samego serwera. Jednak ponowne użycie połączenia może spowodować, że klienci staną się silnie skojarzone z określonym serwerem w farmie z równoważeniem obciążenia, co zmniejsza skuteczność równoważenia obciążenia okrężnego. Jeśli to zachowanie jest `Keep-Alive` niepożądane, protokół HTTP <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> można wyłączyć <xref:System.ServiceModel.Channels.CustomBinding> na serwerze przy użyciu właściwości z lub zdefiniowanym przez <xref:System.ServiceModel.Channels.Binding>użytkownika . W poniższym przykładzie pokazano, jak to zrobić przy użyciu konfiguracji.  
  
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
  
 Za pomocą uproszczonej konfiguracji wprowadzonej w programie .NET Framework 4 to samo zachowanie można wykonać przy użyciu następującej uproszczonej konfiguracji.  
  
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
  
 Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [uproszczona konfiguracja usług WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Równoważenie obciążenia za pomocą powiązania WSHttp i powiązania WSDualHttp  
 Zarówno <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> może być równoważenie obciążenia przy użyciu technik równoważenia obciążenia HTTP pod warunkiem, że kilka modyfikacji są dokonywane w domyślnej konfiguracji powiązania.  
  
- Wyłącz ustanowienie kontekstu zabezpieczeń: można to osiągnąć <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> poprzez <xref:System.ServiceModel.WSHttpBinding> ustawienie `false`właściwości na do . Alternatywnie, jeśli sesje zabezpieczeń są wymagane, można użyć stanowych sesji zabezpieczeń, zgodnie z opisem w temacie [Bezpieczne sesje.](./feature-details/secure-sessions.md) Sesje zabezpieczeń stanowych umożliwiają usługi pozostają bezstanowe, jak cały stan dla sesji zabezpieczeń jest przesyłany z każdego żądania jako część tokenu zabezpieczającego ochrony. Należy zauważyć, że aby włączyć stanową sesję <xref:System.ServiceModel.Channels.CustomBinding> zabezpieczeń, konieczne <xref:System.ServiceModel.Channels.Binding> jest użycie lub zdefiniowane <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSDualHttpBinding> przez użytkownika jako niezbędne ustawienia konfiguracji nie są widoczne i które są dostarczane przez system.  
  
- Nie należy używać niezawodnych sesji. Ta funkcja jest domyślnie wyłączona.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Równoważenie obciążenia powiązaniem Net.TCP  
 Można <xref:System.ServiceModel.NetTcpBinding> równoważyć obciążenie przy użyciu technik równoważenia obciążenia w warstwie IP. Jednak <xref:System.ServiceModel.NetTcpBinding> pule połączeń TCP domyślnie zmniejszyć opóźnienie połączenia. Jest to optymalizacja, która zakłóca podstawowy mechanizm równoważenia obciążenia. Podstawową wartością konfiguracji <xref:System.ServiceModel.NetTcpBinding> do optymalizacji jest limit czasu dzierżawy, który jest częścią ustawień puli połączeń. Buforowanie połączeń powoduje, że połączenia klientów stają się skojarzone z określonymi serwerami w farmie. Wraz ze wzrostem okresu istnienia tych połączeń (współczynnik kontrolowany przez ustawienie limitu czasu dzierżawy), rozkład obciążenia na różnych serwerach w farmie staje się niezrównoważony. W rezultacie średni czas połączenia wzrasta. Dlatego podczas <xref:System.ServiceModel.NetTcpBinding> korzystania z scenariuszy z równoważeniem obciążenia należy rozważyć zmniejszenie domyślnego limitu czasu dzierżawy używanego przez powiązanie. Limit czasu dzierżawy 30-sekundowy jest rozsądnym punktem wyjścia dla scenariuszy z równoważenia obciążenia, chociaż optymalna wartość jest zależna od aplikacji. Aby uzyskać więcej informacji na temat limitu czasu dzierżawy kanału i innych przydziałów transportu, zobacz [Przydziały transportu](./feature-details/transport-quotas.md).  
  
 Aby uzyskać najlepszą wydajność w scenariuszach <xref:System.ServiceModel.NetTcpSecurity> z <xref:System.ServiceModel.SecurityMode.Transport> równoważenia obciążenia, należy rozważyć użycie (albo lub <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Zobacz też

- [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](./feature-details/internet-information-services-hosting-best-practices.md)
