---
title: Wiele punktów końcowych w pojedynczym identyfikatorze ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 8e26cc18ed35c446dda120c678dd7e879c756c0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183487"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Wiele punktów końcowych w pojedynczym identyfikatorze ListenUri
W tym przykładzie pokazano usługę, która obsługuje `ListenUri`wiele punktów końcowych w jednym . Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Jak pokazano w próbce [wiele punktów końcowych,](../../../../docs/framework/wcf/samples/multiple-endpoints.md) usługa może obsługiwać wiele punktów końcowych, każdy z różnych adresów i ewentualnie również różne powiązania. W tym przykładzie pokazano, że jest możliwe hostowanie wielu punktów końcowych pod tym samym adresem. W tym przykładzie pokazano również różnice między dwoma rodzajami `EndpointAddress` adresów, które ma punkt końcowy usługi: i `ListenUri`.  
  
 Jest `EndpointAddress` to logiczny adres usługi. Jest to adres, do którego adresowane są komunikaty SOAP. Jest `ListenUri` to adres fizyczny usługi. Ma informacje o porcie i adresie, w którym punkt końcowy usługi faktycznie nasłuchuje wiadomości na bieżącym komputerze. W większości przypadków nie ma potrzeby, aby te adresy się różniły; gdy `ListenUri` nie jest jawnie określony, domyślnie do `EndpointAddress` identyfikatora URI punktu końcowego. W kilku przypadkach warto je odróżnić, na przykład podczas konfigurowania routera, który może akceptować wiadomości zaadresowane do wielu różnych usług.  
  
## <a name="service"></a>Usługa  
 Usługa w tym przykładzie `ICalculator` ma `IEcho`dwie umowy i . Oprócz niestandardowego punktu `IMetadataExchange` końcowego istnieją trzy punkty końcowe aplikacji, jak pokazano w poniższym kodzie.  
  
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
  
 Wszystkie trzy punkty końcowe są `ListenUri` hostowane w `binding` tym samym czasie `ListenUri` i używają tego samego — punkty końcowe w tym samym musi mieć to samo powiązanie, ponieważ są one udostępnianie stosu pojedynczego kanału, który nasłuchuje wiadomości pod tym adresem fizycznym na komputerze. Każdy `address` punkt końcowy jest URN; chociaż zazwyczaj adresy reprezentują lokalizacje fizyczne, w rzeczywistości adres może być dowolnego rodzaju identyfikatora URI, ponieważ adres jest używany do dopasowywania i filtrowania celów, jak pokazano w tym przykładzie.  
  
 Ponieważ wszystkie trzy punkty końcowe współużytkują to samo `ListenUri`, gdy pojawi się tam komunikat, Windows Communication Foundation (WCF) musi zdecydować, do którego punktu końcowego jest przeznaczona wiadomość. Każdy punkt końcowy ma filtr wiadomości, który składa się z dwóch części: filtr adresu i filtr kontraktu. Filtr adresu jest `To` zgodny z komunikatem SOAP na adres punktu końcowego usługi. Na przykład tylko `To "Urn:OtherEcho"` komunikaty adresowane są kandydatami do trzeciego punktu końcowego tej usługi. Filtr kontraktu jest zgodny z akcjami skojarzonymi z operacjami określonego kontraktu. Na przykład wiadomości z `IEcho`działaniem . `Echo`dopasowuje filtry kontraktu zarówno drugiego, jak i trzeciego punktu końcowego tej `IEcho` usługi, ponieważ oba te punkty końcowe obsługują kontrakt.  
  
 W ten sposób połączenie filtru adresów i filtru kontraktu umożliwia `ListenUri` kierowanie każdej wiadomości, która dociera do tej usługi do prawidłowego punktu końcowego. Trzeci punkt końcowy różni się od pozostałych dwóch, ponieważ akceptuje wiadomości wysyłane na inny adres niż inne punkty końcowe. Pierwszy i drugi punkty końcowe różnią się od siebie na podstawie ich umów (Akcja wiadomości przychodzącej).  
  
## <a name="client"></a>Klient  
 Podobnie jak punkty końcowe na serwerze mają dwa różne adresy, punkty końcowe klienta mają również dwa adresy. Zarówno na serwerze, jak i `EndpointAddress`na kliencie adres logiczny jest nazywany . Ale podczas gdy adres fizyczny jest nazywany `ListenUri` na serwerze, na `Via`kliencie adres fizyczny jest nazywany .  
  
 Podobnie jak na serwerze, domyślnie te dwa adresy są takie same. Aby określić `Via` na kliencie, który różni się `ClientViaBehavior` od adresu punktu końcowego, jest używany:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Jak zwykle adres pochodzi z pliku konfiguracji klienta, który został wygenerowany przez Svcutil.exe. (który `Via` odpowiada `ListenUri` usługi) nie pojawia się w metadanych usługi, a więc te informacje muszą być przekazywane do klienta poza pasmem (podobnie jak adres metadanych usługi).  
  
 Klient w tym przykładzie wysyła komunikaty do każdego z trzech punktów końcowych aplikacji serwera, aby wykazać, że może komunikować się (i odróżniać) wszystkie trzy punkty końcowe, nawet jeśli wszystkie mają takie same `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > W przypadku komputera między komputerem należy zastąpić hosta lokalnego w pliku Client.cs nazwą komputera serwisowego.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
