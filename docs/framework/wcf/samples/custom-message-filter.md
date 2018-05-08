---
title: Niestandardowy filtr komunikatów
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: d01fd0d08a7f5d9b12007bc22a26e6f08e006b64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="custom-message-filter"></a>Niestandardowy filtr komunikatów
W tym przykładzie pokazano, jak zastąpić filtry wiadomości Windows Communication Foundation (WCF) używanych do wysyłania wiadomości do punktów końcowych.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Podczas pierwszej wiadomości w kanale dociera do serwera, serwer musi określenie (jeśli istnieją) z punktów końcowych skojarzonych z tym identyfikatorem URI powinien zostać wyświetlony komunikat. Ten proces jest kontrolowany przez <xref:System.ServiceModel.Dispatcher.MessageFilter> obiektów dołączonych do <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Każdy punkt końcowy usługi ma jeden <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Ma zarówno atrybut <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. Unia te dwa filtry jest używany dla tego punktu końcowego filtr komunikatu.  
  
 Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> dla punktu końcowego odpowiada wiadomości, które są skierowane do adresu pasującego do punktu końcowego usługi <xref:System.ServiceModel.EndpointAddress>. Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> dla punktu końcowego bada akcji wiadomości przychodzącej i dopasowuje dowolny komunikat z akcji, która odpowiada jednej z akcji kontraktu punktu końcowego usługi operations (tylko `IsInitiating` = `true`akcje są traktowane jako). W związku z tym domyślnie filtr dla punktu końcowego jest zgodny tylko w przypadku obu komunikatu do nagłówka <xref:System.ServiceModel.EndpointAddress> punktu końcowego i komunikatu akcji odpowiada jednej akcji Operacja punktu końcowego.  
  
 Filtry można zmienić za pomocą zachowania. W przykładzie tworzy usługę <xref:System.ServiceModel.Description.IEndpointBehavior> zastępuje <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> na <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 Zdefiniowano dwa filtry adresów:  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 `FilteringEndpointBehavior` Można konfigurować i pozwala na dwóch różnych zmian.  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 Zmiana 1 jest zgodna tylko adresy zawierające "e" (ale mają żadnych działań) należy odmiany 2 zgodny tylko adresy, których brakuje "e":  
  
```  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 W pliku konfiguracji usługi rejestruje nowe zachowanie:  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 Tworzy usługę, a następnie `endpointBehavior` konfiguracje dla każdej zmiany:  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 Na koniec punktu końcowego usługi odwołuje się do jednego z `behaviorConfigurations`:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 Implementacja aplikacja kliencka jest bezpośrednie; tworzy dwa kanały do identyfikatora URI usługi (przez przekazywanie tej wartości jako drugi (`via`) parametr <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> i wysyła pojedynczy komunikat na poszczególnych kanałów, ale używa adresy różnych punktów końcowych dla każdego. W związku z tym komunikaty wychodzące z klienta mają różne do oznaczenia, a serwer odpowiada, w związku z tym, jak pokazano w danych wyjściowych klienta:  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Przełączanie zmiany w pliku konfiguracji serwera powoduje, że filtr zamianę i klient widzi przeciwną zachowanie (komunikat `urn:e` zakończy się powodzeniem, podczas gdy komunikat, który ma `urn:a` nie powiedzie się).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Aby uruchomić przykładowy w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) i zmień następujący wiersz w Client.cs.  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Zamień na nazwę serwera hosta lokalnego.  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
  
## <a name="see-also"></a>Zobacz też
