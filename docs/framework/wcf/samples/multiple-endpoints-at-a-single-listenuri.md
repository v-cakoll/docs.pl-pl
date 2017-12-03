---
title: "Wiele punktów końcowych w pojedynczym identyfikatorze ListenUri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8860749430d1c6ec1f9b89c1a9740b836ff28ae9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Wiele punktów końcowych w pojedynczym identyfikatorze ListenUri
W tym przykładzie pokazano, usługa, która obsługuje wiele punktów końcowych w pojedynczym `ListenUri`. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Jak pokazano w [wiele punktów końcowych](../../../../docs/framework/wcf/samples/multiple-endpoints.md) przykład usługa może obsługiwać wiele punktów końcowych, każde z nich różne adresy i prawdopodobnie również różnych powiązania. W tym przykładzie pokazano, czy jest możliwe do hostowania wiele punktów końcowych w ten sam adres. W tym przykładzie przedstawiono również różnice między dwa rodzaje adresów, które ma punkt końcowy usługi: `EndpointAddress` i `ListenUri`.  
  
 `EndpointAddress` Jest adresów logicznych usługi. Jest wiadomości SOAP są wysyłane na adres. `ListenUri` To adres fizyczny usługi. Z informacji adres i port której faktycznie nasłuchuje usługa punktu końcowego wiadomości na bieżącym komputerze. W większości przypadków nie istnieje potrzeba dla tych adresów mogą się różnić; gdy `ListenUri` nie jest jawnie określona, domyślnie identyfikator URI `EndpointAddress` punktu końcowego. W niektórych przypadkach warto odróżnić je, np. podczas konfigurowania routera, który może akceptować komunikaty adresowane do szereg różnych usług.  
  
## <a name="service"></a>Usługa  
 Usługi w tym przykładzie ma dwa kontrakty `ICalculator` i `IEcho`. Oprócz zwyczajowe `IMetadataExchange` punktu końcowego, istnieją trzy punkty końcowe aplikacji, jak pokazano w poniższym kodzie.  
  
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
  
 Wszystkie trzy punkty końcowe znajdują się w tym samym `ListenUri` i używać tego samego `binding` — punkty końcowe w tym samym `ListenUri` musi mieć tego samego powiązania, ponieważ są one udostępnianie stosu pojedynczego kanału, który wiadomości pod tym adresem fizycznym nasłuchuje maszyny. `address` Każdego punktu końcowego jest identyfikatorem URN; chociaż zazwyczaj adresy reprezentują lokalizacje fizyczne, w rzeczywistości adres może być dowolny rodzaj identyfikatora URI, ponieważ adres jest używany do dopasowywania i ich filtrowania, jak przedstawiono w przykładach w tym przykładzie.  
  
 Ponieważ wszystkie trzy punkty końcowe mają takie same `ListenUri`, po nadejściu wiadomości, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] należy zdecydować, który punkt końcowy komunikatu jest przeznaczony do. Każdy punkt końcowy ma filtr komunikatu, który składa się z dwóch części: filtr adresów i filtr umowy. Kryteria filtru adresu `To` wiadomości SOAP adres punktu końcowego usługi. Na przykład tylko komunikaty adresowane `To "Urn:OtherEcho"` nadają się do trzeciego punktu końcowego tej usługi. Akcje skojarzone z operacjami określonej umowy spełniają kryteria filtru kontraktu. Na przykład wiadomości z akcją `IEcho`. `Echo`Dopasowuje filtry kontraktu w drugim i innych punktów końcowych tej usługi, ponieważ oba te punkty końcowe hosta `IEcho` kontraktu.  
  
 W związku z tym kombinację adresu filtry i kontrakt umożliwia trasy każdy komunikat przychodzący w tej usłudze `ListenUri` do właściwego punktu końcowego. Trzeci punktu końcowego jest zróżnicowana od dwóch innych, ponieważ akceptuje on komunikaty wysyłane do innego adresu z innych punktów końcowych. Pierwszy i drugi punktów końcowych, które różnią się od siebie na podstawie ich umów (Akcja wiadomości przychodzącej).  
  
## <a name="client"></a>Klient  
 Tak samo, jak punkty końcowe na serwerze ma dwa różne adresy, punktów końcowych klienta również mieć dwa adresy. Na serwerze i kliencie adresów logicznych jest nazywany `EndpointAddress`. Jednakże adres fizyczny jest nazywany `ListenUri` na serwerze, na kliencie, jest nazywany adresu fizycznego `Via`.  
  
 Na serwerze, domyślnie obu tych adresów są takie same. Aby określić `Via` na kliencie, który różni się od adresu punktu końcowego `ClientViaBehavior` jest używany:  
  
```  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Jak zwykle adres pochodzi z pliku konfiguracji klienta, który został wygenerowany przez Svcutil.exe. `Via` (Które odpowiada `ListenUri` usługi) nie ma w metadanych usługi i dlatego te informacje muszą być przekazywane klienta poza pasmem (podobnie jak adres metadanych usługi).  
  
 W tym przykładzie klient wysyła komunikaty do każdego z punktów końcowych aplikacji trzy serwera wykazać, że może komunikować się z (i odróżnienia) wszystkich trzech punktów końcowych, nawet jeśli wszystkie mają takie same `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Dla między komputerami należy zastąpić localhost w pliku Client.cs o nazwie maszyna usługi.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a>Zobacz też
