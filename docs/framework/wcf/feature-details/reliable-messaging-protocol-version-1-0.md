---
title: Reliable Messaging Protocol w wersji 1.0
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d204600682ec8acbc229240c4e1bc859d8ea4d21
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="a7094-102">Reliable Messaging Protocol w wersji 1.0</span><span class="sxs-lookup"><span data-stu-id="a7094-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="a7094-103">W tym temacie omówiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WS-Reliable Messaging szczegóły implementacji protokołu niezbędne do współpracy przy użyciu transportu HTTP February 2005 (w wersji 1.0).</span><span class="sxs-lookup"><span data-stu-id="a7094-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-104">zgodny ze specyfikacją WS-Reliable Messaging z ograniczeniami i wyjaśnienia opisanego w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="a7094-104"> follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="a7094-105">Należy pamiętać, protokół WS-ReliableMessaging w wersji 1.0 jest zaimplementowana, począwszy od [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7094-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="a7094-106">WS-Reliable Messaging February 2005 protokół jest zaimplementowana w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="a7094-106">The WS-Reliable Messaging February 2005 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="a7094-107">Dla wygody tematu są używane następujące role:</span><span class="sxs-lookup"><span data-stu-id="a7094-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="a7094-108">Inicjator: klienta, który inicjuje tworzenia sekwencji WS-Reliable wiadomości</span><span class="sxs-lookup"><span data-stu-id="a7094-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="a7094-109">Obiekt odpowiadający w trybie: usługa, która odbiera żądania inicjatora</span><span class="sxs-lookup"><span data-stu-id="a7094-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="a7094-110">Ten dokument używa prefiksy i przestrzenie nazw w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a7094-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="a7094-111">Prefiks</span><span class="sxs-lookup"><span data-stu-id="a7094-111">Prefix</span></span>|<span data-ttu-id="a7094-112">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="a7094-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="a7094-113">Menedżer zasobów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a7094-113">wsrm</span></span>|<span data-ttu-id="a7094-114">http://schemas.xmlsoap.org/ws/2005/02/RM</span><span class="sxs-lookup"><span data-stu-id="a7094-114">http://schemas.xmlsoap.org/ws/2005/02/rm</span></span>|  
|<span data-ttu-id="a7094-115">netrm</span><span class="sxs-lookup"><span data-stu-id="a7094-115">netrm</span></span>|<span data-ttu-id="a7094-116">http://schemas.microsoft.com/ws/2006/05/RM</span><span class="sxs-lookup"><span data-stu-id="a7094-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="a7094-117">s</span><span class="sxs-lookup"><span data-stu-id="a7094-117">s</span></span>|<span data-ttu-id="a7094-118">http://www.w3.org/2003/05/SOAP-Envelope</span><span class="sxs-lookup"><span data-stu-id="a7094-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="a7094-119">wsa</span><span class="sxs-lookup"><span data-stu-id="a7094-119">wsa</span></span>|<span data-ttu-id="a7094-120">http://schemas.xmlsoap.org/ws/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="a7094-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="a7094-121">wsse</span><span class="sxs-lookup"><span data-stu-id="a7094-121">wsse</span></span>|<span data-ttu-id="a7094-122">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="a7094-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="a7094-123">Obsługa wiadomości</span><span class="sxs-lookup"><span data-stu-id="a7094-123">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="a7094-124">Komunikaty ustanowienia sekwencji</span><span class="sxs-lookup"><span data-stu-id="a7094-124">Sequence Establishment Messages</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-125">implementuje `CreateSequence` i `CreateSequenceResponse` komunikaty, aby ustanowić sekwencji niezawodny komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a7094-125"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="a7094-126">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="a7094-126">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="a7094-127">B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora nie generuje opcjonalny element wygasa w `CreateSequence` wiadomości lub, w przypadku gdy `CreateSequence` komunikat zawiera `Offer` element, opcjonalny `Expires` element w `Offer` element.</span><span class="sxs-lookup"><span data-stu-id="a7094-127">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="a7094-128">B1102: Podczas uzyskiwania dostępu do `CreateSequence` wiadomości, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `Responder` wysyła i odbiera zarówno `Expires` elementu, jeśli istnieje, ale nie używa ich wartości.</span><span class="sxs-lookup"><span data-stu-id="a7094-128">B1102: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="a7094-129">WS-Reliable Messaging wprowadza `Offer` mechanizmu ustanowienie dwa konwersacji skorelowane sekwencji, które tworzą sesji.</span><span class="sxs-lookup"><span data-stu-id="a7094-129">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="a7094-130">R1103: Jeśli `CreateSequence` zawiera `Offer` elementu niezawodnej obsługi komunikatów udzielenia musi zaakceptować sekwencji oraz odpowiadać, podając `CreateSequenceResponse` zawierający `wsrm:Accept` element tworzące dwa skorelowane konwersacji sekwencji lub odrzucić `CreateSequence` żądania.</span><span class="sxs-lookup"><span data-stu-id="a7094-130">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="a7094-131">R1104: `SequenceAcknowledgement` i komunikatów aplikacji przepływu w kolejności odwrotnej musi zostać wysłany do `ReplyTo` odwołania do punktu końcowego z `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="a7094-131">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="a7094-132">R1105: `AcksTo` i `ReplyTo` odwołania do punktu końcowego w `CreateSequence` musi mieć wartości adresów, które odpowiadają octet-wise.</span><span class="sxs-lookup"><span data-stu-id="a7094-132">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="a7094-133">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie sprawdza, czy identyfikator URI części `AcksTo` i `ReplyTo` określenia opcji są identyczne, przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-133">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="a7094-134">R1106: `AcksTo` i `ReplyTo` odwołania do punktu końcowego w `CreateSequence` powinny mieć ten sam zestaw parametrów odwołania.</span><span class="sxs-lookup"><span data-stu-id="a7094-134">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-135">nie wymusza, ale przyjęto założenie, że [Odwołanie parametry] `AcksTo` i `ReplyTo` na `CreateSequence` są identyczne i używa [Odwołanie parametrów] z `ReplyTo` odwołania do punktu końcowego dla potwierdzeń i odwrotnej sekwencji komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a7094-135"> does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="a7094-136">R1107: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `SequenceAcknowledgement` i przechodzenia w odwrotnej sekwencji komunikatów aplikacji musi zostać wysłany do `ReplyTo` odwołania do punktu końcowego z `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="a7094-136">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="a7094-137">R1108: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą mechanizmu oferta `[address]` właściwość `wsrm:AcksTo` odwołania do punktu końcowego elementu podrzędnego `wsrm:Accept` elementu `CreateSequenceResponse` musi odpowiadać byte-wise docelowego identyfikatora URI z `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="a7094-137">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="a7094-138">R1109: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, komunikaty wysyłane przez inicjatora i potwierdzeń wiadomości przez obiekt odpowiadający w trybie muszą zostać przesłane do odwołania do tego samego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a7094-138">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-139">używa WS-Reliable Messaging ustanowienie sesji niezawodnej między Inicjator i obiekt odpowiadający w trybie.</span><span class="sxs-lookup"><span data-stu-id="a7094-139"> uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-140">w implementacji protokołu WS-Reliable Messaging zapewnia niezawodnej sesji dla jednokierunkowe żądanie odpowiedź i pełny dupleks wzorców do obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a7094-140">'s WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="a7094-141">WS-Reliable Messaging `Offer` mechanizmu na `CreateSequence` / `CreateSequenceResponse` pozwala ustanowić dwóch sekwencji skorelowane odwrotnej i zapewnia protokół sesji, które jest odpowiednie dla wszystkich komunikatów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a7094-141">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="a7094-142">Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia gwarancję zabezpieczeń takich sesji w tym end-to-end ochronę integralności sesji, jest to możliwe zapewnienie komunikaty kierowane do tej samej strony docierają tego samego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="a7094-142">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="a7094-143">Umożliwia to także piggy zapasowy potwierdzeń sekwencji komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7094-143">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="a7094-144">W związku z tym ograniczenia R1104, R1105 i R1108 dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7094-144">Therefore, constraints R1104, R1105, and R1108 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="a7094-145">Przykład `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-145">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="a7094-146">Przykład `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-146">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="sequence"></a><span data-ttu-id="a7094-147">Sekwencja</span><span class="sxs-lookup"><span data-stu-id="a7094-147">Sequence</span></span>  
 <span data-ttu-id="a7094-148">Oto lista ograniczeń, które są stosowane do sekwencji:</span><span class="sxs-lookup"><span data-stu-id="a7094-148">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="a7094-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje i uzyskuje dostęp do numerów sekwencji. nie jest wyższa niż `xs:long`przez wartość maksymalna włącznie, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="a7094-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="a7094-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawsze generuje zabudowanych pusta ostatniego komunikatu z akcją http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="a7094-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates an empty-bodied last message with the action URI of http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
-   <span data-ttu-id="a7094-151">B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odbiera, a następnie dostarcza wiadomość z nagłówkiem sekwencji, który zawiera `LastMessage` tak długo, jak identyfikator URI akcji nie jest http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage elementu.</span><span class="sxs-lookup"><span data-stu-id="a7094-151">B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
 <span data-ttu-id="a7094-152">Przykład nagłówka sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-152">An example of a Sequence Header.</span></span>  
  
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
  
### <a name="ackrequested-header"></a><span data-ttu-id="a7094-153">Nagłówek AckRequested</span><span class="sxs-lookup"><span data-stu-id="a7094-153">AckRequested Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-154">używa `AckRequested` nagłówka jako mechanizmu keep-alive.</span><span class="sxs-lookup"><span data-stu-id="a7094-154"> uses `AckRequested` Header as a keep-alive mechanism.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-155">nie generuje opcjonalny `MessageNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="a7094-155"> does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="a7094-156">Po otrzymaniu wiadomości z `AckRequested` nagłówek, który zawiera `MessageNumber` elementu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignoruje `MessageNumber` wartości elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7094-156">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="a7094-157">Nagłówka SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="a7094-157">SequenceAcknowledgement Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-158">używa mechanizmu nakładka — dla potwierdzeń sekwencji w WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="a7094-158"> uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="a7094-159">R1401: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `SequenceAcknowledgement` nagłówka może być zawarta w każdej wiadomości aplikacji przesyłane do określonego adresata.</span><span class="sxs-lookup"><span data-stu-id="a7094-159">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="a7094-160">B1402: Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] należy wygenerować potwierdzenia przed odebraniem komunikaty sekwencji (na przykład, aby spełniać `AckRequested` wiadomości), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `SequenceAcknowledgement` nagłówka, który zawiera zakres 0-0, jak pokazano w następującym przykład.</span><span class="sxs-lookup"><span data-stu-id="a7094-160">B1402: When [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="a7094-161">B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie generuje `SequenceAcknowledgement` nagłówki, które zawierają `Nack` elementu, ale obsługuje `Nack` elementów.</span><span class="sxs-lookup"><span data-stu-id="a7094-161">B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="a7094-162">Błędy protokołu WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="a7094-162">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="a7094-163">Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementacji protokołu WS-Reliable Messaging błędów:</span><span class="sxs-lookup"><span data-stu-id="a7094-163">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="a7094-164">B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie generuje `MessageNumberRollover` błędów.</span><span class="sxs-lookup"><span data-stu-id="a7094-164">B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="a7094-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego może generować `CreateSequenceRefused` błędów zgodnie z opisem w specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="a7094-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="a7094-166">B1503:when punktu końcowego usługi przez nią miejsce osiągnie limit liczby połączeń i nie może przetworzyć nowe połączenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje dodatkowe `CreateSequenceRefused` fault podrzędny, `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7094-166">B1503:When the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="a7094-167">Protokół WS-Addressing błędów</span><span class="sxs-lookup"><span data-stu-id="a7094-167">WS-Addressing Faults</span></span>  
 <span data-ttu-id="a7094-168">Ponieważ WS-Reliable Messaging korzysta z protokołu WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementacji protokołu WS-Reliable Messaging może generować błędy protokołu WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="a7094-168">Because WS-Reliable Messaging uses WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="a7094-169">Ta obejmuje sekcji WS-Addressing błędów, które [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje jawnie w warstwie usługi WS-Reliable Messaging:</span><span class="sxs-lookup"><span data-stu-id="a7094-169">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="a7094-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje błędów komunikat adresowania nagłówka wymagane, gdy jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a7094-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="a7094-171">Brak komunikatu `Sequence` nagłówka i `Action` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="a7094-171">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="a7094-172">A `CreateSequence` Brak komunikatu `MessageId` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="a7094-172">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="a7094-173">A `CreateSequence` Brak komunikatu `ReplyTo` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="a7094-173">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="a7094-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje błąd akcja nie jest obsługiwana w odpowiedzi na komunikat, który nie istnieje `Sequence` nagłówka i ma `Action` nagłówek, który nie jest rozpoznawaną w specyfikacji WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="a7094-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="a7094-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje błąd punktu końcowego niedostępne, co wskazuje, czy punkt końcowy nie może przetwarzać sekwencji ustalane na podstawie analizy `CreateSequence` nagłówków adresowych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="a7094-176">Protokół kompozycji</span><span class="sxs-lookup"><span data-stu-id="a7094-176">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="a7094-177">Kompozycja z protokołu WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="a7094-177">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-178">obsługuje protokół WS-Addressing dwie wersje: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing 1.0 zalecenia [WS-ADDR-CORE] i [WS-ADDR — SOAP].</span><span class="sxs-lookup"><span data-stu-id="a7094-178"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="a7094-179">Podczas uwagi specyfikacji WS-Reliable Messaging tylko WS-Addressing 2004-08 nie uniemożliwia wersji WS-Addressing do użycia.</span><span class="sxs-lookup"><span data-stu-id="a7094-179">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="a7094-180">Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a7094-180">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="a7094-181">R2101: zarówno WS-Addressing 2004/08 i WS-Addressing 1.0 mogą być używane z WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="a7094-181">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="a7094-182">R2102:A jednej wersji WS-Addressing musi używanego w danej sekwencji WS-Reliable Messaging dysków lub para skorelowane przy użyciu sekwencji odwrotnej `wsrm:Offer` mechanizmu.</span><span class="sxs-lookup"><span data-stu-id="a7094-182">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="a7094-183">Kompozycja z protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="a7094-183">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-184">obsługuje stosowanie SOAP 1.1 i SOAP 1.2 z WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="a7094-184"> supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="a7094-185">Kompozycja i WS-Security WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="a7094-185">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-186">zapewnia ochronę sekwencji WS-Reliable Messaging przy użyciu zabezpieczenia WS konwersacji bezpieczne transportowych (HTTPS), kompozycji z WS-Security i kompozycji.</span><span class="sxs-lookup"><span data-stu-id="a7094-186"> provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="a7094-187">Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a7094-187">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="a7094-188">R2301: ochrony integralności sekwencji WS-Reliable Messaging oprócz integralności i poufności poszczególne wiadomości [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymaga, należy użyć zabezpieczenia WS konwersacji.</span><span class="sxs-lookup"><span data-stu-id="a7094-188">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="a7094-189">R2302:AWS-Secure Conversation sesji muszą być ustalane przed ustanawianie sequence(s) WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="a7094-189">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="a7094-190">R2303: Jeśli WS-Reliable Messaging sekwencji okres istnienia przekracza zabezpieczenia WS konwersacji istnienia sesji `SecurityContextToken` ustanowione przy użyciu zabezpieczenia WS konwersacji należy odnawiać przy użyciu odpowiedniego powiązania odnawiania zabezpieczenia WS konwersacji.</span><span class="sxs-lookup"><span data-stu-id="a7094-190">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="a7094-191">B2304:ws-niezawodna obsługa komunikatów sekwencji dysków lub para skorelowane odwrotnej sekwencje są zawsze powiązane z jednej sesji WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="a7094-191">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="a7094-192">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Źródło generuje `wsse:SecurityTokenReference` element w sekcji rozszerzeń element `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-192">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="a7094-193">R2305:when składa się z zabezpieczenia WS konwersacji `CreateSequence` wiadomości musi zawierać `wsse:SecurityTokenReference` elementu.</span><span class="sxs-lookup"><span data-stu-id="a7094-193">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="a7094-194">WS-Reliable potwierdzenia obsługi wiadomości WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="a7094-194">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-195">używa usługi WS-Reliable Messaging potwierdzenia WS-Policy `wsrm:RMAssertion` do opisywania możliwości punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a7094-195"> uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="a7094-196">Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a7094-196">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="a7094-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dołącza `wsrm:RMAssertion` WS-Policy potwierdzenia do `wsdl:binding` elementów.</span><span class="sxs-lookup"><span data-stu-id="a7094-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-198">obsługuje zarówno załączników do `wsdl:binding` i `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="a7094-198"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="a7094-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje następujące właściwości opcjonalne WS-Reliable Messaging potwierdzenia i zapewnia kontrolę nad nimi na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="a7094-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="a7094-200">Poniżej przedstawiono przykład.</span><span class="sxs-lookup"><span data-stu-id="a7094-200">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="a7094-201">Rozszerzenie obsługi wiadomości WS-Reliable sterowania przepływem</span><span class="sxs-lookup"><span data-stu-id="a7094-201">Flow Control WS-Reliable Messaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-202">używa WS-Reliable Messaging rozszerzalności, aby zapewnić opcjonalne dodatkowe zwiększenie poziomu kontrolę nad przepływ komunikatów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-202"> uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="a7094-203">Przez ustawienie włączone jest sterowanie przepływem `ReliableSessionBindingElement`w `FlowControlEnabled``bool` właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="a7094-203">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``bool` property to `true`.</span></span> <span data-ttu-id="a7094-204">Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a7094-204">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="a7094-205">B4001: Podczas kontroli przepływu komunikatów niezawodnej jest włączona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` elementu w element możliwość rozszerzania `SequenceAcknowledgement` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="a7094-205">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="a7094-206">B4002: Podczas kontroli przepływu komunikatów niezawodnej jest włączona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie wymaga `netrm:BufferRemaining` element znajdować się w `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7094-206">B4002: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="a7094-207">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa `netrm:BufferRemaining` można buforu wskazująca, ile nowe komunikaty niezawodnej obsługi komunikatów docelowego.</span><span class="sxs-lookup"><span data-stu-id="a7094-207">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="a7094-208">B4004: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niezawodnej obsługi komunikatów usługi ogranicza liczbę wiadomości przesyłane, gdy aplikację docelową niezawodnej obsługi komunikatów nie może szybko odbierać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-208">B4004:The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="a7094-209">Komunikaty niezawodnej obsługi komunikatów buforów docelowego i wartości elementu spadnie do 0.</span><span class="sxs-lookup"><span data-stu-id="a7094-209">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="a7094-210">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` liczby całkowitej wartości z zakresu od 0 do 4096 włącznie i odczytuje wartości Liczba całkowita między 0 a `xs:int`w `maxInclusive` wartość 214748364 włącznie.</span><span class="sxs-lookup"><span data-stu-id="a7094-210">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="a7094-211">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="a7094-211">Message Exchange Patterns</span></span>  
 <span data-ttu-id="a7094-212">W tej sekcji opisano [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tego zachowania, gdy WS-Reliable Messaging służy do różnych wzorców wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-212">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="a7094-213">Dla każdego wymiany komunikatów w następujących scenariuszach dwa wdrożenia są traktowane jako:</span><span class="sxs-lookup"><span data-stu-id="a7094-213">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="a7094-214">Inicjator nie rozpozna: Inicjator znajduje się za zaporą; Obiekt odpowiadający w trybie wiadomości mogą być dostarczane do inicjatora tylko na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7094-214">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="a7094-215">Inicjator adresowanego: Inicjator i obiekt odpowiadający mogą być wysyłane żądania HTTP; innymi słowy można ustanowić dwa połączenia HTTP odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="a7094-215">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="a7094-216">Jednokierunkowe, nie mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="a7094-216">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="a7094-217">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="a7094-217">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-218">udostępnia jednokierunkowe wymiany komunikatów przy użyciu jednej sekwencji przez jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7094-218"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-219">używa żądania HTTP do przekazywania wszystkie komunikaty z usług RMS RMD i odpowiedzi HTTP do przekazywania wszystkich komunikatów z RMD RMS.</span><span class="sxs-lookup"><span data-stu-id="a7094-219"> uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="a7094-220">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="a7094-220">CreateSequence Exchange</span></span>  
 <span data-ttu-id="a7094-221">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generuje inicjatora `CreateSequence` wiadomości z żadne oferty.</span><span class="sxs-lookup"><span data-stu-id="a7094-221">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="a7094-222">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma żadne oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-222">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="a7094-223">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie odpowiada `CreateSequence` żądania z `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-223">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="a7094-224">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="a7094-224">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="a7094-225">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Inicjatora przetwarza potwierdzenia w odpowiedzi wszystkie komunikaty z wyjątkiem `CreateSequence` komunikat i komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="a7094-225">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="a7094-226">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie zawsze generuje autonomicznej potwierdzenia w odpowiedzi na oba sekwencji i `AckRequested` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-226">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="a7094-227">Komunikat TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="a7094-227">TerminateSequence message</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-228">traktuje `TerminateSequence` jako Operacja jednokierunkowa, co oznacza odpowiedzi HTTP ma pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="a7094-228"> treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="a7094-229">Jednym ze sposobów, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="a7094-229">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="a7094-230">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="a7094-230">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-231">udostępnia jednokierunkowe wymiany komunikatów przy użyciu jednej sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanału Http.</span><span class="sxs-lookup"><span data-stu-id="a7094-231"> provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-232">używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-232"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="a7094-233">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="a7094-233">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="a7094-234">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="a7094-234">CreateSequence Exchange</span></span>  
 <span data-ttu-id="a7094-235">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generuje inicjatora `CreateSequence` wiadomości z żadne oferty.</span><span class="sxs-lookup"><span data-stu-id="a7094-235">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="a7094-236">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma żadne oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-236">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="a7094-237">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła obiektu odpowiadającego w trybie `CreateSequenceResponse` wiadomości na żądanie HTTP skierowane z `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a7094-237">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="a7094-238">Dupleks, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="a7094-238">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="a7094-239">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="a7094-239">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-240">udostępnia pełni asynchroniczne dwukierunkowe wymiany komunikatów za pomocą dwóch sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanału HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7094-240"> provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-241">używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-241"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="a7094-242">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="a7094-242">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="a7094-243">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="a7094-243">CreateSequence Exchange</span></span>  
 <span data-ttu-id="a7094-244">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generuje inicjatora `CreateSequence` wiadomości z ofertą.</span><span class="sxs-lookup"><span data-stu-id="a7094-244">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="a7094-245">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-245">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-246">wysyła `CreateSequenceResponse` na żądanie HTTP skierowane do `CreateSequence`w `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a7094-246"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="a7094-247">Okres istnienia sekwencji</span><span class="sxs-lookup"><span data-stu-id="a7094-247">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-248">traktuje dwóch sekwencji jako jedna sesja pełni dupleksowych.</span><span class="sxs-lookup"><span data-stu-id="a7094-248"> treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="a7094-249">Podczas generowania błędów, które błędów jedną sekwencję [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oczekuje, że zdalny punkt końcowy do obu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-249">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="a7094-250">Podczas odczytywania usterek, które błędów jedną sekwencję [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] błędów zarówno sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-250">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-251">Zamknij jego sekwencji wychodzących i dalsze przetwarzanie komunikatów na jego przychodzących sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-251"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="a7094-252">Z drugiej strony [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] można przetwarzać zamknięcia sekwencji dla ruchu przychodzącego i kontynuować wysyłanie wiadomości na jego wychodzące sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-252">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="a7094-253">Żądanie odpowiedź, nie mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="a7094-253">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="a7094-254">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="a7094-254">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-255">zapewnia możliwość jednokierunkowych i żądanie odpowiedź wymiany komunikatów za pomocą dwóch sekwencji ponad jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7094-255"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-256">korzysta z żądania HTTP do przekazywania wiadomości sekwencji żądań, a odpowiedzi HTTP do przekazywania komunikatów sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a7094-256"> uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="a7094-257">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="a7094-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="a7094-258">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generuje inicjatora `CreateSequence` wiadomości z ofertą.</span><span class="sxs-lookup"><span data-stu-id="a7094-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="a7094-259">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-259">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="a7094-260">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie odpowiada `CreateSequence` żądania z `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-260">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="a7094-261">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="a7094-261">One-way Message</span></span>  
 <span data-ttu-id="a7094-262">Protokół wymiany komunikat jednokierunkowy pomyślnego wykonania, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora przesyła żądanie komunikatu sekwencji na żądania HTTP i odbiera autonomiczny `SequenceAcknowledgement` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7094-262">To complete a one-way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="a7094-263">`SequenceAcknowledgement` Musi potwierdzić wiadomości przesyłane.</span><span class="sxs-lookup"><span data-stu-id="a7094-263">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="a7094-264">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie może odpowiedzieć na żądanie z potwierdzeniem, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="a7094-264">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="a7094-265">Dwa komunikaty sposób</span><span class="sxs-lookup"><span data-stu-id="a7094-265">Two Way Messages</span></span>  
 <span data-ttu-id="a7094-266">Pomyślnie protokół exchange dwukierunkowej wiadomości, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora przesyła żądanie komunikatu sekwencji na żądania HTTP i odbierania komunikatu sekwencji odpowiedzi na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7094-266">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="a7094-267">Odpowiedzi muszą oni nosić przy sobie `SequenceAcknowledgement` potwierdzeniem wiadomość sekwencji żądanie przesyłane.</span><span class="sxs-lookup"><span data-stu-id="a7094-267">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="a7094-268">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie może odpowiedzieć na żądanie z odpowiedzi aplikacji, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="a7094-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="a7094-269">Z powodu obecności jednokierunkowe komunikaty i czas odpowiedzi aplikacji numer sekwencyjny komunikatu sekwencji żądania i numer sekwencyjny komunikatu odpowiedzi mają nie korelacji.</span><span class="sxs-lookup"><span data-stu-id="a7094-269">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="a7094-270">Ponawianie próby odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="a7094-270">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-271">zależy od korelacja żądań i odpowiedzi HTTP dla korelacji protokół exchange dwukierunkowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-271"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="a7094-272">W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora nie zatrzymuje ponowieniem próby wykonania żądania komunikatu sekwencji żądanie sekwencji komunikat zostaje potwierdzony, ale raczej po, odpowiedź HTTP niesie potwierdzenia, komunikat użytkownika lub fault.</span><span class="sxs-lookup"><span data-stu-id="a7094-272">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="a7094-273">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie ponowi próbę odpowiedzi na etap żądania HTTP żądania, do której są korelowane z odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a7094-273">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="a7094-274">LastMessage programu Exchange</span><span class="sxs-lookup"><span data-stu-id="a7094-274">LastMessage Exchange</span></span>  
 <span data-ttu-id="a7094-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Inicjatora generuje i przesyła pusty zabudowanego ostatniego komunikatu w gałęzi żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7094-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-276">wymaga odpowiedzi, ale ignoruje komunikat odpowiedzi rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="a7094-276"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="a7094-277">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie odpowiada sekwencji żądań zabudowanych pusta ostatniego komunikatu o zabudowanych pusta ostatnią wiadomość w sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a7094-277">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="a7094-278">Jeśli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ostatniego komunikatu, w którym Akcja identyfikator URI nie jest http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, otrzymuje obiekt odpowiadający w trybie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odpowiedzi z ostatniego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a7094-278">If the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder receives a last message in which the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] replies with a last message.</span></span> <span data-ttu-id="a7094-279">W przypadku protokołu exchange dwukierunkowej wiadomości ostatniego komunikatu niesie komunikat aplikacji; w przypadku protokołu exchange komunikat jednokierunkowy ostatniego komunikatu jest pusta.</span><span class="sxs-lookup"><span data-stu-id="a7094-279">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="a7094-280">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie nie wymaga potwierdzenia do zabudowanych pusta ostatnią wiadomość w sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a7094-280">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="a7094-281">TerminateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="a7094-281">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="a7094-282">Gdy wszystkie żądania otrzymali prawidłowy odpowiedzi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora generuje i przesyła sekwencji żądań `TerminateSequence` wiadomości na etap żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7094-282">When all requests have received a valid reply, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-283">wymaga odpowiedzi, ale ignoruje komunikat odpowiedzi rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="a7094-283"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="a7094-284">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie odpowiada sekwencji żądań `TerminateSequence` wiadomość sekwencji odpowiedzi `TerminateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-284">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="a7094-285">W normalnych zamykania zarówno `TerminateSequence` pełny zakres przenoszenia wiadomości `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="a7094-285">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="a7094-286">Żądanie/odpowiedź, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="a7094-286">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="a7094-287">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="a7094-287">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-288">udostępnia wymiany komunikatów żądanie odpowiedź przy użyciu dwóch sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanału HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7094-288"> provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-289">używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7094-289"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="a7094-290">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="a7094-290">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="a7094-291">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="a7094-291">CreateSequence Exchange</span></span>  
 <span data-ttu-id="a7094-292">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Generuje inicjatora `CreateSequence` wiadomości z ofertą.</span><span class="sxs-lookup"><span data-stu-id="a7094-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="a7094-293">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7094-293">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7094-294">wysyła `CreateSequenceResponse` na żądanie HTTP skierowane do `CreateSequence`w `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a7094-294"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="a7094-295">Żądanie i odpowiedź korelacji</span><span class="sxs-lookup"><span data-stu-id="a7094-295">Request/Reply Correlation</span></span>  
 <span data-ttu-id="a7094-296">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Inicjatora zapewnia wszystkie posiadają komunikaty żądania aplikacji `MessageId` i `ReplyTo` odwołanie do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a7094-296">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="a7094-297">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Stosuje inicjatora `CreateSequence` komunikatu `ReplyTo` odwołanie do punktu końcowego na każdy komunikat żądania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7094-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="a7094-298">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie wymaga tego żądania przychodzące komunikaty opatrzone `MessageId` i `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="a7094-298">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="a7094-299">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie zapewnia, że identyfikator URI odwołania do punktu końcowego obu `CreateSequence` i wszystkie komunikaty żądania aplikacji są identyczne.</span><span class="sxs-lookup"><span data-stu-id="a7094-299">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
