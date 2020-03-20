---
title: Zachowanie publikowania metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: dade6d1a53fd99b994fb3c027db4e51392bfdcda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144399"
---
# <a name="metadata-publishing-behavior"></a>Zachowanie publikowania metadanych
Przykład zachowania publikowania metadanych pokazuje, jak kontrolować funkcje publikowania metadanych usługi. Aby zapobiec niezamierzonemu ujawnieniu potencjalnie poufnych metadanych usługi, domyślna konfiguracja usług Windows Communication Foundation (WCF) wyłącza publikowanie metadanych. To zachowanie jest domyślnie bezpieczne, ale oznacza również, że nie można użyć narzędzia importu metadanych (na przykład Svcutil.exe) do generowania kodu klienta wymaganego do wywołania usługi, chyba że zachowanie publikowania metadanych usługi jest jawnie włączone w konfiguracji.  
  
> [!IMPORTANT]
> Dla jasności w tym przykładzie pokazano, jak utworzyć niezabezpieczony punkt końcowy publikowania metadanych. Takie punkty końcowe są potencjalnie dostępne dla anonimowych nieuwierzytetycznych konsumentów i należy zwrócić uwagę przed wdrożeniem takich punktów końcowych, aby upewnić się, że publiczne ujawnienie metadanych usługi jest właściwe. Zobacz przykład [niestandardowego bezpiecznego punktu końcowego metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) dla przykładu, który zabezpiecza punkt końcowy metadanych.  
  
 Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` który implementuje umowy serwisowej. W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Aby usługa uwidaczniała <xref:System.ServiceModel.Description.ServiceMetadataBehavior> metadane, musi być skonfigurowana w usłudze. Gdy to zachowanie jest obecny, można opublikować metadane, <xref:System.ServiceModel.Description.IMetadataExchange> konfigurując punkt końcowy, aby udostępnić kontrakt jako implementację protokołu WS-MetadataExchange (MEX). Dla wygody tego kontraktu nadano skróconą nazwę konfiguracji "IMetadataExchange". W tym przykładzie użyto wiązania standardowego, `mexHttpBinding`który `wsHttpBinding` jest odpowiednikiem `None`z trybem zabezpieczeń ustawionym na . Względny adres "mex" jest używany w punkcie końcowym, który po rozwiązaniu względem adresu `http://localhost/servicemodelsamples/service.svc/mex`podstawowego usług powoduje adres końcowy . Poniżej przedstawiono konfigurację zachowania:  
  
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
  
 Poniżej przedstawiono punkt końcowy MEX.  
  
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
  
 W tym <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> przykładzie `true`ustawia właściwość, która również udostępnia metadane usługi przy użyciu protokołu HTTP GET. Aby włączyć punkt końcowy metadanych HTTP GET, usługa musi mieć adres podstawowy HTTP. Ciąg `?wsdl` zapytania jest używany na adres podstawowy usługi, aby uzyskać dostęp do metadanych. Na przykład, aby wyświetlić WSDL dla usługi w przeglądarce sieci Web, należy użyć adresu `http://localhost/servicemodelsamples/service.svc?wsdl`. Alternatywnie można użyć tego zachowania, aby udostępnić <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> metadane za pośrednictwem protokołu HTTPS, ustawiając na `true`. Wymaga to adresu podstawowego HTTPS.  
  
 Aby uzyskać dostęp do punktu końcowego MEX usługi, użyj [narzędzia narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Spowoduje to wygenerowanie klienta na podstawie metadanych usługi.  
  
 Aby uzyskać dostęp do metadanych usługi za `http://localhost/servicemodelsamples/service.svc?wsdl`pomocą protokołu HTTP GET, wskaż przeglądarkę na .  
  
 Jeśli usuniesz to zachowanie i spróbuj otworzyć usługę, otrzymasz wyjątek. Ten błąd występuje, ponieważ bez zachowania, punkt `IMetadataExchange` końcowy skonfigurowany z umową nie ma implementacji.  
  
 Jeśli ustawisz `HttpGetEnabled` , `false`zostanie wyświetlona strona pomocy CalculatorService zamiast wyświetlania metadanych usługi.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
