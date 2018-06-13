---
title: Reliable Messaging Protocol w wersji 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: f45a0d5e50e9ab8a07a203d2c40ad36ef298a40d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497055"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="1a8c9-102">Reliable Messaging Protocol w wersji 1.0</span><span class="sxs-lookup"><span data-stu-id="1a8c9-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="1a8c9-103">W tym temacie omówiono szczegóły implementacji usługi Windows Communication Foundation (WCF) dla protokołu WS-Reliable Messaging protocol February 2005 (w wersji 1.0) niezbędne do współpracy przy użyciu protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="1a8c9-104">Usługi WCF jest zgodna ze specyfikacją WS-Reliable Messaging z ograniczeniami i wyjaśnienia opisanego w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="1a8c9-105">Należy pamiętać, protokół WS-ReliableMessaging w wersji 1.0 jest zaimplementowana, począwszy od [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a8c9-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="1a8c9-106">WS-Reliable Messaging February 2005 protokół jest zaimplementowana w programie WCF przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="1a8c9-107">Dla wygody tematu są używane następujące role:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="1a8c9-108">Inicjator: klienta, który inicjuje tworzenia sekwencji WS-Reliable wiadomości</span><span class="sxs-lookup"><span data-stu-id="1a8c9-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="1a8c9-109">Obiekt odpowiadający w trybie: usługa, która odbiera żądania inicjatora</span><span class="sxs-lookup"><span data-stu-id="1a8c9-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="1a8c9-110">Ten dokument używa prefiksy i przestrzenie nazw w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="1a8c9-111">Prefiks</span><span class="sxs-lookup"><span data-stu-id="1a8c9-111">Prefix</span></span>|<span data-ttu-id="1a8c9-112">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="1a8c9-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="1a8c9-113">Menedżer zasobów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1a8c9-113">wsrm</span></span>|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|<span data-ttu-id="1a8c9-114">netrm</span><span class="sxs-lookup"><span data-stu-id="1a8c9-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="1a8c9-115">s</span><span class="sxs-lookup"><span data-stu-id="1a8c9-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="1a8c9-116">wsa</span><span class="sxs-lookup"><span data-stu-id="1a8c9-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="1a8c9-117">wsse</span><span class="sxs-lookup"><span data-stu-id="1a8c9-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a><span data-ttu-id="1a8c9-118">Obsługa wiadomości</span><span class="sxs-lookup"><span data-stu-id="1a8c9-118">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="1a8c9-119">Komunikaty ustanowienia sekwencji</span><span class="sxs-lookup"><span data-stu-id="1a8c9-119">Sequence Establishment Messages</span></span>  
 <span data-ttu-id="1a8c9-120">Implementuje WCF `CreateSequence` i `CreateSequenceResponse` komunikaty, aby ustanowić sekwencji niezawodny komunikatu.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="1a8c9-121">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-121">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="1a8c9-122">B1101: Inicjator WCF nie generuje opcjonalny element wygasa w `CreateSequence` wiadomości lub w przypadkach podczas `CreateSequence` komunikat zawiera `Offer` element, opcjonalny `Expires` element w `Offer` elementu.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="1a8c9-123">B1102: Podczas uzyskiwania dostępu do `CreateSequence` komunikatów usługi WCF`Responder` wysyła i odbiera zarówno `Expires` elementu, jeśli istnieje, ale nie używa ich wartości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="1a8c9-124">WS-Reliable Messaging wprowadza `Offer` mechanizmu ustanowienie dwa konwersacji skorelowane sekwencji, które tworzą sesji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="1a8c9-125">R1103: Jeśli `CreateSequence` zawiera `Offer` elementu niezawodnej obsługi komunikatów udzielenia musi zaakceptować sekwencji oraz odpowiadać, podając `CreateSequenceResponse` zawierający `wsrm:Accept` element tworzące dwa skorelowane konwersacji sekwencji lub odrzucić `CreateSequence` żądania.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="1a8c9-126">R1104: `SequenceAcknowledgement` i komunikatów aplikacji przepływu w kolejności odwrotnej musi zostać wysłany do `ReplyTo` odwołania do punktu końcowego z `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="1a8c9-127">R1105: `AcksTo` i `ReplyTo` odwołania do punktu końcowego w `CreateSequence` musi mieć wartości adresów, które odpowiadają octet-wise.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="1a8c9-128">Obiekt odpowiadający w trybie WCF sprawdza, czy identyfikator URI części `AcksTo` i `ReplyTo` określenia opcji są identyczne, przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="1a8c9-129">R1106: `AcksTo` i `ReplyTo` odwołania do punktu końcowego w `CreateSequence` powinny mieć ten sam zestaw parametrów odwołania.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     <span data-ttu-id="1a8c9-130">WCF nie wymusza jednak przyjęto założenie, że [Odwołanie parametry] `AcksTo` i `ReplyTo` na `CreateSequence` są identyczne i używa [Odwołanie parametrów] z `ReplyTo` odwołania do punktu końcowego dla potwierdzeń i odwrotnej sekwencji komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="1a8c9-131">R1107: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `SequenceAcknowledgement` i przechodzenia w odwrotnej sekwencji komunikatów aplikacji musi zostać wysłany do `ReplyTo` odwołania do punktu końcowego z `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="1a8c9-132">R1108: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą mechanizmu oferta `[address]` właściwość `wsrm:AcksTo` odwołania do punktu końcowego elementu podrzędnego `wsrm:Accept` elementu `CreateSequenceResponse` musi odpowiadać byte-wise docelowego identyfikatora URI z `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="1a8c9-133">R1109: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, komunikaty wysyłane przez inicjatora i potwierdzeń wiadomości przez obiekt odpowiadający w trybie muszą zostać przesłane do odwołania do tego samego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     <span data-ttu-id="1a8c9-134">WCF używa do nawiązywania niezawodnych sesji między Inicjator i obiekt odpowiadający WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="1a8c9-135">Implementacja protokołu WS-Reliable Messaging WCF w zapewnia niezawodnej sesji dla jednokierunkowe żądanie odpowiedź i pełny dupleks wzorców do obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="1a8c9-136">WS-Reliable Messaging `Offer` mechanizmu na `CreateSequence` / `CreateSequenceResponse` pozwala ustanowić dwóch sekwencji skorelowane odwrotnej i zapewnia protokół sesji, które jest odpowiednie dla wszystkich komunikatów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="1a8c9-137">Ponieważ WCF zapewnia gwarancję zabezpieczeń dla sesji, w tym na trasie ochronę integralności sesji, jest praktyczne upewnij się, że komunikaty kierowane do tej samej strony docierają tego samego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="1a8c9-138">Umożliwia to także piggy zapasowy potwierdzeń sekwencji komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="1a8c9-139">W związku z tym ograniczenia R1104, R1105 i R1108 dotyczą WCF.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>  
  
 <span data-ttu-id="1a8c9-140">Przykład `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-140">An example of a `CreateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence  
    </a:Action>  
    <a:ReplyTo>  
      <a:Address>          
         http://Business456.com/clientA        
      </a:Address>  
    </a:ReplyTo>  
    <a:MessageID>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:MessageID>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
       <wsa:Address>  
         http://Business456.com/clientA  
       </wsa:Address>  
     </wsrm:AcksTo>  
     <wsrm:Offer>  
      <wsrm:Identifier>  
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496  
      </wsrm:Identifier>  
     </wsrm:Offer>  
   </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="1a8c9-141">Przykład `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-141">An example of a `CreateSequenceResponse` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse  
    </a:Action>  
    <a:RelatesTo>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:RelatesTo>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
   <wsrm:CreateSequenceResponse>  
    <Identifier>  
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386  
    </Identifier>  
    <Accept>  
    <AcksTo>  
      <a:Address>  
        http://BusinessABC.com/serviceA  
      </a:Address>  
    </AcksTo>  
    </Accept>  
   </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence"></a><span data-ttu-id="1a8c9-142">Sekwencja</span><span class="sxs-lookup"><span data-stu-id="1a8c9-142">Sequence</span></span>  
 <span data-ttu-id="1a8c9-143">Oto lista ograniczeń, które są stosowane do sekwencji:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-143">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="1a8c9-144">Generuje B1201:WCF i uzyskuje dostęp do sekwencji liczb nie jest wyższa niż `xs:long`na maksymalną wartość z wartościami granicznymi 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="1a8c9-145">B1202:WCF zawsze generuje zabudowanych pusta ostatniego komunikatu z akcją identyfikatora URI z http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-145">B1202:WCF always generates an empty-bodied last message with the action URI of http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
-   <span data-ttu-id="1a8c9-146">B1203: WCF odbiera, a następnie dostarcza wiadomość z nagłówkiem sekwencji, który zawiera `LastMessage` tak długo, jak akcja identyfikator URI nie jest element http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
 <span data-ttu-id="1a8c9-147">Przykład nagłówka sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-147">An example of a Sequence Header.</span></span>  
  
```xml  
<wsrm:Sequence>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
  <wsrm:MessageNumber>  
    10  
  </wsrm:MessageNumber>  
  <wsrm:LastMessage/>  
 </wsrm:Sequence>  
```  
  
### <a name="ackrequested-header"></a><span data-ttu-id="1a8c9-148">Nagłówek AckRequested</span><span class="sxs-lookup"><span data-stu-id="1a8c9-148">AckRequested Header</span></span>  
 <span data-ttu-id="1a8c9-149">Używa WCF `AckRequested` nagłówka jako mechanizmu keep-alive.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="1a8c9-150">Usługi WCF nie generuje opcjonalny `MessageNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="1a8c9-151">Po otrzymaniu wiadomości z `AckRequested` nagłówek, który zawiera `MessageNumber` ignoruje WCF elementu `MessageNumber` wartości elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="1a8c9-152">Nagłówka SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="1a8c9-152">SequenceAcknowledgement Header</span></span>  
 <span data-ttu-id="1a8c9-153">Usługi WCF używa mechanizmu nakładka — dla potwierdzeń sekwencji w WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="1a8c9-154">R1401: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `SequenceAcknowledgement` nagłówka może być zawarta w każdej wiadomości aplikacji przesyłane do określonego adresata.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="1a8c9-155">B1402: Gdy WCF należy wygenerować potwierdzenia przed odebraniem komunikaty sekwencji (na przykład, aby spełniać `AckRequested` wiadomości), generuje WCF `SequenceAcknowledgement` nagłówek, który zawiera zakres 0-0, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="1a8c9-156">B1403: Usługi WCF nie generuje `SequenceAcknowledgement` nagłówki, które zawierają `Nack` elementu, ale obsługuje `Nack` elementów.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="1a8c9-157">Błędy protokołu WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-157">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="1a8c9-158">Poniżej przedstawiono listę ograniczenia, które dotyczą implementacji WCF WS-Reliable Messaging błędów:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="1a8c9-159">B1501: Usługi WCF nie generuje `MessageNumberRollover` błędów.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="1a8c9-160">Punkt końcowy B1502:WCF może generować `CreateSequenceRefused` błędów zgodnie z opisem w specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="1a8c9-161">B1503:when punktu końcowego usługi przez nią miejsce osiągnie limit liczby połączeń i nie może przetworzyć nowe połączenia, generuje dodatkowe WCF `CreateSequenceRefused` fault podrzędny, `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
    ```xml  
    <s:Envelope>  
      <s:Header>  
        <wsa:Action>  
          http://schemas.xmlsoap.org/ws/2005/08/addressing/fault  
        </wsa:Action>  
      </s:Header>  
      <s:Body>  
        <s:Fault>  
          <s:Code>  
            <s:Value>  
              s:Receiver  
            </s:Value>  
            <s:Subcode>  
              <s:Value>  
                wsrm:CreateSequenceRefused  
              </s:Value>  
              <s:Subcode>  
                <s:Value>  
                  netrm:ConnectionLimitReached  
                </s:Value>  
              </s:Subcode>  
            </s:Subcode>  
          </s:Code>  
          <s:Reason>  
            <s:Text xml:lang="en">  
              [Reason]  
            </s:Text>  
          </s:Reason>  
        </s:Fault>  
      </s:Body>  
    </s:Envelope>  
    ```  
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="1a8c9-162">Protokół WS-Addressing błędów</span><span class="sxs-lookup"><span data-stu-id="1a8c9-162">WS-Addressing Faults</span></span>  
 <span data-ttu-id="1a8c9-163">Ponieważ WS-Reliable Messaging korzysta z protokołu WS-Addressing, implementacja protokołu WS-Reliable Messaging WCF może generować błędy protokołu WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="1a8c9-164">W tej sekcji omówiono WS-Addressing usterek, które WCF jawnie generuje w warstwie usługi WS-Reliable Messaging:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="1a8c9-165">B1601:WCF generuje błędów komunikat adresowania wymaganego nagłówka, gdy spełniony jest jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="1a8c9-166">Brak komunikatu `Sequence` nagłówka i `Action` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-166">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="1a8c9-167">A `CreateSequence` Brak komunikatu `MessageId` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="1a8c9-168">A `CreateSequence` Brak komunikatu `ReplyTo` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="1a8c9-169">B1602:WCF generuje błąd akcja nie jest obsługiwana w odpowiedzi na komunikat, który nie istnieje `Sequence` nagłówka i ma `Action` nagłówek, który nie jest rozpoznawaną w specyfikacji WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="1a8c9-170">B1603:WCF generuje błąd punktu końcowego niedostępne, co wskazuje, czy punkt końcowy nie może przetwarzać sekwencji ustalane na podstawie analizy `CreateSequence` nagłówków adresowych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="1a8c9-171">Protokół kompozycji</span><span class="sxs-lookup"><span data-stu-id="1a8c9-171">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="1a8c9-172">Kompozycja z protokołu WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="1a8c9-172">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="1a8c9-173">Usługi WCF obsługuje dwie wersje usługi WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing 1.0 zalecenia [WS-ADDR-CORE] i [WS-ADDR — SOAP].</span><span class="sxs-lookup"><span data-stu-id="1a8c9-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="1a8c9-174">Podczas uwagi specyfikacji WS-Reliable Messaging tylko WS-Addressing 2004-08 nie uniemożliwia wersji WS-Addressing do użycia.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="1a8c9-175">Oto lista ograniczeń, które są stosowane do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-175">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="1a8c9-176">R2101: zarówno WS-Addressing 2004/08 i WS-Addressing 1.0 mogą być używane z WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="1a8c9-177">R2102:A jednej wersji WS-Addressing musi używanego w danej sekwencji WS-Reliable Messaging dysków lub para skorelowane przy użyciu sekwencji odwrotnej `wsrm:Offer` mechanizmu.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="1a8c9-178">Kompozycja z protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="1a8c9-178">Composition with SOAP</span></span>  
 <span data-ttu-id="1a8c9-179">Usługi WCF obsługuje przy użyciu protokołu SOAP 1.1 i SOAP 1.2 z WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="1a8c9-180">Kompozycja i WS-Security WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="1a8c9-180">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="1a8c9-181">Usługi WCF zapewnia ochronę sekwencji WS-Reliable Messaging przy użyciu zabezpieczenia WS konwersacji bezpieczne transportowych (HTTPS), kompozycji z WS-Security i kompozycji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="1a8c9-182">Oto lista ograniczeń, które są stosowane do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-182">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="1a8c9-183">R2301: Aby chronić integralność sekwencji WS-Reliable Messaging oprócz integralności i poufności poszczególne wiadomości, WCF wymaga, należy użyć zabezpieczenia WS konwersacji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="1a8c9-184">R2302:AWS-Secure Conversation sesji muszą być ustalane przed ustanawianie sequence(s) WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="1a8c9-185">R2303: Jeśli WS-Reliable Messaging sekwencji okres istnienia przekracza zabezpieczenia WS konwersacji istnienia sesji `SecurityContextToken` ustanowione przy użyciu zabezpieczenia WS konwersacji należy odnawiać przy użyciu odpowiedniego powiązania odnawiania zabezpieczenia WS konwersacji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="1a8c9-186">B2304:ws-niezawodna obsługa komunikatów sekwencji dysków lub para skorelowane odwrotnej sekwencje są zawsze powiązane z jednej sesji WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="1a8c9-187">Źródło WCF generuje `wsse:SecurityTokenReference` element w sekcji rozszerzeń element `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="1a8c9-188">R2305:when składa się z zabezpieczenia WS konwersacji `CreateSequence` wiadomości musi zawierać `wsse:SecurityTokenReference` elementu.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="1a8c9-189">WS-Reliable potwierdzenia obsługi wiadomości WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-189">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="1a8c9-190">Usługi WCF używa protokołu WS-Reliable Messaging potwierdzenia WS-Policy `wsrm:RMAssertion` do opisywania możliwości punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="1a8c9-191">Oto lista ograniczeń, które są stosowane do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-191">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="1a8c9-192">B3001: Dołącza WCF `wsrm:RMAssertion` WS-Policy potwierdzenia do `wsdl:binding` elementów.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="1a8c9-193">Usługi WCF obsługuje zarówno załączników do `wsdl:binding` i `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="1a8c9-194">B3002: Obsługuje następujące właściwości opcjonalne WS-Reliable Messaging potwierdzenia WCF i zapewnia kontrolę nad nimi na usługi WCF`ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="1a8c9-195">Poniżej przedstawiono przykład.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-195">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="1a8c9-196">Rozszerzenie obsługi wiadomości WS-Reliable sterowania przepływem</span><span class="sxs-lookup"><span data-stu-id="1a8c9-196">Flow Control WS-Reliable Messaging Extension</span></span>  
 <span data-ttu-id="1a8c9-197">Usługi WCF używa WS-Reliable Messaging rozszerzalności, aby zapewnić opcjonalne dodatkowe zwiększenie poziomu kontrolę nad przepływ komunikatów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="1a8c9-198">Przez ustawienie włączone jest sterowanie przepływem `ReliableSessionBindingElement`w `FlowControlEnabled``bool` właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-198">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``bool` property to `true`.</span></span> <span data-ttu-id="1a8c9-199">Oto lista ograniczeń, które są stosowane do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-199">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="1a8c9-200">B4001: Po włączeniu niezawodnej obsługi komunikatów sterowanie przepływem WCF generuje `netrm:BufferRemaining` elementu w element możliwość rozszerzania `SequenceAcknowledgement` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="1a8c9-201">B4002: Po włączeniu niezawodnej obsługi komunikatów sterowanie przepływem WCF nie wymaga `netrm:BufferRemaining` element znajdować się w `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        http://fabrikam123.com/abc  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>  
        8  
      </netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="1a8c9-202">B4003: Używa WCF `netrm:BufferRemaining` można buforu wskazująca, ile nowe komunikaty niezawodnej obsługi komunikatów docelowego.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="1a8c9-203">B4004: niezawodnej obsługi komunikatów usługi WCF ogranicza liczbę wiadomości przesyłane, gdy aplikację docelową niezawodnej obsługi komunikatów nie może szybko odbierać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="1a8c9-204">Komunikaty niezawodnej obsługi komunikatów buforów docelowego i wartości elementu spadnie do 0.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="1a8c9-205">B4005: Generuje WCF `netrm:BufferRemaining` liczby całkowitej wartości z zakresu od 0 do 4096 włącznie i odczytuje wartości Liczba całkowita między 0 a `xs:int`w `maxInclusive` wartość 214748364 włącznie.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="1a8c9-206">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="1a8c9-206">Message Exchange Patterns</span></span>  
 <span data-ttu-id="1a8c9-207">W tej sekcji opisano zachowanie WCF w przypadku WS-Reliable Messaging służy do różnych wzorców wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="1a8c9-208">Dla każdego wymiany komunikatów w następujących scenariuszach dwa wdrożenia są traktowane jako:</span><span class="sxs-lookup"><span data-stu-id="1a8c9-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="1a8c9-209">Inicjator nie rozpozna: Inicjator znajduje się za zaporą; Obiekt odpowiadający w trybie wiadomości mogą być dostarczane do inicjatora tylko na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="1a8c9-210">Inicjator adresowanego: Inicjator i obiekt odpowiadający mogą być wysyłane żądania HTTP; innymi słowy można ustanowić dwa połączenia HTTP odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="1a8c9-211">Jednokierunkowe, nie mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="1a8c9-211">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="1a8c9-212">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="1a8c9-212">Binding</span></span>  
 <span data-ttu-id="1a8c9-213">Usługi WCF zawiera jednokierunkowe wymiany komunikatów przy użyciu jednej sekwencji przez jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="1a8c9-214">Usługi WCF używa żądania HTTP do przesyłania wszystkie komunikaty z usług RMS RMD i odpowiedzi HTTP do przekazywania wszystkich komunikatów z RMD RMS.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="1a8c9-215">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="1a8c9-215">CreateSequence Exchange</span></span>  
 <span data-ttu-id="1a8c9-216">Generuje inicjatora WCF `CreateSequence` wiadomości z żadne oferty.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="1a8c9-217">Obiekt odpowiadający w trybie WCF zapewnia `CreateSequence` ma żadne oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="1a8c9-218">Obiekt odpowiadający w trybie WCF odpowiada `CreateSequence` żądania z `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="1a8c9-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="1a8c9-219">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="1a8c9-220">Inicjator WCF przetwarza potwierdzenia w odpowiedzi wszystkie komunikaty z wyjątkiem `CreateSequence` komunikat i komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="1a8c9-221">Obiekt odpowiadający w trybie WCF zawsze generuje autonomicznej potwierdzenia w odpowiedzi na oba sekwencji i `AckRequested` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="1a8c9-222">Komunikat TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="1a8c9-222">TerminateSequence message</span></span>  
 <span data-ttu-id="1a8c9-223">Traktuje WCF `TerminateSequence` jako Operacja jednokierunkowa, co oznacza odpowiedzi HTTP ma pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="1a8c9-224">Jednym ze sposobów, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="1a8c9-224">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="1a8c9-225">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="1a8c9-225">Binding</span></span>  
 <span data-ttu-id="1a8c9-226">Usługi WCF zawiera jednokierunkowe wymiany komunikatów przy użyciu jednej sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanału Http.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="1a8c9-227">WCF używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="1a8c9-228">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="1a8c9-229">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="1a8c9-229">CreateSequence Exchange</span></span>  
 <span data-ttu-id="1a8c9-230">Generuje inicjatora WCF `CreateSequence` wiadomości z żadne oferty.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="1a8c9-231">Obiekt odpowiadający w trybie WCF upewnia się, że `CreateSequence` ma żadne oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="1a8c9-232">Obiekt odpowiadający w trybie WCF przesyła `CreateSequenceResponse` wiadomości na żądanie HTTP skierowane z `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="1a8c9-233">Dupleks, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="1a8c9-233">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="1a8c9-234">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="1a8c9-234">Binding</span></span>  
 <span data-ttu-id="1a8c9-235">Usługi WCF zawiera pełni asynchroniczne dwukierunkowe wymiany komunikatów za pomocą dwóch sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanału HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="1a8c9-236">WCF używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="1a8c9-237">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="1a8c9-238">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="1a8c9-238">CreateSequence Exchange</span></span>  
 <span data-ttu-id="1a8c9-239">Generuje inicjatora WCF `CreateSequence` wiadomości z ofertą.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="1a8c9-240">Obiekt odpowiadający w trybie WCF upewnia się, że `CreateSequence` ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="1a8c9-241">Wysyła WCF `CreateSequenceResponse` na żądanie HTTP skierowane do `CreateSequence`w `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="1a8c9-242">Okres istnienia sekwencji</span><span class="sxs-lookup"><span data-stu-id="1a8c9-242">Sequence Lifetime</span></span>  
 <span data-ttu-id="1a8c9-243">Usługi WCF traktuje dwóch sekwencji jako jedna sesja pełni dupleksowych.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-243">WCF treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="1a8c9-244">Podczas generowania błędów, które błędów jedną sekwencję, WCF oczekuje, że zdalny punkt końcowy do obu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="1a8c9-245">Podczas odczytywania usterek, które błędów jedną sekwencję, WCF błędów zarówno sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="1a8c9-246">WCF można zamknąć ich wychodzącego sekwencji i dalsze przetwarzanie komunikatów na jego przychodzących sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="1a8c9-247">Z drugiej strony WCF można przetwarzać zamknięcia sekwencji dla ruchu przychodzącego i kontynuować wysyłanie wiadomości na jego wychodzące sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="1a8c9-248">Żądanie odpowiedź, nie mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="1a8c9-248">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="1a8c9-249">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="1a8c9-249">Binding</span></span>  
 <span data-ttu-id="1a8c9-250">Usługi WCF zapewnia jednokierunkowe i żądanie odpowiedź wymiany komunikatów za pomocą dwóch sekwencji ponad jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="1a8c9-251">Usługi WCF korzysta żądania HTTP do przekazywania wiadomości sekwencji żądań, a odpowiedzi HTTP do przekazywania komunikatów sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="1a8c9-252">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="1a8c9-252">CreateSequence Exchange</span></span>  
 <span data-ttu-id="1a8c9-253">Generuje inicjatora WCF `CreateSequence` wiadomości z ofertą.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="1a8c9-254">Obiekt odpowiadający w trybie WCF upewnia się, że `CreateSequence` ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="1a8c9-255">Obiekt odpowiadający w trybie WCF odpowiada `CreateSequence` żądania z `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="1a8c9-256">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="1a8c9-256">One-way Message</span></span>  
 <span data-ttu-id="1a8c9-257">Pomyślnie protokół wymiany komunikat jednokierunkowy, inicjator WCF przesyła żądanie komunikatu sekwencji na żądania HTTP i odbiera autonomiczny `SequenceAcknowledgement` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="1a8c9-258">`SequenceAcknowledgement` Musi potwierdzić wiadomości przesyłane.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="1a8c9-259">Obiekt odpowiadający w trybie WCF można odpowiedzieć na żądanie z potwierdzeniem, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="1a8c9-260">Dwa komunikaty sposób</span><span class="sxs-lookup"><span data-stu-id="1a8c9-260">Two Way Messages</span></span>  
 <span data-ttu-id="1a8c9-261">Pomyślnie protokół exchange dwukierunkowej wiadomości, inicjator WCF przesyła żądanie komunikatu sekwencji na żądania HTTP i odbiera odpowiedź komunikatu sekwencji odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="1a8c9-262">Odpowiedzi muszą oni nosić przy sobie `SequenceAcknowledgement` potwierdzeniem wiadomość sekwencji żądanie przesyłane.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="1a8c9-263">Obiekt odpowiadający w trybie WCF może odpowiedzieć na żądanie z odpowiedzi aplikacji, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="1a8c9-264">Z powodu obecności jednokierunkowe komunikaty i czas odpowiedzi aplikacji numer sekwencyjny komunikatu sekwencji żądania i numer sekwencyjny komunikatu odpowiedzi mają nie korelacji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="1a8c9-265">Ponawianie próby odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="1a8c9-265">Retrying Replies</span></span>  
 <span data-ttu-id="1a8c9-266">Usługi WCF zależy od korelacja żądań i odpowiedzi HTTP dla korelacji protokół exchange dwukierunkowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="1a8c9-267">W związku z tym inicjatora WCF nie zatrzymuje ponawianie próby komunikatu sekwencji żądania, gdy wiadomość sekwencji żądanie zostało potwierdzone, a raczej odpowiedź HTTP niesie potwierdzenia, komunikat użytkownika lub fault.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="1a8c9-268">Obiekt odpowiadający w trybie WCF ponowi próbę odpowiedzi na etap żądania HTTP żądania, do której są korelowane z odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="1a8c9-269">LastMessage programu Exchange</span><span class="sxs-lookup"><span data-stu-id="1a8c9-269">LastMessage Exchange</span></span>  
 <span data-ttu-id="1a8c9-270">Inicjator WCF generuje i przesyła pusty zabudowanego ostatniego komunikatu w gałęzi żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="1a8c9-271">Usługi WCF wymaga odpowiedzi, ale ignoruje komunikat odpowiedzi rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="1a8c9-272">Obiekt odpowiadający w trybie WCF odpowiedzi sekwencji żądań zabudowanych pusta ostatniego komunikatu o zabudowanych pusta ostatnią wiadomość w sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="1a8c9-273">Jeśli obiekt odpowiadający w trybie WCF odbiera ostatniego komunikatu, w którym Akcja identyfikator URI nie jest http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, WCF odpowiedzi z ostatniego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-273">If the WCF Responder receives a last message in which the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, WCF replies with a last message.</span></span> <span data-ttu-id="1a8c9-274">W przypadku protokołu exchange dwukierunkowej wiadomości ostatniego komunikatu niesie komunikat aplikacji; w przypadku protokołu exchange komunikat jednokierunkowy ostatniego komunikatu jest pusta.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="1a8c9-275">Obiekt odpowiadający w trybie usługi WCF nie wymaga potwierdzenia do zabudowanych pusta ostatnią wiadomość w sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="1a8c9-276">TerminateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="1a8c9-276">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="1a8c9-277">Gdy wszystkie żądania otrzymał prawidłowy odpowiedzi inicjatora WCF generuje i przesyła sekwencji żądań `TerminateSequence` wiadomości na etap żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="1a8c9-278">Usługi WCF wymaga odpowiedzi, ale ignoruje komunikat odpowiedzi rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="1a8c9-279">Obiekt odpowiadający w trybie WCF odpowiada sekwencji żądań `TerminateSequence` wiadomość sekwencji odpowiedzi `TerminateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="1a8c9-280">W normalnych zamykania zarówno `TerminateSequence` pełny zakres przenoszenia wiadomości `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="1a8c9-281">Żądanie/odpowiedź, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="1a8c9-281">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="1a8c9-282">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="1a8c9-282">Binding</span></span>  
 <span data-ttu-id="1a8c9-283">Usługi WCF zawiera wymiany komunikatów żądanie odpowiedź przy użyciu dwóch sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanału HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="1a8c9-284">WCF używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="1a8c9-285">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="1a8c9-286">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="1a8c9-286">CreateSequence Exchange</span></span>  
 <span data-ttu-id="1a8c9-287">Generuje inicjatora WCF `CreateSequence` wiadomości z ofertą.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="1a8c9-288">Obiekt odpowiadający w trybie WCF upewnia się, że `CreateSequence` ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="1a8c9-289">Wysyła WCF `CreateSequenceResponse` na żądanie HTTP skierowane do `CreateSequence`w `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="1a8c9-290">Żądanie i odpowiedź korelacji</span><span class="sxs-lookup"><span data-stu-id="1a8c9-290">Request/Reply Correlation</span></span>  
 <span data-ttu-id="1a8c9-291">Inicjator WCF zapewnia wszystkie posiadają komunikaty żądania aplikacji `MessageId` i `ReplyTo` odwołanie do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="1a8c9-292">Stosuje inicjatora WCF `CreateSequence` komunikatu `ReplyTo` odwołanie do punktu końcowego na każdy komunikat żądania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="1a8c9-293">Obiekt odpowiadający w trybie WCF wymaga tego żądania przychodzące komunikaty opatrzone `MessageId` i `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="1a8c9-294">Obiekt odpowiadający w trybie WCF zapewnia, że identyfikator URI odwołania do punktu końcowego obu `CreateSequence` i wszystkie komunikaty żądania aplikacji są identyczne.</span><span class="sxs-lookup"><span data-stu-id="1a8c9-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
