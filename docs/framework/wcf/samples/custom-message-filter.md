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
# <a name="custom-message-filter"></a><span data-ttu-id="5149c-102">Niestandardowy filtr komunikatów</span><span class="sxs-lookup"><span data-stu-id="5149c-102">Custom Message Filter</span></span>
<span data-ttu-id="5149c-103">W tym przykładzie pokazano, jak zastąpić filtry wiadomości, które program Windows Communication Foundation (WCF) używa do wysyłania wiadomości do punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="5149c-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5149c-104">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5149c-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5149c-105">Gdy pierwszy komunikat na kanale dociera do serwera, serwer musi określić, które (jeśli istnieją) punktów końcowych skojarzonych z tym identyfikatorem URI powinien otrzymać komunikat.</span><span class="sxs-lookup"><span data-stu-id="5149c-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="5149c-106">Proces ten jest <xref:System.ServiceModel.Dispatcher.MessageFilter> kontrolowany przez <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>obiekty dołączone do pliku .</span><span class="sxs-lookup"><span data-stu-id="5149c-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="5149c-107">Każdy punkt końcowy usługi ma <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>jeden .</span><span class="sxs-lookup"><span data-stu-id="5149c-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="5149c-108">Ma <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> zarówno <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="5149c-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="5149c-109">Unia tych dwóch filtrów jest filtr komunikat używany dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="5149c-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="5149c-110">Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> dla punktu końcowego pasuje do każdej wiadomości, która jest skierowana <xref:System.ServiceModel.EndpointAddress>do adresu, który pasuje do punktu końcowego usługi .</span><span class="sxs-lookup"><span data-stu-id="5149c-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="5149c-111"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> Domyślnie dla punktu końcowego sprawdza akcję wiadomości przychodzącej i dopasowuje dowolną wiadomość z akcji, która odpowiada jednej z `IsInitiating` = `true` akcji operacji umowy punktu końcowego usługi (tylko akcje są brane pod uwagę).</span><span class="sxs-lookup"><span data-stu-id="5149c-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="5149c-112">W rezultacie domyślnie filtr dla punktu końcowego jest zgodny tylko wtedy, <xref:System.ServiceModel.EndpointAddress> gdy zarówno nagłówek do wiadomości jest punktem końcowym, a akcja wiadomości odpowiada jednej z akcji operacji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="5149c-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="5149c-113">Filtry te można zmienić za pomocą zachowania.</span><span class="sxs-lookup"><span data-stu-id="5149c-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="5149c-114">W próbce <xref:System.ServiceModel.Description.IEndpointBehavior> usługa tworzy, który <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> zastępuje <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>na:</span><span class="sxs-lookup"><span data-stu-id="5149c-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 <span data-ttu-id="5149c-115">Zdefiniowano dwa filtry adresów:</span><span class="sxs-lookup"><span data-stu-id="5149c-115">Two address filters are defined:</span></span>  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 <span data-ttu-id="5149c-116">Jest `FilteringEndpointBehavior` konfigurowalny i pozwala na dwie różne odmiany.</span><span class="sxs-lookup"><span data-stu-id="5149c-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 <span data-ttu-id="5149c-117">Odmiana 1 pasuje tylko do adresów, które zawierają "e" (ale które mają jakąkolwiek akcję), podczas gdy Odmiana 2 pasuje tylko do adresów, które nie mają "e":</span><span class="sxs-lookup"><span data-stu-id="5149c-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="5149c-118">W pliku konfiguracyjnym usługa rejestruje nowe zachowanie:</span><span class="sxs-lookup"><span data-stu-id="5149c-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 <span data-ttu-id="5149c-119">Następnie usługa `endpointBehavior` tworzy konfiguracje dla każdej odmiany:</span><span class="sxs-lookup"><span data-stu-id="5149c-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
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
  
 <span data-ttu-id="5149c-120">Na koniec punkt końcowy usługi odwołuje się `behaviorConfigurations`do jednego z:</span><span class="sxs-lookup"><span data-stu-id="5149c-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="5149c-121">Implementacja aplikacji klienckiej jest prosta; tworzy dwa kanały do identyfikatora URI usługi (przekazując`via`tę wartość <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> jako drugi ( ) parametr do i wysyła pojedynczą wiadomość na każdym kanale, ale używa różnych adresów punktów końcowych dla każdego.</span><span class="sxs-lookup"><span data-stu-id="5149c-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="5149c-122">W rezultacie wychodzące wiadomości od klienta mają różne oznaczenia Do, a serwer odpowiednio odpowiada, jak wynika z danych wyjściowych klienta:</span><span class="sxs-lookup"><span data-stu-id="5149c-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="5149c-123">Przełączanie zmiany w pliku konfiguracyjnym serwera powoduje, że filtr ma zostać zamieniony, a klient widzi odwrotne zachowanie (komunikat `urn:e` zakończy się pomyślnie, podczas gdy komunikat kończy się `urn:a` niepowodzeniem).</span><span class="sxs-lookup"><span data-stu-id="5149c-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="5149c-124">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5149c-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5149c-125">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="5149c-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5149c-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="5149c-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5149c-127">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5149c-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5149c-128">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="5149c-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5149c-129">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5149c-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="5149c-130">Aby uruchomić przykład w konfiguracji z jednym komputerem, postępuj zgodnie z instrukcjami w [uruchamianiu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5149c-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5149c-131">Aby uruchomić przykład w konfiguracji między komputerami, postępuj zgodnie z instrukcjami w [uruchamianiu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md) i zmień następujący wiersz w Client.cs.</span><span class="sxs-lookup"><span data-stu-id="5149c-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="5149c-132">Zastąp hosta lokalnego nazwą serwera.</span><span class="sxs-lookup"><span data-stu-id="5149c-132">Replace localhost with the name of server.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
