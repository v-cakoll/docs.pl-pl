---
title: Zachowanie publikowania metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 60a5884bb8d1189ab758260bf765c321392e1bfe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584366"
---
# <a name="metadata-publishing-behavior"></a>Zachowanie publikowania metadanych
Przykład zachowania publikowania metadanych pokazuje, jak sterować funkcjami publikowania metadanych usługi. Aby zapobiec przypadkowemu ujawnieniu potencjalnie poufnych metadanych usługi, konfiguracja domyślna dla usług Windows Communication Foundation (WCF) wyłącza Publikowanie metadanych. To zachowanie jest domyślnie bezpieczne, ale oznacza to, że nie można użyć narzędzia do importowania metadanych (takiego jak Svcutil. exe) w celu wygenerowania kodu klienta wymaganego do wywołania usługi, chyba że zachowanie publikowania metadanych usługi jest jawnie włączone w konfiguracji.  
  
> [!IMPORTANT]
> Dla jasności ten przykład pokazuje, jak utworzyć niezabezpieczony punkt końcowy publikowania metadanych. Takie punkty końcowe są potencjalnie dostępne dla anonimowych użytkowników nieuwierzytelnionych i należy zachować ostrożność przed wdrożeniem takich punktów końcowych, aby upewnić się, że można publicznie odzamknąć metadane usługi. Zapoznaj się z przykładem [niestandardowego bezpiecznego punktu końcowego metadanych](custom-secure-metadata-endpoint.md) dla przykładu, który zabezpiecza punkt końcowy metadanych.  
  
 Przykład jest oparty na [wprowadzenie](getting-started-sample.md), który implementuje `ICalculator` kontrakt usługi. W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Aby usługa mogła ujawniać metadane, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> należy ją skonfigurować w usłudze. Gdy to zachowanie jest obecne, można opublikować metadane, konfigurując punkt końcowy, aby udostępnić <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt jako implementację protokołu WS-MetadataExchange (Mex). Jako wygoda, ten kontrakt uzyskał skróconą nazwę konfiguracji "kontraktem IMetadataExchange". W tym przykładzie użyto `mexHttpBinding` , który jest wygodnym powiązaniem standardowym, które jest równoważne z `wsHttpBinding` trybem zabezpieczeń ustawionym na `None` . Adres względny "Mex" jest używany w punkcie końcowym, który po rozwiązaniu z adresem podstawowym usług powoduje adres punktu końcowego `http://localhost/servicemodelsamples/service.svc/mex` . Poniżej przedstawiono konfigurację zachowania:  
  
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
  
 Ten przykład ustawia <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> Właściwość na `true` , która udostępnia również metadane usługi przy użyciu protokołu HTTP GET. Aby włączyć punkt końcowy metadanych HTTP GET, usługa musi mieć podstawowy adres HTTP. Ciąg zapytania `?wsdl` jest używany na adresie podstawowym usługi, aby uzyskać dostęp do metadanych. Na przykład, aby wyświetlić WSDL dla usługi w przeglądarce internetowej, należy użyć adresu `http://localhost/servicemodelsamples/service.svc?wsdl` . Alternatywnie można użyć tego zachowania, aby udostępnić metadane za pośrednictwem protokołu HTTPS przez ustawienie opcji <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> na `true` . Wymaga to adresu podstawowego HTTPS.  
  
 Aby uzyskać dostęp do punktu końcowego MEX usługi, użyj [Narzędzia metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Spowoduje to wygenerowanie klienta na podstawie metadanych usługi.  
  
 Aby uzyskać dostęp do metadanych usługi przy użyciu protokołu HTTP GET, wskaż przeglądarkę `http://localhost/servicemodelsamples/service.svc?wsdl` .  
  
 W przypadku usunięcia tego zachowania i próby otworzenia usługi zostanie wyświetlony wyjątek. Ten błąd występuje ze względu na to, że punkt końcowy skonfigurowany dla `IMetadataExchange` kontraktu nie ma implementacji.  
  
 Jeśli ustawisz `HttpGetEnabled` `false` pozycję na, zobaczysz stronę pomocy CalculatorService zamiast wyświetlania metadanych usługi.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
