---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: c421273d1d08db047a51f1f1e4f9d6c908f12986
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84201787"
---
# \<serviceMetadata>
Określa publikację metadanych usługi i skojarzonych z nią informacji.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceMetadata externalMetadataLocation="String"
                 httpGetBinding="String"
                 httpGetBindingConfiguration="String"
                 httpGetEnabled="Boolean"
                 httpGetUrl="String"
                 httpsGetBinding="String"
                 httpsGetBindingConfiguration="String"
                 httpsGetEnabled="Boolean"
                 httpsGetUrl="String"
                 policyVersion="Policy12/Policy15" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|externalMetadataLocation|Identyfikator URI, który zawiera lokalizację pliku WSDL, który jest zwracany do użytkownika w odpowiedzi na żądania WSDL i MEX zamiast automatycznie generowanego WSDL. Gdy ten atrybut nie jest ustawiony, zwracany jest domyślny element WSDL. Wartość domyślna to pusty ciąg.|  
|httpGetBinding|Ciąg określający typ powiązania, które będzie używane na potrzeby pobierania metadanych za pośrednictwem protokołu HTTP GET. To ustawienie jest opcjonalne. Jeśli nie zostanie określony, zostaną użyte domyślne powiązania.<br /><br /> Obsługiwane są tylko powiązania z wewnętrznymi elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> . Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwość powiązania musi mieć wartość <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .|  
|httpGetBindingConfiguration|Ciąg określający nazwę powiązania, które jest określone w `httpGetBinding` atrybucie, który odwołuje się do dodatkowych informacji konfiguracyjnych tego powiązania. Ta sama nazwa musi być zdefiniowana w `<bindings>` sekcji.|  
|httpGetEnabled|Wartość logiczna określająca, czy publikować metadane usługi do pobrania za pomocą żądania HTTP/GET. Wartość domyślna to `false`.<br /><br /> Jeśli atrybut httpGetUrl nie jest określony, adres usługi, w którym publikowane są metadane, jest adresem usług i "WSDL". Jeśli na przykład adres usługi to `http://localhost:8080/CalculatorService` , adres HTTP/GET metadanych to `http://localhost:8080/CalculatorService?wsdl` .<br /><br /> Jeśli ta właściwość jest `false` lub adres usługi nie jest oparty na protokole HTTP lub https, "WSDL" jest ignorowany.|  
|httpGetUrl|Identyfikator URI, który określa adres, w którym publikowane są metadane do pobrania za pomocą żądania HTTP/GET. Jeśli określono względny identyfikator URI, będzie on traktowany jako względny w stosunku do adresu podstawowego usługi.|  
|httpsGetBinding|Ciąg określający typ powiązania, które będzie używane na potrzeby pobierania metadanych za pośrednictwem protokołu HTTPS GET. To ustawienie jest opcjonalne. Jeśli nie zostanie określony, zostaną użyte domyślne powiązania.<br /><br /> Obsługiwane są tylko powiązania z wewnętrznymi elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> . Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwość powiązania musi mieć wartość <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .|  
|httpsGetBindingConfiguration|Ciąg określający nazwę powiązania, które jest określone w `httpsGetBinding` atrybucie, który odwołuje się do dodatkowych informacji konfiguracyjnych tego powiązania. Ta sama nazwa musi być zdefiniowana w `<bindings>` sekcji.|  
|httpsGetEnabled|Wartość logiczna określająca, czy publikować metadane usługi do pobrania za pomocą żądania HTTPS/GET. Wartość domyślna to `false`.<br /><br /> Jeśli atrybut httpsGetUrl nie jest określony, adres usługi, w którym publikowane są metadane, jest adresem usług i "WSDL". Jeśli na przykład adres usługi to " https://localhost:8080/CalculatorService ", adres HTTP/GET metadanych to " https://localhost:8080/CalculatorService?wsdl ".<br /><br /> Jeśli ta właściwość jest `false` lub adres usługi nie jest oparty na protokole HTTP lub https, "WSDL" jest ignorowany.|  
|httpsGetUrl|Identyfikator URI, który określa adres, w którym publikowane są metadane do pobrania za pomocą żądania HTTPS/GET.|  
|policyVersion|Ciąg określający używaną wersję specyfikacji WS-Policy. Ten atrybut jest typu <xref:System.ServiceModel.Description.PolicyVersion> .|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji umożliwia kontrolowanie funkcji publikowania metadanych usługi. Aby zapobiec przypadkowemu ujawnieniu potencjalnie poufnych metadanych usługi, konfiguracja domyślna dla usług Windows Communication Foundation (WCF) wyłącza Publikowanie metadanych. To zachowanie jest domyślnie bezpieczne, ale oznacza to, że nie można użyć narzędzia do importowania metadanych (takiego jak Svcutil. exe) w celu wygenerowania kodu klienta wymaganego do wywołania usługi, chyba że zachowanie publikowania metadanych usługi jest jawnie włączone w konfiguracji. Za pomocą tego elementu konfiguracji można włączyć to zachowanie publikowania dla usługi.  
  
 Szczegółowy przykład konfigurowania tego zachowania znajduje się w temacie [zachowanie publikowania metadanych](../../../wcf/samples/metadata-publishing-behavior.md).  
  
 Opcjonalne `httpGetBinding` i `httpsGetBinding` atrybuty umożliwiają skonfigurowanie powiązań używanych na potrzeby pobierania metadanych za pośrednictwem protokołu HTTP GET (lub HTTPS GET). Jeśli nie są one określone, domyślne powiązania ( `HttpTransportBindingElement` w przypadku protokołu HTTP i `HttpsTransportBindingElement` , w przypadku protokołu HTTPS) są używane do pobierania metadanych zgodnie z potrzebami. Należy zauważyć, że nie można używać tych atrybutów z wbudowanymi powiązaniami programu WCF. Obsługiwane są tylko powiązania z wewnętrznymi elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> . Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwość powiązania musi mieć wartość <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .  
  
 Aby zmniejszyć narażenie usługi na złośliwych użytkowników, można zabezpieczyć transfer przy użyciu mechanizmu protokołu SSL przez HTTP (HTTPS). W tym celu należy najpierw powiązać odpowiedni certyfikat X. 509 z określonym portem na komputerze hostującym usługę. (Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).) Następnie należy dodać ten element do konfiguracji usługi i ustawić `httpsGetEnabled` atrybut na `true` . Na koniec Ustaw `httpsGetUrl` atrybut na adres URL punktu końcowego metadanych usługi, jak pokazano w poniższym przykładzie.  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="NewBehavior">
      <serviceMetadata httpsGetEnabled="true"
                       httpsGetUrl="https://myComputerName/myEndpoint" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia skonfigurowanie usługi do uwidaczniania metadanych przy użyciu \<serviceMetadata> elementu. Umożliwia również skonfigurowanie punktu końcowego w celu udostępnienia `IMetadataExchange` kontraktu jako implementacji protokołu WS-MetadataExchange (Mex). W przykładzie użyto `mexHttpBinding` , który jest wygodnym powiązaniem standardowym, które jest równoważne z `wsHttpBinding` trybem zabezpieczeń ustawionym na `None` . Adres względny "Mex" jest używany w punkcie końcowym, który po rozwiązaniu z adresem podstawowym usług powoduje adres punktu końcowego `http://localhost/servicemodelsamples/service.svc/mex` .  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Zachowanie publikowania metadanych](../../../wcf/samples/metadata-publishing-behavior.md)
