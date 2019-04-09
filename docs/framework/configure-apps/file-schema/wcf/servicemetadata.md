---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: 0b06d61a33cd6a704a5ab0f75d29bde3f72d77fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115859"
---
# <a name="servicemetadata"></a>\<serviceMetadata>
Określa publikację usługi metadanych i skojarzonych informacji.  
  
\<system.serviceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceMetadata>  
  
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
|externalMetadataLocation|Identyfikator Uri, który zawiera lokalizację pliku WSDL, który jest zwracany do użytkownika w odpowiedzi na żądania WSDL oraz MEX zamiast automatycznie generowanego WSDL. Gdy ten atrybut nie jest ustawiona, wartość domyślna, zwracany jest WSDL. Wartość domyślna to ciąg pusty.|  
|httpGetBinding|Ciąg określający typ powiązania, który będzie używany do pobierania metadanych za pośrednictwem HTTP GET. To ustawienie jest opcjonalne. Jeśli nie zostanie określony, będą używane domyślne powiązania.<br /><br /> Tylko powiązania z elementami wewnętrznymi powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwości powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpGetBindingConfiguration|Ciąg ustawiający nazwę powiązania, który jest określony w `httpGetBinding` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego powiązania. Taką samą nazwę muszą być zdefiniowane w `<bindings>` sekcji.|  
|httpGetEnabled|Wartość logiczna określająca, czy publikować metadane usługi dla pobrania za pomocą żądania HTTP/Get. Wartość domyślna to `false`.<br /><br /> Jeśli nie określono atrybutu httpGetUrl, adres, w którym publikowane są metadane jest adres usługi oraz "? wsdl". Na przykład, jeśli jest adres usługi "http://localhost:8080/CalculatorService", adres metadanych HTTP/Get jest"http://localhost:8080/CalculatorService?wsdl".<br /><br /> Jeśli ta właściwość jest `false`, lub adres usługi nie jest oparty na HTTP lub HTTPS, "? wsdl" zostanie zignorowany.|  
|httpGetUrl|Identyfikator Uri, który określa adres, w którym publikowane są metadane dla pobrania za pomocą żądania HTTP/Get. Jeśli względny identyfikator Uri jest określona, będzie traktowane jak jest określany względem adresu podstawowego tej usługi.|  
|httpsGetBinding|Ciąg określający typ powiązania, które będą używane do pobierania metadanych za pośrednictwem HTTPS GET. To ustawienie jest opcjonalne. Jeśli nie zostanie określony, będą używane domyślne powiązania.<br /><br /> Tylko powiązania z elementami wewnętrznymi powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwości powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpsGetBindingConfiguration|Ciąg ustawiający nazwę powiązania, który jest określony w `httpsGetBinding` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego powiązania. Taką samą nazwę muszą być zdefiniowane w `<bindings>` sekcji.|  
|httpsGetEnabled|Wartość logiczna określająca, czy publikować metadane usługi dla pobrania za pomocą żądania HTTPS/Get. Wartość domyślna to `false`.<br /><br /> Jeśli nie określono atrybutu httpsGetUrl, adres, w którym publikowane są metadane jest adres usługi oraz "? wsdl". Na przykład, jeśli jest adres usługi "https://localhost:8080/CalculatorService", adres metadanych HTTP/Get jest"https://localhost:8080/CalculatorService?wsdl".<br /><br /> Jeśli ta właściwość jest `false`, lub adres usługi nie jest oparty na HTTP lub HTTPS, "? wsdl" zostanie zignorowany.|  
|httpsGetUrl|Identyfikator Uri, który określa adres, w którym publikowane są metadane dla pobrania za pomocą żądania HTTPS/Get.|  
|policyVersion|Ciąg określający używaną wersję specyfikacji WS-Policy używane. Ten atrybut jest typu <xref:System.ServiceModel.Description.PolicyVersion>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji umożliwia kontrolowanie funkcji publikowania metadanych usługi. Aby zapobiegać niezamierzonym ujawnieniem metadanych usługi potencjalnie poufnych, konfigurację domyślną dla usług Windows Communication Foundation (WCF) powoduje wyłączenie publikowania metadanych. To zachowanie jest domyślnie bezpieczny, ale również zaimportować narzędzia (takie jak Svcutil.exe) oznacza, że metadane nie można użyć do wygenerowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie publikowania metadanych usługi w konfiguracji. Korzystając z tego elementu konfiguracji, można włączyć to zachowanie podczas publikowania dla usługi.  
  
 Aby uzyskać szczegółowy przykład konfiguracji tego zachowania, zobacz [zachowanie publikowania metadanych](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).  
  
 Opcjonalny `httpGetBinding` i `httpsGetBinding` atrybutów umożliwiają skonfigurowanie powiązania używane do pobierania metadanych za pośrednictwem HTTP GET (lub HTTPS GET). Jeśli nie są określone, domyślne powiązania (`HttpTransportBindingElement`, w przypadku protokołu HTTP i `HttpsTransportBindingElement`, w przypadku protokołu HTTPS) są używane do pobierania metadanych zgodnie z potrzebami. Należy zauważyć, że nie możesz użyć tych atrybutów z wbudowanych powiązaniami WCF. Tylko powiązania z elementami wewnętrznymi powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwości powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
 Aby zmniejszyć prawdopodobieństwo ujawnienia danych usługi do złośliwych użytkowników, istnieje możliwość bezpiecznego transferu za pomocą protokołu SSL za pośrednictwem mechanizmu HTTP (HTTPS). Aby to zrobić, możesz powiązać odpowiedniego certyfikatu X.509 do określonego portu, na komputerze, który jest hostem usługi. (Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Po drugie, Dodaj ten element do konfiguracji usługi i ustaw `httpsGetEnabled` atrybutu `true`. Wreszcie, ustaw `httpsGetUrl` atrybutu do adresu URL punktu końcowego metadanych usługi, jak pokazano w poniższym przykładzie.  
  
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
 Poniższy przykład Konfigurowanie usługi do udostępnienia metadanych za pomocą \<serviceMetadata w pliku > element. Konfiguruje również punkt końcowy do udostępnienia `IMetadataExchange` kontrakt co implementacją protokołu WS-MetadataExchange (MEX). W przykładzie użyto `mexHttpBinding`, czyli standardowa powiązanie udogodnienie jest odpowiednikiem `wsHttpBinding` tryb zabezpieczeń, ustawiono na `None`. Względna adres "mex" jest używany w punkcie końcowym, który, gdy rozstrzygnięte na usług podstawowy adres skutkuje adres punktu końcowego `http://localhost/servicemodelsamples/service.svc/mex`.  
  
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
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Zachowanie publikowania metadanych](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
