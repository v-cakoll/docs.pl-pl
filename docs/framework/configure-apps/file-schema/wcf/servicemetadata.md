---
title: '&lt;serviceMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4e88c6e5f03cef83e640fbca7434d10f82653f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicemetadatagt"></a>&lt;serviceMetadata&gt;
Określa publikację usługi metadanych i skojarzonych informacji.  
  
\<system.serviceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<serviceMetadata >  
  
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
|externalMetadataLocation|Identyfikator Uri zawiera lokalizację pliku WSDL, który jest zwracany do użytkownika w odpowiedzi na żądania WSDL oraz MEX zamiast automatycznie generowanego WSDL. Ten atrybut nie jest ustawiona, wartość domyślna WSDL jest zwracany w trakcie. Wartość domyślna to ciąg pusty.|  
|httpGetBinding|Ciąg określający typ powiązania, który będzie używany do pobierania metadanych za pośrednictwem HTTP GET. To ustawienie jest opcjonalne. Jeśli nie zostanie określony, będą używane domyślne powiązania.<br /><br /> Tylko powiązania z elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwość powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpGetBindingConfiguration|Ciąg ustawiający nazwę powiązania, które jest określone w `httpGetBinding` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego powiązania. Taką samą nazwę, muszą być zdefiniowane w `<bindings>` sekcji.|  
|httpGetEnabled|Wartość logiczna określająca, czy publikować metadane usługi dla pobierania za pomocą żądania HTTP/Get. Wartość domyślna to `false`.<br /><br /> Jeśli nie określono atrybut httpGetUrl, adres, w którym publikowane są metadane jest adres usługi oraz "? wsdl". Na przykład jeśli adres usługi "adresem http://localhost: 8080/CalculatorService", adres metadanych HTTP/Get jest "adresem http://localhost: 8080/CalculatorService? wsdl".<br /><br /> Jeśli ta właściwość jest `false`, lub adres usługi nie jest oparty na HTTP lub HTTPS, "? wsdl" zostanie zignorowany.|  
|httpGetUrl|Identyfikator Uri, który określa adres, w którym publikowane są metadane dla pobierania za pomocą żądania HTTP/Get. Jeśli względny identyfikator Uri jest określony, będzie traktowane jako względem adres podstawowy usługi.|  
|httpsGetBinding|Ciąg określający typ powiązania, które będą używane do pobierania metadanych za pośrednictwem HTTPS GET. To ustawienie jest opcjonalne. Jeśli nie zostanie określony, będą używane domyślne powiązania.<br /><br /> Tylko powiązania z elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwość powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpsGetBindingConfiguration|Ciąg ustawiający nazwę powiązania, które jest określone w `httpsGetBinding` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego powiązania. Taką samą nazwę, muszą być zdefiniowane w `<bindings>` sekcji.|  
|httpsGetEnabled|Wartość logiczna określająca, czy publikować metadane usługi dla pobierania za pomocą żądania HTTPS/Get. Wartość domyślna to `false`.<br /><br /> Jeśli nie określono atrybut httpsGetUrl, adres, w którym publikowane są metadane jest adres usługi oraz "? wsdl". Na przykład jeśli adres usługi "https://localhost:8080/CalculatorService", adres metadanych HTTP/Get jest "https://localhost:8080/CalculatorService? wsdl".<br /><br /> Jeśli ta właściwość jest `false`, lub adres usługi nie jest oparty na HTTP lub HTTPS, "? wsdl" zostanie zignorowany.|  
|httpsGetUrl|Identyfikator Uri, który określa adres, w którym publikowane są metadane dla pobierania za pomocą żądania HTTPS/Get.|  
|PolicyVersion|Ciąg, który określa wersję specyfikacji WS-Policy używane. Ten atrybut jest typu <xref:System.ServiceModel.Description.PolicyVersion>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji służy do kontrolowania funkcji publikowania metadanych usługi. Aby zapobiec przypadkowe ujawnienie metadanych usługi potencjalnie poufnych, konfigurację domyślną dla [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usług wyłącza Publikowanie metadanych. To zachowanie jest domyślnie bezpieczne, ale również zaimportować narzędzia (na przykład Svcutil.exe) oznacza, że metadane nie można użyć do generowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie podczas publikowania metadanych usługi w konfiguracji. Za pomocą tego elementu konfiguracji, można włączyć to zachowanie podczas publikowania dla usługi.  
  
 Aby uzyskać szczegółowy przykład konfiguracji tego zachowania, zobacz [zachowanie podczas publikowania metadanych](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).  
  
 Opcjonalny `httpGetBinding` i `httpsGetBinding` atrybutów umożliwiają konfigurowanie powiązania używane do pobierania metadanych za pośrednictwem HTTP GET (lub HTTPS GET). Jeśli nie są one określone, powiązania domyślnego (`HttpTransportBindingElement`, w przypadku protokołu HTTP i `HttpsTransportBindingElement`, w przypadku protokołu HTTPS) są używane do pobierania metadanych zależnie od potrzeb. Zwróć uwagę, że nie można użyć tych atrybutów z wbudowanych powiązaniami WCF. Tylko powiązania z elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwość powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
 Aby zmniejszyć ryzyko usługi złośliwych użytkowników, jest możliwe do zabezpieczenia przy użyciu protokołu SSL za pośrednictwem protokołu HTTP (HTTPS) mechanizm transferu. Aby to zrobić, należy najpierw powiązać odpowiedniego certyfikatu X.509 określonego portu na komputerze, na którym uruchomiono usługę. ([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Po drugie, Dodaj ten element w konfiguracji usługi i ustaw `httpsGetEnabled` atrybutu `true`. Wreszcie, ustaw `httpsGetUrl` atrybutu na adres URL punktu końcowego metadanych usługi, jak pokazano w poniższym przykładzie.  
  
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
 Poniższy przykład skonfigurować usługę do udostępnienia metadanych za pomocą \<serviceMetadata > elementu. Konfiguruje również punkt końcowy do udostępnienia `IMetadataExchange` kontrakt, co implementacji protokołu WS-MetadataExchange (MEX). W przykładzie użyto `mexHttpBinding`, który jest powiązanie standardowe udogodnienie jest odpowiednikiem `wsHttpBinding` tryb zabezpieczeń ustawiono na `None`. Względny adres "mex" jest używany w punkcie końcowym, w przypadku których nazwy zostały rozstrzygnięte na podstawowej usługi adres powoduje http://localhost/servicemodelsamples/service.svc/mex adres punktu końcowego.  
  
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
          <!-- The serviceMetadata behavior publishes metadata through   
               the IMetadataExchange contract. When this behavior is   
               present, you can expose this contract through an endpoint   
               as shown above. Setting httpGetEnabled to true publishes   
               the service's WSDL at the <baseaddress>?wsdl  
               eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Zachowanie publikowania metadanych](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
