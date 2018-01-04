---
title: HttpCookieSession
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c06efd7450afe93eaecca1e678eb6f8bf5de7a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="httpcookiesession"></a><span data-ttu-id="43689-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="43689-102">HttpCookieSession</span></span>
<span data-ttu-id="43689-103">W tym przykładzie pokazano, jak zbudować kanału używać plików cookie protokołu HTTP do zarządzania sesji protokołu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="43689-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="43689-104">Ten kanał umożliwia komunikację między [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług i klientów ASMX lub między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi ASMX i klientami.</span><span class="sxs-lookup"><span data-stu-id="43689-104">This channel enables communication between [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services and ASMX clients or between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients and ASMX services.</span></span>  
  
 <span data-ttu-id="43689-105">Kiedy klient wywołuje metody sieci Web w usługi sieci Web ASMX które jest oparte na sesji, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aparat wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="43689-105">When a client calls a Web method in an ASMX Web service that is session-based, the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] engine does the following:</span></span>  
  
-   <span data-ttu-id="43689-106">Generuje unikatowy identyfikator (identyfikator sesji).</span><span class="sxs-lookup"><span data-stu-id="43689-106">Generates a unique ID (session ID).</span></span>  
  
-   <span data-ttu-id="43689-107">Generuje obiekt sesji i kojarzy ją z unikatowego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="43689-107">Generates the session object and associates it with the unique ID.</span></span>  
  
-   <span data-ttu-id="43689-108">Dodaje do odpowiedzi nagłówek HTTP Set-Cookie Unikatowy identyfikator i wysyła go do klienta.</span><span class="sxs-lookup"><span data-stu-id="43689-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
-   <span data-ttu-id="43689-109">Identyfikuje klienta na kolejnych wywołań na podstawie Identyfikatora sesji wysyła do niego.</span><span class="sxs-lookup"><span data-stu-id="43689-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="43689-110">Klient dołącza ten identyfikator sesji w jego kolejnych żądań wysyłanych do serwera.</span><span class="sxs-lookup"><span data-stu-id="43689-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="43689-111">Serwer używa Identyfikatora sesji z klienta można załadować obiektu session odpowiednie dla bieżącego kontekstu HTTP.</span><span class="sxs-lookup"><span data-stu-id="43689-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43689-112">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="43689-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43689-113">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="43689-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="43689-114">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="43689-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43689-115">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="43689-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="43689-116">Kanał HttpCookieSession wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="43689-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="43689-117">W tym przykładzie umożliwia sesji dla scenariuszy ASMX podobne.</span><span class="sxs-lookup"><span data-stu-id="43689-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="43689-118">W dolnej części naszych stosu kanału, istnieje transportu HTTP, która obsługuje <xref:System.ServiceModel.Channels.IRequestChannel> i <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="43689-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="43689-119">To zadanie kanału zapewnienie na wyższe poziomy stosu kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="43689-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="43689-120">Przykład implementuje dwa kanały (<xref:System.ServiceModel.Channels.IRequestSessionChannel> i <xref:System.ServiceModel.Channels.IReplySessionChannel>) obsługują sesji.</span><span class="sxs-lookup"><span data-stu-id="43689-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="43689-121">Kanał usługi</span><span class="sxs-lookup"><span data-stu-id="43689-121">Service Channel</span></span>  
 <span data-ttu-id="43689-122">Przykład zawiera kanału usługi na `HttpCookieReplySessionChannelListener` klasy.</span><span class="sxs-lookup"><span data-stu-id="43689-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="43689-123">Ta klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener> interfejsu i konwertuje <xref:System.ServiceModel.Channels.IReplyChannel> kanału z niższym w stosie kanału, aby <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="43689-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="43689-124">Ten proces można podzielić na następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="43689-124">This process can be divided into the following parts:</span></span>  
  
-   <span data-ttu-id="43689-125">Po otwarciu odbiornika kanałów akceptuje wewnętrzny kanał z jego wewnętrzny odbiornika.</span><span class="sxs-lookup"><span data-stu-id="43689-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="43689-126">Ponieważ wewnętrzny odbiornika jest odbiornik datagram i okres istnienia zaakceptowanych kanałów jest całkowicie niezależna od istnienia odbiornika, możemy zamknąć wewnętrzny odbiornika i zawierać tylko wewnętrznym kanale</span><span class="sxs-lookup"><span data-stu-id="43689-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   <span data-ttu-id="43689-127">Po ukończeniu procesu otwierania skonfigurowanie pętli komunikatów odbierać komunikaty z kanału wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="43689-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
-   <span data-ttu-id="43689-128">Po nadejściu wiadomości, kanał usługi sprawdza identyfikator sesji i demultipleksowanie do kanału sesji odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="43689-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="43689-129">Odbiornik kanału przechowuje słownik, który mapuje identyfikatory sesji z wystąpieniami kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="43689-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="43689-130">`HttpCookieReplySessionChannel` Klasa implementuje <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="43689-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="43689-131">Wyższe poziomy kanału stosu wywołań <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metody żądań odczytu dla tej sesji.</span><span class="sxs-lookup"><span data-stu-id="43689-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="43689-132">Każdy kanał sesji ma prywatną kolejkę komunikatów wypełniany przez kanał usługi.</span><span class="sxs-lookup"><span data-stu-id="43689-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="43689-133">W przypadku, gdy ktoś wywołuje <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metody i nie ma żadnych komunikatów w kolejce wiadomości, kanał czeka na określoną ilość czasu, przed zamknięciem samej siebie.</span><span class="sxs-lookup"><span data-stu-id="43689-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="43689-134">To spowoduje oczyszczenie kanały sesji utworzone dla innego niż[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów.</span><span class="sxs-lookup"><span data-stu-id="43689-134">This cleans up the session channels created for non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients.</span></span>  
  
 <span data-ttu-id="43689-135">Używamy `channelMapping` do śledzenia `ReplySessionChannels`, i firma Microsoft nie zamykaj naszych bazowy `innerChannel` dopóki zaakceptowanych kanałów zostały zamknięte.</span><span class="sxs-lookup"><span data-stu-id="43689-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="43689-136">W ten sposób `HttpCookieReplySessionChannel` może występować poza okres istnienia `HttpCookieReplySessionChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="43689-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="43689-137">Możemy również nie trzeba martwić się odbiornika pobierania bezużytecznych poniżej nam, ponieważ zaakceptowanych kanałów zachować odwołanie do ich odbiornika za pomocą `OnClosed` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="43689-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="43689-138">Kanału klienta</span><span class="sxs-lookup"><span data-stu-id="43689-138">Client channel</span></span>  
 <span data-ttu-id="43689-139">Odpowiedni kanał klienta jest `HttpCookieSessionChannelFactory` klasy.</span><span class="sxs-lookup"><span data-stu-id="43689-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="43689-140">Podczas tworzenia kanału fabryki kanałów opakowuje kanału wewnętrznego żądania z `HttpCookieRequestSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="43689-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="43689-141">`HttpCookieRequestSessionChannel` Klasy przekazuje wywołań podstawowy kanał żądania.</span><span class="sxs-lookup"><span data-stu-id="43689-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="43689-142">Jeśli klient zamyka serwera proxy, `HttpCookieRequestSessionChannel` wysyła komunikat do usługi, która wskazuje, że zamknięcie kanału.</span><span class="sxs-lookup"><span data-stu-id="43689-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="43689-143">W związku z tym stosu kanału usługi można bezpiecznie zamknięcia kanału sesji, który jest używany.</span><span class="sxs-lookup"><span data-stu-id="43689-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="43689-144">Powiązanie i Element powiązania</span><span class="sxs-lookup"><span data-stu-id="43689-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="43689-145">Po utworzeniu usługa i klient kanały, następnym krokiem jest ich do integracji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="43689-145">After creating the service and client channels, the next step is to integrate them into the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime.</span></span> <span data-ttu-id="43689-146">Kanały są widoczne dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] za pośrednictwem powiązania i elementy powiązań.</span><span class="sxs-lookup"><span data-stu-id="43689-146">Channels are exposed to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] through bindings and binding elements.</span></span> <span data-ttu-id="43689-147">Powiązanie składa się z jednego lub wielu elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="43689-147">A binding consists of one or many binding elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="43689-148">oferuje kilka powiązań zdefiniowanych przez system; na przykład klasy BasicHttpBinding lub WSHttpBinding albo obsługę.</span><span class="sxs-lookup"><span data-stu-id="43689-148"> offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="43689-149">`HttpCookieSessionBindingElement` Klasa zawiera implementację elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="43689-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="43689-150">Zastępuje ona, czy niezbędne kanału wystąpień fabryki odbiornika lub kanału odbiornika kanałów i metod tworzenia fabryki kanału.</span><span class="sxs-lookup"><span data-stu-id="43689-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="43689-151">W przykładzie użyto potwierdzeń zasad opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="43689-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="43689-152">Umożliwia to przykład, aby opublikować jej wymagań dotyczących kanału do innych klientów, którzy mogą korzystać z usługi.</span><span class="sxs-lookup"><span data-stu-id="43689-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="43689-153">Na przykład ten element powiązania publikuje potwierdzeń zasad, aby umożliwić klientom potencjalnych wiedzieć, że aplikacja obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="43689-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="43689-154">Ponieważ próbki pozwala `ExchangeTerminateMessage` właściwości w Konfiguracja elementu powiązania, dodaje potwierdzenia niezbędne, aby pokazać, że usługa obsługuje akcję wymiany wiadomości dodatkowe zakończenie sesji konwersacji.</span><span class="sxs-lookup"><span data-stu-id="43689-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="43689-155">Klienci mogą następnie użyj tej akcji.</span><span class="sxs-lookup"><span data-stu-id="43689-155">Clients can then use this action.</span></span> <span data-ttu-id="43689-156">Poniższy kod WSDL przedstawia potwierdzenia zasady utworzone na podstawie `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="43689-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
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
  
 <span data-ttu-id="43689-157">`HttpCookieSessionBinding` Klasa jest powiązania dostarczane przez system, które używa elementu powiązania opisanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="43689-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="43689-158">Dodawanie kanału do systemu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="43689-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="43689-159">Przykład zawiera dwie klasy, które udostępniają kanału próbki za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="43689-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="43689-160">Pierwsza to <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> dla `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="43689-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="43689-161">Delegowane do zbiorczego wdrożenia `HttpCookieSessionBindingConfigurationElement`, która jest pochodną <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="43689-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="43689-162">`HttpCookieSessionBindingConfigurationElement` Ma właściwości, które odpowiadają właściwościom na `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="43689-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="43689-163">Sekcja rozszerzenia elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="43689-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="43689-164">Sekcja `HttpCookieSessionBindingElementSection` jest <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> który uwidacznia `HttpCookieSessionBindingElement` do konfiguracji systemu.</span><span class="sxs-lookup"><span data-stu-id="43689-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="43689-165">Z kilku zastąpień zdefiniowanych nazwę sekcji konfiguracji, typ elementu powiązania i jak można utworzyć elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="43689-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="43689-166">Firma Microsoft może następnie rejestrować sekcji rozszerzeń w pliku konfiguracji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="43689-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
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
  
## <a name="test-code"></a><span data-ttu-id="43689-167">Kod testu</span><span class="sxs-lookup"><span data-stu-id="43689-167">Test Code</span></span>  
 <span data-ttu-id="43689-168">Za pomocą tego transportu przykładowy kod testu jest dostępny w katalogach klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="43689-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="43689-169">Składa się z dwóch testów — jeden test używa powiązania z `allowCookies` ustawioną `true` na kliencie.</span><span class="sxs-lookup"><span data-stu-id="43689-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="43689-170">Drugi test umożliwia zamknięcie jawnego (używając przerwania wymianie wiadomości) dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="43689-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="43689-171">Po uruchomieniu próbki powinny być widoczne następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="43689-171">When you run the sample, you should see the following output:</span></span>  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="43689-172">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="43689-172">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="43689-173">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="43689-173">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="43689-174">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43689-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="43689-175">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43689-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="43689-176">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43689-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43689-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43689-177">See Also</span></span>
