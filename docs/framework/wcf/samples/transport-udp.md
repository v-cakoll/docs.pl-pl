---
title: 'Transport: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: f7dea8a95490377226acd09a3463b102d42834d6
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711925"
---
# <a name="transport-udp"></a><span data-ttu-id="1eeff-102">Transport: UDP</span><span class="sxs-lookup"><span data-stu-id="1eeff-102">Transport: UDP</span></span>
<span data-ttu-id="1eeff-103">Przykład transportu UDP ilustruje sposób implementacji protokołu UDP emisji pojedynczej i multiemisji jako niestandardowego transportu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1eeff-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="1eeff-104">W przykładzie opisano zalecaną procedurę tworzenia niestandardowego transportu w programie WCF przy użyciu struktury kanału i poniższych najlepszych rozwiązań w zakresie usług WCF.</span><span class="sxs-lookup"><span data-stu-id="1eeff-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="1eeff-105">Poniżej przedstawiono procedurę tworzenia transportu niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="1eeff-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="1eeff-106">Podjęcie decyzji o tym, które z [komunikatów](#MessageExchangePatterns) kanału (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel lub IReplyChannel) będą obsługiwane przez obiekt ChannelFactory i ChannelListener.</span><span class="sxs-lookup"><span data-stu-id="1eeff-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="1eeff-107">Następnie zdecyduj, czy będą obsługiwane zmiany w sesji dla tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="1eeff-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="1eeff-108">Utwórz fabrykę kanałów i odbiornik obsługujący wzorzec wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1eeff-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="1eeff-109">Upewnij się, że wszystkie wyjątki specyficzne dla sieci są znormalizowane do odpowiedniej klasy pochodnej <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="1eeff-110">Dodaj element [> powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) , który dodaje niestandardowy transport do stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="1eeff-110">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="1eeff-111">Aby uzyskać więcej informacji, zobacz [Dodawanie elementu powiązania](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="1eeff-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="1eeff-112">Dodaj sekcję rozszerzenie elementu powiązania, aby udostępnić nowy element powiązania do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1eeff-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="1eeff-113">Dodaj rozszerzenia metadanych, aby komunikować możliwości z innymi punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="1eeff-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="1eeff-114">Dodaj powiązanie, które wstępnie konfiguruje stos elementów powiązania zgodnie z dobrze zdefiniowanym profilem.</span><span class="sxs-lookup"><span data-stu-id="1eeff-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="1eeff-115">Aby uzyskać więcej informacji, zobacz [Dodawanie standardowego powiązania](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="1eeff-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="1eeff-116">Dodaj sekcję powiązania i element konfiguracji powiązania, aby uwidocznić powiązanie z systemem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1eeff-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="1eeff-117">Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi konfiguracji](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="1eeff-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="1eeff-118">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="1eeff-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="1eeff-119">Pierwszym krokiem w przypadku pisania niestandardowego transportu jest podjęcie decyzji, które wzorce wymiany komunikatów (MEPs) są wymagane do transportu.</span><span class="sxs-lookup"><span data-stu-id="1eeff-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="1eeff-120">Istnieją trzy MEPs do wyboru:</span><span class="sxs-lookup"><span data-stu-id="1eeff-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="1eeff-121">Datagram (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="1eeff-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="1eeff-122">W przypadku korzystania z unikatowy MEP datagramu klient wysyła komunikat przy użyciu wymiany "pożar i zapomnij".</span><span class="sxs-lookup"><span data-stu-id="1eeff-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="1eeff-123">Usługa Fire i zapomnij wymiany jest taka, która wymaga potwierdzenia pomyślnego dostarczenia poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="1eeff-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="1eeff-124">Komunikat może zostać utracony podczas przesyłania i nigdy nie docierał do usługi.</span><span class="sxs-lookup"><span data-stu-id="1eeff-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="1eeff-125">Jeśli operacja wysyłania zostanie zakończona pomyślnie na końcu klienta, nie gwarantuje to, że zdalny punkt końcowy odebrał komunikat.</span><span class="sxs-lookup"><span data-stu-id="1eeff-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="1eeff-126">Datagram jest podstawowym blokiem konstrukcyjnym do obsługi komunikatów, ponieważ można tworzyć własne protokoły na jego podstawie — w tym niezawodne protokoły i bezpieczne protokoły.</span><span class="sxs-lookup"><span data-stu-id="1eeff-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="1eeff-127">Kanały datagramów klienta implementują interfejsy <xref:System.ServiceModel.Channels.IOutputChannel> interfejs i datagram usługi implementują interfejs <xref:System.ServiceModel.Channels.IInputChannel>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="1eeff-128">Żądanie-odpowiedź (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="1eeff-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="1eeff-129">W tym unikatowy MEP komunikat jest wysyłany, a odpowiedź zostanie odebrana.</span><span class="sxs-lookup"><span data-stu-id="1eeff-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="1eeff-130">Wzorzec składa się z par żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="1eeff-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="1eeff-131">Przykłady wywołań żądania-odpowiedź to zdalne wywołania procedur (RPC) i przeglądarka.</span><span class="sxs-lookup"><span data-stu-id="1eeff-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="1eeff-132">Ten wzorzec jest również znany jako półdupleks.</span><span class="sxs-lookup"><span data-stu-id="1eeff-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="1eeff-133">W tym unikatowy MEP kanały klienta implementują <xref:System.ServiceModel.Channels.IRequestChannel> i kanały usługi implementują <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="1eeff-134">Dupleks (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="1eeff-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="1eeff-135">UNIKATOWY MEP dupleks umożliwia wysyłanie dowolnej liczby komunikatów przez klienta i odbieranie ich w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="1eeff-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="1eeff-136">UNIKATOWY MEP dupleks jest taka sama jak rozmowa telefoniczna, gdzie każdy wypowiadany wyraz jest komunikatem.</span><span class="sxs-lookup"><span data-stu-id="1eeff-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="1eeff-137">Ponieważ obie strony mogą wysyłać i odbierać dane w tym unikatowy MEP, interfejs zaimplementowany przez klienta i kanały usługi jest <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="1eeff-138">Każdy z tych MEPs może również obsługiwać sesje.</span><span class="sxs-lookup"><span data-stu-id="1eeff-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="1eeff-139">Dodatkowe funkcje udostępniane przez kanał obsługujący sesje polegają na tym, że są skorelowane wszystkie komunikaty wysyłane i odbierane w kanale.</span><span class="sxs-lookup"><span data-stu-id="1eeff-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="1eeff-140">Wzorzec żądanie-odpowiedź jest autonomiczną sesją dwustronicową, ponieważ żądanie i odpowiedź są skorelowane.</span><span class="sxs-lookup"><span data-stu-id="1eeff-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="1eeff-141">Z kolei wzorzec żądanie-odpowiedź, który obsługuje sesje, oznacza, że wszystkie pary żądanie/odpowiedź w tym kanale są skorelowane ze sobą.</span><span class="sxs-lookup"><span data-stu-id="1eeff-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="1eeff-142">Dzięki temu można uzyskać łącznie sześć MEPs — datagram, żądanie-odpowiedź, dupleks, datagram z sesjami, żądanie-odpowiedź z sesjami i dupleks z sesjami — do wyboru.</span><span class="sxs-lookup"><span data-stu-id="1eeff-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1eeff-143">W przypadku transportu UDP jedyną obsługiwaną unikatowy MEPą jest datagram, ponieważ protokół UDP jest z natury "pożar i zapomnij".</span><span class="sxs-lookup"><span data-stu-id="1eeff-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="1eeff-144">Interfejs ICommunicationObject i cykl życia obiektów WCF</span><span class="sxs-lookup"><span data-stu-id="1eeff-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="1eeff-145">Program WCF ma wspólny komputer stanu używany do zarządzania cyklem życia obiektów, takimi jak <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>i <xref:System.ServiceModel.Channels.IChannelListener>, które są używane do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="1eeff-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="1eeff-146">Istnieje pięć Stanów, w których te obiekty komunikacyjne mogą istnieć.</span><span class="sxs-lookup"><span data-stu-id="1eeff-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="1eeff-147">Te Stany są reprezentowane przez Wyliczenie <xref:System.ServiceModel.CommunicationState> i są następujące:</span><span class="sxs-lookup"><span data-stu-id="1eeff-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="1eeff-148">Utworzone: jest to stan <xref:System.ServiceModel.ICommunicationObject> podczas pierwszego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1eeff-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="1eeff-149">W tym stanie nie ma danych wejściowych/wyjściowych (we/wy).</span><span class="sxs-lookup"><span data-stu-id="1eeff-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="1eeff-150">Otwieranie: obiekty są przenoszone do tego stanu po wywołaniu <xref:System.ServiceModel.ICommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="1eeff-151">W tym punkcie właściwości są niezmienne, a wejście/wyjście może zacząć.</span><span class="sxs-lookup"><span data-stu-id="1eeff-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="1eeff-152">To przejście jest prawidłowe tylko ze stanu utworzonego.</span><span class="sxs-lookup"><span data-stu-id="1eeff-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="1eeff-153">Otwarte: obiekty są przenoszone do tego stanu po zakończeniu procesu otwierania.</span><span class="sxs-lookup"><span data-stu-id="1eeff-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="1eeff-154">To przejście jest prawidłowe tylko w stanie otwarcia.</span><span class="sxs-lookup"><span data-stu-id="1eeff-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="1eeff-155">W tym momencie obiekt jest w pełni przydatny do przeniesienia.</span><span class="sxs-lookup"><span data-stu-id="1eeff-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="1eeff-156">Zamykanie: obiekty są przenoszone do tego stanu, gdy <xref:System.ServiceModel.ICommunicationObject.Close%2A> jest wywoływana w celu bezpiecznego zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="1eeff-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="1eeff-157">To przejście jest prawidłowe tylko w stanie otwartym.</span><span class="sxs-lookup"><span data-stu-id="1eeff-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="1eeff-158">Zamknięte: w obiektach stanu zamkniętego nie można już używać.</span><span class="sxs-lookup"><span data-stu-id="1eeff-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="1eeff-159">Ogólnie rzecz biorąc, większość konfiguracji jest nadal dostępna do inspekcji, ale nie można przeprowadzić komunikacji.</span><span class="sxs-lookup"><span data-stu-id="1eeff-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="1eeff-160">Ten stan jest równoważny do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="1eeff-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="1eeff-161">Błąd: w stanie błędu, obiekty są dostępne do inspekcji, ale nie są już użyteczne.</span><span class="sxs-lookup"><span data-stu-id="1eeff-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="1eeff-162">Gdy wystąpi błąd nieodwracalny, obiekt przechodzi do tego stanu.</span><span class="sxs-lookup"><span data-stu-id="1eeff-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="1eeff-163">Jedyne prawidłowe przejście z tego stanu jest w stanie `Closed`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="1eeff-164">Istnieją zdarzenia wyzwalane dla każdego przejścia stanu.</span><span class="sxs-lookup"><span data-stu-id="1eeff-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="1eeff-165">Metodę <xref:System.ServiceModel.ICommunicationObject.Abort%2A> można wywołać w dowolnym momencie i powoduje, że obiekt natychmiast przechodzi od bieżącego stanu do stanu zamkniętego.</span><span class="sxs-lookup"><span data-stu-id="1eeff-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="1eeff-166">Wywołanie <xref:System.ServiceModel.ICommunicationObject.Abort%2A> kończy wszystkie nieukończone zadania.</span><span class="sxs-lookup"><span data-stu-id="1eeff-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="1eeff-167">Odbiornik kanałów i kanałów</span><span class="sxs-lookup"><span data-stu-id="1eeff-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="1eeff-168">Następnym krokiem podczas pisania niestandardowego transportu jest utworzenie implementacji <xref:System.ServiceModel.Channels.IChannelFactory> dla kanałów klienta i <xref:System.ServiceModel.Channels.IChannelListener> dla kanałów usługi.</span><span class="sxs-lookup"><span data-stu-id="1eeff-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="1eeff-169">Warstwa kanału używa wzorca fabryki do konstruowania kanałów.</span><span class="sxs-lookup"><span data-stu-id="1eeff-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="1eeff-170">Funkcja WCF udostępnia pomocników klasy bazowej dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="1eeff-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="1eeff-171">Klasa <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza komputer stanu wcześniej opisany w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="1eeff-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

- <span data-ttu-id="1eeff-172">Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednoliconą klasę bazową dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="1eeff-173">Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasą bazową implementującą <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="1eeff-174">Klasa <xref:System.ServiceModel.Channels.ChannelFactoryBase> implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje przeciążenia `CreateChannel` do jednej `OnCreateChannel` metody abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="1eeff-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="1eeff-175">Klasa <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="1eeff-176">Dział IT zajmuje się podstawowym zarządzaniem stanem.</span><span class="sxs-lookup"><span data-stu-id="1eeff-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="1eeff-177">W tym przykładzie implementacja fabryki jest zawarta w UdpChannelFactory.cs, a implementacja odbiornika jest zawarta w UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="1eeff-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="1eeff-178">Implementacje <xref:System.ServiceModel.Channels.IChannel> są w UdpOutputChannel.cs i UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="1eeff-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="1eeff-179">Fabryka kanałów UDP</span><span class="sxs-lookup"><span data-stu-id="1eeff-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="1eeff-180">Klasa `UdpChannelFactory` pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="1eeff-181">Przykład przesłania <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A>, aby zapewnić dostęp do wersji komunikatu kodera wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1eeff-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="1eeff-182">W przykładzie zastąpił również <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A>, aby można było rozdzielić nasze wystąpienie <xref:System.ServiceModel.Channels.BufferManager> po przeniesieniu automatu Stanów.</span><span class="sxs-lookup"><span data-stu-id="1eeff-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="1eeff-183">Kanał wyjściowy UDP</span><span class="sxs-lookup"><span data-stu-id="1eeff-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="1eeff-184">`UdpOutputChannel` implementuje <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="1eeff-185">Konstruktor sprawdza poprawność argumentów i konstruuje obiekt docelowy <xref:System.Net.EndPoint> na podstawie przekazanego <xref:System.ServiceModel.EndpointAddress>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="1eeff-186">Kanał może być zamknięty bezpiecznie lub bezproblemowo.</span><span class="sxs-lookup"><span data-stu-id="1eeff-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="1eeff-187">Jeśli kanał zostanie zamknięty bezpiecznie, gniazdo jest zamknięte, a wywołanie jest nawiązywane z klasą bazową `OnClose` metodzie.</span><span class="sxs-lookup"><span data-stu-id="1eeff-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="1eeff-188">Jeśli zgłasza wyjątek, infrastruktura wywoła `Abort`, aby upewnić się, że kanał jest czyszczony.</span><span class="sxs-lookup"><span data-stu-id="1eeff-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="1eeff-189">Następnie implementujemy `Send()` i `BeginSend()`/`EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="1eeff-190">Ten podział jest podzielony na dwie główne sekcje.</span><span class="sxs-lookup"><span data-stu-id="1eeff-190">This breaks down into two main sections.</span></span> <span data-ttu-id="1eeff-191">Najpierw serializowaćmy komunikat do tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="1eeff-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="1eeff-192">Następnie wysyłamy dane uzyskane w sieci.</span><span class="sxs-lookup"><span data-stu-id="1eeff-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="1eeff-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="1eeff-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="1eeff-194">`UdpChannelListener`, które implementuje przykład dziedziczy z klasy <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="1eeff-195">Do odbierania datagramów jest stosowane pojedyncze gniazdo UDP.</span><span class="sxs-lookup"><span data-stu-id="1eeff-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="1eeff-196">Metoda `OnOpen` odbiera dane przy użyciu gniazda UDP w pętli asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="1eeff-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="1eeff-197">Dane są następnie konwertowane na komunikaty przy użyciu struktury kodowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1eeff-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="1eeff-198">Ponieważ ten sam kanał datagramu reprezentuje komunikat, który dociera z kilku źródeł, `UdpChannelListener` jest pojedynczym odbiornikiem.</span><span class="sxs-lookup"><span data-stu-id="1eeff-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="1eeff-199">Istnieje najwyżej jedna aktywna <xref:System.ServiceModel.Channels.IChannel> skojarzona z tym odbiornikiem.</span><span class="sxs-lookup"><span data-stu-id="1eeff-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="1eeff-200">Przykład generuje inny, tylko wtedy, gdy kanał, który jest zwracany przez metodę `AcceptChannel` jest następnie usuwany.</span><span class="sxs-lookup"><span data-stu-id="1eeff-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="1eeff-201">Po odebraniu komunikatu jest on dodawany do kolejki pojedynczego tego kanału.</span><span class="sxs-lookup"><span data-stu-id="1eeff-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="1eeff-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="1eeff-202">UdpInputChannel</span></span>  
 <span data-ttu-id="1eeff-203">Klasa `UdpInputChannel` implementuje `IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="1eeff-204">Składa się z kolejki komunikatów przychodzących wypełnianych przez gniazdo `UdpChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="1eeff-205">Te komunikaty są dekolejkowane przez metodę `IInputChannel.Receive`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="1eeff-206">Dodawanie elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="1eeff-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="1eeff-207">Teraz, gdy fabryki i kanały są kompilowane, muszą uwidocznić je w środowisku uruchomieniowym ServiceModel za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="1eeff-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="1eeff-208">Powiązanie to kolekcja elementów powiązania, które reprezentują stos komunikacji skojarzony z adresem usługi.</span><span class="sxs-lookup"><span data-stu-id="1eeff-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="1eeff-209">Każdy element w stosie jest reprezentowany przez [\<powiązanie >](../../configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="1eeff-209">Each element in the stack is represented by a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
 <span data-ttu-id="1eeff-210">W przykładzie element Binding jest `UdpTransportBindingElement`, który pochodzi z <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="1eeff-211">Zastępuje on następujące metody tworzenia fabryk skojarzonych z naszymi powiązaniami.</span><span class="sxs-lookup"><span data-stu-id="1eeff-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 <span data-ttu-id="1eeff-212">Zawiera również elementy członkowskie do klonowania `BindingElement` i zwracają nasz schemat (SOAP. UDP).</span><span class="sxs-lookup"><span data-stu-id="1eeff-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="1eeff-213">Dodawanie obsługi metadanych dla elementu powiązania transportowego</span><span class="sxs-lookup"><span data-stu-id="1eeff-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="1eeff-214">Aby zintegrować transport w systemie metadanych, musimy obsługiwać import i eksport zasad.</span><span class="sxs-lookup"><span data-stu-id="1eeff-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="1eeff-215">Dzięki temu można generować klientów naszego powiązania za pomocą [narzędzia Svcutil. exe (narzędzie do przesyłania metadanych)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1eeff-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="1eeff-216">Dodawanie obsługi WSDL</span><span class="sxs-lookup"><span data-stu-id="1eeff-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="1eeff-217">Element powiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji dotyczących adresowania w metadanych.</span><span class="sxs-lookup"><span data-stu-id="1eeff-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="1eeff-218">W przypadku korzystania z powiązania SOAP element powiązania transportu powinien również eksportować prawidłowy identyfikator URI transportu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="1eeff-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="1eeff-219">Eksport WSDL</span><span class="sxs-lookup"><span data-stu-id="1eeff-219">WSDL Export</span></span>  
 <span data-ttu-id="1eeff-220">Aby wyeksportować informacje dotyczące adresowania, `UdpTransportBindingElement` implementuje interfejs `IWsdlExportExtension`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="1eeff-221">Metoda `ExportEndpoint` dodaje do portu WSDL prawidłowe informacje dotyczące adresowania.</span><span class="sxs-lookup"><span data-stu-id="1eeff-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="1eeff-222">`UdpTransportBindingElement` implementacja metody `ExportEndpoint` również eksportuje identyfikator URI transportu, gdy punkt końcowy używa powiązania protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="1eeff-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="1eeff-223">Import WSDL</span><span class="sxs-lookup"><span data-stu-id="1eeff-223">WSDL Import</span></span>  
 <span data-ttu-id="1eeff-224">Aby zwiększyć system importowania WSDL do obsługi importowania adresów, należy dodać następującą konfigurację do pliku konfiguracji programu Svcutil. exe, jak pokazano w pliku Svcutil. exe. config.</span><span class="sxs-lookup"><span data-stu-id="1eeff-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1eeff-225">Podczas uruchamiania programu Svcutil. exe dostępne są dwie opcje pobrania pliku Svcutil. exe w celu załadowania rozszerzeń WSDL:</span><span class="sxs-lookup"><span data-stu-id="1eeff-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="1eeff-226">Wskaż plik konfiguracyjny Svcutil. exe przy użyciu > pliku/SvcutilConfig:\<.</span><span class="sxs-lookup"><span data-stu-id="1eeff-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="1eeff-227">Dodaj sekcję konfiguracji do pliku Svcutil. exe. config w tym samym katalogu, w którym znajduje się Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="1eeff-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="1eeff-228">Typ `UdpBindingElementImporter` implementuje interfejs `IWsdlImportExtension`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="1eeff-229">Metoda `ImportEndpoint` importuje adres z portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="1eeff-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="1eeff-230">Dodawanie obsługi zasad</span><span class="sxs-lookup"><span data-stu-id="1eeff-230">Adding Policy Support</span></span>  
 <span data-ttu-id="1eeff-231">Niestandardowy element powiązania może eksportować potwierdzenia zasad w powiązaniu WSDL dla punktu końcowego usługi, aby przedstawić możliwości tego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="1eeff-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="1eeff-232">Eksport zasad</span><span class="sxs-lookup"><span data-stu-id="1eeff-232">Policy Export</span></span>  
 <span data-ttu-id="1eeff-233">Typ `UdpTransportBindingElement` implementuje `IPolicyExportExtension`, aby dodać obsługę eksportowania zasad.</span><span class="sxs-lookup"><span data-stu-id="1eeff-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="1eeff-234">W związku z tym `System.ServiceModel.MetadataExporter` zawiera `UdpTransportBindingElement` w generacji zasad dla dowolnego powiązania, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="1eeff-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="1eeff-235">W `IPolicyExportExtension.ExportPolicy`dodamy potwierdzenie protokołu UDP i inne potwierdzenie w przypadku trybu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="1eeff-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="1eeff-236">Jest to spowodowane tym, że tryb multiemisji wpływa na sposób konstruowania stosu komunikacji i w związku z tym musi być koordynowany między stronami.</span><span class="sxs-lookup"><span data-stu-id="1eeff-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix, 
        UdpPolicyStrings.MulticastAssertion, 
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="1eeff-237">Ponieważ niestandardowe elementy powiązania transportu są odpowiedzialne za obsługę adresowania, implementacja `IPolicyExportExtension` na `UdpTransportBindingElement` musi również obsługiwać eksportowanie odpowiednich zatwierdzeń zasad WS-Addressing w celu wskazania używanej wersji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="1eeff-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="1eeff-238">Importowanie zasad</span><span class="sxs-lookup"><span data-stu-id="1eeff-238">Policy Import</span></span>  
 <span data-ttu-id="1eeff-239">Aby można było zwiększyć system importowania zasad, należy dodać następującą konfigurację do pliku konfiguracji programu Svcutil. exe, jak pokazano w pliku Svcutil. exe. config.</span><span class="sxs-lookup"><span data-stu-id="1eeff-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1eeff-240">Następnie implementujemy `IPolicyImporterExtension` z naszej zarejestrowanej klasy (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="1eeff-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="1eeff-241">W `ImportPolicy()`przeszukiwania potwierdzeń w naszym obszarze nazw i przetwarzania tych elementów w celu wygenerowania transportu i sprawdzenia, czy jest to multiemisja.</span><span class="sxs-lookup"><span data-stu-id="1eeff-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="1eeff-242">Należy również usunąć z listy potwierdzeń powiązań.</span><span class="sxs-lookup"><span data-stu-id="1eeff-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="1eeff-243">Po uruchomieniu programu Svcutil. exe dostępne są dwie opcje integracji:</span><span class="sxs-lookup"><span data-stu-id="1eeff-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="1eeff-244">Wskaż plik konfiguracyjny Svcutil. exe przy użyciu > pliku/SvcutilConfig:\<.</span><span class="sxs-lookup"><span data-stu-id="1eeff-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="1eeff-245">Dodaj sekcję konfiguracji do pliku Svcutil. exe. config w tym samym katalogu, w którym znajduje się Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="1eeff-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="1eeff-246">Dodawanie powiązania standardowego</span><span class="sxs-lookup"><span data-stu-id="1eeff-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="1eeff-247">Nasz element powiązania może być używany na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="1eeff-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="1eeff-248">Za pośrednictwem niestandardowego powiązania: niestandardowe powiązanie umożliwia użytkownikowi tworzenie własnych powiązań na podstawie dowolnego zestawu elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="1eeff-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="1eeff-249">Za pomocą podanego w systemie powiązania, które zawiera nasz element powiązania.</span><span class="sxs-lookup"><span data-stu-id="1eeff-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="1eeff-250">Funkcja WCF udostępnia wiele takich powiązań zdefiniowanych przez system, takich jak `BasicHttpBinding`, `NetTcpBinding`i `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="1eeff-251">Wszystkie te powiązania są skojarzone ze zdefiniowanym profilem.</span><span class="sxs-lookup"><span data-stu-id="1eeff-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="1eeff-252">Przykład implementuje powiązanie profilu w `SampleProfileUdpBinding`, które wynika z <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="1eeff-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="1eeff-253">`SampleProfileUdpBinding` zawiera maksymalnie cztery elementy powiązania w ramach tej grupy: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`i `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="1eeff-254">Dodawanie niestandardowego importera powiązań standardowych</span><span class="sxs-lookup"><span data-stu-id="1eeff-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="1eeff-255">Svcutil. exe i typ `WsdlImporter` domyślnie rozpoznaje i importuje powiązania zdefiniowane przez system.</span><span class="sxs-lookup"><span data-stu-id="1eeff-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="1eeff-256">W przeciwnym razie powiązanie zostanie zaimportowane jako wystąpienie `CustomBinding`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="1eeff-257">Aby umożliwić programowi Svcutil. exe i `WsdlImporter` Importowanie `SampleProfileUdpBinding` `UdpBindingElementImporter` również działa jako niestandardowy importer powiązań standardowych.</span><span class="sxs-lookup"><span data-stu-id="1eeff-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="1eeff-258">Niestandardowy importer powiązań standardowych implementuje metodę `ImportEndpoint` w interfejsie `IWsdlImportExtension`, aby sprawdzić wystąpienie `CustomBinding` zaimportowane z metadanych, aby sprawdzić, czy mogło zostać wygenerowane przez określone powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="1eeff-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="1eeff-259">Ogólnie rzecz biorąc, implementacja niestandardowego importera powiązań standardowych polega na sprawdzeniu właściwości zaimportowanych elementów powiązania, aby sprawdzić, czy zmieniono tylko właściwości, które mogły zostać ustawione przez powiązanie standardowe, a wszystkie inne właściwości są ich domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="1eeff-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="1eeff-260">Podstawową strategią wdrażania importera powiązań standardowych jest utworzenie wystąpienia standardowego powiązania, propagowanie właściwości z elementów powiązania do standardowego wystąpienia powiązania, które obsługuje powiązanie standardowe, oraz porównanie powiązania elementy ze standardowego powiązania z zaimportowanymi elementami powiązania.</span><span class="sxs-lookup"><span data-stu-id="1eeff-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="1eeff-261">Dodawanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1eeff-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="1eeff-262">Aby udostępnić nasze transporty w konfiguracji, należy zaimplementować dwie sekcje konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="1eeff-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="1eeff-263">Pierwszy to `BindingElementExtensionElement` `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="1eeff-264">Jest tak dlatego, że implementacje `CustomBinding` mogą odwoływać się do naszego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="1eeff-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="1eeff-265">Drugim jest `Configuration` dla naszych `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="1eeff-266">Element rozszerzenia elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="1eeff-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="1eeff-267">Sekcja `UdpTransportElement` jest `BindingElementExtensionElement`, który uwidacznia `UdpTransportBindingElement` do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1eeff-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="1eeff-268">Za pomocą kilku podstawowych zastąpień definiujemy nazwę sekcji konfiguracji, typ naszego elementu powiązania oraz sposób tworzenia naszego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="1eeff-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="1eeff-269">Następnie możemy zarejestrować naszą sekcję rozszerzenia w pliku konfiguracji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1eeff-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1eeff-270">Do rozszerzenia można odwoływać się z niestandardowych powiązań, aby użyć protokołu UDP jako transportu.</span><span class="sxs-lookup"><span data-stu-id="1eeff-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a><span data-ttu-id="1eeff-271">Sekcja powiązania</span><span class="sxs-lookup"><span data-stu-id="1eeff-271">Binding Section</span></span>  
 <span data-ttu-id="1eeff-272">Sekcja `SampleProfileUdpBindingCollectionElement` jest `StandardBindingCollectionElement`, który uwidacznia `SampleProfileUdpBinding` do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1eeff-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="1eeff-273">Zbiorcza implementacja jest delegowana do `SampleProfileUdpBindingConfigurationElement`, który pochodzi z `StandardBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="1eeff-274">`SampleProfileUdpBindingConfigurationElement` ma właściwości, które odpowiadają właściwościom `SampleProfileUdpBinding`i funkcje do mapowania na podstawie powiązania `ConfigurationElement`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="1eeff-275">Na koniec Zastąp metodę `OnApplyConfiguration` w naszym `SampleProfileUdpBinding`, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1eeff-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 <span data-ttu-id="1eeff-276">Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, należy dodać następującą sekcję do odpowiedniego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1eeff-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="1eeff-277">Następnie można się do niego odwoływać z sekcji konfiguracji serviceModel.</span><span class="sxs-lookup"><span data-stu-id="1eeff-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="1eeff-278">Usługa i klient testowy UDP</span><span class="sxs-lookup"><span data-stu-id="1eeff-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="1eeff-279">Kod testowy służący do korzystania z tego przykładowego transportu jest dostępny w katalogach UdpTestService i UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="1eeff-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="1eeff-280">Kod usługi składa się z dwóch testów — jeden test konfiguruje powiązania i punkty końcowe z kodu, a drugi robi to za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1eeff-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="1eeff-281">Oba testy używają dwóch punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="1eeff-281">Both tests use two endpoints.</span></span> <span data-ttu-id="1eeff-282">Jeden punkt końcowy używa `SampleUdpProfileBinding` z [\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) ustawiony na `true`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="1eeff-283">Drugi punkt końcowy używa niestandardowego powiązania z `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="1eeff-284">Jest to równoznaczne z użyciem `SampleUdpProfileBinding` z [\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) ustawionym na `false`.</span><span class="sxs-lookup"><span data-stu-id="1eeff-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="1eeff-285">Oba testy umożliwiają utworzenie usługi, dodanie punktu końcowego dla każdego powiązania, otwarcie usługi i oczekiwanie na naciśnięcie klawisza ENTER przed zamknięciem usługi.</span><span class="sxs-lookup"><span data-stu-id="1eeff-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="1eeff-286">Po uruchomieniu aplikacji testowej usługi powinny zostać wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="1eeff-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="1eeff-287">Następnie możesz uruchomić testową aplikację kliencką dla opublikowanych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="1eeff-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="1eeff-288">Aplikacja testowa klienta tworzy klienta dla każdego punktu końcowego i wysyła pięć komunikatów do każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1eeff-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="1eeff-289">Następujące dane wyjściowe są na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="1eeff-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="1eeff-290">Poniżej przedstawiono pełne dane wyjściowe usługi.</span><span class="sxs-lookup"><span data-stu-id="1eeff-290">The following is the full output on the service.</span></span>  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 <span data-ttu-id="1eeff-291">Aby uruchomić aplikację kliencką dla punktów końcowych publikowanych za pomocą konfiguracji, naciśnij klawisz ENTER w usłudze, a następnie ponownie uruchom klienta testowego.</span><span class="sxs-lookup"><span data-stu-id="1eeff-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="1eeff-292">W usłudze powinny zostać wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="1eeff-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="1eeff-293">Uruchomienie klienta ponownie daje takie samo, jak poprzednie wyniki.</span><span class="sxs-lookup"><span data-stu-id="1eeff-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="1eeff-294">Aby ponownie wygenerować kod i konfigurację klienta przy użyciu programu Svcutil. exe, uruchom aplikację usługi, a następnie uruchom następujący plik Svcutil. exe z katalogu głównego przykładu.</span><span class="sxs-lookup"><span data-stu-id="1eeff-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="1eeff-295">Należy pamiętać, że Svcutil. exe nie generuje konfiguracji rozszerzenia powiązania dla `SampleProfileUdpBinding`, więc należy dodać ją ręcznie.</span><span class="sxs-lookup"><span data-stu-id="1eeff-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>      
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1eeff-296">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="1eeff-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1eeff-297">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1eeff-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="1eeff-298">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1eeff-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1eeff-299">Zapoznaj się z poprzednią sekcją "usługa testowa i klient usługi UDP".</span><span class="sxs-lookup"><span data-stu-id="1eeff-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1eeff-300">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1eeff-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1eeff-301">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="1eeff-301">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1eeff-302">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1eeff-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1eeff-303">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1eeff-303">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
