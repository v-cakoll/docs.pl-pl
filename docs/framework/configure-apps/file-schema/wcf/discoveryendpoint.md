---
title: '&lt;obiektu discoveryEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be4dc40327f7d1bfa713cefe80908cdba5bc7101
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiscoveryendpointgt"></a>&lt;obiektu discoveryEndpoint&gt;

Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem odkrywania. Po dodaniu do konfiguracji usługi, określa gdzie nasłuchiwać komunikatów odnajdywania. Po dodaniu do konfiguracji klienta Określa gdzie wysyłanie zapytań odnajdywania.  
  
\<system.serviceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Składnia

```xml
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed" 
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxResponseDelay="Timespan" 
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty

| Atrybut        | Opis |  
| ---------------- | ----------- |  
| discoveryMode    | Ciąg, który określa tryb protokół RDP. Prawidłowe wartości to "Ad hoc" i "Zarządzany". W trybie zarządzanym protokołu zależy od serwera Proxy odnajdywania, która działa jako repozytorium wykrywalny usług. W trybie ad hoc wymagane używany protokół UDP mechanizmu multiemisji można znaleźć dostępne usługi. Aby uzyskać więcej informacji dotyczących właściwości, zobacz <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>. |  
| discoveryVersion | Ciąg, który określa jeden z dwóch wersji protokołu WS-Discovery. Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005. Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Wartość Timespan określający maksymalną wartość opóźnienia odnajdywania protokołu będzie czekać przed wysłaniem niektóre komunikaty, takie jak sondowania Match lub rozwiązać dopasowania.<br /><br /> Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może spowodować storm sieci. Aby temu zapobiec, ProbeMatches są wysyłane z losowego opóźnienia między każdym ProbeMatch. Opóźnienie losowe jest z zakresu od 0 do wartości tego atrybutu. Jeśli ten atrybut jest ustawiony na 0, ProbeMatches komunikaty są wysyłane w pętli ścisłej bez opóźnień. W przeciwnym razie ProbeMatches komunikaty są wysyłane z niektórych losowe opóźnienie tak, aby całkowity czas wykonywania wszystkich wysyłać ProbeMatches nie przekracza maxResponseDelay. Ta wartość ma zastosowanie tylko dla usług, nie jest on używany przez klientów. |  
| `name`           | Ciąg określający nazwę Konfiguracja standardowego punktu końcowego. Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji. |  
  
### <a name="child-elements"></a>Elementy podrzędne

Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |  
| ------- | ----------- |  
| [\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe. |  
  
## <a name="example"></a>Przykład

W poniższym przykładzie pokazano usługi nasłuchiwania komunikatów odnajdywania za pośrednictwem elementu równorzędnego net transportu multiemisji. W przykładzie jawnie określa WS-Discovery wersji z kwietnia 2005.  
  
Konfiguracja standardowego punktu końcowego jest zdefiniowany dla usługi i nie może być współużytkowana przez usługę. Inna usługa chcą mieć tego samego punktu końcowego odnajdywania, taką samą konfigurację musi zostać dodany do sekcji tej usługi.  
  
```xml
<services>  
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding" 
              address="calculator" 
              contract="ICalculatorService" />  
    <endpoint name="peerNetDiscovery"  
              binding="peerTcpBinding"  
              address="net.p2p://discoveryMesh/multicast"  
              kind="discoveryEndpoint"  
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"  
              bindingConfiguration="discoveryPeerTcpBindingConfig" />      
  </service>  
</services>  
<standardEndpoints>  
  <discoveryEndpoint>  
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"                         
                      version="WSDiscoveryApril2005" />  
  </discoveryEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a>Zobacz także

<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
