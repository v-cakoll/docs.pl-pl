---
title: Wiele punktów końcowych w pojedynczym identyfikatorze ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 80a5c18f1e19ef82f490aca705973e027ee0a634
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163907"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Wiele punktów końcowych w pojedynczym identyfikatorze ListenUri
Niniejszy przykład pokazuje usługi, który obsługuje wiele punktów końcowych w pojedynczym `ListenUri`. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Jak pokazano w [wiele punktów końcowych](../../../../docs/framework/wcf/samples/multiple-endpoints.md) próbki, usługa może obsługiwać wiele punktów końcowych, każdy z różnymi adresami i prawdopodobnie również różnych powiązania. Niniejszy przykład pokazuje, że jest możliwe do hostowania wielu punktów końcowych w ten sam adres. Niniejszy przykład pokazuje także różnice między dwoma rodzajami adresy, które ma punkt końcowy usługi: `EndpointAddress` i `ListenUri`.  
  
 `EndpointAddress` To logiczne adres usługi. Jest to adres, który komunikaty protokołu SOAP są adresowane do. `ListenUri` Jest fizyczny adres usługi. Z informacji adres i port gdzie faktycznie nasłuchuje usługa punktu końcowego dla wiadomości na bieżącym komputerze. W większości przypadków nie ma potrzeby dla tych adresów, które mogą się różnić; gdy `ListenUri` nie jest jawnie określona, jego wartość domyślna to identyfikator URI `EndpointAddress` punktu końcowego. W niektórych przypadkach jest przydatne odróżnić je, np. gdy Konfigurowanie routera, który może akceptować komunikaty adresowane do szereg różnych usług.  
  
## <a name="service"></a>Usługa  
 Usługa, w tym przykładzie ma dwa umów `ICalculator` i `IEcho`. Oprócz zwyczajowego `IMetadataExchange` punktu końcowego, istnieją trzy punktów końcowych w aplikacji, jak pokazano w poniższym kodzie.  
  
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
  
 Wszystkie trzy punkty końcowe są hostowane w tym samym `ListenUri` i używać tego samego `binding` — punkty końcowe, w tym samym `ListenUri` musi mieć tego samego powiązania, ponieważ współużytkują stos pojedynczy kanał, który nasłuchuje komunikatów na ten adres fizyczny na maszyny. `address` Każdego punktu końcowego jest nazwa URN; jednak zazwyczaj adresy reprezentują lokalizacjach fizycznych, w rzeczywistości adres może być dowolnym rodzajem identyfikatora URI, ponieważ adres jest używany do dopasowywania i filtrowania, jak przedstawiono w przykładach w tym przykładzie.  
  
 Ponieważ wszystkie trzy punkty końcowe współużytkować ten sam `ListenUri`, po umieszczeniu komunikatu, Windows Communication Foundation (WCF) należy określić punkt końcowy, który komunikat jest przeznaczony dla. Każdy punkt końcowy ma filtr komunikatów, który składa się z dwóch części: filtr adresów i filtr umowy. Filtr adresu pasuje `To` komunikatu protokołu SOAP adres punktu końcowego usługi. Na przykład tylko komunikaty, które zostały rozwiązane `To "Urn:OtherEcho"` nadają się do trzeciego punktu końcowego tej usługi. Filtr umowy dopasowuje akcje skojarzone z operacjami określonej umowy. Na przykład wiadomości z akcją `IEcho`. `Echo` zgodne z filtrami umowy w drugim i trzecim punktów końcowych tej usługi, ponieważ oba te punkty końcowe hosta `IEcho` kontraktu.  
  
 Zatem kombinacja filtr adresów i filtr umowy sprawia, że można kierować każdy komunikat docierający do tej usługi `ListenUri` właściwego punktu końcowego. Trzeci punkt końcowy jest zróżnicowana od dwóch innych, ponieważ akceptuje ona wiadomości wysyłane do innego adresu z innych punktów końcowych. Punkty końcowe pierwszego i drugiego różnią się od siebie nawzajem na podstawie ich umów (Akcja komunikatu przychodzącego).  
  
## <a name="client"></a>Klient  
 Tak, jak punkty końcowe na serwerze ma dwa różne adresy, punktów końcowych klienta również mieć dwa adresy. Na serwerze i kliencie nosi nazwę logiczną adres `EndpointAddress`. Jednakże nosi nazwę adresu fizycznego `ListenUri` na serwerze, na kliencie, nosi nazwę adresu fizycznego `Via`.  
  
 Te dwa adresy na serwerze, domyślnie są takie same. Aby określić `Via` na komputerze klienckim, który jest inny niż adres punktu końcowego `ClientViaBehavior` jest używany:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Jak zwykle adres pochodzą z pliku konfiguracji klienta, który został wygenerowany przez Svcutil.exe. `Via` (Co odpowiada `ListenUri` usługi) nie jest widoczna w metadanych usługi a zatem te informacje muszą być przekazywane klienta poza pasmem (podobnie jak adres metadanych usługi).  
  
 Klient, w tym przykładzie wysyła komunikaty do poszczególnych punktów końcowych serwera trzech aplikacji pokazują, że może komunikować się z (i odróżnienia) wszystkich trzech punktów końcowych, nawet jeśli wszystkie one mają taką samą `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Dla między komputerami można zastąpić localhost w pliku Client.cs o nazwie maszyna usługi.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
