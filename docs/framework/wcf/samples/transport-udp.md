---
title: 'Transport: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 3fd16ccd634b6875eae1e87547c35c6cba79c857
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143775"
---
# <a name="transport-udp"></a><span data-ttu-id="73455-102">Transport: UDP</span><span class="sxs-lookup"><span data-stu-id="73455-102">Transport: UDP</span></span>
<span data-ttu-id="73455-103">Przykład transportu UDP pokazuje, jak zaimplementować emisję pojedynczą udp i multiemisji jako niestandardowy transport fundacji komunikacji systemu Windows (WCF).</span><span class="sxs-lookup"><span data-stu-id="73455-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="73455-104">W przykładzie opisano zalecaną procedurę tworzenia transportu niestandardowego w WCF, przy użyciu struktury kanału i po WCF najlepszych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="73455-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="73455-105">Kroki tworzenia transportu niestandardowego są następujące:</span><span class="sxs-lookup"><span data-stu-id="73455-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="73455-106">Zdecyduj, który z wzorców [wymiany wiadomości](#MessageExchangePatterns) kanału (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel lub IReplyChannel) będzie obsługiwać channelfactory i ChannelListener.</span><span class="sxs-lookup"><span data-stu-id="73455-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="73455-107">Następnie zdecyduj, czy będzie obsługiwać sesyjne odmiany tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="73455-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="73455-108">Utwórz fabrykę kanałów i odbiornika, które obsługują wzorzec wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="73455-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="73455-109">Upewnij się, że wszelkie wyjątki specyficzne dla sieci <xref:System.ServiceModel.CommunicationException>są znormalizowane do odpowiedniej klasy pochodnej .</span><span class="sxs-lookup"><span data-stu-id="73455-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="73455-110">Dodaj element [ \<>powiązania,](../../configure-apps/file-schema/wcf/bindings.md) który dodaje niestandardowy transport do stosu kanałów.</span><span class="sxs-lookup"><span data-stu-id="73455-110">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="73455-111">Aby uzyskać więcej informacji, zobacz [Dodawanie elementu wiązania](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="73455-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="73455-112">Dodaj sekcję rozszerzenia elementu wiązania, aby udostępnić nowy element wiązania do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="73455-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="73455-113">Dodaj rozszerzenia metadanych, aby komunikować możliwości do innych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="73455-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="73455-114">Dodaj powiązanie, które wstępnie konfiguruje stos elementów wiązania zgodnie z dobrze zdefiniowanym profilem.</span><span class="sxs-lookup"><span data-stu-id="73455-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="73455-115">Aby uzyskać więcej informacji, zobacz [Dodawanie powiązania standardowego](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="73455-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="73455-116">Dodaj sekcję powiązania i element konfiguracji powiązania, aby udostępnić powiązanie do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="73455-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="73455-117">Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi konfiguracji](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="73455-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a><span data-ttu-id="73455-118">Wzorce wymiany wiadomości</span><span class="sxs-lookup"><span data-stu-id="73455-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="73455-119">Pierwszym krokiem w pisaniu transportu niestandardowego jest podjęcie decyzji, które wzorce wymiany komunikatów (MEP) są wymagane dla transportu.</span><span class="sxs-lookup"><span data-stu-id="73455-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="73455-120">Do wyboru jest trzech posłów do PE:</span><span class="sxs-lookup"><span data-stu-id="73455-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="73455-121">Datagram (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="73455-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="73455-122">Podczas korzystania z datagramu PO, klient wysyła wiadomość za pomocą "ogień i zapomnij" wymiany.</span><span class="sxs-lookup"><span data-stu-id="73455-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="73455-123">Wymiana ognia i zapomnij jest taki, który wymaga out-of-band potwierdzenie pomyślnej dostawy.</span><span class="sxs-lookup"><span data-stu-id="73455-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="73455-124">Wiadomość może zostać utracona podczas przesyłania i nigdy nie dotrze do usługi.</span><span class="sxs-lookup"><span data-stu-id="73455-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="73455-125">Jeśli operacja wysyłania zakończy się pomyślnie na końcu klienta, nie gwarantuje, że zdalny punkt końcowy odebrał wiadomość.</span><span class="sxs-lookup"><span data-stu-id="73455-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="73455-126">Datagram jest podstawowym elementem konstrukcyjnym dla wiadomości, ponieważ można tworzyć własne protokoły na nim , w tym niezawodne protokoły i bezpieczne protokoły.</span><span class="sxs-lookup"><span data-stu-id="73455-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="73455-127">Kanały datagramu <xref:System.ServiceModel.Channels.IOutputChannel> klienta implementują interfejs <xref:System.ServiceModel.Channels.IInputChannel> i kanały datagramu usługi implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="73455-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="73455-128">Odpowiedź na żądanie (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="73455-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="73455-129">W tym posłie do PE wysyłana jest wiadomość i odbierana jest odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="73455-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="73455-130">Wzorzec składa się z par żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="73455-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="73455-131">Przykładami wywołań żądanie-odpowiedź są zdalne wywołania procedury (RPC) i kontrolery WIRT przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="73455-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="73455-132">Ten wzorzec jest również znany jako Półdupleks.</span><span class="sxs-lookup"><span data-stu-id="73455-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="73455-133">W tym mep, <xref:System.ServiceModel.Channels.IRequestChannel> kanały klienta <xref:System.ServiceModel.Channels.IReplyChannel>implementowania i kanały usług implementować .</span><span class="sxs-lookup"><span data-stu-id="73455-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="73455-134">Dupleks (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="73455-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="73455-135">Dupleksowy poseł do PE umożliwia dowolną liczbę wiadomości, które mają być wysyłane przez klienta i odbierane w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="73455-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="73455-136">Dupleksowy poseł do PE jest jak rozmowa telefoniczna, gdzie każde wypowiadane słowo jest wiadomością.</span><span class="sxs-lookup"><span data-stu-id="73455-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="73455-137">Ponieważ obie strony mogą wysyłać i odbierać w tym mep, <xref:System.ServiceModel.Channels.IDuplexChannel>interfejs zaimplementowany przez kanały klienta i usługi jest .</span><span class="sxs-lookup"><span data-stu-id="73455-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="73455-138">Każdy z tych posłów do PE może również poprzeć sesje.</span><span class="sxs-lookup"><span data-stu-id="73455-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="73455-139">Dodatkową funkcją zapewnianą przez kanał obsługujący sesję jest to, że koreluje wszystkie wiadomości wysyłane i odbierane na kanale.</span><span class="sxs-lookup"><span data-stu-id="73455-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="73455-140">Wzorzec request-response jest autonomiczną sesją dwóch wiadomości, ponieważ żądanie i odpowiedź są skorelowane.</span><span class="sxs-lookup"><span data-stu-id="73455-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="73455-141">Z drugiej strony wzorzec request-response, który obsługuje sesje oznacza, że wszystkie pary żądania/odpowiedzi na tym kanale są ze sobą skorelowane.</span><span class="sxs-lookup"><span data-stu-id="73455-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="73455-142">Daje to łącznie sześciu posłów do PE — Datagram, Żądanie odpowiedzi, Dupleks, Datagram z sesjami, Żądanie-Odpowiedź z sesjami i Dupleks z sesjami — do wyboru.</span><span class="sxs-lookup"><span data-stu-id="73455-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73455-143">W przypadku transportu UDP jedynym posłem do PE, który jest obsługiwany, jest Datagram, ponieważ UDP jest z natury protokołem "ogień i zapomnij".</span><span class="sxs-lookup"><span data-stu-id="73455-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="73455-144">ICommunicationObject i cykl życia obiektu WCF</span><span class="sxs-lookup"><span data-stu-id="73455-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="73455-145">WCF ma wspólną maszynę stanu, która jest używana <xref:System.ServiceModel.Channels.IChannel> <xref:System.ServiceModel.Channels.IChannelFactory>do <xref:System.ServiceModel.Channels.IChannelListener> zarządzania cyklem życia obiektów, takich jak , i które są używane do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="73455-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="73455-146">Istnieje pięć stanów, w których te obiekty komunikacji mogą istnieć.</span><span class="sxs-lookup"><span data-stu-id="73455-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="73455-147">Te stany są reprezentowane przez wyliczenie <xref:System.ServiceModel.CommunicationState> i są następujące:</span><span class="sxs-lookup"><span data-stu-id="73455-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="73455-148">Utworzone: Jest to <xref:System.ServiceModel.ICommunicationObject> stan, kiedy jest po raz pierwszy wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="73455-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="73455-149">W tym stanie nie występuje wejście/wyjście (We/Wy).</span><span class="sxs-lookup"><span data-stu-id="73455-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="73455-150">Otwieranie: Obiekty przejście <xref:System.ServiceModel.ICommunicationObject.Open%2A> do tego stanu, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="73455-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="73455-151">W tym momencie właściwości są niezmienne i można rozpocząć wejście/wyjście.</span><span class="sxs-lookup"><span data-stu-id="73455-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="73455-152">To przejście jest prawidłowe tylko ze stanu Utworzone.</span><span class="sxs-lookup"><span data-stu-id="73455-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="73455-153">Otwarte: Obiekty przejście do tego stanu po zakończeniu otwartego procesu.</span><span class="sxs-lookup"><span data-stu-id="73455-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="73455-154">To przejście jest prawidłowe tylko ze stanu Otwieranie.</span><span class="sxs-lookup"><span data-stu-id="73455-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="73455-155">W tym momencie obiekt jest w pełni użyteczny do transferu.</span><span class="sxs-lookup"><span data-stu-id="73455-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="73455-156">Zamknięcie: Obiekty przejścia do <xref:System.ServiceModel.ICommunicationObject.Close%2A> tego stanu, gdy jest wywoływana dla bezpiecznego zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="73455-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="73455-157">To przejście jest prawidłowe tylko ze stanu Otwarty.</span><span class="sxs-lookup"><span data-stu-id="73455-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="73455-158">Zamknięte: W stanie zamknięte obiekty nie nadają się już do użytku.</span><span class="sxs-lookup"><span data-stu-id="73455-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="73455-159">Ogólnie rzecz biorąc większość konfiguracji jest nadal dostępna do inspekcji, ale nie może nastąpić żadna komunikacja.</span><span class="sxs-lookup"><span data-stu-id="73455-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="73455-160">Ten stan jest odpowiednikiem unieszkodliwiwania.</span><span class="sxs-lookup"><span data-stu-id="73455-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="73455-161">Uszkodzony: W stanie Faulted obiekty są dostępne do inspekcji, ale nie są już użyteczne.</span><span class="sxs-lookup"><span data-stu-id="73455-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="73455-162">Po wystąpieniu nieodwracalnego błędu obiekt przechodzi do tego stanu.</span><span class="sxs-lookup"><span data-stu-id="73455-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="73455-163">Jedynym prawidłowym przejściem z `Closed` tego stanu jest do stanu.</span><span class="sxs-lookup"><span data-stu-id="73455-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="73455-164">Istnieją zdarzenia, które uruchamiają dla każdego przejścia stanu.</span><span class="sxs-lookup"><span data-stu-id="73455-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="73455-165">Metoda <xref:System.ServiceModel.ICommunicationObject.Abort%2A> może być wywoływana w dowolnym momencie i powoduje, że obiekt do przejścia natychmiast z jego bieżącego stanu do zamkniętego stanu.</span><span class="sxs-lookup"><span data-stu-id="73455-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="73455-166">Wywołanie <xref:System.ServiceModel.ICommunicationObject.Abort%2A> kończy niedokończoną pracę.</span><span class="sxs-lookup"><span data-stu-id="73455-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="73455-167">Fabryka kanałów i odbiornik kanałów</span><span class="sxs-lookup"><span data-stu-id="73455-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="73455-168">Następnym krokiem w pisaniu transportu niestandardowego <xref:System.ServiceModel.Channels.IChannelFactory> jest utworzenie <xref:System.ServiceModel.Channels.IChannelListener> implementacji dla kanałów klienta i dla kanałów usług.</span><span class="sxs-lookup"><span data-stu-id="73455-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="73455-169">Warstwa kanału używa wzorca fabrycznego do konstruowania kanałów.</span><span class="sxs-lookup"><span data-stu-id="73455-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="73455-170">WCF zapewnia pomocników klasy podstawowej dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="73455-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="73455-171">Klasa <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza maszynę stanu wcześniej opisane w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="73455-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span>

- <span data-ttu-id="73455-172">Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednoliconą klasę podstawową dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span><span class="sxs-lookup"><span data-stu-id="73455-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="73455-173">Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> działa w <xref:System.ServiceModel.Channels.ChannelBase>połączeniu z , który jest <xref:System.ServiceModel.Channels.IChannel>klasą podstawową, która implementuje .</span><span class="sxs-lookup"><span data-stu-id="73455-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="73455-174">Klasa <xref:System.ServiceModel.Channels.ChannelFactoryBase> implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` przeciążenia `OnCreateChannel` w jedną metodę abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="73455-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="73455-175">Klasa <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="73455-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="73455-176">Zajmuje się podstawowym zarządzaniem państwem.</span><span class="sxs-lookup"><span data-stu-id="73455-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="73455-177">W tym przykładzie implementacji fabryki znajduje się w UdpChannelFactory.cs i implementacji odbiornika jest zawarty w UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="73455-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="73455-178">Implementacje <xref:System.ServiceModel.Channels.IChannel> są w UdpOutputChannel.cs i UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="73455-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="73455-179">Fabryka kanałów UDP</span><span class="sxs-lookup"><span data-stu-id="73455-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="73455-180">Pochodzi `UdpChannelFactory` z <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="73455-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="73455-181">Przykładowe <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zastąpienia, aby zapewnić dostęp do wersji wiadomości kodera wiadomości.</span><span class="sxs-lookup"><span data-stu-id="73455-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="73455-182">Przykład również <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> zastępuje, dzięki czemu możemy zniszczyć <xref:System.ServiceModel.Channels.BufferManager> nasze wystąpienie, gdy przechodzi maszyny stanu.</span><span class="sxs-lookup"><span data-stu-id="73455-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="73455-183">Kanał wyjściowy UDP</span><span class="sxs-lookup"><span data-stu-id="73455-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="73455-184">Implements `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="73455-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="73455-185">Konstruktor sprawdza poprawność argumentów <xref:System.Net.EndPoint> i konstruuje obiekt docelowy na podstawie <xref:System.ServiceModel.EndpointAddress> tego, który jest przekazywany w.</span><span class="sxs-lookup"><span data-stu-id="73455-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="73455-186">Kanał można zamknąć z gracją lub bezgrawych.</span><span class="sxs-lookup"><span data-stu-id="73455-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="73455-187">Jeśli kanał jest zamknięty bezpiecznie gniazdo jest zamknięty i wywołanie `OnClose` metody klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="73455-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="73455-188">Jeśli to zgłasza wyjątek, `Abort` infrastruktury wywołuje, aby upewnić się, że kanał jest czyszczone.</span><span class="sxs-lookup"><span data-stu-id="73455-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="73455-189">Następnie `Send()` wdrażamy `BeginSend()` / `EndSend()`i .</span><span class="sxs-lookup"><span data-stu-id="73455-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="73455-190">To dzieli się na dwie główne sekcje.</span><span class="sxs-lookup"><span data-stu-id="73455-190">This breaks down into two main sections.</span></span> <span data-ttu-id="73455-191">Najpierw serializujemy wiadomość do tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="73455-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="73455-192">Następnie wysyłamy uzyskane dane na drucie.</span><span class="sxs-lookup"><span data-stu-id="73455-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="73455-193">The UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="73455-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="73455-194">Implementuje `UdpChannelListener` próbki pochodzi z <xref:System.ServiceModel.Channels.ChannelListenerBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="73455-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="73455-195">Używa jednego gniazda UDP do odbierania datagramów.</span><span class="sxs-lookup"><span data-stu-id="73455-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="73455-196">Metoda `OnOpen` odbiera dane przy użyciu gniazda UDP w pętli asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="73455-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="73455-197">Dane są następnie konwertowane na wiadomości przy użyciu struktury kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="73455-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="73455-198">Ponieważ ten sam kanał datagramu reprezentuje komunikaty, `UdpChannelListener` które pochodzą z wielu źródeł, jest detektor singleton.</span><span class="sxs-lookup"><span data-stu-id="73455-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="73455-199">Jest co najwyżej jeden <xref:System.ServiceModel.Channels.IChannel> aktywny związany z tym odbiornikiem naraz.</span><span class="sxs-lookup"><span data-stu-id="73455-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="73455-200">Próbka generuje inny tylko wtedy, gdy kanał, który jest zwracany przez `AcceptChannel` metodę jest następnie usuwane.</span><span class="sxs-lookup"><span data-stu-id="73455-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="73455-201">Po odebraniu wiadomości jest ona likżdowana w tej pojedynczej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="73455-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="73455-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="73455-202">UdpInputChannel</span></span>  
 <span data-ttu-id="73455-203">Klasa `UdpInputChannel` implementuje `IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="73455-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="73455-204">Składa się z kolejki wiadomości przychodzących, `UdpChannelListener`który jest wypełniany przez gniazdo 's.</span><span class="sxs-lookup"><span data-stu-id="73455-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="73455-205">Te komunikaty są usuwane `IInputChannel.Receive` w kolejce przez metodę.</span><span class="sxs-lookup"><span data-stu-id="73455-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a><span data-ttu-id="73455-206">Dodawanie elementu wiązania</span><span class="sxs-lookup"><span data-stu-id="73455-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="73455-207">Teraz, gdy fabryki i kanały są budowane, musimy udostępnić je do środowiska uruchomieniowego ServiceModel za pośrednictwem powiązania.</span><span class="sxs-lookup"><span data-stu-id="73455-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="73455-208">Powiązanie jest kolekcją elementów wiązania, który reprezentuje stos komunikacji skojarzony z adresem usługi.</span><span class="sxs-lookup"><span data-stu-id="73455-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="73455-209">Każdy element w stosie jest reprezentowany przez [ \<element wiązania>.](../../configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="73455-209">Each element in the stack is represented by a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
 <span data-ttu-id="73455-210">W próbce element wiązania `UdpTransportBindingElement`jest , <xref:System.ServiceModel.Channels.TransportBindingElement>który pochodzi z .</span><span class="sxs-lookup"><span data-stu-id="73455-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="73455-211">Zastępuje następujące metody tworzenia fabryk skojarzonych z naszym powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="73455-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
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
  
 <span data-ttu-id="73455-212">Zawiera również członków do `BindingElement` klonowania i powrotu naszego programu (soap.udp).</span><span class="sxs-lookup"><span data-stu-id="73455-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="73455-213">Dodawanie obsługi metadanych dla elementu wiązania transportu</span><span class="sxs-lookup"><span data-stu-id="73455-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="73455-214">Aby zintegrować nasz transport z systemem metadanych, musimy wspierać zarówno import, jak i eksport polityki.</span><span class="sxs-lookup"><span data-stu-id="73455-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="73455-215">Pozwala nam to na generowanie klientów naszego powiązania za pośrednictwem [narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="73455-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="73455-216">Dodawanie obsługi WSDL</span><span class="sxs-lookup"><span data-stu-id="73455-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="73455-217">Element wiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji adresowych w metadanych.</span><span class="sxs-lookup"><span data-stu-id="73455-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="73455-218">Podczas korzystania z powiązania SOAP element wiązania transportu należy również wyeksportować poprawny identyfikator URI transportu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="73455-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="73455-219">Eksport WSDL</span><span class="sxs-lookup"><span data-stu-id="73455-219">WSDL Export</span></span>  
 <span data-ttu-id="73455-220">Aby wyeksportować informacje adresowe implementuje `UdpTransportBindingElement` `IWsdlExportExtension` interfejs.</span><span class="sxs-lookup"><span data-stu-id="73455-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="73455-221">Metoda `ExportEndpoint` dodaje poprawne informacje adresowe do portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="73455-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="73455-222">Implementacja `UdpTransportBindingElement` `ExportEndpoint` metody eksportuje również transportowy identyfikator URI, gdy punkt końcowy używa powiązania SOAP.</span><span class="sxs-lookup"><span data-stu-id="73455-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="73455-223">WSDL Import</span><span class="sxs-lookup"><span data-stu-id="73455-223">WSDL Import</span></span>  
 <span data-ttu-id="73455-224">Aby rozszerzyć system importowania WSDL do obsługi importowania adresów, musimy dodać następującą konfigurację do pliku konfiguracyjnego dla pliku Svcutil.exe, jak pokazano w pliku Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="73455-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="73455-225">Podczas uruchamiania programu Svcutil.exe dostępne są dwie opcje ładowania rozszerzenia importu WSDL przez program Svcutil.exe:</span><span class="sxs-lookup"><span data-stu-id="73455-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="73455-226">Punkt Svcutil.exe do naszego pliku konfiguracyjnego za\<pomocą pliku /SvcutilConfig:>.</span><span class="sxs-lookup"><span data-stu-id="73455-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="73455-227">Dodaj sekcję konfiguracji do pliku Svcutil.exe.config w tym samym katalogu co program Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="73455-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="73455-228">Typ `UdpBindingElementImporter` implementuje `IWsdlImportExtension` interfejs.</span><span class="sxs-lookup"><span data-stu-id="73455-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="73455-229">Metoda `ImportEndpoint` importuje adres z portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="73455-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="73455-230">Dodawanie obsługi zasad</span><span class="sxs-lookup"><span data-stu-id="73455-230">Adding Policy Support</span></span>  
 <span data-ttu-id="73455-231">Element wiązania niestandardowego można eksportować potwierdzeń zasad w powiązanie WSDL dla punktu końcowego usługi do wyrażania możliwości tego elementu wiązania.</span><span class="sxs-lookup"><span data-stu-id="73455-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="73455-232">Eksport zasad</span><span class="sxs-lookup"><span data-stu-id="73455-232">Policy Export</span></span>  
 <span data-ttu-id="73455-233">Typ `UdpTransportBindingElement` implementuje, `IPolicyExportExtension` aby dodać obsługę zasad eksportowania.</span><span class="sxs-lookup"><span data-stu-id="73455-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="73455-234">W rezultacie `System.ServiceModel.MetadataExporter` obejmuje `UdpTransportBindingElement` w generowaniu zasad dla dowolnego powiązania, które go zawiera.</span><span class="sxs-lookup"><span data-stu-id="73455-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="73455-235">W `IPolicyExportExtension.ExportPolicy`, dodajemy potwierdzenia dla UDP i innego potwierdzenia, jeśli jesteśmy w trybie multiemisji.</span><span class="sxs-lookup"><span data-stu-id="73455-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="73455-236">Jest tak, ponieważ tryb multiemisji wpływa na sposób konstruowania stosu komunikacji, a zatem musi być skoordynowane między obiema stronami.</span><span class="sxs-lookup"><span data-stu-id="73455-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="73455-237">Ponieważ niestandardowe elementy wiązania transportu są `IPolicyExportExtension` odpowiedzialne za `UdpTransportBindingElement` obsługę adresowania, implementacja na musi również obsługiwać eksportowanie odpowiednich potwierdzeń zasad adresowania WS, aby wskazać wersję używanego adresowania WS.</span><span class="sxs-lookup"><span data-stu-id="73455-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="73455-238">Import zasad</span><span class="sxs-lookup"><span data-stu-id="73455-238">Policy Import</span></span>  
 <span data-ttu-id="73455-239">Aby rozszerzyć system importu zasad, musimy dodać następującą konfigurację do pliku konfiguracyjnego dla pliku Svcutil.exe, jak pokazano w pliku Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="73455-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="73455-240">Następnie wdrażamy `IPolicyImporterExtension` z naszej`UdpBindingElementImporter`zarejestrowanej klasy ( ).</span><span class="sxs-lookup"><span data-stu-id="73455-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="73455-241">W `ImportPolicy()`, możemy przeglądać potwierdzenia w naszej przestrzeni nazw i przetwarzać te do generowania transportu i sprawdzić, czy jest multiemisji.</span><span class="sxs-lookup"><span data-stu-id="73455-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="73455-242">Musimy również usunąć potwierdzenia, które obsługujemy z listy potwierdzeń wiązania.</span><span class="sxs-lookup"><span data-stu-id="73455-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="73455-243">Ponownie, podczas uruchamiania programu Svcutil.exe dostępne są dwie opcje integracji:</span><span class="sxs-lookup"><span data-stu-id="73455-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="73455-244">Punkt Svcutil.exe do naszego pliku konfiguracyjnego za\<pomocą pliku /SvcutilConfig:>.</span><span class="sxs-lookup"><span data-stu-id="73455-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="73455-245">Dodaj sekcję konfiguracji do pliku Svcutil.exe.config w tym samym katalogu co program Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="73455-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a><span data-ttu-id="73455-246">Dodawanie standardowego powiązania</span><span class="sxs-lookup"><span data-stu-id="73455-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="73455-247">Nasz element wiązania może być używany na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="73455-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="73455-248">Za pośrednictwem niestandardowego powiązania: Niestandardowe powiązanie umożliwia użytkownikowi tworzenie własnego powiązania na podstawie dowolnego zestawu elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="73455-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="73455-249">Za pomocą powiązania dostarczonego przez system, który zawiera nasz element wiązania.</span><span class="sxs-lookup"><span data-stu-id="73455-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="73455-250">WCF udostępnia szereg tych powiązań zdefiniowanych `BasicHttpBinding`przez `NetTcpBinding`system, takich jak , i `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="73455-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="73455-251">Każde z tych powiązań jest skojarzone z dobrze zdefiniowanym profilem.</span><span class="sxs-lookup"><span data-stu-id="73455-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="73455-252">Przykład implementuje powiązanie `SampleProfileUdpBinding`profilu w <xref:System.ServiceModel.Channels.Binding>, który pochodzi od .</span><span class="sxs-lookup"><span data-stu-id="73455-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="73455-253">Zawiera `SampleProfileUdpBinding` do czterech elementów wiązania `UdpTransportBindingElement` `TextMessageEncodingBindingElement CompositeDuplexBindingElement`w `ReliableSessionBindingElement`nim: , , i .</span><span class="sxs-lookup"><span data-stu-id="73455-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="73455-254">Dodawanie niestandardowego importera wiązania standardowego</span><span class="sxs-lookup"><span data-stu-id="73455-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="73455-255">Program Svcutil.exe `WsdlImporter` i typ domyślnie rozpoznają i importują powiązania zdefiniowane przez system.</span><span class="sxs-lookup"><span data-stu-id="73455-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="73455-256">W przeciwnym razie powiązanie `CustomBinding` zostanie zaimportowane jako wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="73455-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="73455-257">Aby włączyć Svcutil.exe `WsdlImporter` i `SampleProfileUdpBinding` importować `UdpBindingElementImporter` również działa jako importer wiązania standard niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="73455-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="73455-258">Importer wiązania niestandardowego standard `ImportEndpoint` implementuje `IWsdlImportExtension` metodę w `CustomBinding` interfejsie, aby sprawdzić wystąpienie importowane z metadanych, aby zobaczyć, czy mogło zostać wygenerowane przez określone powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="73455-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="73455-259">Ogólnie rzecz biorąc implementowanie importera wiązania niestandardowego standard polega na sprawdzeniu właściwości importowanych elementów wiązania, aby sprawdzić, czy tylko właściwości, które mogły zostać ustawione przez standardowe powiązanie zostały zmienione i wszystkie inne właściwości są ich wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="73455-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="73455-260">Podstawową strategią wdrażania standardowego importera wiązania jest utworzenie wystąpienia standardowego powiązania, propagowanie właściwości z elementów wiązania do standardowego wystąpienia wiązania, które obsługuje standardowe powiązanie, oraz porównywanie powiązania elementy ze standardowego powiązania z importowanymi elementami wiązania.</span><span class="sxs-lookup"><span data-stu-id="73455-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a><span data-ttu-id="73455-261">Dodawanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="73455-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="73455-262">Aby udostępnić nasz transport za pomocą konfiguracji, musimy wdrożyć dwie sekcje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="73455-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="73455-263">Pierwszy to `BindingElementExtensionElement` dla `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="73455-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="73455-264">Jest to `CustomBinding` tak, że implementacje można odwołać się do naszego elementu wiązania.</span><span class="sxs-lookup"><span data-stu-id="73455-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="73455-265">Drugi jest `Configuration` dla `SampleProfileUdpBinding`naszych .</span><span class="sxs-lookup"><span data-stu-id="73455-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="73455-266">Element rozszerzenia elementu wiązania</span><span class="sxs-lookup"><span data-stu-id="73455-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="73455-267">Sekcja `UdpTransportElement` `BindingElementExtensionElement` jest, która `UdpTransportBindingElement` udostępnia do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="73455-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="73455-268">Za pomocą kilku podstawowych przesłomów definiujemy naszą nazwę sekcji konfiguracji, typ naszego elementu wiązania i sposób tworzenia naszego elementu wiązania.</span><span class="sxs-lookup"><span data-stu-id="73455-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="73455-269">Następnie możemy zarejestrować naszą sekcję rozszerzenia w pliku konfiguracyjnym, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="73455-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="73455-270">Rozszerzenie można odwoływać się od niestandardowych powiązań do korzystania z protokołu UDP jako transportu.</span><span class="sxs-lookup"><span data-stu-id="73455-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="binding-section"></a><span data-ttu-id="73455-271">Sekcja wiązania</span><span class="sxs-lookup"><span data-stu-id="73455-271">Binding Section</span></span>  
 <span data-ttu-id="73455-272">Sekcja `SampleProfileUdpBindingCollectionElement` `StandardBindingCollectionElement` jest, która `SampleProfileUdpBinding` udostępnia do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="73455-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="73455-273">Większość implementacji jest delegowana `SampleProfileUdpBindingConfigurationElement`do , który `StandardBindingElement`pochodzi z .</span><span class="sxs-lookup"><span data-stu-id="73455-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="73455-274">Ma `SampleProfileUdpBindingConfigurationElement` właściwości, które odpowiadają właściwości `SampleProfileUdpBinding`na , i funkcje do mapowania z `ConfigurationElement` powiązania.</span><span class="sxs-lookup"><span data-stu-id="73455-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="73455-275">Na koniec należy zastąpić `OnApplyConfiguration` metodę `SampleProfileUdpBinding`w naszym , jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="73455-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="73455-276">Aby zarejestrować ten program obsługi w systemie konfiguracji, dodajemy następującą sekcję do odpowiedniego pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="73455-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="73455-277">Następnie można odwoływać się z serviceModel sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="73455-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="73455-278">Usługa testowa UDP i klient</span><span class="sxs-lookup"><span data-stu-id="73455-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="73455-279">Kod testowy do korzystania z tego przykładowego transportu jest dostępny w katalogach UdpTestService i UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="73455-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="73455-280">Kod usługi składa się z dwóch testów — jeden test konfiguruje powiązania i punkty końcowe z kodu, a drugi robi to za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="73455-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="73455-281">Oba testy używają dwóch punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="73455-281">Both tests use two endpoints.</span></span> <span data-ttu-id="73455-282">Jeden punkt końcowy `SampleUdpProfileBinding` używa [ \<z reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) `true`ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="73455-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="73455-283">Drugi punkt końcowy używa niestandardowego `UdpTransportBindingElement`powiązania z programem .</span><span class="sxs-lookup"><span data-stu-id="73455-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="73455-284">Jest to równoważne użyciu `SampleUdpProfileBinding` z `false` [ \<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="73455-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="73455-285">Oba testy tworzą usługę, dodają punkt końcowy dla każdego powiązania, otwierają usługę, a następnie czekają, aż użytkownik trafi enter przed zamknięciem usługi.</span><span class="sxs-lookup"><span data-stu-id="73455-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="73455-286">Po uruchomieniu aplikacji testowej usługi powinny zostać wyświetlenia następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="73455-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="73455-287">Następnie można uruchomić aplikację klienta testowego względem opublikowanych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="73455-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="73455-288">Aplikacja testowa klienta tworzy klienta dla każdego punktu końcowego i wysyła pięć komunikatów do każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="73455-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="73455-289">Następujące dane wyjściowe znajduje się na kliencie.</span><span class="sxs-lookup"><span data-stu-id="73455-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="73455-290">Poniżej przedstawiono pełne dane wyjściowe w usłudze.</span><span class="sxs-lookup"><span data-stu-id="73455-290">The following is the full output on the service.</span></span>  
  
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
  
 <span data-ttu-id="73455-291">Aby uruchomić aplikację kliencką względem punktów końcowych opublikowanych przy użyciu konfiguracji, naciśnij enter w usłudze, a następnie uruchom ponownie klienta testowego.</span><span class="sxs-lookup"><span data-stu-id="73455-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="73455-292">W usłudze powinny zostać wyświetlenia następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="73455-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="73455-293">Uruchamianie klienta ponownie daje takie same jak poprzednie wyniki.</span><span class="sxs-lookup"><span data-stu-id="73455-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="73455-294">Aby ponownie wygenerować kod klienta i konfigurację przy użyciu pliku Svcutil.exe, uruchom aplikację usługi, a następnie uruchom następujący program Svcutil.exe z katalogu głównego próbki.</span><span class="sxs-lookup"><span data-stu-id="73455-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="73455-295">Należy zauważyć, że program Svcutil.exe nie `SampleProfileUdpBinding`generuje konfiguracji rozszerzenia powiązania dla programu , dlatego należy dodać ją ręcznie.</span><span class="sxs-lookup"><span data-stu-id="73455-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="73455-296">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="73455-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="73455-297">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73455-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="73455-298">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73455-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="73455-299">Zapoznaj się z poprzednią sekcją "Usługa testowa I klient UDP".</span><span class="sxs-lookup"><span data-stu-id="73455-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="73455-300">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="73455-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="73455-301">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="73455-301">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="73455-302">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="73455-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="73455-303">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="73455-303">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
