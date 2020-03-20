---
title: Niestandardowy element przechwytujący komunikaty
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 433b14433a7e2dd6edad551a2732e9049a9861ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145089"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="157c3-102">Niestandardowy element przechwytujący komunikaty</span><span class="sxs-lookup"><span data-stu-id="157c3-102">Custom Message Interceptor</span></span>
<span data-ttu-id="157c3-103">W tym przykładzie pokazano użycie modelu rozszerzalności kanału.</span><span class="sxs-lookup"><span data-stu-id="157c3-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="157c3-104">W szczególności pokazuje, jak zaimplementować niestandardowy element wiązania, który tworzy fabryki kanałów i odbiorników kanałów do przechwytywania wszystkich komunikatów przychodzących i wychodzących w określonym punkcie w stosie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="157c3-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="157c3-105">Przykład zawiera również klienta i serwera, które pokazują użycie tych fabryk niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="157c3-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="157c3-106">W tym przykładzie zarówno klient, jak i usługa są programami konsoli (exe).</span><span class="sxs-lookup"><span data-stu-id="157c3-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="157c3-107">Klient i usługa korzystają ze wspólnej biblioteki (.dll), która zawiera niestandardowy element wiązania i skojarzone z nim obiekty w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="157c3-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="157c3-108">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="157c3-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="157c3-109">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="157c3-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="157c3-110">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="157c3-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="157c3-111">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="157c3-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="157c3-112">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="157c3-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="157c3-113">W przykładzie opisano zalecaną procedurę tworzenia niestandardowego kanału warstwowego w programie Windows Communication Foundation (WCF), przy użyciu struktury kanału i postępując zgodnie z najlepszymi rozwiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="157c3-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="157c3-114">Kroki tworzenia niestandardowego kanału warstwowego są następujące:</span><span class="sxs-lookup"><span data-stu-id="157c3-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="157c3-115">Zdecyduj, który z kształtów kanału będzie obsługiwana przez fabrykę kanałów i odbiornik kanałów.</span><span class="sxs-lookup"><span data-stu-id="157c3-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="157c3-116">Utwórz fabrykę kanałów i odbiornik kanałów, które obsługują kształty kanału.</span><span class="sxs-lookup"><span data-stu-id="157c3-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="157c3-117">Dodaj element wiązania, który dodaje niestandardowy kanał warstwowy do stosu kanałów.</span><span class="sxs-lookup"><span data-stu-id="157c3-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="157c3-118">Dodaj sekcję rozszerzenia elementu wiązania, aby udostępnić nowy element wiązania do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="157c3-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="157c3-119">Kształty kanałów</span><span class="sxs-lookup"><span data-stu-id="157c3-119">Channel Shapes</span></span>  
 <span data-ttu-id="157c3-120">Pierwszym krokiem w pisaniu niestandardowego kanału warstwowego jest podjęcie decyzji, które kształty są wymagane dla kanału.</span><span class="sxs-lookup"><span data-stu-id="157c3-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="157c3-121">Dla naszego inspektora wiadomości, obsługujemy każdy kształt, który obsługuje warstwa <xref:System.ServiceModel.Channels.IOutputChannel> poniżej nas (na przykład, jeśli warstwa poniżej nas może zbudować, a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>następnie również wystawiać <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="157c3-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="157c3-122">Fabryka kanałów i fabryka słuchaczy</span><span class="sxs-lookup"><span data-stu-id="157c3-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="157c3-123">Następnym krokiem w pisaniu niestandardowego kanału warstwowego jest utworzenie implementacji <xref:System.ServiceModel.Channels.IChannelFactory> dla kanałów klienckich <xref:System.ServiceModel.Channels.IChannelListener> i dla kanałów usług.</span><span class="sxs-lookup"><span data-stu-id="157c3-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="157c3-124">Te klasy wziąć wewnętrzną fabrykę i odbiornika i delegować wszystkie oprócz `OnCreateChannel` i `OnAcceptChannel` wywołania do wewnętrznej fabryki i odbiornika.</span><span class="sxs-lookup"><span data-stu-id="157c3-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
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
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="157c3-125">Dodawanie elementu wiązania</span><span class="sxs-lookup"><span data-stu-id="157c3-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="157c3-126">Przykład definiuje niestandardowy element `InterceptingBindingElement`wiązania: .</span><span class="sxs-lookup"><span data-stu-id="157c3-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="157c3-127">`InterceptingBindingElement`przyjmuje `ChannelMessageInterceptor` jako dane wejściowe i `ChannelMessageInterceptor` używa tego do manipulowania wiadomościami, które przechodzą przez niego.</span><span class="sxs-lookup"><span data-stu-id="157c3-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="157c3-128">Jest to jedyna klasa, która musi być publiczna.</span><span class="sxs-lookup"><span data-stu-id="157c3-128">This is the only class that must be public.</span></span> <span data-ttu-id="157c3-129">Fabryczna, odbiornik i kanały mogą być wewnętrznymi implementacjami publicznych interfejsów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="157c3-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="157c3-130">Dodawanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="157c3-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="157c3-131">Aby zintegrować z konfiguracją powiązania, biblioteka definiuje program obsługi sekcji konfiguracji jako sekcję rozszerzenia elementu wiązania.</span><span class="sxs-lookup"><span data-stu-id="157c3-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="157c3-132">Pliki konfiguracyjne klienta i serwera muszą zarejestrować rozszerzenie elementu powiązania w systemie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="157c3-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="157c3-133">Implementatory, które chcą udostępnić ich element wiązania do systemu konfiguracji może pochodzić z tej klasy.</span><span class="sxs-lookup"><span data-stu-id="157c3-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="157c3-134">Dodawanie zasad</span><span class="sxs-lookup"><span data-stu-id="157c3-134">Adding Policy</span></span>  
 <span data-ttu-id="157c3-135">Aby zintegrować się `InterceptingBindingElement` z naszym systemem zasad, implementuje IPolicyExportExtension, aby zasygnalizować, że powinniśmy uczestniczyć w generowaniu zasad.</span><span class="sxs-lookup"><span data-stu-id="157c3-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="157c3-136">Aby obsługiwać zasady importowania na wygenerowanym kliencie, `InterceptingBindingElementImporter` `CreateMessageInterceptor`użytkownik może zarejestrować klasę pochodną i `ChannelMessageInterceptor` zastąpić (), aby wygenerować klasę z włączoną zasadą.</span><span class="sxs-lookup"><span data-stu-id="157c3-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="157c3-137">Przykład: Inspektor wiadomości z wypuszczalny</span><span class="sxs-lookup"><span data-stu-id="157c3-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="157c3-138">Zawarte w przykładzie jest przykład `ChannelMessageInspector` implementacji, który porzuca wiadomości.</span><span class="sxs-lookup"><span data-stu-id="157c3-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="157c3-139">Dostęp do niego można uzyskać z konfiguracji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="157c3-139">You can access it from configuration as follows:</span></span>  
  
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
  
 <span data-ttu-id="157c3-140">Zarówno klient, jak i serwer używają tej nowo utworzonej sekcji konfiguracji, aby wstawić fabryki niestandardowe do najniższego poziomu ich stosów kanałów w czasie wykonywania (powyżej poziomu transportu).</span><span class="sxs-lookup"><span data-stu-id="157c3-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="157c3-141">Klient używa biblioteki, `MessageInterceptor` aby dodać niestandardowy nagłówek do wiadomości parzyste.</span><span class="sxs-lookup"><span data-stu-id="157c3-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="157c3-142">Usługa z drugiej strony `MessageInterceptor` używa biblioteki do upuszczania wiadomości, które nie mają tego specjalnego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="157c3-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="157c3-143">Po uruchomieniu usługi, a następnie na kliencie, powinny zostać wyświetlenia następujące dane wyjściowe klienta.</span><span class="sxs-lookup"><span data-stu-id="157c3-143">You should see the following client output after running the service and then the client.</span></span>  
  
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
  
 <span data-ttu-id="157c3-144">Klient zgłasza 10 różnych prędkości wiatru do usługi, ale tylko tagi połowę z nich ze specjalnym nagłówkiem.</span><span class="sxs-lookup"><span data-stu-id="157c3-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="157c3-145">W usłudze powinny zostać wyświetlene następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="157c3-145">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="157c3-146">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="157c3-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="157c3-147">Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="157c3-147">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="157c3-148">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="157c3-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="157c3-149">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="157c3-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="157c3-150">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="157c3-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="157c3-151">Najpierw uruchom program Service.exe, a następnie uruchom program Client.exe i obserwuj oba okna konsoli w celu uzyskania danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="157c3-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
