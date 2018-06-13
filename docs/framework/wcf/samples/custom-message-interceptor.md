---
title: Niestandardowy element przechwytujący komunikaty
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: a59b2075473e2ca4c8cb8751fd6cb733f282238b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806321"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="72b5d-102">Niestandardowy element przechwytujący komunikaty</span><span class="sxs-lookup"><span data-stu-id="72b5d-102">Custom Message Interceptor</span></span>
<span data-ttu-id="72b5d-103">W tym przykładzie przedstawiono stosowania modelu rozszerzalności kanału.</span><span class="sxs-lookup"><span data-stu-id="72b5d-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="72b5d-104">W szczególności widoczny jest sposób implementuje element niestandardowego powiązania, który tworzy fabryk kanałów i odbiorników kanału do przechwycenia wszystkich wiadomości przychodzących i wychodzących w określonym punkcie w stosie czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="72b5d-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="72b5d-105">Przykład obejmuje również klienta i serwera, które przedstawiają sposób używania tych niestandardowych fabryki.</span><span class="sxs-lookup"><span data-stu-id="72b5d-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="72b5d-106">W tym przykładzie zarówno klient, jak i usługi są programy konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="72b5d-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="72b5d-107">Klient i usługa programu użycie wspólnej biblioteki (.dll), który zawiera element niestandardowego powiązania i powiązane obiekty środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="72b5d-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72b5d-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="72b5d-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="72b5d-109">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="72b5d-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="72b5d-110">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="72b5d-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="72b5d-111">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="72b5d-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="72b5d-112">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="72b5d-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="72b5d-113">Przykład opisuje zalecane procedurę tworzenia niestandardowym kanale warstwowych w systemie Windows Communication Foundation (WCF), używając struktura kanału i następujące najlepsze rozwiązania w zakresie WCF.</span><span class="sxs-lookup"><span data-stu-id="72b5d-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="72b5d-114">Kroki, aby utworzyć niestandardowy kanał warstwowego są następujące:</span><span class="sxs-lookup"><span data-stu-id="72b5d-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1.  <span data-ttu-id="72b5d-115">Decyzji, które kształtów kanału będzie obsługiwać Twoje fabryki kanału i odbiornika kanałów.</span><span class="sxs-lookup"><span data-stu-id="72b5d-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2.  <span data-ttu-id="72b5d-116">Tworzenie fabryki kanałów i odbiornik kanału, który obsługuje kanał kształtów.</span><span class="sxs-lookup"><span data-stu-id="72b5d-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3.  <span data-ttu-id="72b5d-117">Dodaj element powiązania, który dodaje niestandardowym kanale warstwowego stos kanału.</span><span class="sxs-lookup"><span data-stu-id="72b5d-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4.  <span data-ttu-id="72b5d-118">Dodaj sekcję rozszerzenia elementu powiązania do udostępnienia element powiązania do konfiguracji systemu.</span><span class="sxs-lookup"><span data-stu-id="72b5d-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="72b5d-119">Kształty kanału</span><span class="sxs-lookup"><span data-stu-id="72b5d-119">Channel Shapes</span></span>  
 <span data-ttu-id="72b5d-120">Pierwszą czynnością przy tworzeniu niestandardowym kanale warstwowego jest podjęcie decyzji, które kształty są wymagane dla kanału.</span><span class="sxs-lookup"><span data-stu-id="72b5d-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="72b5d-121">Dla naszych inspektora komunikat obsługujemy dowolnego kształtu, który obsługuje warstwy poniżej nam (na przykład jeśli warstwa poniżej nam można tworzyć <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, a następnie możemy również ujawniać <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="72b5d-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="72b5d-122">Fabryka kanałów i fabryki odbiornika</span><span class="sxs-lookup"><span data-stu-id="72b5d-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="72b5d-123">Następnym krokiem w niestandardowym kanale warstwowego pisaniu jest utworzenie implementacja <xref:System.ServiceModel.Channels.IChannelFactory> dla kanałów klienta oraz <xref:System.ServiceModel.Channels.IChannelListener> kanałów usługi.</span><span class="sxs-lookup"><span data-stu-id="72b5d-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="72b5d-124">Te klasy wewnętrzna fabryka i odbiornika i delegowanie wszystkie elementy oprócz `OnCreateChannel` i `OnAcceptChannel` wywołania wewnętrzna fabryka i odbiornika.</span><span class="sxs-lookup"><span data-stu-id="72b5d-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="72b5d-125">Dodawanie elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="72b5d-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="72b5d-126">Przykład definiuje element powiązania niestandardowego: `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="72b5d-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="72b5d-127">`InterceptingBindingElement` przyjmuje `ChannelMessageInterceptor` jako dane wejściowe i używa go `ChannelMessageInterceptor` do manipulowania wiadomości, które przechodzą przez go.</span><span class="sxs-lookup"><span data-stu-id="72b5d-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="72b5d-128">Jest to jedyna klasa, która musi być publiczny.</span><span class="sxs-lookup"><span data-stu-id="72b5d-128">This is the only class that must be public.</span></span> <span data-ttu-id="72b5d-129">Fabryka odbiornika i kanały wszystkie może być wewnętrzny implementacje interfejsów publicznych czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="72b5d-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="72b5d-130">Dodawanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="72b5d-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="72b5d-131">Aby zintegrować za pomocą konfiguracji powiązania, biblioteka definiuje modułu obsługi sekcji konfiguracji jako sekcja rozszerzenia elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="72b5d-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="72b5d-132">Pliki konfiguracji klienta i serwera, należy zarejestrować element rozszerzenia powiązania przy użyciu systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="72b5d-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="72b5d-133">Implementujące obiekty, które chcesz udostępnić ich elementu powiązania do konfiguracji systemu może dziedziczyć po tej klasie.</span><span class="sxs-lookup"><span data-stu-id="72b5d-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a><span data-ttu-id="72b5d-134">Dodawanie zasad</span><span class="sxs-lookup"><span data-stu-id="72b5d-134">Adding Policy</span></span>  
 <span data-ttu-id="72b5d-135">Integracja z naszym systemem zasad `InterceptingBindingElement` implementuje IPolicyExportExtension sygnalizują, możemy powinny uczestniczyć w generowania zasad.</span><span class="sxs-lookup"><span data-stu-id="72b5d-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="72b5d-136">Do importowania zasady pomocy technicznej na wygenerowanego klienta, użytkownik może zarejestrować klasy pochodnej z `InterceptingBindingElementImporter` i zastąpić `CreateMessageInterceptor`(), aby wygenerować ich włączone zasady `ChannelMessageInterceptor` klasy.</span><span class="sxs-lookup"><span data-stu-id="72b5d-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="72b5d-137">Przykład: Inspector Droppable wiadomości</span><span class="sxs-lookup"><span data-stu-id="72b5d-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="72b5d-138">Uwzględnione w próbce jest przykładem implementacji `ChannelMessageInspector` który porzuca wiadomości.</span><span class="sxs-lookup"><span data-stu-id="72b5d-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="72b5d-139">Można do niego dostęp z konfiguracji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72b5d-139">You can access it from configuration as follows:</span></span>  
  
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
  
 <span data-ttu-id="72b5d-140">Klient i serwer Użyj tej sekcji konfiguracyjnej nowo utworzony, aby wstawić niestandardowych fabryki do najniższego poziomu ich stosów kanału czasu wykonywania (powyżej poziomu transportu).</span><span class="sxs-lookup"><span data-stu-id="72b5d-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="72b5d-141">Klient używa `MessageInterceptor` biblioteki nawet Dodawanie niestandardowego nagłówka do numerowane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="72b5d-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="72b5d-142">Z drugiej strony używa usługi `MessageInterceptor` biblioteki można usunąć wszystkie komunikaty, które nie mają tego specjalne nagłówka.</span><span class="sxs-lookup"><span data-stu-id="72b5d-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="72b5d-143">Po uruchomieniu usługi, a następnie klienta powinny być widoczne następujące dane wyjściowe klienta.</span><span class="sxs-lookup"><span data-stu-id="72b5d-143">You should see the following client output after running the service and then the client.</span></span>  
  
```  
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
  
 <span data-ttu-id="72b5d-144">Klient raporty 10 knie różnych szybkościach do usługi, ale tylko tagów połowy je za pomocą specjalnych nagłówków.</span><span class="sxs-lookup"><span data-stu-id="72b5d-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="72b5d-145">W usłudze powinny być widoczne następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="72b5d-145">On the service, you should see the following output:</span></span>  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="72b5d-146">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="72b5d-146">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="72b5d-147">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="72b5d-147">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="72b5d-148">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="72b5d-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="72b5d-149">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="72b5d-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="72b5d-150">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="72b5d-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="72b5d-151">Uruchom najpierw Service.exe, a następnie uruchom Client.exe i obejrzyj oba okna konsoli dla danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="72b5d-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b5d-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72b5d-152">See Also</span></span>
