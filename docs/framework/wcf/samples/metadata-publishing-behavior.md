---
title: Zachowanie publikowania metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 547ff9fcaca8b9af7a7559a11ef4c4a8b5996174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505524"
---
# <a name="metadata-publishing-behavior"></a>Zachowanie publikowania metadanych
Przykład zachowania publikowania metadanych pokazuje, jak do kontrolowania funkcji publikowania metadanych usługi. Aby zapobiec przypadkowe ujawnienie metadanych usługi potencjalnie poufnych, konfigurację domyślną dla usług Windows Communication Foundation (WCF) wyłącza Publikowanie metadanych. To zachowanie jest domyślnie bezpieczne, ale również zaimportować narzędzia (na przykład Svcutil.exe) oznacza, że metadane nie można użyć do generowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie podczas publikowania metadanych usługi w konfiguracji.  
  
> [!IMPORTANT]
>  Dla jasności ten przykład przedstawia sposób tworzenia punkt końcowy publikowania metadanych niezabezpieczona. Takie punkty końcowe są potencjalnie dostępne dla anonimowych użytkowników nieuwierzytelnionych i należy uważać przed wdrożeniem takich punktów końcowych w celu zapewnienia publicznie ujawniająca metadanych usługi odpowiednie. Zobacz [punktu końcowego metadanych niestandardowy bezpieczny](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) próbkowania dla przykładu, która zabezpiecza punktu końcowego metadanych.  
  
 Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi. W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Usługi do udostępnienia metadanych <xref:System.ServiceModel.Description.ServiceMetadataBehavior> musi być skonfigurowany w usłudze. Jeśli jest to zachowanie, konfigurując punkt końcowy do udostępnienia można opublikować metadanych <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt, co implementacji protokołu WS-MetadataExchange (MEX). Dla wygody tego kontraktu została podana nazwa skrócona konfiguracji "IMetadataExchange". W przykładzie użyto `mexHttpBinding`, który jest powiązanie standardowe udogodnienie jest odpowiednikiem `wsHttpBinding` tryb zabezpieczeń ustawiono na `None`. Względny adres "mex" jest używany w punkcie końcowym, w przypadku których nazwy zostały rozstrzygnięte na podstawowej usługi adres powoduje adres punktu końcowego http://localhost/servicemodelsamples/service.svc/mex. Poniżej przedstawiono konfigurację zachowania:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Poniżej przedstawiono punktu końcowego MEX.  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 W tym przykładzie ustawia <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true`, który udostępnia również metadanych usługi przy użyciu HTTP GET. Aby włączyć punkt końcowy metadanych HTTP GET, usługa musi mieć określony podstawowy adres HTTP. Ciąg zapytania `?wsdl` na adres podstawowy usługi służy do uzyskania dostępu metadanych. Na przykład, aby zobaczyć WSDL dla usługi w przeglądarce sieci Web możesz użyć adresu http://localhost/servicemodelsamples/service.svc?wsdl. Alternatywnie można użyć tego zachowania do udostępnienia metadanych za pośrednictwem protokołu HTTPS przez ustawienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> do `true`. Wymaga to podstawowy adres HTTPS.  
  
 Użyj punktu końcowego MEX usługi dostępu do [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Spowoduje to wygenerowanie klienta na podstawie metadanych usługi.  
  
 Aby uzyskać dostęp do metadanych usługi przy użyciu HTTP GET, należy wskazać przeglądarkę, aby http://localhost/servicemodelsamples/service.svc?wsdl.  
  
 Usuń ten problem i spróbuj otworzyć usługi spowoduje wyświetlenie Wystąpił wyjątek. Ten błąd występuje, ponieważ bez zachowania, punkt końcowy skonfigurowany z `IMetadataExchange` kontraktu ma implementacji.  
  
 Jeśli ustawisz `HttpGetEnabled` do `false`, zostanie wyświetlona strona pomocy CalculatorService zamiast metadanych usługi.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a>Zobacz też
