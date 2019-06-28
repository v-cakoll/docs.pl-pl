---
title: 'Transport: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 4ae4bf22f452035d10ecba6bcf93bf580ab7f5f8
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422155"
---
# <a name="transport-udp"></a><span data-ttu-id="b8e12-102">Transport: UDP</span><span class="sxs-lookup"><span data-stu-id="b8e12-102">Transport: UDP</span></span>
<span data-ttu-id="b8e12-103">Przykładowe transportu UDP demonstruje sposób implementacji UDP emisji pojedynczej i multiemisji jako niestandardowy transportu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b8e12-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="b8e12-104">Przykład w tym artykule opisano zalecane procedury tworzenia niestandardowych transportu programu WCF, za pomocą struktura kanału i zgodnie z najlepszymi rozwiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="b8e12-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="b8e12-105">Kroki umożliwiające utworzenie niestandardowego transportu są następujące:</span><span class="sxs-lookup"><span data-stu-id="b8e12-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="b8e12-106">Zdecyduj, które kanał [wiadomości programu Exchange wzorców](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel lub IReplyChannel) będzie obsługiwać Twoja elementu ChannelFactory i ChannelListener.</span><span class="sxs-lookup"><span data-stu-id="b8e12-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="b8e12-107">Następnie zdecyduj, czy będzie obsługiwać sesji odchylenia tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="b8e12-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="b8e12-108">Tworzenie fabryki kanałów i odbiornik, który obsługuje usługi wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b8e12-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="b8e12-109">Upewnij się, że wszystkie wyjątki dotyczące sieci są znormalizowane zgodnie z odpowiedniej klasy pochodnej z <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="b8e12-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="b8e12-110">Dodaj [ \<powiązania >](../../../../docs/framework/misc/binding.md) element, który dodaje niestandardowy transportu do stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="b8e12-110">Add a [\<binding>](../../../../docs/framework/misc/binding.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="b8e12-111">Aby uzyskać więcej informacji, zobacz [Dodawanie elementu powiązania](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="b8e12-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="b8e12-112">Dodaj sekcję rozszerzenia elementu powiązania do udostępnienia nowego elementu powiązania do konfiguracji systemu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="b8e12-113">Dodaj rozszerzenia metadanych do komunikowania się funkcji innych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="b8e12-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="b8e12-114">Dodaj powiązanie, które są wstępnie konfiguruje stosie elementów wiązania zgodnie z profilem dobrze zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="b8e12-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="b8e12-115">Aby uzyskać więcej informacji, zobacz [dodając powiązanie standardowe](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="b8e12-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="b8e12-116">Dodaj sekcję wiązania i element konfiguracji powiązania aby uwidocznić powiązania do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b8e12-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="b8e12-117">Aby uzyskać więcej informacji, zobacz [dodanie obsługi konfiguracji](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="b8e12-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="b8e12-118">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="b8e12-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="b8e12-119">Pierwszym krokiem Pisanie niestandardowych transportu jest podjęcie decyzji, które wzorców wymiany komunikatów (MEPs) są wymagane dla transportu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="b8e12-120">Istnieją trzy MEPs do wyboru:</span><span class="sxs-lookup"><span data-stu-id="b8e12-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="b8e12-121">Datagramów (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="b8e12-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="b8e12-122">Korzystając z datagram MEP, klient wysyła komunikat "fire and forget" program exchange jest używany.</span><span class="sxs-lookup"><span data-stu-id="b8e12-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="b8e12-123">Element zostanie wyzwolony i zapomnij programu exchange to taki, który wymaga potwierdzenia out-of-band skutecznej.</span><span class="sxs-lookup"><span data-stu-id="b8e12-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="b8e12-124">Komunikat może zostać utracone podczas przesyłania i nigdy nie dotrzeć do usługi.</span><span class="sxs-lookup"><span data-stu-id="b8e12-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="b8e12-125">Jeśli operacja wysyłania zakończy się pomyślnie po stronie klienta, nie gwarantuje to, że zdalny punkt końcowy otrzymał komunikat.</span><span class="sxs-lookup"><span data-stu-id="b8e12-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="b8e12-126">Datagram jest elementem konstrukcyjnym podstawowych do obsługi komunikatów, możesz tworzyć własne protokołów na jego podstawie — w tym protokoły niezawodne i bezpieczne protokoły.</span><span class="sxs-lookup"><span data-stu-id="b8e12-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="b8e12-127">Implementowanie kanały datagram klientów <xref:System.ServiceModel.Channels.IOutputChannel> implementuje interfejs i usługi kanały datagram <xref:System.ServiceModel.Channels.IInputChannel> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="b8e12-128">Request-Response (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="b8e12-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="b8e12-129">W tym MEP wiadomość jest wysyłana i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="b8e12-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="b8e12-130">Wzorzec składa się z pary odpowiedź na żądanie.</span><span class="sxs-lookup"><span data-stu-id="b8e12-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="b8e12-131">Odpowiedź na żądanie wywołania przykłady zdalnych wywołań procedur (RPC) i przeglądarka pobiera.</span><span class="sxs-lookup"><span data-stu-id="b8e12-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="b8e12-132">Ten wzorzec jest nazywany również półdupleks.</span><span class="sxs-lookup"><span data-stu-id="b8e12-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="b8e12-133">W tym MEP zaimplementuj kanały klientów <xref:System.ServiceModel.Channels.IRequestChannel> i zaimplementować usługi kanały <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="b8e12-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="b8e12-134">Duplex (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="b8e12-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="b8e12-135">Dwukierunkowe MEP umożliwia dowolną liczbę wiadomości wysłane przez klienta i odbieranie w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="b8e12-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="b8e12-136">Dwukierunkowego MEP przypomina rozmowy telefonicznej, gdzie każdy wyraz mowy jest komunikat.</span><span class="sxs-lookup"><span data-stu-id="b8e12-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="b8e12-137">Obie strony może wysyłać i odbierać w tym MEP, interfejs implementowany przez kanały klient internetowy i usługa jest <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="b8e12-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="b8e12-138">Każda z tych MEPs również obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="b8e12-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="b8e12-139">Dodano funkcje udostępniane przez kanał sesji aware jest, czy jest skorelowane wszystkie komunikaty wysłane i odebrane w kanale.</span><span class="sxs-lookup"><span data-stu-id="b8e12-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="b8e12-140">Wzorzec odpowiedź na żądanie jest sesję komunikat dwóch autonomicznych, jak żądania i odpowiedzi są powiązane.</span><span class="sxs-lookup"><span data-stu-id="b8e12-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="b8e12-141">Z kolei wzorzec odpowiedź na żądanie, który obsługuje sesji oznacza, że wszystkie pary żądanie/odpowiedź, w tym kanale są powiązane ze sobą.</span><span class="sxs-lookup"><span data-stu-id="b8e12-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="b8e12-142">Daje w sumie sześć MEPs — Datagram, odpowiedź na żądanie, dupleks, Datagram z sesjami, odpowiedź na żądanie z sesji i dwukierunkowe z sesjami — do wyboru.</span><span class="sxs-lookup"><span data-stu-id="b8e12-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8e12-143">Dla transportu UDP Datagram, jest tylko MEP, która jest obsługiwana, ponieważ UDP jest protokołem "fire and forget".</span><span class="sxs-lookup"><span data-stu-id="b8e12-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="b8e12-144">ICommunicationObject i cyklem życia obiektu programu WCF</span><span class="sxs-lookup"><span data-stu-id="b8e12-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="b8e12-145">Usługi WCF ma typowe automatu stanów, który służy do zarządzania cyklem życia obiektów, takich jak <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, i <xref:System.ServiceModel.Channels.IChannelListener> służące do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="b8e12-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="b8e12-146">Istnieje pięć państw, w których może istnieć tych obiektów komunikacyjnych.</span><span class="sxs-lookup"><span data-stu-id="b8e12-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="b8e12-147">Te stany są reprezentowane przez <xref:System.ServiceModel.CommunicationState> wyliczenie i są w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b8e12-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="b8e12-148">Utworzone: Jest to stan <xref:System.ServiceModel.ICommunicationObject> po raz pierwszy zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="b8e12-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="b8e12-149">Nie wejścia/wyjścia (We/Wy) występuje w tym stanie.</span><span class="sxs-lookup"><span data-stu-id="b8e12-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="b8e12-150">Otwieranie: Stan przejścia obiektów do tego, kiedy <xref:System.ServiceModel.ICommunicationObject.Open%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b8e12-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="b8e12-151">W tym momencie są wprowadzane niezmienialnych właściwości i rozpocząć wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="b8e12-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="b8e12-152">Ten proces przejścia jest prawidłowy tylko w stanie Created.</span><span class="sxs-lookup"><span data-stu-id="b8e12-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="b8e12-153">Otwarta: Obiekty przejście do tego stanu po zakończeniu procesu otwierania.</span><span class="sxs-lookup"><span data-stu-id="b8e12-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="b8e12-154">Ten proces przejścia jest prawidłowy tylko w stanie otwarcia.</span><span class="sxs-lookup"><span data-stu-id="b8e12-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="b8e12-155">W tym momencie obiekt jest w pełni użyteczne do przeniesienia.</span><span class="sxs-lookup"><span data-stu-id="b8e12-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="b8e12-156">Zamknięcie: Stan przejścia obiektów do tego, kiedy <xref:System.ServiceModel.ICommunicationObject.Close%2A> jest wywoływana dla łagodne zamykanie.</span><span class="sxs-lookup"><span data-stu-id="b8e12-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="b8e12-157">Ten proces przejścia jest prawidłowy tylko w stanie otwartym.</span><span class="sxs-lookup"><span data-stu-id="b8e12-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="b8e12-158">Zamknięte: W polu Zamknięto obiekty stanu nie są już można używać.</span><span class="sxs-lookup"><span data-stu-id="b8e12-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="b8e12-159">Ogólnie rzecz biorąc większość konfiguracji jest nadal dostępne dla kontroli, ale nie można komunikować się.</span><span class="sxs-lookup"><span data-stu-id="b8e12-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="b8e12-160">Ten stan jest odpowiednikiem zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="b8e12-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="b8e12-161">Wystąpił błąd: W stanie Faulted obiekty są dostępne do wglądu, ale można już używać.</span><span class="sxs-lookup"><span data-stu-id="b8e12-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="b8e12-162">Gdy wystąpi błąd nieodwracalny, obiekt przechodzi w ten stan.</span><span class="sxs-lookup"><span data-stu-id="b8e12-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="b8e12-163">Jedyne prawidłowe przejścia z tego stanu jest do `Closed` stanu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="b8e12-164">Występują zdarzenia, które są aktywowane, dla każdego przejścia stanu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="b8e12-165"><xref:System.ServiceModel.ICommunicationObject.Abort%2A> Metodę można wywołać w dowolnym momencie i sprawia, że obiekt do którego nastąpi przejście od razu od bieżącego stanu w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="b8e12-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="b8e12-166">Wywoływanie <xref:System.ServiceModel.ICommunicationObject.Abort%2A> kończy się dowolnym niedokończona praca.</span><span class="sxs-lookup"><span data-stu-id="b8e12-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="b8e12-167">Fabryka kanałów i odbiornika kanałów</span><span class="sxs-lookup"><span data-stu-id="b8e12-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="b8e12-168">Następnym krokiem w pisaniu niestandardowe transportu jest utworzenie implementacji klasy <xref:System.ServiceModel.Channels.IChannelFactory> kanały klientów i z <xref:System.ServiceModel.Channels.IChannelListener> kanałach usługi.</span><span class="sxs-lookup"><span data-stu-id="b8e12-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="b8e12-169">Warstwy kanału korzysta ze wzorca fabryki tworzenia kanałów.</span><span class="sxs-lookup"><span data-stu-id="b8e12-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="b8e12-170">Usługi WCF zapewnia pomocnicy klasy bazowej dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="b8e12-171"><xref:System.ServiceModel.Channels.CommunicationObject> Klasy implementuje <xref:System.ServiceModel.ICommunicationObject> oraz wymusza automatu stanów opisany wcześniej w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="b8e12-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

- <span data-ttu-id="b8e12-172"><xref:System.ServiceModel.Channels.ChannelManagerBase> Klasy implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednolicone klasa bazowa dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span><span class="sxs-lookup"><span data-stu-id="b8e12-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="b8e12-173"><xref:System.ServiceModel.Channels.ChannelManagerBase> Klasy działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasą bazową, która implementuje <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="b8e12-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="b8e12-174"><xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasy implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` przeciążeń w jednym `OnCreateChannel` metody abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="b8e12-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="b8e12-175"><xref:System.ServiceModel.Channels.ChannelListenerBase> Klasy implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="b8e12-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="b8e12-176">Ta odpowiada za zarządzanie stanem podstawowe.</span><span class="sxs-lookup"><span data-stu-id="b8e12-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="b8e12-177">W tym przykładzie wdrożenie fabryki znajduje się w UdpChannelFactory.cs i implementacji odbiornik znajduje się w UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="b8e12-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="b8e12-178"><xref:System.ServiceModel.Channels.IChannel> Implementacje są UdpOutputChannel.cs i UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="b8e12-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="b8e12-179">Fabryka kanałów UDP</span><span class="sxs-lookup"><span data-stu-id="b8e12-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="b8e12-180">`UdpChannelFactory` Pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="b8e12-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="b8e12-181">Przykład zastępuje <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zapewnienie dostępu do wersji wiadomości koder komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b8e12-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="b8e12-182">Zastępuje również próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> , dzięki czemu możemy zatrzymywania naszych wystąpienie <xref:System.ServiceModel.Channels.BufferManager> podczas przejścia automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="b8e12-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="b8e12-183">Kanał danych wyjściowych UDP</span><span class="sxs-lookup"><span data-stu-id="b8e12-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="b8e12-184">`UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="b8e12-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="b8e12-185">Konstruktor weryfikuje argumentów i tworzy miejsce docelowe <xref:System.Net.EndPoint> na podstawie obiektu <xref:System.ServiceModel.EndpointAddress> który jest przekazywany w.</span><span class="sxs-lookup"><span data-stu-id="b8e12-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="b8e12-186">Kanał może zostać zamknięty, bez problemu zmieniała lub ungracefully.</span><span class="sxs-lookup"><span data-stu-id="b8e12-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="b8e12-187">Jeśli kanał jest zamknięta bez problemu zmieniała gniazda zostanie zamknięte, a wywołanie klasy bazowej `OnClose` metody.</span><span class="sxs-lookup"><span data-stu-id="b8e12-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="b8e12-188">Jeśli to zgłasza wyjątek, wywołuje metodę infrastruktury `Abort` zapewnienie kanał jest czyszczony.</span><span class="sxs-lookup"><span data-stu-id="b8e12-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="b8e12-189">Następnie wdrożymy `Send()` i `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="b8e12-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="b8e12-190">To dzieli się na dwóch głównych sekcji.</span><span class="sxs-lookup"><span data-stu-id="b8e12-190">This breaks down into two main sections.</span></span> <span data-ttu-id="b8e12-191">Najpierw możemy serializować komunikatu do tablicy typu byte.</span><span class="sxs-lookup"><span data-stu-id="b8e12-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="b8e12-192">Firma Microsoft wyśle dane wynikowe w sieci.</span><span class="sxs-lookup"><span data-stu-id="b8e12-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="b8e12-193">The UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="b8e12-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="b8e12-194">`UdpChannelListener` Że próbki implementuje pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelListenerBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="b8e12-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="b8e12-195">Aby otrzymać datagramy używa jedno gniazdo UDP.</span><span class="sxs-lookup"><span data-stu-id="b8e12-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="b8e12-196">`OnOpen` Metoda otrzymuje dane przy użyciu gniazda UDP pętlę asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="b8e12-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="b8e12-197">Dane są następnie przekształcana w wiadomości przy użyciu Framework Kodowanie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="b8e12-198">Ponieważ ten sam kanał datagram reprezentuje komunikaty przychodzące z różnych źródeł, `UdpChannelListener` jest odbiornika pojedynczego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b8e12-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="b8e12-199">Na większości, jednym aktywnym <xref:System.ServiceModel.Channels.IChannel> skojarzony z tym odbiornik naraz.</span><span class="sxs-lookup"><span data-stu-id="b8e12-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="b8e12-200">Przykład generuje inny tylko wtedy, gdy kanał, który jest zwracany przez `AcceptChannel` metoda później zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="b8e12-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="b8e12-201">Gdy wiadomość zostaje odebrana, to umieszczonych w kolejce do tego kanału pojedynczego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b8e12-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="b8e12-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="b8e12-202">UdpInputChannel</span></span>  
 <span data-ttu-id="b8e12-203">`UdpInputChannel` Klasy implementuje `IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="b8e12-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="b8e12-204">Składa się z kolejki wiadomości przychodzących, które jest wypełniana przez `UdpChannelListener`w gniazda.</span><span class="sxs-lookup"><span data-stu-id="b8e12-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="b8e12-205">Te komunikaty są usuwane z kolejki przez `IInputChannel.Receive` metody.</span><span class="sxs-lookup"><span data-stu-id="b8e12-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="b8e12-206">Dodawanie elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="b8e12-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="b8e12-207">Teraz, gdy są kompilowane fabryk i kanałów, firma Microsoft musi narażają je do środowiska uruchomieniowego ServiceModel za pośrednictwem powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8e12-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="b8e12-208">Powiązanie to kolekcja elementów wiązania, który reprezentuje stos komunikacji skojarzone z adresem usługi.</span><span class="sxs-lookup"><span data-stu-id="b8e12-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="b8e12-209">Każdy element w stosie jest reprezentowany przez [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-209">Each element in the stack is represented by a [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
 <span data-ttu-id="b8e12-210">W tym przykładzie jest element powiązania `UdpTransportBindingElement`, która jest pochodną <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b8e12-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="b8e12-211">Zastępuje ona poniższych metod, aby tworzyć fabryki skojarzone z naszych powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8e12-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
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
  
 <span data-ttu-id="b8e12-212">Zawiera również członków do klonowania `BindingElement` i zwracanie tym schemacie (soap.udp).</span><span class="sxs-lookup"><span data-stu-id="b8e12-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="b8e12-213">Dodanie obsługi metadanych elementu powiązania transportu</span><span class="sxs-lookup"><span data-stu-id="b8e12-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="b8e12-214">Do integracji naszego transportu w systemie metadanych, firma Microsoft obsługuje import i Eksport zasad.</span><span class="sxs-lookup"><span data-stu-id="b8e12-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="b8e12-215">Dzięki temu można wygenerować klientów naszych powiązania za pomocą [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b8e12-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="b8e12-216">Dodawanie pomocy technicznej WSDL</span><span class="sxs-lookup"><span data-stu-id="b8e12-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="b8e12-217">Element powiązania transportu powiązanie jest odpowiedzialny za eksportowanie i importowanie informacji o adresach w metadanych.</span><span class="sxs-lookup"><span data-stu-id="b8e12-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="b8e12-218">Korzystając z powiązania protokołu SOAP, element powiązania transportu powinien również wyeksportować poprawne transportu identyfikatora URI w metadanych.</span><span class="sxs-lookup"><span data-stu-id="b8e12-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="b8e12-219">WSDL Export</span><span class="sxs-lookup"><span data-stu-id="b8e12-219">WSDL Export</span></span>  
 <span data-ttu-id="b8e12-220">Aby wyeksportować informacje dotyczące adresowania `UdpTransportBindingElement` implementuje `IWsdlExportExtension` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="b8e12-221">`ExportEndpoint` Metoda dodaje poprawnych informacji adresowania do portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="b8e12-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="b8e12-222">`UdpTransportBindingElement` Implementacji `ExportEndpoint` metoda również eksportuje transportu identyfikatora URI, gdy punkt końcowy korzysta z powiązania protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b8e12-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="b8e12-223">WSDL Import</span><span class="sxs-lookup"><span data-stu-id="b8e12-223">WSDL Import</span></span>  
 <span data-ttu-id="b8e12-224">Aby rozszerzyć system importu WSDL do obsługi adresów importowania, firma Microsoft należy dodać następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="b8e12-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="b8e12-225">Podczas uruchamiania Svcutil.exe, istnieją dwie opcje w celu uzyskania Svcutil.exe można załadować rozszerzenia importu WSDL:</span><span class="sxs-lookup"><span data-stu-id="b8e12-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="b8e12-226">Punkt Svcutil.exe do naszego pliku konfiguracji, za pomocą /SvcutilConfig:\<pliku >.</span><span class="sxs-lookup"><span data-stu-id="b8e12-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="b8e12-227">Dodaj sekcję konfiguracji do Svcutil.exe.config, w tym samym katalogu co Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="b8e12-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="b8e12-228">`UdpBindingElementImporter` Typ implementuje `IWsdlImportExtension` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="b8e12-229">`ImportEndpoint` Metoda importuje adres z portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="b8e12-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="b8e12-230">Dodanie obsługi zasad</span><span class="sxs-lookup"><span data-stu-id="b8e12-230">Adding Policy Support</span></span>  
 <span data-ttu-id="b8e12-231">Element niestandardowego powiązania, można wyeksportować asercji zasad Powiązanie WSDL dla punktu końcowego usługi do wyrażenia możliwości tego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8e12-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="b8e12-232">Eksportowanie zasad</span><span class="sxs-lookup"><span data-stu-id="b8e12-232">Policy Export</span></span>  
 <span data-ttu-id="b8e12-233">`UdpTransportBindingElement` Typ implementuje `IPolicyExportExtension` się Dodaj pomoc techniczna dotycząca eksportowania zasad.</span><span class="sxs-lookup"><span data-stu-id="b8e12-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="b8e12-234">W rezultacie `System.ServiceModel.MetadataExporter` obejmuje `UdpTransportBindingElement` podczas generowania zasady dla powiązania zawierający go.</span><span class="sxs-lookup"><span data-stu-id="b8e12-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="b8e12-235">W `IPolicyExportExtension.ExportPolicy`, możemy dodać potwierdzenia dla protokołów UDP i innym potwierdzenie, jeśli firma Microsoft w trybie multiemisji.</span><span class="sxs-lookup"><span data-stu-id="b8e12-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="b8e12-236">Jest to spowodowane ma wpływ tryb multiemisji jak stos komunikacji jest tworzony i dlatego musi być koordynowane między obie strony.</span><span class="sxs-lookup"><span data-stu-id="b8e12-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="b8e12-237">Ponieważ elementy powiązania transportu niestandardowego jest odpowiedzialny za obsługę adresowania, `IPolicyExportExtension` implementacji na `UdpTransportBindingElement` muszą również obsługiwać eksportowania odpowiednie WS-Addressing asercji zasad do wskazania wersji WS-Addressing jest używane.</span><span class="sxs-lookup"><span data-stu-id="b8e12-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="b8e12-238">Importuj zasady</span><span class="sxs-lookup"><span data-stu-id="b8e12-238">Policy Import</span></span>  
 <span data-ttu-id="b8e12-239">Aby rozszerzyć system zaimportować zasad, firma Microsoft Dodaj następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="b8e12-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="b8e12-240">Następnie wdrożymy `IPolicyImporterExtension` z naszych zarejestrowanych klasy (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="b8e12-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="b8e12-241">W `ImportPolicy()`, firma Microsoft za pośrednictwem potwierdzenia w naszych przestrzeni nazw i przetwarzać te generowania transportu i sprawdź, czy jest multiemisji.</span><span class="sxs-lookup"><span data-stu-id="b8e12-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="b8e12-242">Możemy również usunąć potwierdzenia, które będziemy obsługiwać z listy powiązania potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="b8e12-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="b8e12-243">Ponownie uruchamiając Svcutil.exe, dostępne są dwie opcje integracji:</span><span class="sxs-lookup"><span data-stu-id="b8e12-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="b8e12-244">Punkt Svcutil.exe do naszego pliku konfiguracji, za pomocą /SvcutilConfig:\<pliku >.</span><span class="sxs-lookup"><span data-stu-id="b8e12-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="b8e12-245">Dodaj sekcję konfiguracji do Svcutil.exe.config, w tym samym katalogu co Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="b8e12-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="b8e12-246">Dodawanie standardowych powiązania</span><span class="sxs-lookup"><span data-stu-id="b8e12-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="b8e12-247">Nasz element powiązania może służyć w następujących dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="b8e12-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="b8e12-248">Za pośrednictwem powiązania niestandardowego: Powiązanie niestandardowe umożliwia użytkownikowi tworzenie własnych powiązania na podstawie dowolnego zestawu elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="b8e12-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="b8e12-249">Za pomocą powiązania dostarczane przez system obejmuje to nasz element powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8e12-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="b8e12-250">WCF udostępnia wiele z tych powiązań zdefiniowanych przez system, takie jak `BasicHttpBinding`, `NetTcpBinding`, i `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="b8e12-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="b8e12-251">Każda z tych powiązań jest skojarzona z profilem dobrze zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="b8e12-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="b8e12-252">Przykład implementuje powiązanie profilu w `SampleProfileUdpBinding`, która jest pochodną <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="b8e12-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="b8e12-253">`SampleProfileUdpBinding` Zawiera maksymalnie cztery elementy powiązania w niej: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, i `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="b8e12-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="b8e12-254">Dodawanie niestandardowych standardowego powiązanie importera</span><span class="sxs-lookup"><span data-stu-id="b8e12-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="b8e12-255">Svcutil.exe i `WsdlImporter` typu domyślnie, rozpoznaje i importuje powiązań zdefiniowanych przez system.</span><span class="sxs-lookup"><span data-stu-id="b8e12-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="b8e12-256">W przeciwnym razie powiązanie pobiera importowane jako `CustomBinding` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b8e12-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="b8e12-257">Aby włączyć Svcutil.exe i `WsdlImporter` do zaimportowania `SampleProfileUdpBinding` `UdpBindingElementImporter` działa również jako importera niestandardowego powiązania standardowych.</span><span class="sxs-lookup"><span data-stu-id="b8e12-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="b8e12-258">Implementuje importera niestandardowego powiązania standardowa `ImportEndpoint` metody `IWsdlImportExtension` interfejsu do sprawdzenia `CustomBinding` wystąpienia zaimportowane z metadanych, aby zobaczyć, czy może on zostać wygenerowane przez określone powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="b8e12-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="b8e12-259">Ogólnie rzecz biorąc Implementowanie importera niestandardowego powiązania standardowa polega na sprawdzeniu właściwości elementów wiązania zaimportowanych, aby sprawdzić, czy tylko właściwości, które można ustawić przez powiązanie standardowe zostały zmienione, a wszystkie pozostałe właściwości są ich wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="b8e12-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="b8e12-260">Podstawowe strategii wykonywania importera Powiązanie standardowe jest utworzenie wystąpienia standard powiązania Propagacja powiązania właściwości z elementy powiązania wystąpienie Powiązanie standardowe, które obsługuje standardowe powiązania w celu porównania elementy wiązania standardowa elementami importowanych powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8e12-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="b8e12-261">Dodanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b8e12-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="b8e12-262">Aby udostępnić naszym transportu za pomocą konfiguracji, musimy zaimplementować dwie sekcje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b8e12-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="b8e12-263">Pierwsza to `BindingElementExtensionElement` dla `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="b8e12-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="b8e12-264">Jest to tak, aby `CustomBinding` implementacji może odwoływać się do naszych element powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8e12-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="b8e12-265">Drugi to `Configuration` dla naszych `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="b8e12-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="b8e12-266">Element rozszerzenia elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="b8e12-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="b8e12-267">Sekcja `UdpTransportElement` jest `BindingElementExtensionElement` który uwidacznia `UdpTransportBindingElement` systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b8e12-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="b8e12-268">Za pomocą kilku podstawowych zastąpień definiujemy naszych nazwa sekcji konfiguracji, typ nasz element powiązania oraz sposób tworzenia nasz element powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8e12-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="b8e12-269">Firma Microsoft można zarejestrować naszej sekcji rozszerzeń w pliku konfiguracji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b8e12-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="b8e12-270">Rozszerzenia mogą być przywoływane z powiązań niestandardowych, aby używać protokołu UDP transportu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="binding-section"></a><span data-ttu-id="b8e12-271">Sekcja powiązania</span><span class="sxs-lookup"><span data-stu-id="b8e12-271">Binding Section</span></span>  
 <span data-ttu-id="b8e12-272">Sekcja `SampleProfileUdpBindingCollectionElement` jest `StandardBindingCollectionElement` który uwidacznia `SampleProfileUdpBinding` systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b8e12-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="b8e12-273">Duża część wykonania jest delegowane do `SampleProfileUdpBindingConfigurationElement`, która jest pochodną `StandardBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="b8e12-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="b8e12-274">`SampleProfileUdpBindingConfigurationElement` Ma właściwości, które odnoszą się do właściwości `SampleProfileUdpBinding`i funkcji do mapowania z `ConfigurationElement` powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8e12-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="b8e12-275">Na koniec Zastąp `OnApplyConfiguration` method in Class metoda naszych `SampleProfileUdpBinding`, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b8e12-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="b8e12-276">Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, można dodać następującą sekcję do pliku konfiguracji związanych z.</span><span class="sxs-lookup"><span data-stu-id="b8e12-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="b8e12-277">Go mogą następnie odwoływać się w sekcji Konfiguracja modelu serviceModel.</span><span class="sxs-lookup"><span data-stu-id="b8e12-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="b8e12-278">Usługa Test UDP i klienta</span><span class="sxs-lookup"><span data-stu-id="b8e12-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="b8e12-279">Za pomocą transportu ten przykładowy kod testu jest dostępna w katalogach UdpTestService i UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="b8e12-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="b8e12-280">Kod usługi składa się z dwóch testów — jeden test ustawia powiązania i punktów końcowych z kodu i innych zrobi to za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b8e12-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="b8e12-281">Oba testy używają dwa punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="b8e12-281">Both tests use two endpoints.</span></span> <span data-ttu-id="b8e12-282">Jeden punkt końcowy korzysta z `SampleUdpProfileBinding` z [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) równa `true`.</span><span class="sxs-lookup"><span data-stu-id="b8e12-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="b8e12-283">Inny punkt końcowy korzysta z niestandardowego powiązania za pomocą `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="b8e12-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="b8e12-284">Jest to równoważne użyciu `SampleUdpProfileBinding` z [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) równa `false`.</span><span class="sxs-lookup"><span data-stu-id="b8e12-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="b8e12-285">Oba testy utworzyć usługę, Dodaj punkt końcowy dla każdego powiązania, otwórz usługę i zaczekaj, aż użytkownikowi przed zamknięciem usługi naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="b8e12-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="b8e12-286">Po uruchomieniu aplikacji testowej usługi powinny pojawić się następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="b8e12-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="b8e12-287">Następnie można uruchomić aplikacji klienckiej testu względem opublikowanych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="b8e12-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="b8e12-288">Aplikacja testowa klienta tworzy klienta dla każdego punktu końcowego i wysyła pięć wiadomości do każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b8e12-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="b8e12-289">Następujące dane wyjściowe to na kliencie.</span><span class="sxs-lookup"><span data-stu-id="b8e12-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="b8e12-290">Poniżej przedstawiono pełne dane wyjściowe w usłudze.</span><span class="sxs-lookup"><span data-stu-id="b8e12-290">The following is the full output on the service.</span></span>  
  
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
  
 <span data-ttu-id="b8e12-291">Aby uruchomić aplikacji klienckiej względem punktów końcowych opublikowanych przy użyciu konfiguracji, naciśnij klawisz ENTER w usłudze, a następnie ponownie uruchom klienta testowego.</span><span class="sxs-lookup"><span data-stu-id="b8e12-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="b8e12-292">Następujące dane wyjściowe powinny być widoczne w usłudze.</span><span class="sxs-lookup"><span data-stu-id="b8e12-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="b8e12-293">Ponowne uruchomienie klienta daje takie same jak w poprzednim.</span><span class="sxs-lookup"><span data-stu-id="b8e12-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="b8e12-294">Aby ponownie wygenerować kod klienta i konfiguracji za pomocą Svcutil.exe, uruchamiania aplikacji usługi, a następnie uruchom następujące Svcutil.exe z katalogu głównego przykładowego.</span><span class="sxs-lookup"><span data-stu-id="b8e12-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="b8e12-295">Należy pamiętać, Svcutil.exe nie generuje konfigurację rozszerzenia powiązania `SampleProfileUdpBinding`, dlatego należy je dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="b8e12-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8e12-296">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="b8e12-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b8e12-297">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8e12-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="b8e12-298">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8e12-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b8e12-299">Zapoznaj się z poprzedniej sekcji "UDP testu i klienta usługi".</span><span class="sxs-lookup"><span data-stu-id="b8e12-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8e12-300">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b8e12-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8e12-301">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b8e12-301">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8e12-302">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="b8e12-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8e12-303">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b8e12-303">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
