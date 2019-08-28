---
title: Wiele punktów końcowych w pojedynczym identyfikatorze ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 8e514b28d9b3719a52d420551c607c49c70738e1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044846"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Wiele punktów końcowych w pojedynczym identyfikatorze ListenUri
Ten przykład pokazuje usługę, która hostuje wiele punktów końcowych `ListenUri`w jednym. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Jak pokazano w przykładzie [wielu punktów końcowych](../../../../docs/framework/wcf/samples/multiple-endpoints.md) , usługa może obsługiwać wiele punktów końcowych, z których każdy ma różne adresy, a także inne powiązania. Ten przykład pokazuje, że możliwe jest hostowanie wielu punktów końcowych o tym samym adresie. Ten przykład ilustruje także różnice między dwoma rodzajami adresów, które ma punkt końcowy usługi: `EndpointAddress` i. `ListenUri`  
  
 `EndpointAddress` Jest to adres logiczny usługi. Jest to adres, na który są adresowane komunikaty protokołu SOAP. `ListenUri` Jest adresem fizycznym usługi. Zawiera informacje o porcie i adresie, w których punkt końcowy usługi faktycznie nasłuchuje komunikatów na bieżącym komputerze. W większości przypadków nie ma potrzeby, aby te adresy różniły się; gdy wartość `ListenUri` nie jest jawnie określona, domyślnie jest identyfikator URI `EndpointAddress` punktu końcowego. W kilku przypadkach warto je rozróżnić, na przykład podczas konfigurowania routera, który może akceptować komunikaty rozkierowane do wielu różnych usług.  
  
## <a name="service"></a>Usługa  
 Usługa w tym przykładzie ma dwie umowy `ICalculator` i. `IEcho` Oprócz niestandardowego `IMetadataExchange` punktu końcowego istnieją trzy punkty końcowe aplikacji, jak pokazano w poniższym kodzie.  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 Wszystkie trzy punkty końcowe są hostowane w `ListenUri` tym samym miejscu i `binding` używają tych samych punktów końcowych `ListenUri` , które mają takie samo powiązanie, ponieważ udostępniają one stos pojedynczego kanału, który nasłuchuje komunikatów na tym adresie fizycznym w maszynie. `address` Każdy punkt końcowy jest identyfikatorem urn; chociaż zazwyczaj adresy reprezentują lokalizacje fizyczne, w rzeczywistości adres może być dowolnym rodzajem identyfikatora URI, ponieważ adres jest używany do dopasowywania i filtrowania, jak pokazano w tym przykładzie.  
  
 Ponieważ wszystkie trzy punkty końcowe mają tę `ListenUri`samą wartość, po nadejściu komunikatu Windows Communication Foundation (WCF) musi zdecydować, który punkt końcowy jest przeznaczony dla wiadomości. Każdy punkt końcowy ma filtr komunikatów składający się z dwóch części: filtr adresów i filtr kontraktu. Filtr adresów dopasowuje `To` komunikat protokołu SOAP do adresu punktu końcowego usługi. Na przykład tylko wysyłane wiadomości `To "Urn:OtherEcho"` są kandydatami dla trzeciego punktu końcowego tej usługi. Filtr kontraktu jest zgodny z akcjami związanymi z operacjami określonego kontraktu. Na przykład komunikaty z akcją `IEcho`. `Echo`dopasowuje filtry umów zarówno dla drugiego, jak i trzeciego punktu końcowego tej usługi, ponieważ oba te punkty końcowe obsługują `IEcho` kontrakt.  
  
 W ten sposób kombinacja filtru adresów i filtru umów umożliwia kierowanie poszczególnych komunikatów docierających `ListenUri` do tej usługi do prawidłowego punktu końcowego. Trzeci punkt końcowy jest zróżnicowany od innych, ponieważ akceptuje komunikaty wysyłane na inny adres z innych punktów końcowych. Pierwszy i drugi punkt końcowy różnią się od siebie w zależności od ich umów (Akcja komunikatu przychodzącego).  
  
## <a name="client"></a>Klient  
 Podobnie jak punkty końcowe na serwerze mają dwa różne adresy, punkty końcowe klienta mają również dwa adresy. Na serwerze i kliencie adres logiczny nosi nazwę `EndpointAddress`. Chociaż adres fizyczny jest wywoływany `ListenUri` na serwerze, na kliencie adres fizyczny nosi `Via`nazwę.  
  
 Tak jak na serwerze, domyślnie te dwa adresy są takie same. Do określenia `Via` na kliencie, który różni się od adresu punktu końcowego, `ClientViaBehavior` jest używany:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Jak zwykle, adres pochodzi z pliku konfiguracji klienta, który został wygenerowany przez Svcutil. exe. (Która odnosi się `ListenUri` do usługi) nie jest wyświetlana w metadanych usługi i dlatego te informacje muszą być przekazywane do klienta poza pasmem (podobnie jak w przypadku adresu metadanych usługi). `Via`  
  
 Klient w tym przykładzie wysyła komunikaty do każdego z trzech punktów końcowych aplikacji serwera, aby wykazać, że może komunikować się z (i odróżnić) wszystkie trzy punkty końcowe, nawet jeśli wszystkie te same `Via`są takie same.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Dla wielu maszyn należy zastąpić localhost w pliku Client.cs nazwą komputera usługi.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
