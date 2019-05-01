---
title: Równoważenie obciążenia
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: a43546b9cbb95cd16c1d94372e786acd103ea0bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921956"
---
# <a name="load-balancing"></a>Równoważenie obciążenia
Jednym ze sposobów, aby zwiększyć jej pojemność aplikacji Windows Communication Foundation (WCF) jest Skaluj je automatycznie przez wdrażanie ich do farmy serwerów z równoważeniem obciążenia. Aplikacji WCF może być równoważone za pomocą standardowych równoważenia technik, w tym oprogramowania równoważenia obciążenia, takich jak Windows Równoważenie obciążenia sieciowego, a także oparte na sprzęcie równoważenia urządzenia.  
  
 W poniższych sekcjach omówiono zagadnienia dotyczące aplikacji WCF utworzone przy użyciu różnych powiązania dostarczane przez system równoważenia obciążenia.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Równoważenie obciążenia za pomocą powiązania protokołu HTTP podstawowe  
 Z punktu widzenia Równoważenie obciążenia, aplikacji WCF, które komunikują się za pomocą <xref:System.ServiceModel.BasicHttpBinding> są inne niż inne typowe rodzaje HTTP w sieci (statyczne zawartość HTML strony ASP.NET i usług sieci Web ASMX). Kanały programu WCF, korzystające z tego wiązania są założenia bezstanowe i zakończyć swoje połączenia, po zamknięciu kanału. W efekcie <xref:System.ServiceModel.BasicHttpBinding> dobrze działa z istniejącymi równoważenia technik obciążenia HTTP.  
  
 Domyślnie <xref:System.ServiceModel.BasicHttpBinding> wysyła nagłówek połączenia HTTP w komunikatach o `Keep-Alive` wartość, która umożliwia klientom ustanowienia połączeń trwałych usług, które je obsługują. Ta konfiguracja zapewnia zwiększoną przepływność, ponieważ wcześniej ustanowione, że połączenia mogą być ponownie używane do wysyłania kolejnych komunikatów na ten sam serwer. Jednak ponowne użycie połączenia może spowodować klientom stają się silnie skojarzona z określonego serwera w farmie ze zrównoważonym obciążeniem, co zmniejsza skuteczności równoważenia obciążenia działania okrężnego. Jeśli to zachowanie jest niepożądany, HTTP `Keep-Alive` można wyłączyć na serwerze za pomocą <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> właściwość o <xref:System.ServiceModel.Channels.CustomBinding> lub zdefiniowany przez użytkownika <xref:System.ServiceModel.Channels.Binding>. Poniższy przykład pokazuje, jak to zrobić za pomocą konfiguracji.  
  
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
  
 Za pomocą uproszczona konfiguracja wprowadzona w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], samo można osiągnąć przy użyciu następującej konfiguracji uproszczone.  
  
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
  
 Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Równoważenie obciążenia za pomocą powiązania WSHttp i powiązanie WSDualHttp  
 Zarówno <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> może być ze zrównoważonym obciążeniem przy użyciu technik równoważenia obciążenia HTTP, pod warunkiem kilka modyfikacje są dokonywane na domyślne powiązania konfiguracji.  
  
- Wyłącz ustanawiania kontekstu zabezpieczeń: można to osiągnąć przez ustawienie <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwość <xref:System.ServiceModel.WSHttpBinding> do `false`. Alternatywnie, jeśli sesje zabezpieczeń są wymagane, jest możliwość użycia sesji zabezpieczeń stanową, zgodnie z opisem w [Secure sesje](../../../docs/framework/wcf/feature-details/secure-sessions.md) tematu. Sesje zabezpieczeń stanową włączyć usługi jest zachowywana bezstanowe cały stan sesji zabezpieczeń są przesyłane z każdym żądaniem jako część tokenu zabezpieczającego ochrony. Należy pamiętać, że aby włączyć sesji zabezpieczeń stanową, trzeba użyć <xref:System.ServiceModel.Channels.CustomBinding> lub zdefiniowany przez użytkownika <xref:System.ServiceModel.Channels.Binding> jako niezbędną konfigurację ustawienia nie są widoczne na <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> są dostarczane przez system.  
  
- Nie używaj niezawodnych sesji. Ta funkcja jest domyślnie wyłączona.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Powiązanie Net.TCP równoważenia obciążenia  
 <xref:System.ServiceModel.NetTcpBinding> Może być ze zrównoważonym obciążeniem technik równoważenia obciążenia dla warstwy IP. Jednak <xref:System.ServiceModel.NetTcpBinding> pul połączeń TCP domyślnie, aby zmniejszyć czas oczekiwania na połączenie. Jest to optymalizacji, które będzie zakłócać podstawowy mechanizm równoważenia obciążenia. Wartość podstawowa konfiguracja optymalizacji <xref:System.ServiceModel.NetTcpBinding> jest limit czasu dzierżawy, który jest częścią ustawienia puli połączeń. Pula połączeń powoduje, że połączeń klientów z stają się skojarzona z określonych serwerów w farmie. Jak okres istnienia tych połączeń można zwiększyć (współczynnik kontrolowane przez ustawienie limitu czasu dzierżawy), dystrybucji obciążenia na różnych serwerach w farmie staje się niezrównoważone. W wyniku średnią wywołać wzrostu czasu. Tak, korzystając z <xref:System.ServiceModel.NetTcpBinding> w scenariuszach ze zrównoważonym obciążeniem, należy rozważyć zmniejszenie domyślny limit czasu dzierżawy, używanym przez wiązanie. Limit czasu dzierżawy 30 sekund jest uzasadnione punkt początkowy dla scenariuszy z równoważeniem obciążenia, mimo że wartość optymalną jest zależne od aplikacji. Aby uzyskać więcej informacji na temat limitu czasu dzierżawy kanału i innych przydziały dla transportu, zobacz [przydziały dla transportu](../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Aby uzyskać najlepszą wydajność w scenariuszach ze zrównoważonym obciążeniem, należy wziąć pod uwagę przy użyciu <xref:System.ServiceModel.NetTcpSecurity> (albo <xref:System.ServiceModel.SecurityMode.Transport> lub <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Zobacz także

- [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
