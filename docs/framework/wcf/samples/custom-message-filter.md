---
title: Niestandardowy filtr komunikatów
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 79edba14eff5403591cf43592415d923dbd321be
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716827"
---
# <a name="custom-message-filter"></a>Niestandardowy filtr komunikatów
Ten przykład pokazuje, jak zastąpić filtry komunikatów, które są używane przez Windows Communication Foundation (WCF) do wysyłania wiadomości do punktów końcowych.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Gdy pierwsza wiadomość w kanale dociera do serwera, serwer musi określić, który (Jeśli którykolwiek) punktów końcowych skojarzonych z tym identyfikatorem URI powinien odebrać komunikat. Ten proces jest kontrolowany przez <xref:System.ServiceModel.Dispatcher.MessageFilter> obiekty dołączone do <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Każdy punkt końcowy usługi ma jeden <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> ma zarówno <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>, jak i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. W związku z tymi dwoma filtrami jest stosowany filtr komunikatów dla tego punktu końcowego.  
  
 Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> dla punktu końcowego dopasowuje dowolny komunikat, który jest rozkierowany na adres pasujący do <xref:System.ServiceModel.EndpointAddress>punktu końcowego usługi. Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> dla punktu końcowego sprawdza działanie komunikatu przychodzącego i dopasowuje komunikat z akcją odpowiadającą jednej z akcji związanych z operacjami kontraktu punktu końcowego usługi (tylko `IsInitiating`=akcjami `true`). W związku z tym domyślnie filtr dla punktu końcowego dopasowuje się tylko wtedy, gdy zarówno komunikat do nagłówka jest <xref:System.ServiceModel.EndpointAddress> punktu końcowego, a akcja komunikatu jest zgodna z jedną z akcji punktu końcowego.  
  
 Te filtry można zmienić przy użyciu zachowania. W przykładzie usługa tworzy <xref:System.ServiceModel.Description.IEndpointBehavior>, który zastępuje <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> na <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
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
  
 `FilteringEndpointBehavior` można konfigurować i umożliwiać korzystanie z dwóch różnych odmian.  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 Odmiana 1 dopasowuje tylko adresy, które zawierają "e" (ale z jakąkolwiek akcją), natomiast odmiana 2 dopasowuje tylko adresy, które nie mają "e":  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 W pliku konfiguracji Usługa rejestruje nowe zachowanie:  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 Następnie usługa tworzy `endpointBehavior` konfiguracje dla każdej odmiany:  
  
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
  
 Na koniec punkt końcowy usługi odwołuje się do jednej z `behaviorConfigurations`:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 Implementacja aplikacji klienckiej jest prosta; tworzy dwa kanały dla identyfikatora URI usługi (przez przekazanie tej wartości jako drugi parametr (`via`) do <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> i wysyła pojedynczą wiadomość w każdym kanale, ale używa różnych adresów punktów końcowych dla każdego z nich. W związku z tym komunikaty wychodzące od klienta różnią się w zależności od tego, a serwer odpowiada zgodnie z danymi wyjściowymi klienta:  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Przełączenie zmian w pliku konfiguracji serwera powoduje zamianę filtru, a klient zobaczy zachowanie odwrotne (komunikat, że `urn:e` się powiedzie, podczas gdy komunikat `urn:a` się niepowodzeniem).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Aby uruchomić przykład w konfiguracji pojedynczej maszyny, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji między maszynami, postępuj zgodnie z instrukcjami w temacie [uruchamianie Windows Communication Foundation próbek](../../../../docs/framework/wcf/samples/running-the-samples.md) i zmień następujący wiersz w Client.cs.  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Zastąp wartość localhost nazwą serwera.  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
