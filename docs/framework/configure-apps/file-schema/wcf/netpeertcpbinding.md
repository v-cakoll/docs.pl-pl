---
title: '&lt;netPeerTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a890243ee12202efa9743a6151255525c7f78be2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltnetpeertcpbindinggt"></a>&lt;netPeerTcpBinding&gt;
Definiuje powiązanie dla równorzędnego kanału określonych dla obsługi wiadomości TCP.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netPeerTcpBinding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netPeerBinding>  
    <binding name="string"  
         closeTimeout="TimeSpan"  
         openTimeout="TimeSpan"   
         receiveTimeout="TimeSpan"  
         sendTimeout="TimeSpan"  
         listenIPAddress="String"  
          maxBufferPoolSize="integer"  
         maxReceiveMessageSize="Integer"   
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|listenIPAddress|Ciąg, który określa adres IP, na którym węzeł elementu równorzędnego będzie nasłuchiwać komunikatów TCP. Wartość domyślna to `null`.|  
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524,288 bajtów (512 * 1024). Bufory za pomocą wielu części programu Windows Communication Foundation (WCF). Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna. Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe. W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, odebranych z kanału skonfigurowane dla tego wiązania. Nadawcy wiadomości przekracza ten limit, zostanie wyświetlony błąd protokołu SOAP. Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|nazwa|Ciąg zawierający nazwę konfiguracji powiązania. Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|port|Liczba całkowita określająca port interfejsu sieciowego, na którym to powiązanie będzie przetwarzało równorzędny kanał komunikatów TCP. Ta wartość musi należeć do zakresu od <xref:System.Net.IPEndPoint.MinPort> i <xref:System.Net.IPEndPoint.MaxPort>. Wartość domyślna to 0.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|sendTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<resolver>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Określa program rozpoznawania elementów równorzędnych używany przez to powiązanie do rozpoznawania elementu równorzędnego ID siatki adresy IP punktu końcowego węzłach w obrębie siatki elementów równorzędnych.|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|Definiuje ustawienia zabezpieczeń dla wiadomości. Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 To powiązanie umożliwia tworzenie aplikacji peer-to-peer lub wielopartyjnej przy użyciu transportu elementu równorzędnego za pośrednictwem protokołu TCP. Każdy węzeł równorzędny może obsługiwać wiele kanałów elementów równorzędnych zdefiniowane przy użyciu tego typu powiązania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, za pomocą tego powiązania NetPeerTcpBinding, która zapewnia wielopartyjnej komunikacji przy użyciu kanału równorzędnego. Szczegółowe scenariusz użycia tego powiązania, zobacz [Net TCP równorzędnej](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
         openTimeout="00:00:20"   
         receiveTimeout="00:00:30"  
         sendTimeout="00:00:40"  
         maxBufferSize="1001"  
         maxConnections="123"   
         maxReceiveMessageSize="1000">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00"  
            enabled="true" />  
        <security mode="TransportWithMessageCredential">  
            <message clientCredentialType="CardSpace" />  
        </security>  
    </binding>  
</netPeerBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NetPeerTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)  
 [NET elementów równorzędnych protokołu TCP](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)  
 [Sieci równorzędne](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
