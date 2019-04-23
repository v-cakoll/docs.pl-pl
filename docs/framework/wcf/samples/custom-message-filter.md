---
title: Niestandardowy filtr komunikatów
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 34e6d851bd0aa3515c5c43521be6213451b7ed12
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773080"
---
# <a name="custom-message-filter"></a>Niestandardowy filtr komunikatów
Niniejszy przykład pokazuje, jak zastąpić filtry komunikatów, używane przez program Windows Communication Foundation (WCF) do wysyłania wiadomości do punktów końcowych.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Podczas pierwszego komunikatu w kanale dociera do serwera, serwera należy określić, które (jeśli istnieje) punktów końcowych skojarzonych z tym, że identyfikator URI powinien zostać wyświetlony komunikat. Ten proces jest kontrolowana przez <xref:System.ServiceModel.Dispatcher.MessageFilter> obiektów dołączonych do <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Każdy punkt końcowy usługi ma jeden <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Znajdują się oba <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. Sumę tych dwóch filtrów jest używany dla tego punktu końcowego filtr komunikatu.  
  
 Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> wiadomości, które są skierowane do adresu, który pasuje do punktu końcowego usługi jest zgodna z punktu końcowego <xref:System.ServiceModel.EndpointAddress>. Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> dla punktu końcowego sprawdza akcję wiadomości przychodzącej i dopasowuje każdy komunikat z akcją, która odpowiada jednemu akcje operacji kontraktu punktu końcowego usługi (tylko `IsInitiating` = `true`akcje są traktowane jako). Co w efekcie domyślnie filtr dla punktu końcowego jest zgodny tylko w przypadku obu komunikatu do nagłówka <xref:System.ServiceModel.EndpointAddress> punktu końcowego i działań wiadomości pasuje do jednej akcji operacji punktu końcowego.  
  
 Filtry te można zmienić za pomocą zachowania. W tym przykładzie tworzy usługę <xref:System.ServiceModel.Description.IEndpointBehavior> zastępuje <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> na <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
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
  
 `FilteringEndpointBehavior` Można konfigurować i pozwala na dwie różne odmiany.  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 Odmiana 1 odpowiada tylko adresy, które zawierają "e" (ale mają dowolną akcję) natomiast 2 odmiany pasuje tylko adresy, które nie mają "e":  
  
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
  
 A następnie tworzy usługę `endpointBehavior` konfiguracje dla poszczególnych odmian:  
  
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
  
 Implementacja aplikacja kliencka jest prosta; tworzy on dwa kanały do identyfikatora URI usługi (przez przekazanie wartości jako drugi (`via`) parametr <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> i wysyła pojedynczy komunikat z poszczególnych kanałów, ale używa adresy różnych punktów końcowych dla każdego. W rezultacie komunikaty wychodzące z klienta mają różne do oznaczenia, a serwer odpowiada, w związku z tym, jak pokazano w danych wyjściowych klienta:  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Przełączanie zmiany w pliku konfiguracji serwera powoduje, że filtr, które mają być zamienione i klient widzi przeciwny zachowanie (komunikat, który ma `urn:e` zakończy się powodzeniem, natomiast komunikat, który ma `urn:a` nie powiedzie się).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Do uruchomienia przykładu w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji między komputerami, postępuj zgodnie z instrukcjami w artykule [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) i zmień następujący wiersz w Client.cs.  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Zastąp ciąg localhost nazwę serwera.  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
