---
title: Niestandardowy filtr komunikatów
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 30405800cd219f56fcc08b8e8d22f4fe0b907e32
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928689"
---
# <a name="custom-message-filter"></a><span data-ttu-id="46f91-102">Niestandardowy filtr komunikatów</span><span class="sxs-lookup"><span data-stu-id="46f91-102">Custom Message Filter</span></span>
<span data-ttu-id="46f91-103">Ten przykład pokazuje, jak zastąpić filtry komunikatów, które są używane przez Windows Communication Foundation (WCF) do wysyłania wiadomości do punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="46f91-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46f91-104">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="46f91-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="46f91-105">Gdy pierwsza wiadomość w kanale dociera do serwera, serwer musi określić, który (Jeśli którykolwiek) punktów końcowych skojarzonych z tym identyfikatorem URI powinien odebrać komunikat.</span><span class="sxs-lookup"><span data-stu-id="46f91-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="46f91-106">Ten proces jest kontrolowany przez <xref:System.ServiceModel.Dispatcher.MessageFilter> obiekty dołączone <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>do.</span><span class="sxs-lookup"><span data-stu-id="46f91-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="46f91-107">Każdy punkt końcowy usługi ma jeden <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="46f91-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="46f91-108">Ma zarówno a, jak i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A></span><span class="sxs-lookup"><span data-stu-id="46f91-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="46f91-109">W związku z tymi dwoma filtrami jest stosowany filtr komunikatów dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="46f91-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="46f91-110">Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> punkt końcowy dopasowuje dowolny komunikat, który jest rozkierowany na adres pasujący do <xref:System.ServiceModel.EndpointAddress>punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="46f91-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="46f91-111">Domyślnie <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> dla punktu końcowego program sprawdza działanie komunikatu przychodzącego i dopasowuje komunikat z akcją odpowiadającą jednej z akcji związanych z operacjami kontraktu punktu końcowego usługi (tylko `IsInitiating` = `true`działania są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="46f91-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="46f91-112">W związku z tym domyślnie filtr dla punktu końcowego dopasowuje się tylko wtedy, gdy zarówno komunikat do nagłówka jest <xref:System.ServiceModel.EndpointAddress> punktem końcowym, jak i Akcja komunikatu jest zgodna z jedną z akcji operacji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="46f91-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="46f91-113">Te filtry można zmienić przy użyciu zachowania.</span><span class="sxs-lookup"><span data-stu-id="46f91-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="46f91-114">W przykładzie <xref:System.ServiceModel.Description.IEndpointBehavior> Usługa tworzy obiekt, który <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> zastępuje i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> w <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span><span class="sxs-lookup"><span data-stu-id="46f91-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 <span data-ttu-id="46f91-115">Zdefiniowano dwa filtry adresów:</span><span class="sxs-lookup"><span data-stu-id="46f91-115">Two address filters are defined:</span></span>  
  
```csharp  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 <span data-ttu-id="46f91-116">Program `FilteringEndpointBehavior` jest konfigurowalny i umożliwia korzystanie z dwóch różnych odmian.</span><span class="sxs-lookup"><span data-stu-id="46f91-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```csharp  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 <span data-ttu-id="46f91-117">Odmiana 1 dopasowuje tylko adresy, które zawierają "e" (ale z jakąkolwiek akcją), natomiast odmiana 2 dopasowuje tylko adresy, które nie mają "e":</span><span class="sxs-lookup"><span data-stu-id="46f91-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```csharp  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="46f91-118">W pliku konfiguracji Usługa rejestruje nowe zachowanie:</span><span class="sxs-lookup"><span data-stu-id="46f91-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 <span data-ttu-id="46f91-119">Następnie usługa tworzy `endpointBehavior` konfiguracje dla każdej odmiany:</span><span class="sxs-lookup"><span data-stu-id="46f91-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
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
  
 <span data-ttu-id="46f91-120">Na koniec punkt końcowy usługi odwołuje się do jednej `behaviorConfigurations`z:</span><span class="sxs-lookup"><span data-stu-id="46f91-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="46f91-121">Implementacja aplikacji klienckiej jest prosta; tworzy dwa kanały dla identyfikatora URI usługi (przez przekazanie tej wartości jako drugi (`via`) parametru do <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> i wysyła pojedynczą wiadomość w każdym kanale, ale używa różnych adresów punktów końcowych dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="46f91-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="46f91-122">W związku z tym komunikaty wychodzące od klienta różnią się w zależności od tego, a serwer odpowiada zgodnie z danymi wyjściowymi klienta:</span><span class="sxs-lookup"><span data-stu-id="46f91-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="46f91-123">Przełączenie zmian w pliku konfiguracyjnym serwera powoduje zamianę filtru, a klient zobaczy odwrotne zachowanie (komunikat, `urn:e` `urn:a` aby zakończyć się niepowodzeniem).</span><span class="sxs-lookup"><span data-stu-id="46f91-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="46f91-124">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="46f91-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="46f91-125">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="46f91-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="46f91-126">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="46f91-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46f91-127">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="46f91-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="46f91-128">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="46f91-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="46f91-129">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="46f91-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="46f91-130">Aby uruchomić przykład w konfiguracji pojedynczej maszyny, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="46f91-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="46f91-131">Aby uruchomić przykład w konfiguracji między maszynami, postępuj zgodnie z instrukcjami w temacie [uruchamianie Windows Communication Foundation próbek](../../../../docs/framework/wcf/samples/running-the-samples.md) i zmień następujący wiersz w Client.cs.</span><span class="sxs-lookup"><span data-stu-id="46f91-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```csharp  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="46f91-132">Zastąp wartość localhost nazwą serwera.</span><span class="sxs-lookup"><span data-stu-id="46f91-132">Replace localhost with the name of server.</span></span>  
  
    ```csharp  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
