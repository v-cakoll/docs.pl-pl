---
title: Równoważenie obciążenia
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: c9a1e889ab5adcb8f0eb5ea851c81a4f9ee56e95
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138544"
---
# <a name="load-balancing"></a>Równoważenie obciążenia
Jednym ze sposobów zwiększenia pojemności aplikacji Windows Communication Foundation (WCF) jest skalowanie ich przez wdrożenie ich do farmy serwerów z równoważeniem obciążenia. Aplikacje WCF mogą być zrównoważone obciążenie przy użyciu standardowych technik równoważenia obciążenia, w tym programowych modułów równoważenia obciążenia, takich jak równoważenie obciążenia sieciowego systemu Windows, a także urządzenia równoważenia obciążenia opartego na sprzęcie.  
  
 W poniższych sekcjach omówiono zagadnienia dotyczące równoważenia obciążenia aplikacji WCF utworzonych przy użyciu różnych powiązań dostarczanych przez system.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Równoważenie obciążenia przy użyciu podstawowego powiązania HTTP  
 Z punktu widzenia równoważenia obciążenia aplikacje WCF, które komunikują się przy użyciu <xref:System.ServiceModel.BasicHttpBinding> nie różnią się od innych typów ruchu sieciowego protokołu HTTP (statyczna zawartość HTML, ASP.NET stron lub ASMX usługi sieci Web). Kanały WCF korzystające z tego powiązania są z natury bezstanowe i przerywają połączenia po zamknięciu kanału. W związku z tym <xref:System.ServiceModel.BasicHttpBinding> dobrze sprawdza się w przypadku istniejących technik równoważenia obciążenia HTTP.  
  
 Domyślnie <xref:System.ServiceModel.BasicHttpBinding> wysyła nagłówek HTTP połączenia w komunikatach z wartością `Keep-Alive`, co umożliwia klientom ustanawianie trwałych połączeń z usługami, które je obsługują. Ta konfiguracja zapewnia zwiększoną przepływność, ponieważ wcześniej ustanowiono połączenia mogą być ponownie używane do wysyłania kolejnych komunikatów do tego samego serwera. Jednak ponowne użycie połączenia może spowodować, że klienci staną się silnie powiązane z określonym serwerem w farmie z równoważeniem obciążenia, co zmniejsza efektywność równoważenia obciążenia z działaniem okrężnym. Jeśli takie zachowanie jest niepożądane, `Keep-Alive` protokołu HTTP można wyłączyć na serwerze przy użyciu właściwości <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> z <xref:System.ServiceModel.Channels.CustomBinding> lub <xref:System.ServiceModel.Channels.Binding>zdefiniowanym przez użytkownika. Poniższy przykład pokazuje, jak to zrobić za pomocą konfiguracji.  
  
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
  
 Przy użyciu uproszczonej konfiguracji wprowadzonej w .NET Framework 4, takie samo zachowanie można wykonać przy użyciu następującej uproszczonej konfiguracji.  
  
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
  
 Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Równoważenie obciążenia za pomocą powiązania WSHttp i powiązania WSDualHttp  
 Zarówno <xref:System.ServiceModel.WSHttpBinding>, jak i <xref:System.ServiceModel.WSDualHttpBinding> można zrównoważyć obciążenie przy użyciu technik równoważenia obciążenia HTTP, pod warunkiem, że wprowadzono kilka modyfikacji domyślnych konfiguracji powiązań.  
  
- Wyłącz zakładanie kontekstu zabezpieczeń: można to osiągnąć przez ustawienie właściwości <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> w <xref:System.ServiceModel.WSHttpBinding> do `false`. Alternatywnie, jeśli są wymagane sesje zabezpieczeń, możliwe jest użycie stanowych sesji zabezpieczeń zgodnie z opisem w temacie [bezpieczne sesje](./feature-details/secure-sessions.md) . Bezstanowe sesje zabezpieczeń umożliwiają usłudze, która pozostanie bez zmian, ponieważ wszystkie Stany sesji zabezpieczeń są przesyłane z każdym żądaniem jako część tokenu zabezpieczeń ochrony. Należy pamiętać, że aby włączyć bezstanową sesję zabezpieczeń, należy użyć <xref:System.ServiceModel.Channels.CustomBinding> lub <xref:System.ServiceModel.Channels.Binding> zdefiniowanej przez użytkownika, ponieważ niezbędne ustawienia konfiguracji nie są dostępne w <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding>, które są udostępniane przez system.  
  
- Nie używaj niezawodnych sesji. Ta funkcja jest domyślnie wyłączona.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Równoważenie obciążenia powiązania net. TCP  
 <xref:System.ServiceModel.NetTcpBinding> można zrównoważyć obciążenie przy użyciu technik równoważenia obciążenia warstwy IP. Jednak <xref:System.ServiceModel.NetTcpBinding> pule domyślnie połączeń TCP, aby zmniejszyć opóźnienie połączenia. Jest to Optymalizacja, która zakłóca podstawowy mechanizm równoważenia obciążenia. Podstawową wartością konfiguracji optymalizacji <xref:System.ServiceModel.NetTcpBinding> jest limit czasu dzierżawy, który jest częścią ustawień puli połączeń. Buforowanie połączeń powoduje, że połączenia klienckie są skojarzone z konkretnymi serwerami w farmie. W miarę wzrostu okresu istnienia tych połączeń (czynniki kontrolowane przez ustawienie limitu czasu dzierżawy) rozkład obciążenia na różnych serwerach w farmie jest niezrównoważony. W wyniku tego średniego czasu wywołania wzrasta. Dlatego w przypadku używania <xref:System.ServiceModel.NetTcpBinding> w scenariuszach z równoważeniem obciążenia należy rozważyć zmniejszenie domyślnego limitu czasu dzierżawy używanego przez powiązanie. Limit czasu dzierżawy 30 sekund to rozsądny punkt początkowy dla scenariuszy o zrównoważonym obciążeniu, chociaż optymalna wartość jest zależna od aplikacji. Aby uzyskać więcej informacji na temat limitu czasu dzierżawy kanału i innych przydziałów transportu, zobacz [przydziały transportowe](./feature-details/transport-quotas.md).  
  
 Aby uzyskać najlepszą wydajność w scenariuszach z równoważeniem obciążenia, należy rozważyć użycie <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> lub <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Zobacz także

- [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](./feature-details/internet-information-services-hosting-best-practices.md)
