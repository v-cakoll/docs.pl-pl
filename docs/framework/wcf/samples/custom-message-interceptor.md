---
title: Niestandardowy element przechwytujący komunikaty
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: daa041bf63442dace0d33e1e3207d0857b6b7312
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928919"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="6b6b6-102">Niestandardowy element przechwytujący komunikaty</span><span class="sxs-lookup"><span data-stu-id="6b6b6-102">Custom Message Interceptor</span></span>
<span data-ttu-id="6b6b6-103">Ten przykład ilustruje użycie modelu rozszerzalności kanałów.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="6b6b6-104">W szczególności pokazano, jak zaimplementować niestandardowy element powiązania, który tworzy fabryki kanałów i odbiorniki kanałów do przechwytywania wszystkich komunikatów przychodzących i wychodzących w konkretnym momencie w stosie czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="6b6b6-105">Przykład zawiera również klienta i serwer, który pokazuje użycie tych niestandardowych fabryk.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="6b6b6-106">W tym przykładzie zarówno klient, jak i usługa są programami konsolowymi (. exe).</span><span class="sxs-lookup"><span data-stu-id="6b6b6-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="6b6b6-107">Klient i usługa korzystają ze wspólnej biblioteki (. dll), która zawiera niestandardowy element powiązania i powiązane z nim obiekty czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b6b6-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6b6b6-109">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b6b6-110">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="6b6b6-110">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="6b6b6-111">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b6b6-112">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-112">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="6b6b6-113">W przykładzie opisano zalecaną procedurę tworzenia niestandardowego kanału warstwowego w Windows Communication Foundation (WCF), przy użyciu struktury kanału oraz najlepszych rozwiązań w zakresie usług WCF.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="6b6b6-114">Poniżej przedstawiono procedurę tworzenia niestandardowego kanału warstwowego:</span><span class="sxs-lookup"><span data-stu-id="6b6b6-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="6b6b6-115">Określ, które kształty kanałów będą obsługiwane przez fabrykę kanałów i odbiornik kanału.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="6b6b6-116">Utwórz fabrykę kanałów i odbiornik kanału obsługujący kształty kanałów.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="6b6b6-117">Dodaj element powiązania, który dodaje niestandardowy kanał warstwowy do stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="6b6b6-118">Dodaj sekcję rozszerzenie elementu powiązania, aby udostępnić nowy element powiązania do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="6b6b6-119">Kształty kanału</span><span class="sxs-lookup"><span data-stu-id="6b6b6-119">Channel Shapes</span></span>  
 <span data-ttu-id="6b6b6-120">Pierwszym krokiem w przypadku pisania niestandardowego kanału warstwowego jest określenie, które kształty są wymagane dla kanału.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="6b6b6-121">W naszym Inspektorze komunikatów obsługujemy dowolny kształt, który obsługuje warstwa poniżej US (na przykład jeśli warstwa poniżej Stanów Zjednoczonych może kompilować <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel> <xref:System.ServiceModel.Channels.IOutputChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="6b6b6-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="6b6b6-122">Fabryka kanałów i fabryka odbiorników</span><span class="sxs-lookup"><span data-stu-id="6b6b6-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="6b6b6-123">Następnym krokiem w przypadku pisania niestandardowego kanału warstwowego jest utworzenie implementacji <xref:System.ServiceModel.Channels.IChannelFactory> dla kanałów klienta <xref:System.ServiceModel.Channels.IChannelListener> i kanałów usługi.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="6b6b6-124">Klasy te przyjmują wewnętrzną fabrykę i odbiornik oraz umożliwiają delegowanie `OnCreateChannel` wszystkich `OnAcceptChannel` wywołań, ale do wewnętrznej fabryki i odbiornika.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```csharp  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ 
    //... 
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ 
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="6b6b6-125">Dodawanie elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="6b6b6-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="6b6b6-126">Przykład definiuje niestandardowy element powiązania: `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="6b6b6-127">`InterceptingBindingElement`przyjmuje jako dane wejściowe i używa tego `ChannelMessageInterceptor` do manipulowania wiadomościami, które przechodzą przez nią. `ChannelMessageInterceptor`</span><span class="sxs-lookup"><span data-stu-id="6b6b6-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="6b6b6-128">Jest to jedyna klasa, która musi być publiczna.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-128">This is the only class that must be public.</span></span> <span data-ttu-id="6b6b6-129">Fabryki, odbiornik i kanały mogą być wewnętrznymi implementacjami publicznych interfejsów czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement 
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="6b6b6-130">Dodawanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6b6b6-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="6b6b6-131">W celu zintegrowania z konfiguracją powiązań Biblioteka definiuje procedurę obsługi sekcji konfiguracji jako element powiązania sekcji rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="6b6b6-132">Pliki konfiguracji klienta i serwera muszą rejestrować rozszerzenie elementu powiązania z systemem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="6b6b6-133">Realizatorzy, którzy chcą uwidocznić swój element powiązania w systemie konfiguracji, mogą pochodzić od tej klasy.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement 
{ 
    //... 
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="6b6b6-134">Dodawanie zasad</span><span class="sxs-lookup"><span data-stu-id="6b6b6-134">Adding Policy</span></span>  
 <span data-ttu-id="6b6b6-135">Aby przeprowadzić integrację z naszym systemem `InterceptingBindingElement` zasad, program implementuje IPolicyExportExtension, aby sygnalizować, że będziemy uczestniczyć w generowaniu zasad.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="6b6b6-136">Aby umożliwić obsługę importowania zasad na wygenerowanym kliencie, użytkownik może zarejestrować klasę `InterceptingBindingElementImporter` pochodną i zastąpić `CreateMessageInterceptor`() w celu wygenerowania klasy z obsługą `ChannelMessageInterceptor` zasad.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="6b6b6-137">Przykład: Inspektor komunikatów droppable</span><span class="sxs-lookup"><span data-stu-id="6b6b6-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="6b6b6-138">W przykładzie przedstawiono przykładową implementację `ChannelMessageInspector` , która odrzuca komunikaty.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="6b6b6-139">Możesz uzyskać do niego dostęp z konfiguracji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6b6b6-139">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"   
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="6b6b6-140">Zarówno klient, jak i serwer używają tej nowo utworzonej sekcji konfiguracji, aby wstawić niestandardowe fabryki do najniższego poziomu swoich stosów kanałów czasu wykonywania (powyżej poziomu transportu).</span><span class="sxs-lookup"><span data-stu-id="6b6b6-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="6b6b6-141">Klient używa `MessageInterceptor` biblioteki programu w celu dodania niestandardowego nagłówka do parzystych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="6b6b6-142">Usługa z drugiej strony używa `MessageInterceptor` biblioteki do usuwania wszelkich komunikatów, które nie mają tego nagłówka specjalnego.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="6b6b6-143">Po uruchomieniu usługi należy zobaczyć następujące dane wyjściowe klienta programu, a następnie klienta.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-143">You should see the following client output after running the service and then the client.</span></span>  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="6b6b6-144">Klient raportuje 10 różnych szybkości wiatru do usługi, ale tylko Tagi mające połowę z nagłówka specjalnego.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="6b6b6-145">W usłudze powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6b6b6-145">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6b6b6-146">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="6b6b6-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6b6b6-147">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-147">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="6b6b6-148">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b6b6-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="6b6b6-149">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b6b6-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="6b6b6-150">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b6b6-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="6b6b6-151">Uruchom najpierw program Service. exe, a następnie uruchom program Client. exe i obejrzyj oba okna konsoli dla danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="6b6b6-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
