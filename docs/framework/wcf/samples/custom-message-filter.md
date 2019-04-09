---
title: Niestandardowy filtr komunikatów
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 31816ae67e3273e033b53951ff78d662ef8192c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172838"
---
# <a name="custom-message-filter"></a><span data-ttu-id="a0b33-102">Niestandardowy filtr komunikatów</span><span class="sxs-lookup"><span data-stu-id="a0b33-102">Custom Message Filter</span></span>
<span data-ttu-id="a0b33-103">Niniejszy przykład pokazuje, jak zastąpić filtry komunikatów, używane przez program Windows Communication Foundation (WCF) do wysyłania wiadomości do punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a0b33-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0b33-104">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a0b33-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a0b33-105">Podczas pierwszego komunikatu w kanale dociera do serwera, serwera należy określić, które (jeśli istnieje) punktów końcowych skojarzonych z tym, że identyfikator URI powinien zostać wyświetlony komunikat.</span><span class="sxs-lookup"><span data-stu-id="a0b33-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="a0b33-106">Ten proces jest kontrolowana przez <xref:System.ServiceModel.Dispatcher.MessageFilter> obiektów dołączonych do <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="a0b33-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="a0b33-107">Każdy punkt końcowy usługi ma jeden <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="a0b33-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="a0b33-108"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Znajdują się oba <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0b33-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="a0b33-109">Sumę tych dwóch filtrów jest używany dla tego punktu końcowego filtr komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a0b33-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="a0b33-110">Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> wiadomości, które są skierowane do adresu, który pasuje do punktu końcowego usługi jest zgodna z punktu końcowego <xref:System.ServiceModel.EndpointAddress>.</span><span class="sxs-lookup"><span data-stu-id="a0b33-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="a0b33-111">Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> dla punktu końcowego sprawdza akcję wiadomości przychodzącej i dopasowuje każdy komunikat z akcją, która odpowiada jednemu akcje operacji kontraktu punktu końcowego usługi (tylko `IsInitiating` = `true`akcje są traktowane jako).</span><span class="sxs-lookup"><span data-stu-id="a0b33-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="a0b33-112">Co w efekcie domyślnie filtr dla punktu końcowego jest zgodny tylko w przypadku obu komunikatu do nagłówka <xref:System.ServiceModel.EndpointAddress> punktu końcowego i działań wiadomości pasuje do jednej akcji operacji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a0b33-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="a0b33-113">Filtry te można zmienić za pomocą zachowania.</span><span class="sxs-lookup"><span data-stu-id="a0b33-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="a0b33-114">W tym przykładzie tworzy usługę <xref:System.ServiceModel.Description.IEndpointBehavior> zastępuje <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> na <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span><span class="sxs-lookup"><span data-stu-id="a0b33-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 <span data-ttu-id="a0b33-115">Zdefiniowano dwa filtry adresów:</span><span class="sxs-lookup"><span data-stu-id="a0b33-115">Two address filters are defined:</span></span>  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 <span data-ttu-id="a0b33-116">`FilteringEndpointBehavior` Można konfigurować i pozwala na dwie różne odmiany.</span><span class="sxs-lookup"><span data-stu-id="a0b33-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 <span data-ttu-id="a0b33-117">Odmiana 1 odpowiada tylko adresy, które zawierają "e" (ale mają dowolną akcję) natomiast 2 odmiany pasuje tylko adresy, które nie mają "e":</span><span class="sxs-lookup"><span data-stu-id="a0b33-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="a0b33-118">W pliku konfiguracji usługi rejestruje nowe zachowanie:</span><span class="sxs-lookup"><span data-stu-id="a0b33-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 <span data-ttu-id="a0b33-119">A następnie tworzy usługę `endpointBehavior` konfiguracje dla poszczególnych odmian:</span><span class="sxs-lookup"><span data-stu-id="a0b33-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
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
  
 <span data-ttu-id="a0b33-120">Na koniec punktu końcowego usługi odwołuje się do jednego z `behaviorConfigurations`:</span><span class="sxs-lookup"><span data-stu-id="a0b33-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="a0b33-121">Implementacja aplikacja kliencka jest prosta; tworzy on dwa kanały do identyfikatora URI usługi (przez przekazanie wartości jako drugi (`via`) parametr <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> i wysyła pojedynczy komunikat z poszczególnych kanałów, ale używa adresy różnych punktów końcowych dla każdego.</span><span class="sxs-lookup"><span data-stu-id="a0b33-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="a0b33-122">W rezultacie komunikaty wychodzące z klienta mają różne do oznaczenia, a serwer odpowiada, w związku z tym, jak pokazano w danych wyjściowych klienta:</span><span class="sxs-lookup"><span data-stu-id="a0b33-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="a0b33-123">Przełączanie zmiany w pliku konfiguracji serwera powoduje, że filtr, które mają być zamienione i klient widzi przeciwny zachowanie (komunikat, który ma `urn:e` zakończy się powodzeniem, natomiast komunikat, który ma `urn:a` nie powiedzie się).</span><span class="sxs-lookup"><span data-stu-id="a0b33-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0b33-124">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a0b33-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a0b33-125">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a0b33-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a0b33-126">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="a0b33-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0b33-127">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a0b33-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a0b33-128">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="a0b33-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a0b33-129">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0b33-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="a0b33-130">Do uruchomienia przykładu w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0b33-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a0b33-131">Do uruchomienia przykładu w konfiguracji między komputerami, postępuj zgodnie z instrukcjami w artykule [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) i zmień następujący wiersz w Client.cs.</span><span class="sxs-lookup"><span data-stu-id="a0b33-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="a0b33-132">Zastąp ciąg localhost nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="a0b33-132">Replace localhost with the name of server.</span></span>  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
