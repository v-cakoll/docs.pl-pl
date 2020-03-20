---
title: Niestandardowy filtr komunikatów
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 896407a218073eba53676baa4bcbd125593c80ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183889"
---
# <a name="custom-message-filter"></a>Niestandardowy filtr komunikatów
W tym przykładzie pokazano, jak zastąpić filtry wiadomości, które program Windows Communication Foundation (WCF) używa do wysyłania wiadomości do punktów końcowych.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Gdy pierwszy komunikat na kanale dociera do serwera, serwer musi określić, które (jeśli istnieją) punktów końcowych skojarzonych z tym identyfikatorem URI powinien otrzymać komunikat. Proces ten jest <xref:System.ServiceModel.Dispatcher.MessageFilter> kontrolowany przez <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>obiekty dołączone do pliku .  
  
 Każdy punkt końcowy usługi ma <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>jeden . Ma <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> zarówno <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. Unia tych dwóch filtrów jest filtr komunikat używany dla tego punktu końcowego.  
  
 Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> dla punktu końcowego pasuje do każdej wiadomości, która jest skierowana <xref:System.ServiceModel.EndpointAddress>do adresu, który pasuje do punktu końcowego usługi . <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> Domyślnie dla punktu końcowego sprawdza akcję wiadomości przychodzącej i dopasowuje dowolną wiadomość z akcji, która odpowiada jednej z `IsInitiating` = `true` akcji operacji umowy punktu końcowego usługi (tylko akcje są brane pod uwagę). W rezultacie domyślnie filtr dla punktu końcowego jest zgodny tylko wtedy, <xref:System.ServiceModel.EndpointAddress> gdy zarówno nagłówek do wiadomości jest punktem końcowym, a akcja wiadomości odpowiada jednej z akcji operacji punktu końcowego.  
  
 Filtry te można zmienić za pomocą zachowania. W próbce <xref:System.ServiceModel.Description.IEndpointBehavior> usługa tworzy, który <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> zastępuje <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>na:  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 Zdefiniowano dwa filtry adresów:  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 Jest `FilteringEndpointBehavior` konfigurowalny i pozwala na dwie różne odmiany.  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 Odmiana 1 pasuje tylko do adresów, które zawierają "e" (ale które mają jakąkolwiek akcję), podczas gdy Odmiana 2 pasuje tylko do adresów, które nie mają "e":  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 W pliku konfiguracyjnym usługa rejestruje nowe zachowanie:  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 Następnie usługa `endpointBehavior` tworzy konfiguracje dla każdej odmiany:  
  
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
  
 Na koniec punkt końcowy usługi odwołuje się `behaviorConfigurations`do jednego z:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 Implementacja aplikacji klienckiej jest prosta; tworzy dwa kanały do identyfikatora URI usługi (przekazując`via`tę wartość <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> jako drugi ( ) parametr do i wysyła pojedynczą wiadomość na każdym kanale, ale używa różnych adresów punktów końcowych dla każdego. W rezultacie wychodzące wiadomości od klienta mają różne oznaczenia Do, a serwer odpowiednio odpowiada, jak wynika z danych wyjściowych klienta:  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Przełączanie zmiany w pliku konfiguracyjnym serwera powoduje, że filtr ma zostać zamieniony, a klient widzi odwrotne zachowanie (komunikat `urn:e` zakończy się pomyślnie, podczas gdy komunikat kończy się `urn:a` niepowodzeniem).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Aby uruchomić przykład w konfiguracji z jednym komputerem, postępuj zgodnie z instrukcjami w [uruchamianiu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji między komputerami, postępuj zgodnie z instrukcjami w [uruchamianiu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md) i zmień następujący wiersz w Client.cs.  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Zastąp hosta lokalnego nazwą serwera.  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
