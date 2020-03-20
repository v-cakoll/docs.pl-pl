---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 6b7a72fdd814aa9d2e0f125cf4dbdaf63ba753e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183627"
---
# <a name="httpcookiesession"></a><span data-ttu-id="c2183-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="c2183-102">HttpCookieSession</span></span>
<span data-ttu-id="c2183-103">W tym przykładzie pokazano, jak utworzyć niestandardowy kanał protokołu do używania plików cookie HTTP do zarządzania sesjami.</span><span class="sxs-lookup"><span data-stu-id="c2183-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="c2183-104">Ten kanał umożliwia komunikację między usługami Windows Communication Foundation (WCF) a klientami ASMX lub między klientami WCF a usługami ASMX.</span><span class="sxs-lookup"><span data-stu-id="c2183-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="c2183-105">Gdy klient wywołuje metodę sieci Web w usłudze sieci Web ASMX opartą na sesji, aparat ASP.NET wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c2183-105">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="c2183-106">Generuje unikatowy identyfikator (identyfikator sesji).</span><span class="sxs-lookup"><span data-stu-id="c2183-106">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="c2183-107">Generuje obiekt sesji i kojarzy go z unikatowym identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="c2183-107">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="c2183-108">Dodaje unikatowy identyfikator do nagłówka odpowiedzi HTTP set-cookie i wysyła go do klienta.</span><span class="sxs-lookup"><span data-stu-id="c2183-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="c2183-109">Identyfikuje klienta na kolejnych wywołaniach na podstawie identyfikatora sesji, który wysyła do niego.</span><span class="sxs-lookup"><span data-stu-id="c2183-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="c2183-110">Klient zawiera ten identyfikator sesji w kolejnych żądaniach do serwera.</span><span class="sxs-lookup"><span data-stu-id="c2183-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="c2183-111">Serwer używa identyfikatora sesji od klienta, aby załadować odpowiedni obiekt sesji dla bieżącego kontekstu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c2183-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c2183-112">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c2183-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2183-113">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="c2183-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c2183-114">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c2183-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2183-115">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2183-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="c2183-116">Wzorzec wymiany komunikatów kanału HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="c2183-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="c2183-117">Ten przykład umożliwia sesje dla scenariuszy podobnych do ASMX.</span><span class="sxs-lookup"><span data-stu-id="c2183-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="c2183-118">W dolnej części naszego stosu kanałów <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IReplyChannel>mamy transport HTTP, który obsługuje i .</span><span class="sxs-lookup"><span data-stu-id="c2183-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="c2183-119">Zadaniem kanału jest zapewnienie sesji do wyższych poziomów stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="c2183-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="c2183-120">Przykład implementuje dwa kanały (<xref:System.ServiceModel.Channels.IRequestSessionChannel> i <xref:System.ServiceModel.Channels.IReplySessionChannel>), które obsługują sesje.</span><span class="sxs-lookup"><span data-stu-id="c2183-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="c2183-121">Kanał usługi</span><span class="sxs-lookup"><span data-stu-id="c2183-121">Service Channel</span></span>  
 <span data-ttu-id="c2183-122">Przykład zapewnia kanał usługi `HttpCookieReplySessionChannelListener` w klasie.</span><span class="sxs-lookup"><span data-stu-id="c2183-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="c2183-123">Ta klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener> interfejs i <xref:System.ServiceModel.Channels.IReplyChannel> konwertuje kanał z <xref:System.ServiceModel.Channels.IReplySessionChannel>dolnej w stosie kanału na .</span><span class="sxs-lookup"><span data-stu-id="c2183-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="c2183-124">Proces ten można podzielić na następujące części:</span><span class="sxs-lookup"><span data-stu-id="c2183-124">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="c2183-125">Po otwarciu odbiornika kanału, akceptuje kanał wewnętrzny z jego odbiornika wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="c2183-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="c2183-126">Ponieważ wewnętrzny odbiornik jest odbiornikiem datagramu, a okres istnienia akceptowanego kanału jest oddzielony od okresu istnienia odbiornika, możemy zamknąć odbiornik wewnętrzny i trzymać tylko kanał wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="c2183-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="c2183-127">Po zakończeniu otwartego procesu skonfigurujemy pętlę komunikatów do odbierania wiadomości z kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="c2183-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="c2183-128">Po odebraniu wiadomości kanał usługi sprawdza identyfikator sesji i de-multipleksy do odpowiedniego kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="c2183-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="c2183-129">Odbiornik kanału przechowuje słownik, który mapuje identyfikatory sesji do wystąpień kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="c2183-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="c2183-130">Klasa `HttpCookieReplySessionChannel` implementuje <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="c2183-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="c2183-131">Wyższe poziomy stosu kanału <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> wywołać metodę odczytu żądań dla tej sesji.</span><span class="sxs-lookup"><span data-stu-id="c2183-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="c2183-132">Każdy kanał sesji ma prywatną kolejkę komunikatów, która jest wypełniona przez kanał usługi.</span><span class="sxs-lookup"><span data-stu-id="c2183-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="c2183-133">W przypadku, gdy <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> ktoś wywołuje metodę i nie ma żadnych wiadomości w kolejce wiadomości, kanał czeka na określoną ilość czasu przed zamknięciem się.</span><span class="sxs-lookup"><span data-stu-id="c2183-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="c2183-134">Spowoduje to oczyszczenie kanałów sesji utworzonych dla klientów innych niż WCF.</span><span class="sxs-lookup"><span data-stu-id="c2183-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="c2183-135">Używamy `channelMapping` do śledzenia `ReplySessionChannels`, i nie zamykamy `innerChannel` naszych podstawowych, dopóki wszystkie akceptowane kanały zostały zamknięte.</span><span class="sxs-lookup"><span data-stu-id="c2183-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="c2183-136">W `HttpCookieReplySessionChannel` ten sposób może `HttpCookieReplySessionChannelListener`istnieć poza okresem istnienia .</span><span class="sxs-lookup"><span data-stu-id="c2183-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="c2183-137">Nie musimy się również martwić o słuchacza coraz śmieci zebrane pod nami, ponieważ akceptowane `OnClosed` kanały zachować odniesienie do ich słuchacza poprzez wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="c2183-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="c2183-138">Kanał klienta</span><span class="sxs-lookup"><span data-stu-id="c2183-138">Client channel</span></span>  
 <span data-ttu-id="c2183-139">Odpowiedni kanał klienta znajduje `HttpCookieSessionChannelFactory` się w klasie.</span><span class="sxs-lookup"><span data-stu-id="c2183-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="c2183-140">Podczas tworzenia kanału fabryka kanału zawija `HttpCookieRequestSessionChannel`wewnętrzny kanał żądania za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="c2183-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="c2183-141">Klasa `HttpCookieRequestSessionChannel` przekazuje wywołania do kanału żądania źródłowego.</span><span class="sxs-lookup"><span data-stu-id="c2183-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="c2183-142">Gdy klient zamyka serwer `HttpCookieRequestSessionChannel` proxy, wysyła komunikat do usługi, który wskazuje, że kanał jest zamykany.</span><span class="sxs-lookup"><span data-stu-id="c2183-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="c2183-143">W związku z tym stos kanału usługi można bezpiecznie zamknąć kanał sesji, który jest w użyciu.</span><span class="sxs-lookup"><span data-stu-id="c2183-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="c2183-144">Element wiązania i wiązania</span><span class="sxs-lookup"><span data-stu-id="c2183-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="c2183-145">Po utworzeniu kanałów usługi i klienta następnym krokiem jest zintegrowanie ich ze środowiska wykonawczego WCF.</span><span class="sxs-lookup"><span data-stu-id="c2183-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="c2183-146">Kanały są narażone na WCF za pośrednictwem wiązań i elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="c2183-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="c2183-147">Powiązanie składa się z jednego lub wielu elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="c2183-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="c2183-148">WCF oferuje kilka powiązań zdefiniowanych przez system; na przykład Podstawowehttpbinowanie lub WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="c2183-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="c2183-149">Klasa `HttpCookieSessionBindingElement` zawiera implementację dla elementu wiązania.</span><span class="sxs-lookup"><span data-stu-id="c2183-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="c2183-150">Zastępuje odbiornik kanału i metody tworzenia fabryki kanałów, aby wykonać niezbędne metody odbiornika kanału lub wystąpienia fabryczne kanału.</span><span class="sxs-lookup"><span data-stu-id="c2183-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="c2183-151">W przykładzie użyto potwierdzeń zasad dla opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="c2183-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="c2183-152">Dzięki temu przykład opublikować jego wymagania dotyczące kanału do innych klientów, którzy mogą korzystać z usługi.</span><span class="sxs-lookup"><span data-stu-id="c2183-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="c2183-153">Na przykład ten element wiązania publikuje potwierdzenia zasad, aby poinformować potencjalnych klientów, że obsługuje sesje.</span><span class="sxs-lookup"><span data-stu-id="c2183-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="c2183-154">Ponieważ przykład umożliwia `ExchangeTerminateMessage` właściwość w konfiguracji elementu wiązania, dodaje niezbędne potwierdzenia, aby pokazać, że usługa obsługuje dodatkową akcję wymiany wiadomości, aby zakończyć konwersację sesji.</span><span class="sxs-lookup"><span data-stu-id="c2183-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="c2183-155">Klienci mogą następnie użyć tej akcji.</span><span class="sxs-lookup"><span data-stu-id="c2183-155">Clients can then use this action.</span></span> <span data-ttu-id="c2183-156">Poniższy kod WSDL pokazuje potwierdzenia zasad `HttpCookieSessionBindingElement`utworzone z pliku .</span><span class="sxs-lookup"><span data-stu-id="c2183-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="c2183-157">Klasa `HttpCookieSessionBinding` jest powiązanie dostarczone przez system, który używa elementu wiązania opisane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="c2183-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="c2183-158">Dodawanie kanału do systemu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c2183-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="c2183-159">Próbka zawiera dwie klasy, które udostępniają kanał próbki za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c2183-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="c2183-160">Pierwszy z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> nich `HttpCookieSessionBindingElement`to dla .</span><span class="sxs-lookup"><span data-stu-id="c2183-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="c2183-161">Większość implementacji jest delegowana `HttpCookieSessionBindingConfigurationElement`do , który <xref:System.ServiceModel.Configuration.StandardBindingElement>pochodzi z .</span><span class="sxs-lookup"><span data-stu-id="c2183-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="c2183-162">Ma `HttpCookieSessionBindingConfigurationElement` właściwości, które odpowiadają właściwości `HttpCookieSessionBindingElement`na .</span><span class="sxs-lookup"><span data-stu-id="c2183-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="c2183-163">Sekcja rozszerzenia elementu wiązania</span><span class="sxs-lookup"><span data-stu-id="c2183-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="c2183-164">Sekcja `HttpCookieSessionBindingElementSection` <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> jest, która `HttpCookieSessionBindingElement` udostępnia do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c2183-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="c2183-165">Z kilku zastępuje nazwę sekcji konfiguracji, typ elementu wiązania i jak utworzyć element wiązania są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="c2183-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="c2183-166">Następnie możemy zarejestrować sekcję rozszerzenia w pliku konfiguracyjnym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c2183-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
```xml  
<configuration>
    <system.serviceModel>
      <extensions>
        <bindingElementExtensions>
          <add name="httpCookieSession"
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,
                    HttpCookieSessionExtension, Version=1.0.0.0,
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>
    </system.serviceModel>
</configuration>  
```  
  
## <a name="test-code"></a><span data-ttu-id="c2183-167">Kod testu</span><span class="sxs-lookup"><span data-stu-id="c2183-167">Test Code</span></span>  
 <span data-ttu-id="c2183-168">Kod testowy do korzystania z tego przykładowego transportu jest dostępny w katalogach klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="c2183-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="c2183-169">Składa się z dwóch testów — jeden `allowCookies` test `true` używa powiązania z zestawem na kliencie.</span><span class="sxs-lookup"><span data-stu-id="c2183-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="c2183-170">Drugi test umożliwia jawne zamknięcie (przy użyciu wymiany komunikatów zakończenia) na powiązanie.</span><span class="sxs-lookup"><span data-stu-id="c2183-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="c2183-171">Po uruchomieniu próbki powinny zostać wyświetlene następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="c2183-171">When you run the sample, you should see the following output:</span></span>  
  
```console  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2183-172">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="c2183-172">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c2183-173">Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c2183-173">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="c2183-174">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2183-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="c2183-175">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2183-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c2183-176">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2183-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
